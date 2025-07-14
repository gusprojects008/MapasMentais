# Arch linux: conceitos básicos + instalação

## Por que usar arch linux?
- Melhor entendimento do funcionamento do computador, e sistema operacional.
- Ideal para quem está estudando e começando na área da computação!
- É um software livre e código aberto para todos. Fornecendo mais transparência para quem utiliza.
- Liberdade em escolher programas e aplicações livres e de código aberto, que não coletam dados, ou, que te dá a possibilidade de escolher quais dados fornecer (Privacidade).
- Fornecendo um maior controle sobre seu sistema, o que é utilizado nele e o que você utiliza no dia a dia.
- Esses programas de código aberto, podem e são analisados por várias pessoas. E que constantemente estão em desenvolvimento, recebendo atualizações para correção de bugs e vulnerabilidades.

---

## Conceitos básicos

### Tabelas de partições
Um sistema de tabela de partições, define como um dispositivo de armazenamento gerencia e organiza as partições dele.

### Firmwares
O firmware de um dispositivo específico como um adaptador ou placa de rede wifi, é responsavel por fazer o gerenciamento e controle interno dos recursos do circuito do dispositvo, como:
- Inicialização de circuitos, micro-controladores, módulos de hardware
- Gerenciamento e modo de energia (modo de economia ou desempenho)
- Processamento de comandos vindos do driver
- Implementação de operações do protocolo 802.11 em tempo real
- Monitoramento de falhas

O firmware de uma placa mãe de um computador é o software responsável por identificar, analisar, iniciar e gerenciar o comportamento incial dos dispositivos básicos do computador, CPU, memória RAM, dispositivos I/O, dispositivos de armazenameento como: HD(Hard disk), SSD(Solid State Driver) entre outros. Fazendo a inter-comunicaçao, e controlando a distribuição de recursos entre eles, como energia e memoria.

> Em ambos os casos, ele é geralmente armazenado em um circuito integrado (chip) de memória na placa mãe, ou do circuito específico, como: ROM(Read Only Memory), PROM, EPROM ou memória flash. Mas em muitos dispositivos modernos que recebem atualizações regulares de firmware, para implementação de funcionalidades e correção de bugs, a própria fabricante fornece o(s) binário(s) do firmware do dispositivo, para assim, o próprio kernel do sistema operacional durante a inicialização, carregar eles na memória RAM ou no dispositivo em si.

É o tipo mais básico de firmware, que fornece uma interface e funcionalidades básicas para gerenciar as configurações internas do computador e seus dispositivos, assim como a inicialização deles.

Baseado primeiramente no firmware EFI, que surgiu justamente para superar as limitações do firmware BIOS. Por conta dos avanços nas capacidades dos hadwares ná época, foi necessário surgir o EFI.

Possui muitas limitações com os dispositivos existentes hoje em dia.
Ele suporta apenas dispositivos de armazenamento que utilizam o sistema de tabela de partições MBR (Master Boot Record).

Baseado primeiramente no firmware EFI, que surgiu justamente para superar as limitações do firmware BIOS. Por conta dos avanços nas capacidades dos hadwares ná época, foi necessário surgir o EFI.

O UEFI é uma extensão unificada e padronizada do EFI, baseado nas funcionalidades e capacidades do EFI.

O EFI foi projetado para utilizar o sistema de tabela de partições GPT, ideal para os dispositivos de hoje em dia, que possuem uma maior capacidade de armazenamento.

O UEFI como uma extensão do EFI, já possui recursos e funcionalidades que permitem suporte a mais dispositivos e definição de configurações específicas para eles.


Durante a instalação do Archlinux, os pacotes são instalados no partição raiz que o sistema operacional irá utilizar, por meio do pacstrap e repositorios AUR (Arch User Repository). E no pacote "base" do  repositorio AUR, irá possuir as  principais ferramentas utilizadas pelo sistema  operacional, como o gerenciador de pacotes usado no archlinux "PACMAN", usado para instalar os outros programas e pacotes dos respositorios AUR.

É uma partição usada para criar outras partições lógicas dentro dela.
Essas partições lógicas geralmente são usadas para armazenar arquivos e em alguns casos sistema operacionais. Mas que geralmente não podem ser usadas para inicializar sistema operacionais.

São partições usadas para armazenar arquivos e sistemas operacionais.
Também são partições que o firmware pode usar para incializar os sistemas operacionais, essas são as partições de bootloader.

É um sistema de tabela de partições antigo, utlizado pelo firmware BIOS.
Que funciona através da inicialização do primeiro setor de armazenamento valido para boot, conhecico como MBR, identifcado através de uma flag de boot (0x55AA). Ele armazena um pequeno código que lê a tabela de partições do MBR, e identifica a partição (VBR) ativa para transferir o controle para o setor de boot dela, e iniciar o segundo estágio de boot. Iniciando o kernel diretamente em sistema mais avançados, ou iniciando o bootloader na forma mais comum.

Dentro do setor MBR são usados 64 bytes para tabelar e definir as 4 partições do dispositivo de armazenamento, entre elas existe a ativa VBR, que o código de boot do MBR usa para transferir o controle a ela, e iniciar o sistema.

Ele é compativel e usado com firmware BIOS.
Mas possui muitas limitações comparado ao seu sucessor GPT, que surgiu exatamente para superar as limitações que tinha, como:

O setor de dispositivo de armazenamento, é o menor bloco físico de armazenamento acessível, ou melhor dizendo: a menor unidade física de armazenamento em um dispositivo.
Tendo geralmente um espaço de armazenamento de 512 bytes.

2TB por partição e apenas 4 partições primárias, ou 3 partições primárias e uma partição estendida, que pode armazenar até 63 sub-partições lógicas.

É um sistema de tabela de partições naturalmente compatível e nativa com o firmware UEFI. e GUID (Globally Unique Identifier) para as partições. Ele Funciona através de GUIDs (Globally Unique Identifier) para cada
partição.
Dessa forma, no GPT não existe os conceitos de partições estendidas ou lógicas, mas apenas primárias, pois todas possuem um identificador global único que diferencia cada uma delas no sistema de tabela de partições.
Assim, podem ser criadas 128 ou mais partições primárias, e com tamanhos de até 9.4ZT.

Como a distruibuiçao de energia entre os componentes e microcontroladores, assim como a comunicação (troca de informaçoes internas entre eles).

Por fim, o firmware é responsável por executar as operações internas (manipulando os recursos, componentes e micro-controldores no circuito) para o dispositvo executar as funções pela qual ele foi desenvolvido para fazer.

São os softwares responsáveis por definir como os dados (arquivos) serão armazenados, organizados e gerenciados em uma partição. Eles também possuem a responsabilidade de definir as informações sobre os arquivos (metadados), como data e hora de registro, permissões etc...

Muitos sistemas de arquivos oferecem várias funcionalidades como journaling paa o registro de logs de operações de leitura ou escrita em arquivos, assim dando mais segurança contra corrupção dados, e facilitando a identificação de erros.

Ao apertar o botão de Power Switch (PS), um circuito da placa mãe detecta a mudança de estado (normalmente fechando o circuito momentaneamente). Esse sinal elétrico é enviado para o chipset ou um controlador de energia da placa mãe, fazendo com que ele interprete o sinal e incie o sequenciamento de energia.

Fazendo com que os componentes sejam inicializados de forma específica e correta, para evitar danos a eles.

O controlador envia um sinal de PS_ON (Power Supply On) para a fonte de alimentação, e após o circuito da fonte de alimentação verificar a tensão, ela retorna um sinal de PG (Power Good) para o controlador, indicando a ele que é seguro iniciar o processo de inicialização e (POST (Power-On Self-test)).

Assim que o sinal PG é recebido, o controlador ou chipset libera a CPU do seu estado atual (RESET)  e assim prepara a CPU para executar o código do firmware, que está em um endereço de memória correspondente ao chip de memória onde o firmware está armazenado.

Então quando a CPU acessa e executa as instruções do firmware, é iniciado o teste de POST realizado pelo código do firmware.

É responsável por inicializar o sistema operacional na memória RAM do computador.
O bootloader pode ser armazenado em uma partição especial do dispositivo de armazenamento (HD, SSD) como partição EFI em casos de GPT/UEFI ou em setores específicos do dispositivo de armazenamento, caso utilize MBR.

São softwares, genéricos ou desenvolvidos pelos própríos fabricantes, responsáveis por realizarem a comunicação direta com o dispositivo específico, executando operações nele diretamente, ou transmitindo instruções que o firmware do dispositivo irá processar e executar no hardware em si.

ve

Ventoy

### Links e referências
    - **História da arquitetura do linux e outros sistemas operacionais baseados em Unix [Unix](https://pt.wikipedia.org/wiki/Unix)**

    - **Sistema de tabela de partições [GPT](https://www.easeus.com/images/en/screenshot/partition-manager/gpt-disk-layout.png) e [MBR](https://br.easeus.com/images/en/screenshot/partition-manager/mbr-disk-structure.png)**

    - **[Sistema de arquivos](https://pt.wikibooks.org/wiki/Sistemas_operacionais/Sistemas_de_arquivos)**

    **Memória ROM, RAM, NVRAM**
        - [ROM](https://siaguanta.com/wp-content/uploads/2019/12/rom2.png)
        - [Pendrives e cartões SD](https://miracomosehace.com/wp-content/uploads/2020/05/usb-blanco.jpg)
        - [Memória RAM](https://www.guiahardware.es/wp-content/webp-express/webp-images/uploads/2018/12/memoria-ram-1024x512.jpeg.webp)
        - [NVRAM](https://comphome.ru/wp-content/uploads/post/nvram.jpg)

    **UEFI protocols**
        - [UEFI LoadFile](https://uefi.org/specs/UEFI/2.10/13_Protocols_Media_Access.html#efi-load-file-protocol-loadfile)
        - [UEFI Block I/O](https://uefi.org/specs/UEFI/2.10/13_Protocols_Media_Access.html#block-i-o-protocol)
        - [UEFI Media Access](https://uefi.org/specs/UEFI/2.10/13_Protocols_Media_Access.html)

    **Bootloaders, initramfs.img, loopback.cfg, iso9660, GRUB2 mode**
        - https://gist.github.com/Hanaasagi/2665e1e28ffcf91d5d62f72fa52fb732/revisions
        - https://gist.github.com/Hanaasagi/2665e1e28ffcf91d5d62f72fa52fb732
        - [loopback](https://github.com/Jolicloud/grub2/blob/master/disk/loopback.c)
        - [SuperGRUB loopback.cfg](https://www.supergrubdisk.org/wiki/Loopback.cfg)
        - [GRUB2 iso9660](https://github.com/Jolicloud/grub2/blob/master/fs/iso9660.c)
        - [GRUB2 BOOT](https://www.ventoy.net/en/doc_grub2boot.html)

    **Pendrive bootavel, ventoy**
        - https://www.ventoy.net
        - https://www.ventoy.net/en/doc_disk_layout.html

O firmware identifica essas partições de boot,
por meio da leitura da estrutura de dados sobre partições do dispositivo de armazenamento, criada pelo sistema de tabela de partições (GPT, MBR etc...). Na estrutura, ele indentifica a primeira entrada de partição que possua a flag de "boot", Indicando que ela é inicializavel.

O bootloader localiza e carrega o kernel comprimido na memória RAM, transfere o controle a ele, e então, o kernel se descomprime sozinho na memória RAM, através do código de descompressão que ele carrega, conhecido como "bootstrapping code". E após ser carregado, o kernel assume o controle e inicia as operações básicas, como: alocação e gerenciamento de memória e processos, e comunicação com o hardware. Ficando responsável por carregar os drivers e módulos básicos e essenciais para carregar e iniciar o initramfs.img na mamória RAM.

E utilizar o sistema de arquivos raiz dele temporariamente, para que possa localizar, montar e iniciar o sistema de arquivos da partição raiz real e definitiva do sistema operacional "/", por meio de scripts do sistema de arquivos do initramfs.img, de montagem e inicialização da partição raiz "/", de acordo com as configurações de boot que o usuário definiu. Após a inicialização do sistema de arquivos da partição raiz, o kernel encontra e inicia o "init" do sistema, como o systemd ou Ruinit, como processo número 1 do sistema.

Através do initramfs.img configurações específicas de montagem e inicialização da partição raiz podem ser definidas. De acordo com os objetivos ou propósitos do usuário, como geralmente, a criptográfia de disco, ou configurações de rede específicas, geralmente utilizadas em servidores.

initramfs.img é um sistema de arquivos raiz  temporário carregado na memória ram, agindo como um "mini sistema operacional" que possui drivers, módulos e scripts específicos usados pelo kernel, para poder localizar, montar e inicializar o sistema de arquivos da partição raiz real do sistema operacional, de acordo com as configurações de boot que o usuário definiu para esse processo.

Esse processo torna a arquitetura do sistema operacional, mais limpa, modular, eficiente, flexível e adaptável para diferentes, contextos, gosto, propósitos e objetivos.
Dividindo o sistema operacional em diferentes partes, tornando mais mais fácil a manutênção, análise e adaptação do sistema e softwares para diferentes contextos.
Fornecendo mais flexibilidade e facilidade para a manutênção e análise para identificação de vulnerabilidades nesses sistema.

Após kernel montar e inicializar sistema de arquivo raiz, ele carrega o inicializador de sistema (init), como o systemd ou runit, e através dele os serviços e processos do sistema são incializados em ordem de dependência.

Incializando serviços e processos básico, essenciais ou definidos pelo usuário, como: Serviços de rede, terminal e shell básico como o tty, servidor gráfico como o Xorg, gerenciadores de login como o GDM, LightDM, SDDM.

É responsável por executar e gerenciar a comunicação do usuário com o hardware, os programas e o sistema operacional, e vice-versa.

Fazendo operações como alocação de memória, gerenciamento de drivers, módulos, recursos e dispositivos do sistema operacional e computador.
Lidando com a execução de programas, e gerenciamento de permissões e privilégios que usuários e programas possuem sobre outros arquivos, usuários, dispositivos e componentes do computador e sistema operacional como um todo.

Inicializadores de sistema (serviços)

O ventoy é uma ferramenta usada criar um pendrive multi-boot, ou seja, capaz de inicializar vários tipos de sistemas operacionais a partir da mídia de instalação deles, sem a necessidade de extrair o conteúdo delas. Ele suporta esses arquivos de mídia em diferentes formatos, como .iso/.img/.vhd/.efi/ etc...

Na inicialização, o firmware UEFI irá consultar sua tabela interna de configurações de entradas de boot registradas (armazenada em NVRAM), para determinar qual arquivo .efi de boot ele deve carregar e executar. Cada entrada de boot registrada na tabela interna dele, possui um identificador de entrada (label) e o caminho absoluto para o arquivo .efi na partição ESP.

Ao configurar o pendrive de boot com o ventoy, na inicialização, o firmware UEFI irá consultar sua tabela interna de configurações de entradas de boot resgistradas (armazenada em NVRAM), para determinar qual arquivo .efi de boot ele deve carregar e executar, cada entrada de boot ressgistrada na tabela interna dele, aponta para um .efi da partição ESP/EFI do bootloader.

Se na tabela interna dele, não houver uma entrada para um arquivo .efi específico, ele carrega e executa o BOOTX64.efi, que pode ser para um sistema operacional específico, e se não houver nenhum arquivo .efi, o firmware UEFI retorna um error e reiniciar o computador e redirecionar à interface do firmware.

Ao configurar o pendrive de boot com o ventoy, na inicialização, o firmware UEFI irá consultar sua tabela interna de configurações de entradas de boot resgistradas (armazenada em NVRAM), para determinar qual arquivo .efi de boot ele deve carregar e executar, cada entrada de boot ressgistrada na tabela interna dele, aponta para um .efi da partição ESP/EFI do bootloader.

Se na tabela interna dele, não houver uma entrada para um arquivo .efi específico, ele carrega e executa o BOOTX64.efi, que pode ser para um sistema operacional específico, e se não houver nenhum arquivo .efi, o firmware UEFI retorna um error e reiniciar o computador e redirecionar à interface do firmware.

Básicamente o ventoy utiliza uma versão do GRUB modifcada, que nativamente possui suporte ao acesso e leitura da estrutura de arquivos e dirétorios do .iso, e assim iniclizar o bootloader dentro ISO
Mas esse processo ocorre de maneiras diferentes, dependendo do firmware que é utilizado.

NVRAM (Non-Volatile Random Access Memory) é uma memória não volatil, usada para armazenar informações cruciais para o funcionamento do computador e do firmware UEFI.

Arquivos .efi são binários utilizados pelo firmware UEFI durante a inicialização. Eles geralmente são  gerados e utilizados por bootloaders (GRUB, sysboot etc...), eles geralmente ficam na partição ESP de boot. O firmware UEFI fica responsável por carregar e executar o arquivo .efi correto, com base nas configurações de entradas de boot registradas na tabela interna armazenada na NVRAM.

Se na tabela interna dele, não houver uma entrada para um arquivo .efi específico, ele carrega e executa o BOOTX64.efi como fallback, em casos de dispositvos removiveis. E se não houver nenhum arquivo .efi, o firmware UEFI retorna um error, espera a intervenção do usuário, e então reinicia o computador redirecionando o usuário para interface do firmware UEFI.

Em alguns casos pode-se usar o "efibootmgr" para resgistar uma entrada boot diretamente para o kernel. Para o kernel  deve ser compilado para um arquivo no formato .efi, para que firmware possa carregar e executar ele diretamente, sem a necessidade do GRUB.

Esses arquivos são responsáveis por executarem o processo de inicialização do sistema operacional. Esse processo de inicialização varia de acordo com o bootloader utilizado.

Ao escolher o ISO, o ventoy fornece 3 opções de boot a partir do arquivo ISO. E cada forma é util em diferentes contextos, e são usadas dependendo do firmware utilzado e do ISO.

O firmware UEFI localiza a entrada de boot na sua tabela, e carrega o arquivo binário BOOTX64.efi do ventoy, ele é responsável por carregar os outro "drivers" .efi e realizar a inicialização básica do ventoy. Para então carregar o seu grubx64.efi para scanear por mídias de inicialização suportadas e exibir o menu de ISOs, que ele encontrou na sua partição reservada para elas.

No caso do ventoy, o firmware UEFI inicializa a partição ESP VFAT do dispositivos de armazenamento. Essa partição foi criada pelo ventoy para armazenar os arquivos de BOOT usados por ele, e pelo firmware UEFI durante inicialização.

Em ambas as formas, o ventoy também será responsável por localizar, acessar e fazer o chainload do binário .efi ou .bin de bootloader do ISO, assim fazendo com que o firmware carregue e execute o bootloader do ISO. Esse bootloader do ISO irá acessar e carregar os arquivos de inicialização do sistema operacional (como o kernel e initramfs.img) do ISO, a partir do dispositivo bloco virtual que ventoy disponibiliza.

E no fim, o próprio initramfs.img do irá será  também irá carregar diretamente

.

Em sistema UEFI

Ao escolher o ISO do sistema operacional para incializar, o ventoy pode tratar o ISO de duas formas, mas no fim, em ambas as formas, o ventoy irá montar o arquivo ISO como um dispositivo bloco virtual:

Ao escolher inicializar o sistema operacional do ISO em modo GRUB2. O próprio ventoy carrega seu GRUB2, e ele é responsável por criar o dispositivo virtual de bloco (loop) para o ISO.
Para assim, localizar o arquivo grub.cfg/loopback.cfg, e então carrega-lo, pasando também as informações básicas para o grub.cfg do ISO poder localizar e carregar o kernel e initramfs.img do ISO.

Utilizado por firmwares e mídias de instalação mais antigas BIOS-legacy real-mode 16-bit. Ao selecionar o modo "Memdisk Mode" para inicializar o sistema operacional do ISO, o ventoy carrega o módulo "memdisk" do Sysllnux via linux16/initrd16.

No UEFI, ao escolher inicializar os sistema operacional do ISO em modo normal (compativel), o bootloader .efi do ventoy vai registrar um handler/driver que utiliza o protocolo UEFI Block I/O junto com filesystem ISO9660 para ler os blocos físicos do ISO corretamente. E então acessar e carregar a imagem (LoadImage()) do loader .efi do ISO, passando o mesmo handler/driver do ISO para ele.

O firmware BIOS carrega o MBR que está no pendrive, onde está instalado o primeiro estágio do ventoy. No segundo estágio o ventoy carrega menu de ISOs, ao escolher o modo normal para inicializar o sistema operacional do ISO.

Ao escolher incializar o sistema operacional do ISO em modo normal, o driver do ventoy será responsável por emular o ISO como um CD-ROM, para assim poder expor o sistema de arquivos do ISO e então acessar e carregar o bootloader .efi do ISO.

Esse handler do ventoy, vai fornecer uma abstração para bootloader .efi do ISO acessar os dirétorios e arquivos do ISO.
Quando o ventoy carrega o bootloader .efi do ISO, ele automatiamcente passa o mesmo handler de CD-DVD virtual do ISO para ele. Para assim, o bootloader .efi do ISO requisitar as operações de leitura do CD-ROM virtual do ISO, através do handler passado para ele. E esse handler do ventoy vai ser responsável por ler blocos de dados do ISO e devolver os bytes para o bootloader .efi do ISO, em execução.

Apresentar o as fontes e trechos de código para confirmar a explicação.

Ao selecionar o modo GRUB2 para inicializar o sistema operacional do ISO, o ventoy carrega seu próprio GRUB2 e os módulos dele, como ISO9960 para mapear e interpretar a estrutura de dados do ISO.

O handler do ventoy vai possibilitar mapear os blocos de dados do ISO, e mapear as entradas de diretorios e arquivos por meio de um simple file system via ISO9660/UDF.efi. Esse handler possui um Device Path associado a ele, que aponta diretamente para o arquivo ISO em si.

Pois dessa forma, o bootloader .efi do ISO irá carregar o kernel e o initramfs.img através da interface de CD-ROM do ISO, que o ventoy disponibiliza.

Na emulação de CD-ROM em BIOS, o ventoy instala hook de INT 13h (funções de leitura de setor do BIOS) para então responder às requisições de leitura de setor, como se fosse um "drive" de CD/DVD real.

INT 13h é uma das interrupções do BIOS, presente na tabela de vetores de interrupção (IVT), ela acontece em modo real 16-bit. Essa interrupção é usada para chamadas para leitura/gravação em setores do disco.

Dessa forma, o hook de INT 13h do ventoy irá interceptar as requisições do

.

Esse é o modo mais usado, pois é o mais compativel com a maioria dos sistemas operacionais e firmwares.

Esse handle implementa o protocolo UEFI block I/O, e um SimpleFileSystem com o "driver" ISO9660.efi para interpretar os blocos físicos do ISO corretamente.

Nesse momento, o GRUB2 monta o próprio ISO como um dispositivo de bloco virtual de loop, utilizando o sistema de arquivos ISO9660, para mepear a estrutura de dados corretamente do ISO.

O initramfs.img do ISO é responsável por montar o sistema de arquivos raiz que o usuário utilizara no sistema operacional live. Esse sistema de arquivos fornecera as ferramentas necessárias para a instalação real do sistema operacional.

Além de fornecer

loopbakc

Para isso o GRUB2 possui seus próprios modulos compilados, como o loopback.mod para a criação de dispositivos virtuais de bloco (loop) para arquivos .ISO. E iso9660/udf.mod para poder interpretar os arquivos e dirétorios dos blocos do ISO.

Para isso, o initramfs.img do ISO vai criar um dispositivo virtual de bloco (loop) para o sistema de arquivos raiz que o próprio ISO disponibiliza para ser usado no ambiente LIVE (airootfs.sfs ou roofs.sfs). SFS (Squash FIle System) é um sistema de arquivos comprimido e read-only.

Muitas distros, usam o .sfs para embalar todo o sistema que vai rodar em RAM. No boot, o initramfs inicializa um device loop para o .sfs, monta-o e faz um overlay (unionfs) para permitir gravação em RAM sem alterar o arquivo original do sistema de arquivos raiz do .sfs.

O módulo memdisk aloca um buffer em RAM do mesmo tamanho da imagem de disco e copia os bytes dele para lá. Em real-mode, ele intercepta chamadas INT 13h leitura/escrita de setor e as redireciona para buffer em RAM, assim,  emulando um dispositivo de bloco físico.
O memdisk fica responsável por carregar o bootloader da imagem de disco, e assim iniciar o processo de inicialização real, usando o buffer em RAM como "disco".

VMs (Virtual Machines) são ambientes virtuais que simulam um computador, incluindo seus componentes de hardware e software.

Isso é feito por meio do processo de virtualização. Através de softwares que emulam hardwares, e que fornecem suporte para outros softwares serem executados neles.
Criando uma cópia isolada de um sistema físico, dentro do atual sistema.

Dessa forma, permitindo executar sistemas operacionais e programas dentro delas.

Baseado primeiramente no firmware EFI, que surgiu justamente para superar as limitações do firmware BIOS. Por conta dos avanços nas capacidades dos hadwares ná época, foi necessário surgir o EFI.
Possui muitas limitações com os dispositivos existentes hoje em dia.
Ele suporta apenas dispositivos de armazenamento que utilizam o sistema de tabela de partições MBR (Master Boot Record).
O UEFI é uma extensão unificada e padronizada do EFI, baseado nas funcionalidades e capacidades do EFI.
O EFI foi projetado para suportar dispositivos de bloco que utilizam o sistema de tabela de partições GPT, assim, ele fornece suporte a múltiplas partições de incialização e dispositivos.
O UEFI como uma extensão do EFI, já possui recursos e funcionalidades que permitem suporte a mais dispositivos e definição de configurações específicas para eles.
É uma partição usada para criar outras partições lógicas dentro dela.
Essas partições lógicas geralmente são usadas para armazenar arquivos e em alguns casos sistema operacionais. Mas que geralmente não podem ser usadas para inicializar sistema operacionais.
São partições usadas para armazenar arquivos e sistemas operacionais.
Também são partições que o firmware pode usar para incializar os sistemas operacionais, essas são as partições de bootloader.
É um sistema de tabela de partições que funciona através da inicialização do primeiro setor de armazenamento valido para boot, conhecico como MBR, identifcado através de uma flag de boot (0x55AA). Ele armazena um pequeno código que lê a tabela de partições do MBR, e identifica a partição (VBR) ativa para transferir o controle para o setor de boot dela, e iniciar o segundo estágio de boot. Iniciando o kernel diretamente em sistema mais avançados, ou iniciando o bootloader na forma mais comum.
Dentro do setor MBR são usados 64 bytes para tabelar e definir as 4 partições do dispositivo de armazenamento, entre elas existe a ativa VBR, que o código de boot do MBR usa para transferir o controle a ela, e iniciar o sistema.
Ele é compativel e usado com firmware BIOS.
Mas possui muitas limitações comparado ao seu sucessor GPT, que surgiu exatamente para superar as limitações que tinha, como:
O setor de dispositivo de armazenamento, é o menor bloco físico de armazenamento acessível, ou melhor dizendo: a menor unidade física de armazenamento em um dispositivo.
Tendo geralmente um espaço de armazenamento de 512 bytes.
2TB por partição e apenas 4 partições primárias, ou 3 partições primárias e uma partição estendida, que pode armazenar até 63 sub-partições lógicas.
É um sistema de tabela de partições naturalmente compatível e nativa com o firmware UEFI. e GUID (Globally Unique Identifier) para as partições. Ele Funciona através de GUIDs (Globally Unique Identifier) para cada
partição.
Dessa forma, no GPT não existe os conceitos de partições estendidas ou lógicas, mas apenas primárias, pois todas possuem um identificador global único que diferencia cada uma delas no sistema de tabela de partições.
Assim, podem ser criadas 128 ou mais partições primárias, e com tamanhos de até 9.4ZT.
O firmware de um dispositivo especifico,
 é responsavel por fazer o gerenciamento e controle interno dos recursos do circuito do dispositvo.
Como a distruibuiçao de energia entre os componentes e microcontroladores, assim como a comunicaço (troca de informaçoes internas entre eles).
Por fim, o firmware é responsavel por executar as operações internas (manipulando os recursos, componentes e micro-controldores no circuito) para o dispositvo executar as funções pela qual ele foi desenvolvido para fazer.
São os softwares responsáveis por definir como os dados (arquivos) serão armazenados, organizados e gerenciados em uma partição. Eles também possuem a responsabilidade de definir as informações sobre os arquivos (metadados), como dara e hora de registro, permissões etc...
Muitos sistemas de arquivos oferecem várias funcionalidades como journaling paa o registro de logs de operações de leitura ou escrita em arquivos, assim dando mais segurança contra corrupção dados, e facilitando a identificação de erros.
Ao apertar o botão de Power Switch (PS), um circuito da placa mãe detecta a mudança de estado (normalmente fechando o circuito). Esse sinal elétrico é enviado para o chipset ou um controlador de energia da placa mãe, fazendo com que ele interprete o sinal e incie o sequenciamento de energia.
Fazendo com que os componentes seja inicializados de forma específica e correta, para evitar danos a eles.
O controlador envia um sinal de PS_ON (Power Supply On) para a fonte de alimentação, e após o circuito da fonte de alimentação verificar a tensão, ela retorna um sinal de PG (Power Good) para o controlador, indicando a ele que é seguro iniciar o processo de inicialização e (POST (Power-On Self-test)).
Assim que o sinal PG é recebido, o controlador ou chipset libera a CPU do seu estado atual (RESET)  e assim preparar a preparar a CPU para executar o código do firmware, que está em um endereço de memória correspondente ao chip de memória de onde o firmware está armazenado.
Então quando a CPU acessa e executa as instruções do firmware, é iniciado o test de POST realizado pelo código do firmware.
É responsável por inicializar o sistema operacional na memória RAM do computador.
O bootloader pode ser armazenado em uma partição especial do dispositivo de armazenamento (HD, SSD) como partição EFI em casos de GPT/UEFI ou em setores específicos do dispositivo de armazenamento, caso utilize MBR.
São softwares, genéricos ou desenvolvidos pelos própríos fabricantes, responsáveis por realizarem a comunicação direta com o dispositivo, executando operações nele diretamente, ou transmitindo instruções que o firmware do dispositivo irá processar e executar no hardware em si.
O firmware identifica essas partições de boot,
por meio da leitura da estrutura de dados sobre partições do dispositivo de armazenamento, criada pelo sistema de tabela de partições (GPT, MBR etc...). Na estrutura, ele indentifica a primeira entrada de partição que possua a flag de "boot", Indicando que ela é inicializavel.
O bootloader localiza e carrega o kernel comprimido na memória RAM, transfere o controle a ele, e então, o kernel se descomprime sozinho na memória RAM, através do código de descompressão que ele carrega, conhecido como "bootstrapping code". E após ser carregado, o kernel assume o controle e inicia as operações básicas, como: alocação e gerenciamento de memória e processos, e comunicação com o hardware. Ficando responsável por carregar os drivers e módulos básicos e essenciais para carregar e iniciar o initramfs.img na mamória RAM.
E utilizar o sistema de arquivos raiz dele temporariamente, para que possa localizar, montar e iniciar o sistema de arquivos da partição raiz real e definitiva do sistema operacional "/", por meio de scripts do sistema de arquivos do initramfs.img, de montagem e inicialização da partição raiz "/", de acordo com as configurações de boot que o usuário definiu. Após a inicialização do sistema de arquivos da partição raiz, o kernel encontra e inicia o "init" do sistema, como o systemd ou Ruinit, como processo número 1 do sistema.
Através do initramfs.img configurações específicas de montagem e inicialização da partição raiz podem ser definidas. De acordo com os objetivos ou propósitos do usuário, como geralmente, a criptográfia de disco, ou configurações de rede específicas, geralmente utilizadas em servidores.
initramfs.img é um sistema de arquivos raiz  temporário carregado na memória ram, agindo como um "mini sistema operacional" que possui drivers, módulos e scripts específicos usados pelo kernel, para poder localizar, montar e inicializar o sistema de arquivos da partição raiz real do sistema operacional, de acordo com as configurações de boot que o usuário definiu para esse processo.
Esse processo torna a arquitetura do sistema operacional, mais limpa, modular, eficiente, flexível e adaptável para diferentes, contextos, gosto, propósitos e objetivos.
Dividindo o sistema operacional em diferentes partes, tornando mais mais fácil a manutênção, análise e adaptação do sistema e softwares para diferentes contextos.
Fornecendo mais flexibilidade e facilidade para a manutênção e análise para identificação de vulnerabilidades nesses sistema.
Após kernel montar e inicializar sistema de arquivo raiz, ele carrega o inicializador de sistema (init), como o systemd ou runit, e através dele os serviços e processos do sistema são incializados em ordem de dependência.
Incializando serviços e processos básico, essenciais ou definidos pelo usuário, como: Serviços de rede, terminal e shell básico como o tty, servidor gráfico como o Xorg, gerenciadores de login como o GDM, LightDM, SDDM.
É responsável por executar e gerenciar a comunicação do usuário com o hardware, os programas e o sistema operacional, e vice-versa.
Fazendo operações como alocação de memória, gerenciamento de drivers, módulos, recursos e dispositivos do sistema operacional e computador.
Lidando com a execução de programas, e gerenciamento de permissões e privilégios que usuários e programas possuem sobre outros arquivos, usários, dispositivos e componentes do computador sistema operacional como um todo.
O ventoy é uma ferramenta usada criar um pendrive multi-boot, ou seja, capaz de inicializar vários tipos de sistemas operacionais a partir da mídia de instalação deles, sem a necessidade de extrair o conteúdo delas. Ele suporta esses arquivos de mídia em diferentes formatos, como .iso/.img/.vhd/.efi/ etc...
Na inicialização, o firmware UEFI irá consultar sua tabela interna de configurações de entradas de boot registradas (armazenada em NVRAM), para determinar qual arquivo .efi de boot ele deve carregar e executar. Cada entrada de boot registrada na tabela interna dele, possui um identificador de entrada (label) e o caminho absoluto para o arquivo .efi na partição ESP.
NVRAM (Non-Volatile Random Access Memory) é uma memória não volatil, usada para armazenar informações cruciais para o funcionamento do computador e do firmware UEFI.
Arquivos .efi são binários utilizados pelo firmware UEFI durante a inicialização. Eles geralmente são  gerados e utilizados por bootloaders (GRUB, sysboot etc...), eles geralmente ficam na partição ESP de boot. O firmware UEFI fica responsável por carregar e executar o arquivo .efi correto, com base nas configurações de entradas de boot registradas na tabela interna armazenada na NVRAM.
Esses arquivos são responsáveis por executarem o processo de inicialização do sistema operacional. Esse processo de inicialização varia de acordo com o bootloader utilizado.
Ao escolher o ISO, o ventoy fornece 3 opções de boot a partir do arquivo ISO. E cada forma é util em diferentes contextos, e são usadas dependendo do firmware utilzado e do ISO.
O firmware UEFI localiza a entrada de boot na sua tabela, e carrega o arquivo binário BOOTX64.efi do ventoy, ele é responsável por carregar os outro "drivers" .efi e realizar a inicialização básica do ventoy. Para então carregar o seu grubx64.efi para scanear por mídias de inicialização suportadas e exibir o menu de ISOs, que ele encontrou na sua partição reservada para elas.
No caso do ventoy, o firmware UEFI inicializa a partição ESP VFAT do dispositivos de armazenamento. Essa partição foi criada pelo ventoy para armazenar os arquivos de BOOT usados por ele, e pelo firmware UEFI durante inicialização.
Em ambas as formas, o ventoy também será responsável por localizar, acessar e fazer o chainload do binário .efi ou .bin de bootloader do ISO, assim fazendo com que o firmware carregue e execute o bootloader do ISO. Esse bootloader do ISO irá acessar e carregar os arquivos de inicialização do sistema operacional (como o kernel e initramfs.img) do ISO, a partir do dispositivo bloco virtual que ventoy disponibiliza.
Ao escolher inicializar o sistema operacional do ISO em modo GRUB2. O próprio ventoy carrega seu GRUB2, e ele é responsável por criar o dispositivo virtual de bloco (loop) para o ISO.
Para assim, localizar o arquivo grub.cfg/loopback.cfg, e então carrega-lo, pasando também as informações básicas para o grub.cfg do ISO poder localizar e carregar o kernel e initramfs.img do ISO.
Utilizado por firmwares e mídias de instalação mais antigas BIOS-legacy real-mode 16-bit. Ao selecionar o modo "Memdisk Mode" para inicializar o sistema operacional do ISO, o ventoy carrega o módulo "memdisk" do Sysllnux via linux16/initrd.
O memdisk transforma qualquer imagem de disco, em uma unidade em RAM.
No UEFI, ao escolher inicializar os sistema operacional do ISO em modo normal (compativel), o bootloader .efi do ventoy vai registrar um handler/driver que utiliza o protocolo UEFI Block I/O junto com filesystem ISO9660 para ler os blocos físicos do ISO corretamente. E então acessar e carregar a imagem (LoadImage()) do bootloader .efi do ISO, passando o mesmo handler/driver do ISO para ele.
O firmware BIOS carrega o MBR que está no pendrive, onde está instalado o primiero estágio do ventoy. No primeiro estágio o ventoy carrega menu de ISOs, ao escolher o modo normal para inicializar o sistema operacional do ISO, o estágio 2 começa.
Esse handler do ventoy, vai fornecer uma abstração para bootloader .efi do ISO acessar os dirétorios e arquivos do ISO.
Quando o ventoy carrega o bootloader .efi do ISO, ele automatiamcente passa o mesmo handler de CD-DVD virtual do ISO para ele. Para assim, o bootloader .efi do ISO requisitar as operações de leitura do CD-ROM virtual do ISO, através do handler passado para ele. E esse handler do ventoy vai ser responsável por ler blocos de dados do ISO e devolver os bytes para o bootloader .efi do ISO, em execução.
Apresentar o as fontes e trechos de código para confirmar a explicação.
O módulo memdisk transforma qualquer imagem de disco, em uma unidade na RAM. Ou seja, ele copia todo o sistema de arquivos do para a RAM.O handler do ventoy vai possibilitar mapear os blocos de dados do ISO, e mapear as entradas de diretorios e arquivos por meio de um simple file system via ISO9660/UDF.efi. Esse handler possui um Device Path associado a ele, que aponta diretamente para o arquivo ISO em si.
Na emulação de CD-ROM em BIOS, o ventoy instala hook de INT 13h (funções de leitura de setor do BIOS) para então responder às requisições de leitura de setor, como se fosse um "drive" de CD/DVD real.
INT 13h é uma das interrupções do BIOS, presente na tabela de vetores de interrupção (IVT), ela acontece em modo real 16-bit. Essa interrupção é usada para chamadas para leitura/gravação em setores do disco.
Esse é o modo mais usado, pois é o mais compativel com a maioria dos sistemas operacionais e firmwares.
O initramfs.img do ISO é responsável por montar o sistema de arquivos raiz que o usuário utilizara no sistema operacional live. Esse sistema de arquivos fornecera as ferramentas necessárias para a instalação real do sistema operacional.
Para isso o GRUB2 possui seus próprios modulos compilados, como o loopback.mod para a criação de dispositivos virtuais de bloco (loop) para arquivos .ISO. E iso9660/udf.mod para poder interpretar os arquivos e dirétorios dos blocos do ISO.
Para isso, o initramfs.img do ISO vai criar um dispositivo virtual de bloco (loop) para o sistema de arquivos raiz que o próprio ISO disponibiliza para ser usado no ambiente LIVE (airootfs.sfs ou roofs.sfs). SFS (Squash FIle System) é um sistema de arquivos comprimido e read-only.
Muitas distros, usam o .sfs para embalar todo o sistema que vai rodar em RAM. No boot, o initramfs inicializa um device loop para o .sfs, monta-o e faz um overlay (unionfs) para permitir gravação em RAM sem alterar o arquivo original do sistema de arquivos raiz do .sfs.
O módulo memdisk aloca um buffer em RAM do mesmo tamanho da imagem de disco e copia os bytes dele para lá. Em real-mode, ele intercepta chamadas INT 13h leitura/escrita de setor e as redireciona para buffer em RAM, assim,  emulando um dispositivo de bloco físico.
O memdisk fica responsável por carregar o bootloader da imagem de disco, e assim iniciar o processo de inicialização real, usando o buffer em RAM como "disco".
VMs (Virtual Machines) são ambientes virtuais que simulam um computador, incluindo seus componentes de hardware e software.
Isso é feito por meio do processo de virtualização. Através de softwares que emulam hardwares, e que fornecem suporte para outros softwares serem executados neles.
Criando uma cópia isolada de um sistema físico, dentro do atual sistema.
Dessa forma, permitindo executar sistemas operacionais e programas dentro delas.

É o tipo mais básico de firmware, que fornece uma interface e funcionalidades básicas para gerenciar as configurações internas do computador e seus dispositivos, assim como a inicialização deles.
Baseado primeiramente no firmware EFI, que surgiu justamente para superar as limitações do firmware BIOS. Por conta dos avanços nas capacidades dos hadwares ná época, foi necessário surgir o EFI.
Possui muitas limitações com os dispositivos existentes hoje em dia.
Ele suporta apenas dispositivos de armazenamento que utilizam o sistema de tabela de partições MBR (Master Boot Record).
O UEFI é uma extensão unificada e padronizada do EFI, baseado nas funcionalidades e capacidades do EFI.
O EFI foi projetado para suportar dispositivos de bloco que utilizam o sistema de tabela de partições GPT, assim, ele fornece suporte a múltiplas partições de incialização e dispositivos.
O UEFI como uma extensão do EFI, já possui recursos e funcionalidades que permitem suporte a mais dispositivos e definição de configurações específicas para eles.
É uma partição usada para criar outras partições lógicas dentro dela.
Essas partições lógicas geralmente são usadas para armazenar arquivos e em alguns casos sistema operacionais. Mas que geralmente não podem ser usadas para inicializar sistema operacionais.
São partições usadas para armazenar arquivos e sistemas operacionais.
Também são partições que o firmware pode usar para incializar os sistemas operacionais, essas são as partições de bootloader.
É um sistema de tabela de partições que funciona através da inicialização do primeiro setor de armazenamento valido para boot, conhecico como MBR, identifcado através de uma flag de boot (0x55AA). Ele armazena um pequeno código que lê a tabela de partições do MBR, e identifica a partição (VBR) ativa para transferir o controle para o setor de boot dela, e iniciar o segundo estágio de boot. Iniciando o kernel diretamente em sistema mais avançados, ou iniciando o bootloader na forma mais comum.
Dentro do setor MBR são usados 64 bytes para tabelar e definir as 4 partições do dispositivo de armazenamento, entre elas existe a ativa VBR, que o código de boot do MBR usa para transferir o controle a ela, e iniciar o sistema.
Ele é compativel e usado com firmware BIOS.
Mas possui muitas limitações comparado ao seu sucessor GPT, que surgiu exatamente para superar as limitações que tinha, como:
O setor de dispositivo de armazenamento, é o menor bloco físico de armazenamento acessível, ou melhor dizendo: a menor unidade física de armazenamento em um dispositivo.
Tendo geralmente um espaço de armazenamento de 512 bytes.
2TB por partição e apenas 4 partições primárias, ou 3 partições primárias e uma partição estendida, que pode armazenar até 63 sub-partições lógicas.
É um sistema de tabela de partições naturalmente compatível e nativa com o firmware UEFI. e GUID (Globally Unique Identifier) para as partições. Ele Funciona através de GUIDs (Globally Unique Identifier) para cada
partição.
Dessa forma, no GPT não existe os conceitos de partições estendidas ou lógicas, mas apenas primárias, pois todas possuem um identificador global único que diferencia cada uma delas no sistema de tabela de partições.
Assim, podem ser criadas 128 ou mais partições primárias, e com tamanhos de até 9.4ZT.
O firmware de um dispositivo especifico,
 é responsavel por fazer o gerenciamento e controle interno dos recursos do circuito do dispositvo.
Como a distruibuiçao de energia entre os componentes e microcontroladores, assim como a comunicaço (troca de informaçoes internas entre eles).
Por fim, o firmware é responsavel por executar as operações internas (manipulando os recursos, componentes e micro-controldores no circuito) para o dispositvo executar as funções pela qual ele foi desenvolvido para fazer.
São os softwares responsáveis por definir como os dados (arquivos) serão armazenados, organizados e gerenciados em uma partição. Eles também possuem a responsabilidade de definir as informações sobre os arquivos (metadados), como dara e hora de registro, permissões etc...
Muitos sistemas de arquivos oferecem várias funcionalidades como journaling paa o registro de logs de operações de leitura ou escrita em arquivos, assim dando mais segurança contra corrupção dados, e facilitando a identificação de erros.
Ao apertar o botão de Power Switch (PS), um circuito da placa mãe detecta a mudança de estado (normalmente fechando o circuito). Esse sinal elétrico é enviado para o chipset ou um controlador de energia da placa mãe, fazendo com que ele interprete o sinal e incie o sequenciamento de energia.
Fazendo com que os componentes seja inicializados de forma específica e correta, para evitar danos a eles.
O controlador envia um sinal de PS_ON (Power Supply On) para a fonte de alimentação, e após o circuito da fonte de alimentação verificar a tensão, ela retorna um sinal de PG (Power Good) para o controlador, indicando a ele que é seguro iniciar o processo de inicialização e (POST (Power-On Self-test)).
Assim que o sinal PG é recebido, o controlador ou chipset libera a CPU do seu estado atual (RESET)  e assim preparar a preparar a CPU para executar o código do firmware, que está em um endereço de memória correspondente ao chip de memória de onde o firmware está armazenado.
Então quando a CPU acessa e executa as instruções do firmware, é iniciado o test de POST realizado pelo código do firmware.
É responsável por inicializar o sistema operacional na memória RAM do computador.
O bootloader pode ser armazenado em uma partição especial do dispositivo de armazenamento (HD, SSD) como partição EFI em casos de GPT/UEFI ou em setores específicos do dispositivo de armazenamento, caso utilize MBR.
São softwares, genéricos ou desenvolvidos pelos própríos fabricantes, responsáveis por realizarem a comunicação direta com o dispositivo, executando operações nele diretamente, ou transmitindo instruções que o firmware do dispositivo irá processar e executar no hardware em si.
O firmware identifica essas partições de boot,
por meio da leitura da estrutura de dados sobre partições do dispositivo de armazenamento, criada pelo sistema de tabela de partições (GPT, MBR etc...). Na estrutura, ele indentifica a primeira entrada de partição que possua a flag de "boot", Indicando que ela é inicializavel.
O bootloader localiza e carrega o kernel comprimido na memória RAM, transfere o controle a ele, e então, o kernel se descomprime sozinho na memória RAM, através do código de descompressão que ele carrega, conhecido como "bootstrapping code". E após ser carregado, o kernel assume o controle e inicia as operações básicas, como: alocação e gerenciamento de memória e processos, e comunicação com o hardware. Ficando responsável por carregar os drivers e módulos básicos e essenciais para carregar e iniciar o initramfs.img na mamória RAM.
E utilizar o sistema de arquivos raiz dele temporariamente, para que possa localizar, montar e iniciar o sistema de arquivos da partição raiz real e definitiva do sistema operacional "/", por meio de scripts do sistema de arquivos do initramfs.img, de montagem e inicialização da partição raiz "/", de acordo com as configurações de boot que o usuário definiu. Após a inicialização do sistema de arquivos da partição raiz, o kernel encontra e inicia o "init" do sistema, como o systemd ou Ruinit, como processo número 1 do sistema.
Através do initramfs.img configurações específicas de montagem e inicialização da partição raiz podem ser definidas. De acordo com os objetivos ou propósitos do usuário, como geralmente, a criptográfia de disco, ou configurações de rede específicas, geralmente utilizadas em servidores.
initramfs.img é um sistema de arquivos raiz  temporário carregado na memória ram, agindo como um "mini sistema operacional" que possui drivers, módulos e scripts específicos usados pelo kernel, para poder localizar, montar e inicializar o sistema de arquivos da partição raiz real do sistema operacional, de acordo com as configurações de boot que o usuário definiu para esse processo.
Esse processo torna a arquitetura do sistema operacional, mais limpa, modular, eficiente, flexível e adaptável para diferentes, contextos, gosto, propósitos e objetivos.
Dividindo o sistema operacional em diferentes partes, tornando mais mais fácil a manutênção, análise e adaptação do sistema e softwares para diferentes contextos.
Fornecendo mais flexibilidade e facilidade para a manutênção e análise para identificação de vulnerabilidades nesses sistema.
Após kernel montar e inicializar sistema de arquivo raiz, ele carrega o inicializador de sistema (init), como o systemd ou runit, e através dele os serviços e processos do sistema são incializados em ordem de dependência.
Incializando serviços e processos básico, essenciais ou definidos pelo usuário, como: Serviços de rede, terminal e shell básico como o tty, servidor gráfico como o Xorg, gerenciadores de login como o GDM, LightDM, SDDM.
É responsável por executar e gerenciar a comunicação do usuário com o hardware, os programas e o sistema operacional, e vice-versa.
Fazendo operações como alocação de memória, gerenciamento de drivers, módulos, recursos e dispositivos do sistema operacional e computador.
Lidando com a execução de programas, e gerenciamento de permissões e privilégios que usuários e programas possuem sobre outros arquivos, usários, dispositivos e componentes do computador sistema operacional como um todo.
O ventoy é uma ferramenta usada criar um pendrive multi-boot, ou seja, capaz de inicializar vários tipos de sistemas operacionais a partir da mídia de instalação deles, sem a necessidade de extrair o conteúdo delas. Ele suporta esses arquivos de mídia em diferentes formatos, como .iso/.img/.vhd/.efi/ etc...
Na inicialização, o firmware UEFI irá consultar sua tabela interna de configurações de entradas de boot registradas (armazenada em NVRAM), para determinar qual arquivo .efi de boot ele deve carregar e executar. Cada entrada de boot registrada na tabela interna dele, possui um identificador de entrada (label) e o caminho absoluto para o arquivo .efi na partição ESP.
NVRAM (Non-Volatile Random Access Memory) é uma memória não volatil, usada para armazenar informações cruciais para o funcionamento do computador e do firmware UEFI.
Arquivos .efi são binários utilizados pelo firmware UEFI durante a inicialização. Eles geralmente são  gerados e utilizados por bootloaders (GRUB, sysboot etc...), eles geralmente ficam na partição ESP de boot. O firmware UEFI fica responsável por carregar e executar o arquivo .efi correto, com base nas configurações de entradas de boot registradas na tabela interna armazenada na NVRAM.
Esses arquivos são responsáveis por executarem o processo de inicialização do sistema operacional. Esse processo de inicialização varia de acordo com o bootloader utilizado.
Ao escolher o ISO, o ventoy fornece 3 opções de boot a partir do arquivo ISO. E cada forma é util em diferentes contextos, e são usadas dependendo do firmware utilzado e do ISO.
O firmware UEFI localiza a entrada de boot na sua tabela, e carrega o arquivo binário BOOTX64.efi do ventoy, ele é responsável por carregar os outro "drivers" .efi e realizar a inicialização básica do ventoy. Para então carregar o seu grubx64.efi para scanear por mídias de inicialização suportadas e exibir o menu de ISOs, que ele encontrou na sua partição reservada para elas.
No caso do ventoy, o firmware UEFI inicializa a partição ESP VFAT do dispositivos de armazenamento. Essa partição foi criada pelo ventoy para armazenar os arquivos de BOOT usados por ele, e pelo firmware UEFI durante inicialização.
Em ambas as formas, o ventoy também será responsável por localizar, acessar e fazer o chainload do binário .efi ou .bin de bootloader do ISO, assim fazendo com que o firmware carregue e execute o bootloader do ISO. Esse bootloader do ISO irá acessar e carregar os arquivos de inicialização do sistema operacional (como o kernel e initramfs.img) do ISO, a partir do dispositivo bloco virtual que ventoy disponibiliza.
Ao escolher inicializar o sistema operacional do ISO em modo GRUB2. O próprio ventoy carrega seu GRUB2, e ele é responsável por criar o dispositivo virtual de bloco (loop) para o ISO.
Para assim, localizar o arquivo grub.cfg/loopback.cfg, e então carrega-lo, pasando também as informações básicas para o grub.cfg do ISO poder localizar e carregar o kernel e initramfs.img do ISO.
Utilizado por firmwares e mídias de instalação mais antigas BIOS-legacy real-mode 16-bit. Ao selecionar o modo "Memdisk Mode" para inicializar o sistema operacional do ISO, o ventoy carrega o módulo "memdisk" do Sysllnux via linux16/initrd.
O memdisk transforma qualquer imagem de disco, em uma unidade em RAM.
No UEFI, ao escolher inicializar os sistema operacional do ISO em modo normal (compativel), o bootloader .efi do ventoy vai registrar um handler/driver que utiliza o protocolo UEFI Block I/O junto com filesystem ISO9660 para ler os blocos físicos do ISO corretamente. E então acessar e carregar a imagem (LoadImage()) do bootloader .efi do ISO, passando o mesmo handler/driver do ISO para ele.
O firmware BIOS carrega o MBR que está no pendrive, onde está instalado o primiero estágio do ventoy. No primeiro estágio o ventoy carrega menu de ISOs, ao escolher o modo normal para inicializar o sistema operacional do ISO, o estágio 2 começa.
Esse handler do ventoy, vai fornecer uma abstração para bootloader .efi do ISO acessar os dirétorios e arquivos do ISO.
Quando o ventoy carrega o bootloader .efi do ISO, ele automatiamcente passa o mesmo handler de CD-DVD virtual do ISO para ele. Para assim, o bootloader .efi do ISO requisitar as operações de leitura do CD-ROM virtual do ISO, através do handler passado para ele. E esse handler do ventoy vai ser responsável por ler blocos de dados do ISO e devolver os bytes para o bootloader .efi do ISO, em execução.
Apresentar o as fontes e trechos de código para confirmar a explicação.
O módulo memdisk transforma qualquer imagem de disco, em uma unidade na RAM. Ou seja, ele copia todo o sistema de arquivos do para a RAM.O handler do ventoy vai possibilitar mapear os blocos de dados do ISO, e mapear as entradas de diretorios e arquivos por meio de um simple file system via ISO9660/UDF.efi. Esse handler possui um Device Path associado a ele, que aponta diretamente para o arquivo ISO em si.
Na emulação de CD-ROM em BIOS, o ventoy instala hook de INT 13h (funções de leitura de setor do BIOS) para então responder às requisições de leitura de setor, como se fosse um "drive" de CD/DVD real.
INT 13h é uma das interrupções do BIOS, presente na tabela de vetores de interrupção (IVT), ela acontece em modo real 16-bit. Essa interrupção é usada para chamadas para leitura/gravação em setores do disco.
Esse é o modo mais usado, pois é o mais compativel com a maioria dos sistemas operacionais e firmwares.
O initramfs.img do ISO é responsável por montar o sistema de arquivos raiz que o usuário utilizara no sistema operacional live. Esse sistema de arquivos fornecera as ferramentas necessárias para a instalação real do sistema operacional.
Para isso o GRUB2 possui seus próprios modulos compilados, como o loopback.mod para a criação de dispositivos virtuais de bloco (loop) para arquivos .ISO. E iso9660/udf.mod para poder interpretar os arquivos e dirétorios dos blocos do ISO.
Para isso, o initramfs.img do ISO vai criar um dispositivo virtual de bloco (loop) para o sistema de arquivos raiz que o próprio ISO disponibiliza para ser usado no ambiente LIVE (airootfs.sfs ou roofs.sfs). SFS (Squash FIle System) é um sistema de arquivos comprimido e read-only.
Muitas distros, usam o .sfs para embalar todo o sistema que vai rodar em RAM. No boot, o initramfs inicializa um device loop para o .sfs, monta-o e faz um overlay (unionfs) para permitir gravação em RAM sem alterar o arquivo original do sistema de arquivos raiz do .sfs.
O módulo memdisk aloca um buffer em RAM do mesmo tamanho da imagem de disco e copia os bytes dele para lá. Em real-mode, ele intercepta chamadas INT 13h leitura/escrita de setor e as redireciona para buffer em RAM, assim,  emulando um dispositivo de bloco físico.
O memdisk fica responsável por carregar o bootloader da imagem de disco, e assim iniciar o processo de inicialização real, usando o buffer em RAM como "disco".
VMs (Virtual Machines) são ambientes virtuais que simulam um computador, incluindo seus componentes de hardware e software.
Isso é feito por meio do processo de virtualização. Através de softwares que emulam hardwares, e que fornecem suporte para outros softwares serem executados neles.
Criando uma cópia isolada de um sistema físico, dentro do atual sistema.
Dessa forma, permitindo executar sistemas operacionais e programas dentro delas.
Large block will not be editable or searchable to not slow down the app, please use another editor to edit this block.
Melhor entendimento do funcionamento do computador, e sistema operacional.
Define como um dispositivo de armazenamento gerencia e organiza as partições que contém sistemas de arquivos.
Ideal para quem está estudando e começando na área da computação!
Fornecendo um maior controle sobre seu sistema, o que é utilizado nele e o que você utiliza no dia a dia.
Liberdade de escolha sobre softwares críticos no sistema, e escolher de acordo com o propósito e objetivo de cada um.
Liberdade em escolher programas e aplicações livre e de código aberto, que não coletam dados, ou, que te dá a possibilidade de escolher quais dados fornecer.
São programas de código aberto, que passam po auditorias de segurança regulares. E que constantemente está em desenvolvimento, recebendo atualizações para correção de bugs e vulnerabilidades.
Pois é um software livre e codigo aberto para todos.
Fornecendo mais transparência para quem utiliza.
Durante a instalação do  Archlinux, é instalado os  pacotes do repositorio  AUR(Arch User Repository),  e no pacote "base" do  repositorio AUR, possui as  principais ferramentas  usadas pelo sistema  operacional, como o gerenciador de pacotes usado no archlinux, usado para instalar os outros programas e pacotes do respositorio AUR.
Em um computador, é o software responsável por identificar, análisar, iniciar e gerenciar o comportamento incial dos dispositivos básicos do computador, CPU, memória RAM, dispositivos I/O, dispositivos de armazenameento como: HD(Hard disk), SSD(Solid State Driver) entre outros. Fazendo a inter-comunicaçao entre eles, e controlando a distribuição de recursos entre eles, como energia e memoria.
Ele é armazenado em um circuito integrado (chip) de memória na placa mãe, como: ROM(Read Only Memory), PROM, EPROM ou memória flash.
É o tipo mais básico de firmware, que fornece uma interface e funcionalidades básicas para gerenciar as configurações internas do computador e seus dispositivos, assim como a inicialização deles.
Baseado primeiramente no firmware EFI, que surgiu justamente para superar as limitações do firmware BIOS. Por conta dos avanços nas capacidades dos hadwares ná época, foi necessário surgir o EFI.
Possui muitas limitações com os dispositivos existentes hoje em dia.
Ele suporta apenas dispositivos de armazenamento que utilizam o sistema de tabela de partições MBR (Master Boot Record).
O UEFI é uma extensão unificada e padronizada do EFI, baseado nas funcionalidades e capacidades do EFI.
O EFI foi projetado para suportar dispositivos de bloco que utilizam o sistema de tabela de partições GPT, assim, ele fornece suporte a múltiplas partições de incialização e dispositivos.
O UEFI como uma extensão do EFI, já possui recursos e funcionalidades que permitem suporte a mais dispositivos e definição de configurações específicas para eles.
É uma partição usada para criar outras partições lógicas dentro dela.
Essas partições lógicas geralmente são usadas para armazenar arquivos e em alguns casos sistema operacionais. Mas que geralmente não podem ser usadas para inicializar sistema operacionais.
São partições usadas para armazenar arquivos e sistemas operacionais.
Também são partições que o firmware pode usar para incializar os sistemas operacionais, essas são as partições de bootloader.
É um sistema de tabela de partições que funciona através da inicialização do primeiro setor de armazenamento valido para boot, conhecico como MBR, identifcado através de uma flag de boot (0x55AA). Ele armazena um pequeno código que lê a tabela de partições do MBR, e identifica a partição (VBR) ativa para transferir o controle para o setor de boot dela, e iniciar o segundo estágio de boot. Iniciando o kernel diretamente em sistema mais avançados, ou iniciando o bootloader na forma mais comum.
Dentro do setor MBR são usados 64 bytes para tabelar e definir as 4 partições do dispositivo de armazenamento, entre elas existe a ativa VBR, que o código de boot do MBR usa para transferir o controle a ela, e iniciar o sistema.
Ele é compativel e usado com firmware BIOS.
Mas possui muitas limitações comparado ao seu sucessor GPT, que surgiu exatamente para superar as limitações que tinha, como:
O setor de dispositivo de armazenamento, é o menor bloco físico de armazenamento acessível, ou melhor dizendo: a menor unidade física de armazenamento em um dispositivo.
Tendo geralmente um espaço de armazenamento de 512 bytes.
2TB por partição e apenas 4 partições primárias, ou 3 partições primárias e uma partição estendida, que pode armazenar até 63 sub-partições lógicas.
É um sistema de tabela de partições naturalmente compatível e nativa com o firmware UEFI. e GUID (Globally Unique Identifier) para as partições. Ele Funciona através de GUIDs (Globally Unique Identifier) para cada
partição.
Dessa forma, no GPT não existe os conceitos de partições estendidas ou lógicas, mas apenas primárias, pois todas possuem um identificador global único que diferencia cada uma delas no sistema de tabela de partições.
Assim, podem ser criadas 128 ou mais partições primárias, e com tamanhos de até 9.4ZT.
O firmware de um dispositivo especifico,
 é responsavel por fazer o gerenciamento e controle interno dos recursos do circuito do dispositvo.
Como a distruibuiçao de energia entre os componentes e microcontroladores, assim como a comunicaço (troca de informaçoes internas entre eles).
Por fim, o firmware é responsavel por executar as operações internas (manipulando os recursos, componentes e micro-controldores no circuito) para o dispositvo executar as funções pela qual ele foi desenvolvido para fazer.
São os softwares responsáveis por definir como os dados (arquivos) serão armazenados, organizados e gerenciados em uma partição. Eles também possuem a responsabilidade de definir as informações sobre os arquivos (metadados), como dara e hora de registro, permissões etc...
Muitos sistemas de arquivos oferecem várias funcionalidades como journaling paa o registro de logs de operações de leitura ou escrita em arquivos, assim dando mais segurança contra corrupção dados, e facilitando a identificação de erros.
Ao apertar o botão de Power Switch (PS), um circuito da placa mãe detecta a mudança de estado (normalmente fechando o circuito). Esse sinal elétrico é enviado para o chipset ou um controlador de energia da placa mãe, fazendo com que ele interprete o sinal e incie o sequenciamento de energia.
Fazendo com que os componentes seja inicializados de forma específica e correta, para evitar danos a eles.
O controlador envia um sinal de PS_ON (Power Supply On) para a fonte de alimentação, e após o circuito da fonte de alimentação verificar a tensão, ela retorna um sinal de PG (Power Good) para o controlador, indicando a ele que é seguro iniciar o processo de inicialização e (POST (Power-On Self-test)).
Assim que o sinal PG é recebido, o controlador ou chipset libera a CPU do seu estado atual (RESET)  e assim preparar a preparar a CPU para executar o código do firmware, que está em um endereço de memória correspondente ao chip de memória de onde o firmware está armazenado.
Então quando a CPU acessa e executa as instruções do firmware, é iniciado o test de POST realizado pelo código do firmware.
É responsável por inicializar o sistema operacional na memória RAM do computador.
O bootloader pode ser armazenado em uma partição especial do dispositivo de armazenamento (HD, SSD) como partição EFI em casos de GPT/UEFI ou em setores específicos do dispositivo de armazenamento, caso utilize MBR.
São softwares, genéricos ou desenvolvidos pelos própríos fabricantes, responsáveis por realizarem a comunicação direta com o dispositivo, executando operações nele diretamente, ou transmitindo instruções que o firmware do dispositivo irá processar e executar no hardware em si.
O firmware identifica essas partições de boot,
por meio da leitura da estrutura de dados sobre partições do dispositivo de armazenamento, criada pelo sistema de tabela de partições (GPT, MBR etc...). Na estrutura, ele indentifica a primeira entrada de partição que possua a flag de "boot", Indicando que ela é inicializavel.
O bootloader localiza e carrega o kernel comprimido na memória RAM, transfere o controle a ele, e então, o kernel se descomprime sozinho na memória RAM, através do código de descompressão que ele carrega, conhecido como "bootstrapping code". E após ser carregado, o kernel assume o controle e inicia as operações básicas, como: alocação e gerenciamento de memória e processos, e comunicação com o hardware. Ficando responsável por carregar os drivers e módulos básicos e essenciais para carregar e iniciar o initramfs.img na mamória RAM.
E utilizar o sistema de arquivos raiz dele temporariamente, para que possa localizar, montar e iniciar o sistema de arquivos da partição raiz real e definitiva do sistema operacional "/", por meio de scripts do sistema de arquivos do initramfs.img, de montagem e inicialização da partição raiz "/", de acordo com as configurações de boot que o usuário definiu. Após a inicialização do sistema de arquivos da partição raiz, o kernel encontra e inicia o "init" do sistema, como o systemd ou Ruinit, como processo número 1 do sistema.
Através do initramfs.img configurações específicas de montagem e inicialização da partição raiz podem ser definidas. De acordo com os objetivos ou propósitos do usuário, como geralmente, a criptográfia de disco, ou configurações de rede específicas, geralmente utilizadas em servidores.
initramfs.img é um sistema de arquivos raiz  temporário carregado na memória ram, agindo como um "mini sistema operacional" que possui drivers, módulos e scripts específicos usados pelo kernel, para poder localizar, montar e inicializar o sistema de arquivos da partição raiz real do sistema operacional, de acordo com as configurações de boot que o usuário definiu para esse processo.
Esse processo torna a arquitetura do sistema operacional, mais limpa, modular, eficiente, flexível e adaptável para diferentes, contextos, gosto, propósitos e objetivos.
Dividindo o sistema operacional em diferentes partes, tornando mais mais fácil a manutênção, análise e adaptação do sistema e softwares para diferentes contextos.
Fornecendo mais flexibilidade e facilidade para a manutênção e análise para identificação de vulnerabilidades nesses sistema.
Após kernel montar e inicializar sistema de arquivo raiz, ele carrega o inicializador de sistema (init), como o systemd ou runit, e através dele os serviços e processos do sistema são incializados em ordem de dependência.
Incializando serviços e processos básico, essenciais ou definidos pelo usuário, como: Serviços de rede, terminal e shell básico como o tty, servidor gráfico como o Xorg, gerenciadores de login como o GDM, LightDM, SDDM.
É responsável por executar e gerenciar a comunicação do usuário com o hardware, os programas e o sistema operacional, e vice-versa.
Fazendo operações como alocação de memória, gerenciamento de drivers, módulos, recursos e dispositivos do sistema operacional e computador.
Lidando com a execução de programas, e gerenciamento de permissões e privilégios que usuários e programas possuem sobre outros arquivos, usários, dispositivos e componentes do computador sistema operacional como um todo.
O ventoy é uma ferramenta usada criar um pendrive multi-boot, ou seja, capaz de inicializar vários tipos de sistemas operacionais a partir da mídia de instalação deles, sem a necessidade de extrair o conteúdo delas. Ele suporta esses arquivos de mídia em diferentes formatos, como .iso/.img/.vhd/.efi/ etc...
Na inicialização, o firmware UEFI irá consultar sua tabela interna de configurações de entradas de boot registradas (armazenada em NVRAM), para determinar qual arquivo .efi de boot ele deve carregar e executar. Cada entrada de boot registrada na tabela interna dele, possui um identificador de entrada (label) e o caminho absoluto para o arquivo .efi na partição ESP.
NVRAM (Non-Volatile Random Access Memory) é uma memória não volatil, usada para armazenar informações cruciais para o funcionamento do computador e do firmware UEFI.
Arquivos .efi são binários utilizados pelo firmware UEFI durante a inicialização. Eles geralmente são  gerados e utilizados por bootloaders (GRUB, sysboot etc...), eles geralmente ficam na partição ESP de boot. O firmware UEFI fica responsável por carregar e executar o arquivo .efi correto, com base nas configurações de entradas de boot registradas na tabela interna armazenada na NVRAM.
Esses arquivos são responsáveis por executarem o processo de inicialização do sistema operacional. Esse processo de inicialização varia de acordo com o bootloader utilizado.
Ao escolher o ISO, o ventoy fornece 3 opções de boot a partir do arquivo ISO. E cada forma é util em diferentes contextos, e são usadas dependendo do firmware utilzado e do ISO.
O firmware UEFI localiza a entrada de boot na sua tabela, e carrega o arquivo binário BOOTX64.efi do ventoy, ele é responsável por carregar os outro "drivers" .efi e realizar a inicialização básica do ventoy. Para então carregar o seu grubx64.efi para scanear por mídias de inicialização suportadas e exibir o menu de ISOs, que ele encontrou na sua partição reservada para elas.
No caso do ventoy, o firmware UEFI inicializa a partição ESP VFAT do dispositivos de armazenamento. Essa partição foi criada pelo ventoy para armazenar os arquivos de BOOT usados por ele, e pelo firmware UEFI durante inicialização.
Em ambas as formas, o ventoy também será responsável por localizar, acessar e fazer o chainload do binário .efi ou .bin de bootloader do ISO, assim fazendo com que o firmware carregue e execute o bootloader do ISO. Esse bootloader do ISO irá acessar e carregar os arquivos de inicialização do sistema operacional (como o kernel e initramfs.img) do ISO, a partir do dispositivo bloco virtual que ventoy disponibiliza.
Ao escolher inicializar o sistema operacional do ISO em modo GRUB2. O próprio ventoy carrega seu GRUB2, e ele é responsável por criar o dispositivo virtual de bloco (loop) para o ISO.
Para assim, localizar o arquivo grub.cfg/loopback.cfg, e então carrega-lo, pasando também as informações básicas para o grub.cfg do ISO poder localizar e carregar o kernel e initramfs.img do ISO.
Utilizado por firmwares e mídias de instalação mais antigas BIOS-legacy real-mode 16-bit. Ao selecionar o modo "Memdisk Mode" para inicializar o sistema operacional do ISO, o ventoy carrega o módulo "memdisk" do Sysllnux via linux16/initrd.
O memdisk transforma qualquer imagem de disco, em uma unidade em RAM.
No UEFI, ao escolher inicializar os sistema operacional do ISO em modo normal (compativel), o bootloader .efi do ventoy vai registrar um handler/driver que utiliza o protocolo UEFI Block I/O junto com filesystem ISO9660 para ler os blocos físicos do ISO corretamente. E então acessar e carregar a imagem (LoadImage()) do bootloader .efi do ISO, passando o mesmo handler/driver do ISO para ele.
O firmware BIOS carrega o MBR que está no pendrive, onde está instalado o primiero estágio do ventoy. No primeiro estágio o ventoy carrega menu de ISOs, ao escolher o modo normal para inicializar o sistema operacional do ISO, o estágio 2 começa.
Esse handler do ventoy, vai fornecer uma abstração para bootloader .efi do ISO acessar os dirétorios e arquivos do ISO.
Quando o ventoy carrega o bootloader .efi do ISO, ele automatiamcente passa o mesmo handler de CD-DVD virtual do ISO para ele. Para assim, o bootloader .efi do ISO requisitar as operações de leitura do CD-ROM virtual do ISO, através do handler passado para ele. E esse handler do ventoy vai ser responsável por ler blocos de dados do ISO e devolver os bytes para o bootloader .efi do ISO, em execução.
Apresentar o as fontes e trechos de código para confirmar a explicação.
O módulo memdisk transforma qualquer imagem de disco, em uma unidade na RAM. Ou seja, ele copia todo o sistema de arquivos do para a RAM.O handler do ventoy vai possibilitar mapear os blocos de dados do ISO, e mapear as entradas de diretorios e arquivos por meio de um simple file system via ISO9660/UDF.efi. Esse handler possui um Device Path associado a ele, que aponta diretamente para o arquivo ISO em si.
Na emulação de CD-ROM em BIOS, o ventoy instala hook de INT 13h (funções de leitura de setor do BIOS) para então responder às requisições de leitura de setor, como se fosse um "drive" de CD/DVD real.
INT 13h é uma das interrupções do BIOS, presente na tabela de vetores de interrupção (IVT), ela acontece em modo real 16-bit. Essa interrupção é usada para chamadas para leitura/gravação em setores do disco.
Esse é o modo mais usado, pois é o mais compativel com a maioria dos sistemas operacionais e firmwares.
O initramfs.img do ISO é responsável por montar o sistema de arquivos raiz que o usuário utilizara no sistema operacional live. Esse sistema de arquivos fornecera as ferramentas necessárias para a instalação real do sistema operacional.
Para isso o GRUB2 possui seus próprios modulos compilados, como o loopback.mod para a criação de dispositivos virtuais de bloco (loop) para arquivos .ISO. E iso9660/udf.mod para poder interpretar os arquivos e dirétorios dos blocos do ISO.
Para isso, o initramfs.img do ISO vai criar um dispositivo virtual de bloco (loop) para o sistema de arquivos raiz que o próprio ISO disponibiliza para ser usado no ambiente LIVE (airootfs.sfs ou roofs.sfs). SFS (Squash FIle System) é um sistema de arquivos comprimido e read-only.
Muitas distros, usam o .sfs para embalar todo o sistema que vai rodar em RAM. No boot, o initramfs inicializa um device loop para o .sfs, monta-o e faz um overlay (unionfs) para permitir gravação em RAM sem alterar o arquivo original do sistema de arquivos raiz do .sfs.
O módulo memdisk aloca um buffer em RAM do mesmo tamanho da imagem de disco e copia os bytes dele para lá. Em real-mode, ele intercepta chamadas INT 13h leitura/escrita de setor e as redireciona para buffer em RAM, assim,  emulando um dispositivo de bloco físico.
O memdisk fica responsável por carregar o bootloader da imagem de disco, e assim iniciar o processo de inicialização real, usando o buffer em RAM como "disco".
VMs (Virtual Machines) são ambientes virtuais que simulam um computador, incluindo seus componentes de hardware e software.
Isso é feito por meio do processo de virtualização. Através de softwares que emulam hardwares, e que fornecem suporte para outros softwares serem executados neles.
Criando uma cópia isolada de um sistema físico, dentro do atual sistema.
Dessa forma, permitindo executar sistemas operacionais e programas dentro delas.

O módulo memdisk transforma qualquer imagem de disco, em uma unidade na RAM. Ou seja, ele copia todo o sistema de arquivos do ISO para a RAM.

