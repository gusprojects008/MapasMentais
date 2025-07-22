# Arch Linux: Conceitos Básicos + Instalação

## Por que usar Arch Linux?
- Melhor entendimento do funcionamento do computador e **sistema operacional**.
- Ideal para quem está estudando e começando na área da **computação**.
- É um **software livre** e de **código aberto**, fornecendo mais **transparência**.
- Liberdade em escolher programas e aplicações livres e de código aberto, que não coletam dados, ou que permitem a escolha de quais dados fornecer (**privacidade**).
- Maior controle sobre o sistema, o que é utilizado e o que você usa no dia a dia.
- Programas de código aberto são analisados por várias pessoas e estão constantemente em desenvolvimento, recebendo **atualizações** para correção de bugs e vulnerabilidades.

---

## Conceitos Básicos

### Tabelas de Partições
- Um sistema de tabela de partições define como um dispositivo de armazenamento gerencia e organiza suas partições.

#### Partição Estendida (Legacy)
- Usada para criar outras **partições lógicas** dentro dela.
- Geralmente usadas para armazenar arquivos e, em alguns casos, sistemas operacionais.
- Normalmente não podem ser usadas para inicializar sistemas operacionais.

#### Partições Primárias (Legacy e Moderno)
- Usadas para armazenar arquivos e sistemas operacionais.
- Também são as partições que o firmware pode usar para inicializar os sistemas operacionais, sendo as **partições de bootloader**.

#### Setor de Dispositivo de Armazenamento
- O menor bloco físico de armazenamento acessível em um dispositivo, geralmente com 512 bytes de espaço.

#### MBR (Master Boot Record)
- Sistema de tabela de partições antigo, utilizado pelo **firmware BIOS**.
- Funciona através da inicialização do primeiro setor de armazenamento válido para boot, conhecido como **MBR**, identificado por uma flag de boot (`0x55AA`).
- O MBR armazena um pequeno código que lê a tabela de partições do MBR, identifica a partição **VBR (Volume Boot Record)** ativa para transferir o controle para o setor de boot dela e iniciar o segundo estágio de boot. Isso pode iniciar o kernel diretamente em sistemas mais avançados, ou mais comumente, iniciar o bootloader.
- Dentro do setor MBR, 64 bytes são usados para tabelar e definir as 4 partições do dispositivo de armazenamento, incluindo a VBR ativa.
- Compatível e usado com **firmware BIOS**.
- Possui limitações significativas comparado ao GPT, como: 2TB por partição e apenas 4 partições primárias, ou 3 partições primárias e uma partição estendida, que pode armazenar até 63 sub-partições lógicas.

#### GPT (GUID Partition Table)
- Sistema de tabela de partições nativamente compatível com o **firmware UEFI**.
- Utiliza **GUIDs (Globally Unique Identifier)** para cada partição.
- Não existem conceitos de partições estendidas ou lógicas; todas são **primárias**, cada uma com um identificador global único.
- Permite a criação de 128 ou mais partições primárias, com tamanhos de até 9.4 Zettabytes (ZT).

### Firmwares
- O **firmware** de um dispositivo específico (como um adaptador Wi-Fi ou placa de rede) é o software responsável por gerenciar e controlar internamente os recursos do circuito do dispositivo.
- Responsável por:
    - Inicialização de circuitos, microcontroladores e módulos de hardware.
    - Gerenciamento de modo de energia (economia ou desempenho).
    - Processamento de comandos vindos do driver.
    - Implementação de operações de protocolo (ex: 802.11 em tempo real).
    - Monitoramento de falhas.
- O firmware de uma **placa-mãe** é o software que identifica, analisa, inicia e gerencia o comportamento inicial dos dispositivos básicos do computador (CPU, RAM, I/O, armazenamento como HD e SSD), realizando a intercomunicação e controlando a distribuição de recursos como energia e memória.
- Geralmente armazenado em um chip de memória (ROM, PROM, EPROM ou memória flash) na placa-mãe ou no circuito específico.
- Em muitos dispositivos modernos que recebem atualizações regulares, os fabricantes fornecem os binários do firmware para que o kernel do sistema operacional os carregue na RAM ou no próprio dispositivo durante a inicialização.
- O firmware é por fim, responsável por executar as operações internas (manipulando recursos, componentes e microcontroladores no circuito) para que o dispositivo execute suas funções.

#### BIOS (Basic Input/Output System)
- É o tipo mais básico de firmware, que fornece uma interface e funcionalidades básicas para gerenciar as configurações internas do computador e seus dispositivos, assim como a inicialização deles.
- Possui muitas limitações com os dispositivos atuais.
- Suporta apenas dispositivos de armazenamento que utilizam o sistema de tabela de partições **MBR**.

#### EFI (Extensible Firmware Interface)
- Surgiu para superar as limitações do firmware BIOS devido aos avanços nas capacidades do hardware na época.
- Projetado para utilizar o sistema de tabela de partições **GPT**, ideal para dispositivos de maior capacidade de armazenamento.

#### UEFI (Unified Extensible Firmware Interface)
- Uma extensão unificada e padronizada do EFI, baseada em suas funcionalidades e capacidades.
- Possui recursos e funcionalidades que permitem suporte a mais dispositivos e a definição de configurações específicas para eles.

### Processo de Inicialização do Computador
- **Power Switch (PS):** Ao pressionar o botão de energia, um circuito na placa-mãe detecta a mudança de estado (normalmente fechando o circuito momentaneamente). Esse sinal elétrico é enviado para o chipset ou um controlador de energia da placa-mãe, fazendo com que ele interprete o sinal e inicie o sequenciamento de energia.
- **Sequenciamento de Energia:** Os componentes são inicializados de forma específica e correta para evitar danos.
- **Sinal PS_ON e PG:** O controlador envia um sinal PS_ON (Power Supply On) para a fonte de alimentação. Após o circuito da fonte de alimentação verificar a tensão, ela retorna um sinal de PG (Power Good) para o controlador, indicando que é seguro iniciar o processo de inicialização e o **POST (Power-On Self-Test)**.
- **Liberação da CPU:** Com o sinal PG recebido, o controlador ou chipset libera a CPU do seu estado atual (RESET) e a prepara para executar o código do firmware, que está em um endereço de memória correspondente ao chip de memória onde o firmware está armazenado.
- **Execução do Firmware e POST:** A CPU acessa e executa as instruções do firmware, que inicia o teste de POST.

### Sistemas de Arquivos
- Softwares responsáveis por definir como os dados (arquivos) serão armazenados, organizados e gerenciados em uma partição.
- Definem informações sobre os arquivos (metadados), como data e hora de registro, permissões etc.
- Muitos oferecem funcionalidades como **journaling** para registro de logs de operações de leitura ou escrita em arquivos, aumentando a segurança contra corrupção de dados e facilitando a identificação de erros.

### Drivers
- Softwares, genéricos ou desenvolvidos pelos próprios fabricantes, responsáveis por realizar a comunicação direta com o dispositivo específico, executando operações diretamente nele, ou transmitindo instruções que o firmware do dispositivo irá processar e executar no hardware em si.

### Bootloaders
- Responsável por inicializar o sistema operacional na **memória RAM** do computador.
- Pode ser armazenado em uma partição especial do dispositivo de armazenamento (HD, SSD) como partição EFI em casos de GPT/UEFI, ou em setores específicos do dispositivo de armazenamento, caso utilize MBR.
- O firmware identifica as partições de boot por meio da leitura da estrutura de dados sobre partições do dispositivo de armazenamento, criada pelo sistema de tabela de partições (GPT, MBR etc...). Na estrutura, ele identifica a primeira entrada de partição que possua a flag de "boot", indicando que ela é inicializável.
- O bootloader localiza e carrega o kernel comprimido na memória RAM, transfere o controle a ele. O kernel se descomprime sozinho na memória RAM, através do código de descompressão que ele carrega, conhecido como "bootstrapping code".
- Após ser carregado, o kernel assume o controle e inicia as operações básicas, como: alocação e gerenciamento de memória e processos, e comunicação com o hardware. Fica responsável por carregar os drivers e módulos básicos e essenciais para carregar e iniciar o **initramfs.img** na memória RAM.
- E utilizar o sistema de arquivos raiz dele temporariamente, para que possa localizar, montar e iniciar o sistema de arquivos da partição raiz real e definitiva do sistema operacional "/", por meio de scripts do sistema de arquivos do initramfs.img, de montagem e inicialização da partição raiz "/", de acordo com as configurações de boot que o usuário definiu.
- Após a inicialização do sistema de arquivos da partição raiz, o kernel encontra e inicia o "init" do sistema, como o **systemd** ou **runit**, como processo número 1 do sistema.

### initramfs.img
- Um sistema de arquivos raiz temporário carregado na memória RAM, agindo como um "mini sistema operacional".
- Possui drivers, módulos e scripts específicos usados pelo kernel, para poder localizar, montar e inicializar o sistema de arquivos da partição raiz real do sistema operacional, de acordo com as configurações de boot que o usuário definiu para esse processo.
- Através do `initramfs.img`, configurações específicas de montagem e inicialização da partição raiz podem ser definidas, de acordo com os objetivos ou propósitos do usuário, como criptografia de disco, ou configurações de rede específicas, geralmente utilizadas em servidores.
- Esse processo torna a arquitetura do sistema operacional mais limpa, modular, eficiente, flexível e adaptável para diferentes contextos, gostos, propósitos e objetivos.
- Dividindo o sistema operacional em diferentes partes, torna mais fácil a manutenção, análise e adaptação do sistema e softwares para diferentes contextos.
- Fornece mais flexibilidade e facilidade para a manutenção e análise para identificação de vulnerabilidades no sistema.

### Kernel
- Responsável por executar e gerenciar a comunicação do usuário com o hardware, os programas e o sistema operacional, e vice-versa.
- Faz operações como alocação de memória, gerenciamento de drivers, módulos, recursos e dispositivos do sistema operacional e computador.
- Lida com a execução de programas, e gerenciamento de permissões e privilégios que usuários e programas possuem sobre outros arquivos, usuários, dispositivos e componentes do computador e sistema operacional como um todo.

### PACMAN
- Gerenciador de pacotes usado no Arch Linux.
- Durante a instalação do Arch Linux, os pacotes são instalados na partição raiz que o sistema operacional irá utilizar, por meio do `pacstrap`.

### NVRAM (Non-Volatile Random Access Memory)
- Memória não volátil, usada para armazenar informações cruciais para o funcionamento do computador e do firmware UEFI.
- Armazena a tabela interna de configurações de entradas de boot registradas do firmware UEFI.

### Arquivos `.efi`
- Binários utilizados pelo firmware UEFI durante a inicialização.
- Geralmente ficam na partição ESP de boot.
- O firmware UEFI é responsável por carregar e executar o arquivo `.efi` correto, com base nas configurações de entradas de boot registradas na tabela interna armazenada na NVRAM.
- Se na tabela interna não houver uma entrada para um arquivo `.efi` específico, ele carrega e executa o `BOOTX64.efi` como fallback, em casos de dispositivos removíveis. Se não houver nenhum arquivo `.efi`, o firmware UEFI retorna um erro, espera a intervenção do usuário, e então reinicia o computador redirecionando o usuário para a interface do firmware UEFI.
- Em alguns casos, pode-se usar o "efibootmgr" para registrar uma entrada de boot diretamente para o kernel, caso o kernel seja compilado para um arquivo no formato `.efi`, para que o firmware possa carregar e executar ele diretamente, sem a necessidade do GRUB ou outro bootloader.
- Esses arquivos são responsáveis por executarem o processo de inicialização do sistema operacional, que varia de acordo com o bootloader utilizado.

### Ventoy
- Ferramenta usada para criar um pendrive multi-boot, capaz de inicializar vários tipos de sistemas operacionais a partir da mídia de instalação deles, sem a necessidade de extrair o conteúdo.
- Suporta arquivos de mídia em diferentes formatos, como .iso/.img/.vhd/.efi/ etc....

#### Inicialização do Ventoy em UEFI
- Na inicialização, o firmware UEFI consulta sua tabela interna de configurações de entradas de boot registradas (armazenada em NVRAM), para determinar qual arquivo `.efi` de boot ele deve carregar e executar. Cada entrada de boot registrada na tabela interna aponta para um `.efi` da partição ESP/EFI do bootloader.
- No caso do Ventoy, o firmware UEFI inicializa a partição ESP VFAT do dispositivo de armazenamento. Essa partição foi criada pelo Ventoy para armazenar os arquivos de BOOT usados por ele e pelo firmware UEFI durante a inicialização.
- O firmware UEFI localiza a entrada de boot na sua tabela e carrega o arquivo binário `BOOTX64.efi` do Ventoy. Ele é responsável por carregar os outros "drivers" `.efi` e realizar a inicialização básica do Ventoy. Para então carregar o seu `grubx64.efi` para escanear por mídias de inicialização suportadas e exibir o menu de ISOs, que ele encontrou na sua partição reservada para elas.
- Basicamente, o Ventoy utiliza uma versão do GRUB modificada, que nativamente possui suporte ao acesso e leitura da estrutura de arquivos e diretórios do `.iso`, e assim inicializar o bootloader dentro do ISO. Mas esse processo ocorre de maneiras diferentes, dependendo do firmware que é utilizado.
- Em ambas as formas, o Ventoy também será responsável por localizar, acessar e fazer o `chainload` do binário `.efi` ou `.bin` de bootloader do ISO, assim fazendo com que o firmware carregue e execute o bootloader do ISO. Esse bootloader do ISO irá acessar e carregar os arquivos de inicialização do sistema operacional (como o kernel e initramfs.img) do ISO, a partir do dispositivo bloco virtual que o Ventoy disponibiliza.

##### Modos de Boot do Ventoy para ISO (UEFI)
- Ao escolher o ISO, o Ventoy fornece 3 opções de boot a partir do arquivo ISO. Cada forma é útil em diferentes contextos e é usada dependendo do firmware e do ISO utilizados.
- Ao escolher inicializar o sistema operacional do ISO em modo GRUB2, o próprio Ventoy carrega seu GRUB2, e ele é responsável por criar o dispositivo virtual de bloco (loop) para o ISO. Para isso, ele localiza o arquivo `grub.cfg/loopback.cfg`, e então o carrega, passando também as informações básicas para o `grub.cfg` do ISO poder localizar e carregar o kernel e initramfs.img do ISO. Para isso, o GRUB2 possui seus próprios módulos compilados, como o `loopback.mod` para a criação de dispositivos virtuais de bloco (loop) para arquivos `.ISO`, e `iso9660/udf.mod` para poder interpretar os arquivos e diretórios dos blocos do ISO.
- No UEFI, ao escolher inicializar o sistema operacional do ISO em modo normal (compatível), o bootloader `.efi` do Ventoy vai registrar um *handler/driver* que utiliza o protocolo **UEFI Block I/O** junto com o *filesystem* ISO9660 para ler os blocos físicos do ISO corretamente. E então acessar e carregar a imagem (`LoadImage()`) do bootloader `.efi` do ISO, passando o mesmo *handler/driver* do ISO para ele.
- Esse *handler* do Ventoy vai fornecer uma abstração para o bootloader `.efi` do ISO acessar os diretórios e arquivos do ISO. Quando o Ventoy carrega o bootloader `.efi` do ISO, ele automaticamente passa o mesmo *handler* de CD-DVD virtual do ISO para ele. Para assim, o bootloader `.efi` do ISO requisitar as operações de leitura do CD-ROM virtual do ISO, através do *handler* passado para ele. E esse *handler* do Ventoy vai ser responsável por ler blocos de dados do ISO e devolver os bytes para o bootloader `.efi` do ISO, em execução.
- O *handler* do Ventoy vai possibilitar mapear os blocos de dados do ISO, e mapear as entradas de diretórios e arquivos por meio de um *simple file system* via `ISO9660/UDF.efi`. Esse *handler* possui um *Device Path* associado a ele, que aponta diretamente para o arquivo ISO em si.
- Este é o modo mais usado, pois é o mais compatível com a maioria dos sistemas operacionais e firmwares.

#### Inicialização do Ventoy em BIOS
- O firmware BIOS carrega o **MBR** que está no pendrive, onde está instalado o primeiro estágio do Ventoy. No primeiro estágio, o Ventoy carrega o menu de ISOs. Ao escolher o modo normal para inicializar o sistema operacional do ISO, o estágio 2 começa.
- Na emulação de CD-ROM em BIOS, o Ventoy instala um *hook* de **INT 13h** (funções de leitura de setor do BIOS) para então responder às requisições de leitura de setor, como se fosse um "drive" de CD/DVD real.
- **INT 13h** é uma das interrupções do BIOS, presente na tabela de vetores de interrupção (IVT), que acontece em modo real 16-bit. Essa interrupção é usada para chamadas para leitura/gravação em setores do disco.

##### Modo Memdisk (Legacy)
- Utilizado por firmwares e mídias de instalação mais antigas (BIOS-legacy real-mode 16-bit).
- Ao selecionar o modo "Memdisk Mode" para inicializar o sistema operacional do ISO, o Ventoy carrega o módulo "memdisk" do Syslinux via `linux16/initrd`.
- O módulo `memdisk` aloca um buffer em RAM do mesmo tamanho da imagem de disco e copia os bytes dele para lá. Em *real-mode*, ele intercepta chamadas **INT 13h** de leitura/escrita de setor e as redireciona para o buffer em RAM, assim, emulando um dispositivo de bloco físico.
- O `memdisk` fica responsável por carregar o bootloader da imagem de disco, e assim iniciar o processo de inicialização real, usando o buffer em RAM como "disco".

### initramfs.img do ISO (Ambiente Live)
- O `initramfs.img` do ISO é responsável por montar o sistema de arquivos raiz que o usuário utilizará no sistema operacional live. Esse sistema de arquivos fornecerá as ferramentas necessárias para a instalação real do sistema operacional.
- Para isso, o `initramfs.img` do ISO vai criar um dispositivo virtual de bloco (loop) para o sistema de arquivos raiz que o próprio ISO disponibiliza para ser usado no ambiente LIVE (`airootfs.sfs` ou `rootfs.sfs`).
- **SFS (Squash File System)** é um sistema de arquivos comprimido e *read-only*.
- Muitas distros usam o `.sfs` para empacotar todo o sistema que vai rodar em RAM. No boot, o `initramfs` inicializa um *device loop* para o `.sfs`, monta-o e faz um *overlay (unionfs)* para permitir gravação em RAM sem alterar o arquivo original do sistema de arquivos raiz do `.sfs`.

### VMs (Virtual Machines)
- Ambientes virtuais que simulam um computador, incluindo seus componentes de hardware e software.
- Isso é feito por meio do processo de virtualização. Através de softwares que emulam hardwares, e que fornecem suporte para outros softwares serem executados neles.
- Criam uma cópia isolada de um sistema físico, dentro do atual sistema.
- Dessa forma, permitem executar sistemas operacionais e programas dentro delas.

---

### Links e Referências
- **História da arquitetura do Linux e outros sistemas operacionais baseados em Unix:** [Unix](https://pt.wikipedia.org/wiki/Unix)
- **Sistema de tabela de partições:**
  - [GPT](https://www.easeus.com/images/en/screenshot/partition-manager/gpt-disk-layout.png)
  - [MBR](https://br.easeus.com/images/en/screenshot/partition-manager/mbr-disk-structure.png)
- **Sistema de arquivos:** [Sistemas de arquivos](https://pt.wikibooks.org/wiki/Sistemas_operacionais/Sistemas_de_arquivos)
- **Memória ROM, RAM, NVRAM:**
  - [ROM](https://siaguanta.com/wp-content/uploads/2019/12/rom2.png)
  - [Pendrives e cartões SD](https://miracomosehace.com/wp-content/uploads/2020/05/usb-blanco.jpg)
  - [Memória RAM](https://www.guiahardware.es/wp-content/webp-express/webp-images/uploads/2018/12/memoria-ram-1024x512.jpeg.webp)
  - [NVRAM](https://comphome.ru/wp-content/uploads/post/nvram.jpg)
- **UEFI Protocols:**
  - [UEFI LoadFile](https://uefi.org/specs/UEFI/2.10/13_Protocols_Media_Access.html#efi-load-file-protocol-loadfile)
  - [UEFI Block I/O](https://uefi.org/specs/UEFI/2.10/13_Protocols_Media_Access.html#block-i-o-protocol)
  - [UEFI Media Access](https://uefi.org/specs/UEFI/2.10/13_Protocols_Media_Access.html)
- **Bootloaders, initramfs.img, loopback.cfg, iso9660, GRUB2 mode:**
  - https://gist.github.com/Hanaasagi/2665e1e28ffcf91d5d62f72fa52fb732/revisions
  - https://gist.github.com/Hanaasagi/2665e1e28ffcf91d5d62f72fa52fb732
  - [loopback](https://github.com/Jolicloud/grub2/blob/master/disk/loopback.c)
  - [SuperGRUB loopback.cfg](https://www.supergrubdisk.org/wiki/Loopback.cfg)
  - [GRUB2 iso9660](https://github.com/Jolicloud/grub2/blob/master/fs/iso9660.c)
  - [GRUB2 BOOT](https://www.ventoy.net/en/doc_grub2boot.html)
- **Pendrive bootável, Ventoy:**
  - [https://www.ventoy.net](https://www.ventoy.net)
  - [https://www.ventoy.net/en/doc_disk_layout.html](https://www.ventoy.net/en/doc_disk_layout.html)
