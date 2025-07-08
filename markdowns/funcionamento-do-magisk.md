# funcionamento do magisk

Send the boot.img file to the smatphone with command: "adb push boot.img /storage/Download".

Open Magisk APK and update boot.img. Then use the command "adb pull /storage/Download/magiskboot.img" to get the updated version of boot.img.

Basically, magisk receives the official boot.img or ramdisk (initramfs) file as input and modifies it, returning as output a new version of boot.img/ramdisk with binaries and scripts added to provide root access, through an "overlay" technique that makes it possible to modify the system without altering critical partitions such as /system /vendor among others. In this way, magisk's approach becomes "systemless", that is, it does not modify the real system, but only a mounted copy of it.

Magisk internal details: https://topjohnwu.github.io/Magisk/details.html
https://android.stackexchange.com/questions/213167/how-does-magisk-work

Official Docs:
https://github.com/topjohnwu/Magisk/tree/master/docs
https://magisk.readthedocs.io/en/latest/developers/internaldetails.html

Vantagens e desvantagens do magisk.
Mostrar formas de entender como o magisk funciona: Desempacotar o boot.img original e o do magisk, e comparar eles.
Explorar debug_ramdisk e /data/adb.
Ler documentação oficial, usar binários do magisk, analisar o comportamento dele em tempo real e processo.
Ler init.rc.

Para entender melhor isso, é necessário saber que o magisk pode definir à inicialização do init magisk de 2 maneiras diferentes, dependendo do dispositivo.

SELinux é o subsistema de segurança do kernel Linux, ele implementa o conceito de segurança obrigatoria MAC (Mandatory Access Control).
Esse vai além do modelo tradicional de segurança linux, baseado em permissões, grupos e usuários.

Geralmente o init do magisk é iniciado com o PID 1, e dependendo da forma de como a SEPolicies do sistema é organizada, o magisk vai configurar ele  de maneira diferente, podendo levar o init_secod_stage (init original) a ser PID 1.

A inicialização do init do magisk pode ser realizada de 2 formas:
O init original poder ser modificado para redirecionar e executar o init customizado do magisk.

O magisk substitui o init original pelo magiskinit, ele faz todo processo necessário como configurar SEPolicies, criar overlays, adicionarseus scripts, deamon e outros binários em init.rc (para serem executado automaticamente), para então por fim executa o init original do sistema em /system.

O magisk substitui o init original do sistema pelo init do magisk, e também adiciona alguns binários e scripts necessários. Ele é responsável por montar overlays, injetar hooks em init.rc configurar/injeta o patch do SELinux, inicia magiskd (deamon) e então inicia e transferir o controle para o init original do android.

O SELinux dita quem pode e o quê acessar no sistema, como recursos abertos e dispositivos.
Ele faz isso por meio das configurações do SEPolicies, que pode ser um arquivo compilado, ou um conjunto de arquivos.

Dependendo da forma de como o seu SELinux está organizado, o magisk escolher 2 estrategias para injetar/configurar o SEPolicies sem alterar o binário e partições originais.

Em sistema onde o SEPolicies é um único arquivo binário, o magisk precisa gerar um novo blob (arquivo binário SEPolicies) com seu próprio correação (patch), que adiciona seus próprios domínios, módulos de política etc...
Dessa forma o kernel irá carregar o SEPolicies corrigido do magisk.

O SEPolicies do magisk contém os labels ( context=u:r:magisk:s0), dóminios do magisk  configurações

Módulos de política: cada módulo (.pp ou CIL) agrupa regras para um subsistema ou app específico, Ex: (módulo para init, para o Magisk, entre outros).

Type Enforcement (TE):
É o núcleo da política, formado por:
Domínios: representam processos ou classes de processos, Ex: (init, system_server, magiskd).

Tipos de objeto: file, socket, device_file.
Atributos permitem agrupar tipos e domínios para simplificar regras.

Role-based Access Control (RBAC):
Cada domínio é associado a um papel, controlando quais domínios podem transitar para outros, ex: como system_r, untrusted_app_r, magisk_r. 

Type Transitions: Regras que definem qual domínio o processo entra quando executa certos binários, ex: executar binário "su" leva do domínio shell para o domínio shell_magisk.

File contexts: arquivo file_context mapeia caminhos de aquivo para tipos SELinux, dessa forma o kernel sabe associar contextos a cada arquivo no disco, ex: (/system/bin/* system_file).

Port, Sockets e Netif Contexts: Mapas de portas de rede para tipos de socket, e interfaces de rede para contextos.
Dessa forma, é possível controlar quais domínios podem usar quais portas ou interfaces, ex: (80 tcp_port_t).

MLS (Multi-Level) / MCS (Multi-Category Security):
MLS: define níveis (ex: s0-s15) e categorias para isolamento de dados; raramente usado em Android padrão.
MCS: variante simplificada usada por containers (cada app recebe uma categoria única).

Booleans:
Flags que podem habilitar/desabilitar grupos de regras em tempo de execução, sem recarregar, ou alterar a política inteira. Usado para cenários de debug, compatibilidade ou para módulos como o Magisk ligarem permissões adicionais.

O SELinux pode ter 2 tipos política, e o magisk lida de forma diferente em cada delas.

O init de fábrica percorre um diretorio exemplo: ("/vendor/etc/seelinux/*.cil") dessa forma, para cada arquivo, ele faz inernamente: "security_load_policy(fd, size)" para assim carregar e formar o SEPolicy completo na memória.

Essa forma fornece uma maior modularidade,
permitindo adição ou remoção de políticas de forma mais facilitada, mas permitindo o magisk implementar um hook que intercepta (via LD_PRELOAD e FIFOs em seelinuxfs) a chamada security_load_policy() para um arquivo e logo depois adicionar seu(s) próprio(s) policy.

Este é o daemon do Magisk, um serviço executado pelo "init" original do sistema por meio do arquivo "init.rc", que foi temporariamente modificado pelo "magiskinit" para inserir o comando que inicializa o daemon ("magisk --daemon").

O magisk implmenta vários métodos de overlay para poder fornecer e aplicar sua abordagem "systemless".

OverlayFS é um sistema de arquivos que permite combinar múltiplos diretórios um um sistema de arquivos virtual, que no caso irá ser um arquivo magisk.img que usa o filesystem ext4 ou ext2. Ele geralmente é usado para guardar alterações dessas partições do sistema de forma não persistente.

O magisk básicamente faz: "mount -t overlay -o lowerdir=/system,upperdir=/magisk/system,wordir=/magisk/.work overlay /system".

lowerdir representa a camada inferior, geralmente é um filesystem existente no dispositivo, como /system (partição original, read-only).
upperdir é a camada superior qualquer alteração feita será salva nela, deixando a camada inferior "/system" original intacto.
workdir é o diretório temporario exigido pelo kernel linux para operações internas do OverlayFS, como mesclar arquivos ou lidar com exclusões.
O /system no final, é o ponto de montagem usado para "exibir" o resultado das camadas combinadas.

Nesse método o magisk não utiliza OverlayFS e nem arquivo-espaço, o magisk basicamente realiza um bind-mount recursivo dos diretórios do magisk para os diretórios reais do sistema, isso significa que ele associa todas alterações que estão no seu diretório, para o diretório real do sistema, mas sem altera-lo realmente, pois as alterações só serão refletidas nos diretório reais enquanto o bind-mounts recursivo estiver ativo.

Exemplo:
mount --rbind /magisk/system/app /system/app
mount --rbind /magisk/system/lib /system/lib
Todas as alterações em /magisk/system/app serão refletidas em /system/app original, enquanto esse rbind estiver ativo.

mount --rbind /magisk/system/app /system/app
mount --rbind /magisk/system/lib /system/lib

# …para cada pasta modificada

Neste modo o init do magisk utiliza um TMPFS para criar um ambiente virtual onde as modificações serão aplicadas. Como o TMPFS é um sistema arquivos que armazena dados na RAM, as modificações serão perdidas após a reinicialização, isso torna bem seguro, mas existem suas desvantagens caso deseje que as alterações persistam.

Inicialmente, o init do magisk irá criar o tmpfs "base" usado para armazenar os scripts e binários do magisk, ex ("mount -t tmpfs magisk /debug_ramdisk" ("magisk"  é apenas um rótulo)).
Dessa forma, o /debug_ramdisk utiliza o tmpfs e se torna um ponto de montagem para armazenar dados de forma volátil na memória RAM.

O init do magisk executa:
xz -d /overlay.d/sbin/magisk.xz > /debug_ramdisk
xz -d /overlay.d/init-ld.xz > /debug_ramdisk
xz -d /overlay.d/stub.xz > /debug_ramdisk
mkdir -p /system/system_ext/bin/
xz -d /overlay.d/sbin/magisk.xz > /system/system_ext/bin/magisk
xz -d /overlay.d/init-ld.xz > /system/system_ext/bin/init-ld
xz -d /overlay.d/stub.xz > /system/system_ext/bin/stub

Assim ele pode extrair os binários para debug_ramdisk e depois fazer uma cópia deles para /system/system_ext/bin.

Após isso, o magisk possui seus binários necessários para processeguir com a inicialização do deamon e ouras configurações

Esse é responsável por gerenciar o root de forma dinâmica, comunicação com o magisk manager e aplicação de módulos e patches em runtime.

