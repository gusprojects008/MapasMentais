# process structure

jk

Images source:

Recommended content:

RAM (Random Access Memory) is a passive component that only has the function of storing data in the physical addresses of the memory cells, temporarily storing the code, data and files of the programs during their execution.
Thus, the processor dynamically searches for and accesses the data in the physical memory addresses, loads it into the registers or cache, processes it and executes the instructions and operations in its internal logic circuits.

RAM is a passive component that only has the function of storing data in the physical addresses of the memory cells, temporarily storing the code, data and files of the programs during their execution.
Thus, the processor dynamically searches for and accesses the data in the physical memory addresses, loads it into the registers or cache, processes it and executes the instructions and operations in its internal logic circuits.

Translated with DeepL.com (free version)

Some RAM modules (DDRM4/DDR5) have auxiliary circuits and firmware to provide additional and specific functionalities, such as:

Power Management Integrated Circuit (PMIC)

Error Correction Code (ECC)

:

is

Unlike other devices or components, conventional RAM does not use or have driver or active firmware to handle internal data processing, such as allocating information and updating it.
As such, it is the physical ram memory units that manage and manipulate , which are responsible for communicating with it directly.

Create programs in languages that use fewer abstractions, such as C, C++, rust, assembly and others... to understand and apply these concepts in a practical way.

O kernel é o núcleo do sistema operacional, ele é armazenado na partição de boot "/boot" do dispositivo de armazenamento (HD ou SSD).
Ele é compilado e comprimido (bzimage geralmente) para ser carregado mais rápidamente na memória RAM pelo bootloader (grub, syslinux, efiboormgr (para registrar o kernel diretamente na partição EFI), etc...), ele se descomprime sozinho na memória RAM (em código máquina) e assume o controle dando continuidade a inicialização do sistema.

PCB (Process Control Block):
https://duckduckgo.com/?q=estrutura+PCB+process+control+block&t=ffab&iar=images&iai=https%3A%2F%2Fcdn.testbook.com%2Fimages%2Fseo%2Fprocess-control-block.png

Armazenamento, memória ram e outras:
https://www.newtoncbraga.com.br/eletronica-digital/16358-curso-de-eletronica-eletronica-digital-memorias-adcs-e-dacs-cur5013.html

Memórias virtuais e PCB:
https://ajamias.github.io/openos/textbook/mm/intro.html
https://pt.wikipedia.org/wiki/Bloco_de_controle_de_processo
https://soescola.com/glossario/o-que-e-file-descriptor#gsc.tab=0

Compiladores, montadores, arquivos objeto, linkers e executáveis e formatos de executáveis:
https://pt.wikipedia.org/wiki/Arquivo_objeto

Processadores e componentes eletrônicos:
https://wiki.sj.ifsc.edu.br/index.php/MI1022806_2020_2_AULA08#Interrup%C3%A7%C3%B5es
https://gil0mendes.gitbooks.io/assembly/content/system_calls.html
https://www.cin.ufpe.br/~cagf/if677/2017-2/slides/04-05_processo+interrupcao+syscall.pdf
https://www.passeidireto.com/arquivo/65117084/barramentos-arquitetura-de-computadores
https://youtu.be/dX9CGRZwD-w?feature=shared
https://youtu.be/AF8d72mA41M?feature=shared
https://youtu.be/e_hU6sAON2U?feature=shared
https://youtu.be/uByQnP5FsVY?feature=shared
https://youtu.be/uQPiyxoCk9E?feature=shared

Armazenamento, memória ram e outras:
https://www.newtoncbraga.com.br/eletronica-digital/16358-curso-de-eletronica-eletronica-digital-memorias-adcs-e-dacs-cur5013.html

Memórias virtuais e estrutura de

Nenhum programa ou mesmo o kernel 
O kernel é apenas executado na memória ram, e possui a capacidade de reagir a eventos, e executar as cadeias de funções que reage a esse eveto

Nenhum programa ou mesmo o kernel, consegue gerar bytes ou código "do nada". Para o kernel executar um instrução no processador, é preciso ocorrer um evento (ponta pé incial/motivo) para ele executarou possui a capacidade de reagir a eventos, e executar as cadeias de funções que reage a esse evento

Ele é pré-programado para fornecer instruções e assumir o controle da comunicação entre os softwares e os hardwares do computador.
Para isso, ele possui drivers e módulo básicos, sub-sistemas e funções prontas para lidar com os eventos do sistema, que podem ser: interrupções, exeções, timers, eventos de dispositivos, entre outros...

As interrupções são inicialmente identificadas através do um circuito lógico interno da própria CPU, que é responsável por identificar uma sequência específica que indica uma syscall pelo programa,  assim, a CPU verifica o valor da syscall já passada pelas instruções do programa, na tabela IDT inicializada e configurada pelo kernel durante a inicialização, assim a CPU obtém o endereço da ISR associada ao valor da syscall, para assim a ISR resolver a interrupção do programa.

Cada interrupção possui um nível de prioridade específico de acordo com o processador.

Detalhes importantes saber para entender como a CPU executa syscalls ou lida com outros eventos do sistema:

A CPU

Em contexto de criação e gerenciamento de pocessos, o kernel é reponsável por fornecer suporte para a CPU executar as intruções dos programas.
Ele faz isso através de vários mecanismos, sub-sistemas e funções já pré programadas e carregadas na memória RAM (através do bootloader durante a inicialização). Prontas para serem executadas quando a CPU detectar interrupções (hardware/software) ou outros eventos do sistema (através do circuito interno dela, responsável por detectar interrupções como syscalls (int 0x80 ou "syscall" em x86/x64) durante a execução de instruções, e assim iniciar o processo para resolver ela).

Dessa forma, quando um programa é executado, o kernel geralmente executa syscall fork() e execve() proveniente do processo pai que forneceu suporte ao usuário para executar um programa no sistema. Esse processo pai pode ser um shell que recebeu um comando do terminal a partir da entrada do usuário através do teclado. Ou a partir do clique do usuário através do mouse, no ícone de um programa, disparando um evento no servidor gráfico, e assim o servidor gráfico se comunica com o gerenciador de janelas do usuário, fazendo com que o gerenciador de janelas chama a syscall fork() e execve(). Ou a execução pode acontecer também de outras formas como atalhos ou processos agendados.

Possíveis duvidas em situações práticas

Então o que acontece quando estou na interface gráfica e clico no ícone do terminal? quem será o processo pai nesse caso?

Mostrar os mapas de memória que refletem as informações das page tables dos processos, em "/proc/PID/maps".

Usar ferramentas de depuração como o strace para mostrar na prática a criação de processos.
"strace -o output.log -e trace=read,mmap etc... command"

Mostrar logs do kernel criando as page tables e alocando memória.

Mostrar como kernel lê e carrega as seções o cabeçalho ELF em páginas da table pages de um processo na memória RAM.
Usar "xxd" para ler o código assembly, e ver como os mnemonicos convertidos para opcodes em hexadecimal.

Mostrar exemplos de códigos usados que aplicam os conceitos:
PCB, page tables, syscall usadas pelos programas para gerenciar memória e executar programas, tabela IDT e as ISRs.
"linux/kernel/fork.c"
"linux/include/linux/sched.h"
"linux/mm/memory.c"
"linux/mm/mmap.c"
"linux/arch/x86/kernel/idt.c"
"linux/arch/x86/kernel/traps.c"
"/proc/interrupts/"
"lsof"

Mostrar a comunicação i2c do kernel, para mostrar o funcionamento básico do teclado.
Através de: "cat /dev/kmsg | grep "i2c""

Quando o código do processo filho tenta escrever em uma PTE (Page Tables Entrie ou página) dele, a CPU gera uma exeção chamada "page fault", pois as páginas estão mapeadas para apontarem para os endereços físicos das páginas do processo pai. Dessa forma, as unidades do processador: MMU e IMC; não conseguirão fazer a operação de escrita, pois a página do processo filho está apenas para leitura e não possui um endereço físico próprio na RAM para a MMU através do IMC acessar e fazer a operação de escrita.

A memória RAM possui circuitos passivos para acessar e executar as operações do IMC do processador, que são passadas através de barramentos para os circuitos do módulo de RAM. Os endereços de memória das células, são na verdade dados que os circuitos passivos internos da memória RAM, interpretam e usam para acessar linhas e colunas específica que acessam uma célula específica, e assim armazenando ou acessando a informação que o  IMC enviou ou requisitou. Os circuito internos da memória ram utilizam multiplexadores e demultiplexadores para acessarem linha e colunas específicas das memórias.

O kernel é responsável por gerenciar eles, para isso, ele utiliza várias funções e sub-sistemas prontos para fazerem o gerenciamento de memória e execução de programas. Mas para o kernel ter mais controle e organização no fluxo de execução de processos pela CPU, e no gerenciamento da hierarquia e compartilhamento ou herança de recursos entre processos, ele utiliza uma estrutura PCB para cada tabela de páginas de um programa.
Dessa forma, através da estrutura PCB que kernel define para cada tabela de páginas, podemos monitorar e gerenciar os processos dos programas em execução, por meio de um gerenciador de processos (task manager ou htop/top).

Assim o IMC da memória RAM por exemplo, envia através de barramentos um endereço de memória e o bit a ser armazenado em uma célula específica. Então os circuitos internos lógicas da memória RAM, decodificam o endereço de memória para obter o bits que acessam a linha e os bits que acessam a coluna da memória, e gravar ou ler a célula específica.

Processos no sistema operacional, são instâncias de um programa carregado na memória RAM e em um estado específico, podendo estar em execução, pronto para ser executado, dormindo, ou outros estado dependo da função do programa ou estado do sistema operacional.

A CPU possui um papel muito importante na execução das instruções dos programas, incluindo as operações do kernel, responsável também por fornecer o suporte para a execução dos programas, atendendo as chamadas de funções deles, comunicação com os dispositivos e I/O. A

A CPU (Unidade de Processamento Central) é o componente principal do computador, ela é consituida por vários circuitos lógicos, 
e organizados em unidades de acordo com suas funções. Os circuitos são compostos por vários componentes eletrônicos, fabricados com materias específicos, selecionados de acordo com suas propriedades fisicas, capacidades e funções.  Dessa forma, a CPU consegue processar e interpretar vários dados de acordo com as instruções dos programas, manipulando o fluxo de elétrons em operações binárias (lógicas e aritméticas) realizadas pelos circuitos, ondes os resultados são representados como bits.

A CPU possui as unidades responsáveis pelo gerenciamento de memória e comunicação com a memória RAM, local onde os dados e instruções dos programas são carregados e executados de acordo com o fluxo de processamento e execução do programa.

A MMU (Memory Management Unit) é responsável por mapear os endereços virtuais das page tables dos processos para endereços físicos nas células dos chips de memória RAM, para assim, através da unidade IMC (Integrated Memory Controller) do processador, poder acessar os endereços de memória e fazer a as operações requisitadas pelas instruções do programa ou kernel.

A MMU entra em ação quando instruções de um programa em execução, tentam acessar valores, dados ou outras instruções em um endereço de memória virtual que está na tabela de páginas do processo do programa, ou seja, no espaço de memória do programa em execução. Assim ela fica responsável por "interceptar" e resolver os endereços virtuais para físicos na memória, e utilizar o IMC pra acessar os dados e fazer as operações de leitura ou escrita.

A MMU também pode entrar em ação quando o kernel altera o registrador especial utilizado pela MMU.
O registrador CR3 é conhecido como PTBR (Page Table Base Register), ele é gerenciado pelo kernel, e é responsável por armazenar o endereço físico utilizado pela MMU para localizar 
a PGD (Page Global Directory) a página raiz do processo.

Assim, o kernel altera o endereço físico dele quando necessário, em situações como: trocas contexto de execução (troca de processos), criação de novos processos fork() e execve(), ou em casos de modificação ou atualização de uma tabela de páginas específica.

A syscall fork() é chamada pelo processo pai, e é responsável por criar o processo fliho através do processo de COW (Copy-On-Write).
O fork() cria uma page tables para o processo filho, baseada nas entradas do pai, ou seja, os endereços virtuais de cada página da table pages do processo filho, apontam para os endereços físicos associados as páginas da page tables do processo pai.
Porém, as paǵinas do processo filho são automaticamente Read-Only, então caso o processo filhos tente fazer alguma modificação nas PTEs , ele recebera uma exeção "Page Fault".

Pois as PTEs do processo filho possuem apenas endereços virtuais mapeados, ou seja, o kernel não definiu um endereço físico para elas na memória RAM, além de elas estarem apenas para leitura.

A syscall execve() é responsável por obter o caminho do executável, argumentos e as variáveis de ambiente do local de execução.
Assim o kernel é responsável por chamar o driver do dispositivos de armazenamento, localizar,  abrir e ler o conteúdo do executável (open()/read()), para assim poder mapear as seções dele, defindas pelo cabeçalho ELF (Executable and Linkable Format) e então carregar e organizar o conteúdo delas em páginas da page tables do processo filho, e também alocar as áreas de memória virtual Heap e Stack. Durante o mapeamento das seções para páginas na tabela de páginas do processo filho, a página é geralmente mapeada para endereços físicos, qundo ocorre "page fault".

Para o kernel resolver essa exeção, ele aloca endereços físicos para as páginas na tabela de páginas do processo, e atualiza a tabela de páginas.

As seções do cabeçalho ELF de um executável, são divididas em:
".text": Local onde as instruções de máquina são organizadas.
".data": Local onde são organizados os endereços virtuais das variáveis globais ou estáticas. Esses endereços são resolvidos pelo compilador/loader.
".bss": Para organizar variáveis não inicializadas em páginas zeradas.
".rodata":  Utilizada para organizar endereços virtuais de constantes e literais.
".Heap": Local para armazenamento de vlores dinâmicos durante a execução. 
".Stack": Local utilizado para armazenar variáveis locais e de escopo de execução. Ela também armazena o path do executável e as variáveis de ambiente da execução dele.

O durante a execução do programa, o kernel será responsável por lidar com as syscalls do programa para alocar mais memória na heap ou expandir a stack (o kernel gerencia a stack automaticamente sob demanda do programa).

Outras syscall que são usadas para criar processos e executar programas em contextos específicos:
clone(): Cria processos ou threads mas com o compartilhamento de recursos controlado. Usado em threads ou containers.
posix_spawn(): Cria e executa um novo processo em uma única chamada, dessa forma, não é preciso fazer cópias desnecessárias com fork() e depois alocar o conteúdo do executável e áreas de memória com execve().

Conceitos:
Overhead: É a sobrecarga de processamento por meio de com operações desncessárias ou ineficiêntes. Por exemplo: o fork() copia todas as áreas de memória da tabela de páginas do processo pai, mesmo que execve() seja executado em seguida para substuitir o conteúdo das páginas do processo filho, pela a imagem do executável.

Race conditions: Situação em que dois processos ou threads concorrentes compartilham os mesmos e recursos, e tentam executar as mesmas operações ao mesmo tempo. Sem respeitarem a sincronia e o tempo de execução do outro. Levando assim, a resultados imprévisiveis ou inseguros.

O kernel se comunica com a memória RAM através da criação e manipulação das tabelas de páginas que a MMU utiliza para mapear endereços virtuais utilizados pelos programas, para endereços físicos na memória RAM.
O kernel faz as operações de criação e manipulação das tabelas de páginas dos processos, através das syscalls prontas e já carregadas no espaço de memória do kernel. Assim, quando a CPU detecta uma syscall de fork() ou execve(), ela utiliza o valor armazenado no registrador para consultar a tabela IDT (Interruption Descriptor Table) gerenciada, definda e configurada pelo kernel durante a inicialização (ele passa o endereço da tabela para a CPU). Dessa forma, a CPU obtém o valor do endereço físico de memória para a função da tabela de ISRs (Interruption Service Runtime), que corresponde e resolve a syscall, ou seja, o código que executa a função da syscall, como copiar áreas de memória do processo pai e escrever na tabela de páginas do filho (fork()). Ou buscar o executável na unidade armazenamento (SSD/HD) e carregar e mapear as seções do binário para as páginas da tabela de páginas do processo filho, além utilizalas para alocar as áreas de memória virtual stack e heap. A tabela ISR é gerenciada e definida pelo kernel na incialização. Ela possui os as instruções para resolver cada interrupção ou evento específico.

A estrutura PCB é gerenciada e armazenada pelo kernel dentro de um espaço de memória dele (ela não é páginavel ou swappada, ela reside em uma parte da memória do kernel).
Ela pode existir independentemente de uma tabela de páginas ativa.

Através das estruturas PCB, programas como gerenciadores de tarefas conseguem representar processos em execução e suas informações. Ou seja, nós vemos apenas estruturas PCBs relacionadas a tabelas de páginas gerenciadas pelo kernel, ou que ainda vão ser criadas e mapeadas.

Em sistemas Gnu/Linux um processo é definido por 2 estruturas críticas:
PCB (Process control block): utilizado e gerenciado pelo kernel para manter o controle e organização hierarquica de programas em exe
Tabela de páginas: Criada e gerenciada pelo kernel, para carregar o programa na memória RAM, e fazer o gerenciamento dinâmico dele durante a execução, atendendo syscalls ou outras necessidades.

Em assembly você manipula diretamente o conteúdo das seções do binário, que o kernel vai mapear para as páginas da tabela de páginas do processo.

Um teclado que utiliza conexão USB (Universal Serial Bus), ele segue o protocolo USB HID (Human Interface Device), que define como dispositivos de entrada, como teclados, comunicam dados ao sistema. Dessa forma, o firmware do teclado fica responsável por implementar protocolos como PS/2, USB ou Bluetooth dependendo do tipo de teclado.

A comunicação entre o usuário, teclado até chegar terminal e shell, passa por bastantes processos, e várias operações são feitas. Mas a questão é que existem várias formas para que essa comunicação possa acontecer, e vai depender principalemente da implementação do sistema e funcionamento do teclado.

Além disso o firmware também é responsável por converter o sinal das teclas pressionadas, em scan codes, para então enviar elas da forma correta de acordo com a conexão e protocolo de comunicação de dados com o computador.
Em um teclado que utiliza conexão USB e portanto utiliza o protocolo USB HID, um processo génerico pode ser assim:

Além disso o firmware também é responsável por converter o sinal das teclas pressionadas, em scan codes, e então mover para o local de armazenamento correto, geralmente buffers do teclado, controlador USB na placa mãe ou para a placa de wireless do computador.

O teclado então Quando uma tecla é pressionada no teclado, é gerado um sinal elétrico específico, que o controlador do teclado, lê e converte para um scan code que é armazenado no buffer em uma

O controlador através do firmware, detecta e converte o sinal da tecla pressionada para um scan code, e em seguida encapsula esses scan codes para pacotes (seguindo o protocolo USB HID). Assim, o controlador pode enviar e armazenar os scan codes no próprio buffer do teclado, ou no buffer do controlador USB da placa mãe, através de pacotes USB.

o controlador através do firmware, converterem o scan code

para o local de armazenamento correto, geralmente buffers do teclado, controlador USB na placa mãe ou para a placa wireless do computador.

O teclado então Quando uma tecla é pressionada no teclado, é gerado um sinal elétrico específico, que o controlador do teclado, lê e converte para um scan code que é armazenado no buffer em uma

A interrupção pode ser enviada imediatamente, ou em um período de tempo específico, como 8ms, isso pode ser configurado no conntrolador USB. Após a CPU receber a interrupção de hardware, ela salva os dados infromações da instrução quu estava executando  enviado uma interrupção imediatamente ou a cada  a partir do teclado, ele pode move o valor do scan code para um buffer do teclado, onde o controlador  que é 

para o local de armazenamento correto, geralmente buffers do teclado, controlador USB na placa mãe ou para a placa wireless do computador.

O teclado então Quando uma tecla é pressionada no teclado, é gerado um sinal elétrico específico, que o controlador do teclado, lê e converte para um scan code que é armazenado no buffer em uma

enviado uma interrupção imediatamente ou a cada  a partir do teclado, ele pode move o valor do scan code para um buffer do teclado, onde o controlador  que é

para o local de armazenamento correto, geralmente buffers do teclado, controlador USB na placa mãe ou para a placa wireless do computador.

O teclado então Quando uma tecla é pressionada no teclado, é gerado um sinal elétrico específico,

Podendo armazenar os scans codes recebidos no próprio buffer, e enviar um sinal para o controlador USB, para que o driver periodicamente ou imédiatamente colete-os. Ou o controlador pode enviar uma interrupção de hardware para CPU, sempre quando receber novos pacotes, ou uma certa quantidade deles em periodo de tempo específico ou não. Para assim, após a CPU receber a interrupção de hardware, ela para sua execução normal, e muda o contexto execução para buscar o endereço da ISR corresponde a syscall do valor da interrupção de hardware recebida.

Para isso, a CPU usa o valor recebido associado à interrupção, e busca ele na tabela de IDT (Interruption Descriptor Table) do kernel, que mapeia o valor associado a interrupção, para  o endereço físico de memória da ISR (Interruptor Service Runtime) responsável por lidar com a interrupção. Assim, nesse caso, ela é responsável por notificar o evento para o sub-sistema usb do kernel, que chama o driver associado ao teclado, responsável por coletar os scan codes no buffer do controlador USB (ou do teclado) e então codificar ou interpretar eles de acordo com configuração do driver.

A tabela IDT (Interruption Descriptor Table) é gerenciada e criada pelo kernel durante o processo de incialização. Ela possui o mapeamento dos valores correspondestes as insterrupções, junto com o endereço para a ISR correspondente a ela.

A ISR (interrupt Service Runtime) vai ser ter o conjunto de instruções responsáveis por lidar com a interrupção de hardware gerada pelo controlador USB, após receber novo pacotes USB do controlador teclado. A ISR relacionada ao controlador USB, notifica o sub-sistema USB do kernel, que identifica o dispositivo e chama o driver correto (génerico ou dedicado) associado ao teclado.

Sempre que um dispositivo USB é conectado, o firmware dele envia várias informações para o controlador USB do dispositivo. Essas informações são processadas e utilizadas pelo sub-sistema USB do kernel, para identificar os dispositivos e registrar um ou mais drivers para eles, além de definir outras configurações específicas para eles.

Em seguida, o driver é responsável por coordenar os dados codificados, para o buffer reservado no espaço de memória do kernel. Assim, o kernel pode criar e gerenciar um arquivo de dispositivo de caracter para fornecer uma interface os dados do teclado. Em /dev/input/device-exemplo

Assim, bibliotecas ou aplicações podem fornecer funções para que programas possam ler o buffer do kernel relacionado a um dispositivo de entrada específico por exemplo, e assim obter o máximo de dados transmitidos por eles. Eles podem abrir e ler o conteúdo do arquivo de dispositivo de caracter /dev/input/mouse-exemplo e então ler e interpretar os valores X e Y do mouse, e simular eles, dessa forma conseguindo obter a posição exata da seta do mouse em uma tela com resolução específica.

Durante a incialização, o kernel automaticamente cria, configura e gerencia o TTY (Terminal TeleType) no sistema de arquivos da partição raiz "/", e é representado em "/dev/tty1". Ele serve para fornecer uma interface básica de texto e linha de comando para o usuário.

Os programas geralmente usam APIs para obter o valor da entrada do usuário, do buffer do kernel.

Dessa forma, quando um terminal está em execução, ele basicamente utiliza a função read()
 para entrar em modo de leitura e aguardar dados de entrada do teclado. 
Assim que os dados são recebidos, eles são armazenados no buffer do 
próprio processo e, em seguida, renderizados na interface gráfica.

Funções como input() ou outras para obter os dados de entrada do usuário, são de bibliotecas utilizadas pelos programas, para poder facilitar o desenvolvimento da aplicação.

Essas funções geralmente utilizam uma API para ler o buffer de dados de entrada do kernel, ou utilizam a syscall read() pra ler ele diretamente ele. Assim, elas interpretam os dados brutos e retornam eles para a aplicação. Em alguns casos a API pode ler diretamente os dados a partir do arquivo de dispositivo de caracter, que o kernel fornece.

Em outros casos o terminal pode também ler o buffer do kernel diretamente através da syscall read(), e interpretar os dados brutos dele.

Quando o usuário pressiona "Enter" no terminal, o terminal detecta a ação e envia os dados do seu buffer para o buffer do shell(que é executado como processo um filho do terminal). Assim, o shell fica responsável por interpretar esses dados e processá-los da forma correta.

Ao receber os dados em seu buffer, o shell utiliza read() para ler eles, e ele interpreta o "/n" como sinal de que o comando terminou, e inicia o processamento dele.
Nesse momento, ele verifica se o comando ou os comandos fazem parte do próprio shell, pois se fizerem, o próprio shell irá executa-los no mesmo processo, ou seja, não chamara as syscalls fork() e execve() para criarem um novo processo filho e executarem o comando.

Para isso, o init do sistema é responsável por inicializar esse terminal através da interface que o kernel disponibiliza em "/dev/tty1". Assim como vários outros dispositivos são representados por arquivos especiais em /dev.

O init do sistema inicializa e configura o terminal para o usuário através do comando "getty /dev/tty1", que é responsável por configurar o terminal e exibir a tela de login para o usuário.

A tabela de páginas do processo filho pode herdar recursos e capacidades do processo pai.
Ela pode herdar a tabela de file descriptors abertos pelo processo pai.

FIle descriptors são números inteiros não negativos que representam recursos abertos por um processo. Os processos realizam operações em arquivos, dispositivos ou sockets, através de syscalls que utilizam o valor do file descriptor relacionado ao recurso que o programa quer interagir, para realizarem suas operações. Um programa realiza uma syscall para um dispositivo, arquivo ou socket, dessa forma exemplo: "write(fd, "Hello", 5)", dependendo número relacionado ao file descriptor utilizado, o dado "Hello World" pode ser escrito no buffer do kernel relacionado ao console virtual principal "/dev/tty1", e assim "Hello World" pode ser renderizado no terminal em execução que lê o buffer do kernel relacionado ao console virtual principal, representado em "/dev/tty1".
O kernel mantém uma tabela global de estruturas relacionada a cada file descriptor aberto e usado pelo sistema operacional e processos. As ISRs tratam as syscalls, e podem utilizar o valor do FD que vem junto com a syscall, para localizar a estrutura relacionada ao file descriptor, e chamar a função do driver ou sistema de arquivos, para executar a(s) operações da syscall.

Todo processo possui uma tabela própria de file descriptors abertos e usados por ele. Essa tabela faz parte da estrutura PCB do processo, que é gerenciada pelo kernel.

O valor do FD passado na syscall, corresponde a uma estrutura de dados na tabela global de FDs, gerencia pelo kernel. Cada entrada nessa tabela corresponde a uma estrutura de dados relacionada a um arquivo, dispositivo ou socket aberto. Essa estrutura contém dados que correspondem ao file descriptor.

O kernel se comunica com um dispositivo, chamando as funções do driver correspondente a ele. A ISR do kernel, chama a(s) função(ções) apropriada e disponível para realizar a(s) tarefa(s) da syscall. Para isso, ele localiza a estutura inode do arquivo/dispositivo,  que contém a estrutura file_operations do driver ou sistema de arquivos, assim, a ISR chama a função apropriada, passando a estrutura file e ponteiros para buffers e tamanho de dados dependo da operação. Assim o driver executa a operação fazendo o trabalho necessário para se comunicar o hardware. Então o driver então retorna o resultado ao buffer kernel relacionado ao dispositivo, e assim o kernel pode passar o resultado para uma saída de dados padrão como como o buffer do console virtual principal "/dev/tty1", ou passado para a área de memória utilizada pelo processo para entrada e saída de dados I/O.

A estrutura de dados correspondente a um file descriptor é:
Ponteiro para a estrutura de inode.
Ponteiro para a estrutura de file_operation do driver ou sistema de arquivos.
Informações adicionais como: estado do FD, permissões de acesso e posição de leitura/escrita(offset).

A estrutura inode contém dados que representam o arquivo ou dispositivo no sistema de arquivos. Ele contém metdados e um ponteiro para a estrutura de file_operations.

A estrutura file_operations contém as funções específicas do driver ou sistema de arquivos que kernel utiliza para realizar as operações, como: read(ler dispositivo), write(escrever no dispositivo), ioctl(realizar operações específicas nele), open(abrir device), release(fechar device).

A estrutura file contém dados utilizados pelo kernel como argumentos para chamar e executar funções do driver ou sistema de arquivos. Ele contém as informações do estado atual do recurso. Dados como: flags de acesso e ponteiro para a entrada correspondente na tabela global.

Quando um processo é criado, o kernel já define uma tabela para file descriptors que o processo irá utilizar, e nela ele também define os 3 números de file descriptors básicos para o processo:
0: está mapeado para a entrada padrão de dados, standard input/stdin, que pode ser teclado ou outro dispositivo configurado.
1: está mapeado para a saída padrão do programa, standard output/stdout, que no caso é o terminal.
2: está mapeado para a saída padrão de errors do programa, standard error/stderr, que no caso pode ser o terminal.

O "/dev/tty1" é um arquivo de dispositivo de caracter, o console virtual principal do linux, gerenciado pelo driver virtual dele, que gerencia o buffer de I/O que o kernel usa para passar dados de teclas dígitadas. Os dados de teclas digitadas que o kernel recebeu em seu buffer relacionado ao dispositivo de entrada de dados, nesse caso o teclado, são provenientes do driver do teclado, que executou a função que a ISR chamou para realizar a operação da syscall que programa executou.

Images source:
Recommended content:
RAM (Random Access Memory) is a passive component that only has the function of storing data in the physical addresses of the memory cells, temporarily storing the code, data and files of the programs during their execution.
Thus, the processor dynamically searches for and accesses the data in the physical memory addresses, loads it into the registers or cache, processes it and executes the instructions and operations in its internal logic circuits.
Some RAM modules (DDRM4/DDR5) have auxiliary circuits and firmware to provide additional and specific functionalities, such as:
Power Management Integrated Circuit (PMIC)
Error Correction Code (ECC)
Unlike other devices or components, conventional RAM does not use or have driver or active firmware to handle internal data processing, such as allocating information and updating it.
As such, it is the physical ram memory units that manage and manipulate , which are responsible for communicating with it directly.
PCB (Process Control Block):
https://duckduckgo.com/?q=estrutura+PCB+process+control+block&t=ffab&iar=images&iai=https%3A%2F%2Fcdn.testbook.com%2Fimages%2Fseo%2Fprocess-control-block.png
Armazenamento, memória ram e outras:
https://www.newtoncbraga.com.br/eletronica-digital/16358-curso-de-eletronica-eletronica-digital-memorias-adcs-e-dacs-cur5013.html

Memórias virtuais e PCB:
https://ajamias.github.io/openos/textbook/mm/intro.html
https://pt.wikipedia.org/wiki/Bloco_de_controle_de_processo
https://soescola.com/glossario/o-que-e-file-descriptor#gsc.tab=0

Compiladores, montadores, arquivos objeto, linkers e executáveis e formatos de executáveis:
https://pt.wikipedia.org/wiki/Arquivo_objeto

Processadores e componentes eletrônicos:
https://wiki.sj.ifsc.edu.br/index.php/MI1022806_2020_2_AULA08#Interrup%C3%A7%C3%B5es
https://gil0mendes.gitbooks.io/assembly/content/system_calls.html
https://www.cin.ufpe.br/~cagf/if677/2017-2/slides/04-05_processo+interrupcao+syscall.pdf
https://www.passeidireto.com/arquivo/65117084/barramentos-arquitetura-de-computadores
https://youtu.be/dX9CGRZwD-w?feature=shared
https://youtu.be/AF8d72mA41M?feature=shared
https://youtu.be/e_hU6sAON2U?feature=shared
https://youtu.be/uByQnP5FsVY?feature=shared
https://youtu.be/uQPiyxoCk9E?feature=shared
Em contexto de criação e gerenciamento de pocessos, o kernel é reponsável por fornecer suporte para a CPU executar as intruções dos programas.
Ele faz isso através de vários mecanismos, sub-sistemas e funções já pré programadas e carregadas na memória RAM (através do bootloader durante a inicialização). Prontas para serem executadas quando a CPU detectar interrupções (hardware/software) ou outros eventos do sistema (através do circuito interno dela, responsável por detectar interrupções como syscalls (int 0x80 ou "syscall" em x86/x64) durante a execução de instruções, e assim iniciar o processo para resolver ela).
Dessa forma, quando um programa é executado, o kernel geralmente executa syscall fork() e execve() proveniente do processo pai que forneceu suporte ao usuário para executar um programa no sistema. Esse processo pai pode ser um shell que recebeu um comando do terminal a partir da entrada do usuário através do teclado. Ou a partir do clique do usuário através do mouse, no ícone de um programa, disparando um evento no servidor gráfico, e assim o servidor gráfico se comunica com o gerenciador de janelas do usuário, fazendo com que o gerenciador de janelas chama a syscall fork() e execve(). Ou a execução pode acontecer também de outras formas como atalhos ou processos agendados.
Mostrar os mapas de memória que refletem as informações das page tables dos processos, em "/proc/PID/maps".

Usar ferramentas de depuração como o strace para mostrar na prática a criação de processos.
"strace -o output.log -e trace=read,mmap etc... command"

Mostrar logs do kernel criando as page tables e alocando memória.

Mostrar como kernel lê e carrega as seções o cabeçalho ELF em páginas da table pages de um processo na memória RAM.
Usar "xxd" para ler o código assembly, e ver como os mnemonicos convertidos para opcodes em hexadecimal.

Mostrar exemplos de códigos usados que aplicam os conceitos:
PCB, page tables, syscall usadas pelos programas para gerenciar memória e executar programas, tabela IDT e as ISRs.
"linux/kernel/fork.c"
"linux/include/linux/sched.h"
"linux/mm/memory.c"
"linux/mm/mmap.c"
"linux/arch/x86/kernel/idt.c"
"linux/arch/x86/kernel/traps.c"
"/proc/interrupts/"
"lsof"

Mostrar a comunicação i2c do kernel, para mostrar o funcionamento básico do teclado.
Através de: "cat /dev/kmsg | grep "i2c""
A memória RAM possui circuitos passivos para acessar e executar as operações do IMC do processador, que são passadas através de barramentos para os circuitos do módulo de RAM. Os endereços de memória das células, são na verdade dados que os circuitos passivos internos da memória RAM, interpretam e usam para acessar linhas e colunas específica que acessam uma célula específica, e assim armazenando ou acessando a informação que o  IMC enviou ou requisitou. Os circuito internos da memória ram utilizam multiplexadores e demultiplexadores para acessarem linha e colunas específicas das memórias.
O kernel é responsável por gerenciar eles, para isso, ele utiliza várias funções e sub-sistemas prontos para fazerem o gerenciamento de memória e execução de programas. Mas para o kernel ter mais controle e organização no fluxo de execução de processos pela CPU, e no gerenciamento da hierarquia e compartilhamento ou herança de recursos entre processos, ele utiliza uma estrutura PCB para cada tabela de páginas de um programa.
Dessa forma, através da estrutura PCB que kernel define para cada tabela de páginas, podemos monitorar e gerenciar os processos dos programas em execução, por meio de um gerenciador de processos (task manager ou htop/top).
Assim o IMC da memória RAM por exemplo, envia através de barramentos um endereço de memória e o bit a ser armazenado em uma célula específica. Então os circuitos internos lógicas da memória RAM, decodificam o endereço de memória para obter o bits que acessam a linha e os bits que acessam a coluna da memória, e gravar ou ler a célula específica.
Processos no sistema operacional, são instâncias de um programa carregado na memória RAM e em um estado específico, podendo estar em execução, pronto para ser executado, dormindo, ou outros estado dependo da função do programa ou estado do sistema operacional.
A CPU (Unidade de Processamento Central) é o componente principal do computador, ela é consituida por vários circuitos lógicos, 
e organizados em unidades de acordo com suas funções. Os circuitos são compostos por vários componentes eletrônicos, fabricados com materias específicos, selecionados de acordo com suas propriedades fisicas, capacidades e funções.  Dessa forma, a CPU consegue processar e interpretar vários dados de acordo com as instruções dos programas, manipulando o fluxo de elétrons em operações binárias (lógicas e aritméticas) realizadas pelos circuitos, ondes os resultados são representados como bits.
A CPU possui as unidades responsáveis pelo gerenciamento de memória e comunicação com a memória RAM, local onde os dados e instruções dos programas são carregados e executados de acordo com o fluxo de processamento e execução do programa.
A MMU (Memory Management Unit) é responsável por mapear os endereços virtuais das page tables dos processos para endereços físicos nas células dos chips de memória RAM, para assim, através da unidade IMC (Integrated Memory Controller) do processador, poder acessar os endereços de memória e fazer a as operações requisitadas pelas instruções do programa ou kernel.
A MMU entra em ação quando instruções de um programa em execução, tentam acessar valores, dados ou outras instruções em um endereço de memória virtual que está na tabela de páginas do processo do programa, ou seja, no espaço de memória do programa em execução. Assim ela fica responsável por "interceptar" e resolver os endereços virtuais para físicos na memória, e utilizar o IMC pra acessar os dados e fazer as operações de leitura ou escrita.
A MMU também pode entrar em ação quando o kernel altera o registrador especial utilizado pela MMU.
O registrador CR3 é conhecido como PTBR (Page Table Base Register), ele é gerenciado pelo kernel, e é responsável por armazenar o endereço físico utilizado pela MMU para localizar 
a PGD (Page Global Directory) a página raiz do processo.
Assim, o kernel altera o endereço físico dele quando necessário, em situações como: trocas contexto de execução (troca de processos), criação de novos processos fork() e execve(), ou em casos de modificação ou atualização de uma tabela de páginas específica.
A syscall fork() é chamada pelo processo pai, e é responsável por criar o processo fliho através do processo de COW (Copy-On-Write).
O fork() cria uma page tables para o processo filho, baseada nas entradas do pai, ou seja, os endereços virtuais de cada página da table pages do processo filho, apontam para os endereços físicos associados as páginas da page tables do processo pai.
Porém, as paǵinas do processo filho são automaticamente Read-Only, então caso o processo filhos tente fazer alguma modificação nas PTEs , ele recebera uma exeção "Page Fault".
Pois as PTEs do processo filho possuem apenas endereços virtuais mapeados, ou seja, o kernel não definiu um endereço físico para elas na memória RAM, além de elas estarem apenas para leitura.
A syscall execve() é responsável por obter o caminho do executável, argumentos e as variáveis de ambiente do local de execução.
Assim o kernel é responsável por chamar o driver do dispositivos de armazenamento, localizar,  abrir e ler o conteúdo do executável (open()/read()), para assim poder mapear as seções dele, defindas pelo cabeçalho ELF (Executable and Linkable Format) e então carregar e organizar o conteúdo delas em páginas da page tables do processo filho, e também alocar as áreas de memória virtual Heap e Stack. Durante o mapeamento das seções para páginas na tabela de páginas do processo filho, a página é geralmente mapeada para endereços físicos, qundo ocorre "page fault".
Para o kernel resolver essa exeção, ele aloca endereços físicos para as páginas na tabela de páginas do processo, e atualiza a tabela de páginas.
As seções do cabeçalho ELF de um executável, são divididas em:
".text": Local onde as instruções de máquina são organizadas.
".data": Local onde são organizados os endereços virtuais das variáveis globais ou estáticas. Esses endereços são resolvidos pelo compilador/loader.
".bss": Para organizar variáveis não inicializadas em páginas zeradas.
".rodata":  Utilizada para organizar endereços virtuais de constantes e literais.
".Heap": Local para armazenamento de vlores dinâmicos durante a execução. 
".Stack": Local utilizado para armazenar variáveis locais e de escopo de execução. Ela também armazena o path do executável e as variáveis de ambiente da execução dele.
O durante a execução do programa, o kernel será responsável por lidar com as syscalls do programa para alocar mais memória na heap ou expandir a stack (o kernel gerencia a stack automaticamente sob demanda do programa).
Outras syscall que são usadas para criar processos e executar programas em contextos específicos:
clone(): Cria processos ou threads mas com o compartilhamento de recursos controlado. Usado em threads ou containers.
posix_spawn(): Cria e executa um novo processo em uma única chamada, dessa forma, não é preciso fazer cópias desnecessárias com fork() e depois alocar o conteúdo do executável e áreas de memória com execve().

Conceitos:
Overhead: É a sobrecarga de processamento por meio de com operações desncessárias ou ineficiêntes. Por exemplo: o fork() copia todas as áreas de memória da tabela de páginas do processo pai, mesmo que execve() seja executado em seguida para substuitir o conteúdo das páginas do processo filho, pela a imagem do executável.

Race conditions: Situação em que dois processos ou threads concorrentes compartilham os mesmos e recursos, e tentam executar as mesmas operações ao mesmo tempo. Sem respeitarem a sincronia e o tempo de execução do outro. Levando assim, a resultados imprévisiveis ou inseguros.
O kernel se comunica com a memória RAM através da criação e manipulação das tabelas de páginas que a MMU utiliza para mapear endereços virtuais utilizados pelos programas, para endereços físicos na memória RAM.
O kernel faz as operações de criação e manipulação das tabelas de páginas dos processos, através das syscalls prontas e já carregadas no espaço de memória do kernel. Assim, quando a CPU detecta uma syscall de fork() ou execve(), ela utiliza o valor armazenado no registrador para consultar a tabela IDT (Interruption Descriptor Table) gerenciada, definda e configurada pelo kernel durante a inicialização (ele passa o endereço da tabela para a CPU). Dessa forma, a CPU obtém o valor do endereço físico de memória para a função da tabela de ISRs (Interruption Service Runtime), que corresponde e resolve a syscall, ou seja, o código que executa a função da syscall, como copiar áreas de memória do processo pai e escrever na tabela de páginas do filho (fork()). Ou buscar o executável na unidade armazenamento (SSD/HD) e carregar e mapear as seções do binário para as páginas da tabela de páginas do processo filho, além utilizalas para alocar as áreas de memória virtual stack e heap. A tabela ISR é gerenciada e definida pelo kernel na incialização. Ela possui os as instruções para resolver cada interrupção ou evento específico.
A estrutura PCB é gerenciada e armazenada pelo kernel dentro de um espaço de memória dele (ela não é páginavel ou swappada, ela reside em uma parte da memória do kernel).
Ela pode existir independentemente de uma tabela de páginas ativa.
Através das estruturas PCB, programas como gerenciadores de tarefas conseguem representar processos em execução e suas informações. Ou seja, nós vemos apenas estruturas PCBs relacionadas a tabelas de páginas gerenciadas pelo kernel, ou que ainda vão ser criadas e mapeadas.
Em sistemas Gnu/Linux um processo é definido por 2 estruturas críticas:
PCB (Process control block): utilizado e gerenciado pelo kernel para manter o controle e organização hierarquica de programas em exe
Tabela de páginas: Criada e gerenciada pelo kernel, para carregar o programa na memória RAM, e fazer o gerenciamento dinâmico dele durante a execução, atendendo syscalls ou outras necessidades.
Em assembly você manipula diretamente o conteúdo das seções do binário, que o kernel vai mapear para as páginas da tabela de páginas do processo.
Um teclado que utiliza conexão USB (Universal Serial Bus), ele segue o protocolo USB HID (Human Interface Device), que define como dispositivos de entrada, como teclados, comunicam dados ao sistema. Dessa forma, o firmware do teclado fica responsável por implementar protocolos como PS/2, USB ou Bluetooth dependendo do tipo de teclado.
A comunicação entre o usuário, teclado até chegar terminal e shell, passa por bastantes processos, e várias operações são feitas. Mas a questão é que existem várias formas para que essa comunicação possa acontecer, e vai depender principalemente da implementação do sistema e funcionamento do teclado.
Além disso o firmware também é responsável por converter o sinal das teclas pressionadas, em scan codes, para então enviar elas da forma correta de acordo com a conexão e protocolo de comunicação de dados com o computador.
Em um teclado que utiliza conexão USB e portanto utiliza o protocolo USB HID, um processo génerico pode ser assim:
O controlador através do firmware, detecta e converte o sinal da tecla pressionada para um scan code, e em seguida encapsula esses scan codes para pacotes (seguindo o protocolo USB HID). Assim, o controlador pode enviar e armazenar os scan codes no próprio buffer do teclado, ou no buffer do controlador USB da placa mãe, através de pacotes USB.
A interrupção pode ser enviada imediatamente, ou em um período de tempo específico, como 8ms, isso pode ser configurado no conntrolador USB. Após a CPU receber a interrupção de hardware, ela salva os dados infromações da instrução quu estava executando  enviado uma interrupção imediatamente ou a cada  a partir do teclado, ele pode move o valor do scan code para um buffer do teclado, onde o controlador  que é 

para o local de armazenamento correto, geralmente buffers do teclado, controlador USB na placa mãe ou para a placa wireless do computador.

O teclado então Quando uma tecla é pressionada no teclado, é gerado um sinal elétrico específico, que o controlador do teclado, lê e converte para um scan code que é armazenado no buffer em uma
Podendo armazenar os scans codes recebidos no próprio buffer, e enviar um sinal para o controlador USB, para que o driver periodicamente ou imédiatamente colete-os. Ou o controlador pode enviar uma interrupção de hardware para CPU, sempre quando receber novos pacotes, ou uma certa quantidade deles em periodo de tempo específico ou não. Para assim, após a CPU receber a interrupção de hardware, ela para sua execução normal, e muda o contexto execução para buscar o endereço da ISR corresponde a syscall do valor da interrupção de hardware recebida.
Para isso, a CPU usa o valor recebido associado à interrupção, e busca ele na tabela de IDT (Interruption Descriptor Table) do kernel, que mapeia o valor associado a interrupção, para  o endereço físico de memória da ISR (Interruptor Service Runtime) responsável por lidar com a interrupção. Assim, nesse caso, ela é responsável por notificar o evento para o sub-sistema usb do kernel, que chama o driver associado ao teclado, responsável por coletar os scan codes no buffer do controlador USB (ou do teclado) e então codificar ou interpretar eles de acordo com configuração do driver.
A tabela IDT (Interruption Descriptor Table) é gerenciada e criada pelo kernel durante o processo de incialização. Ela possui o mapeamento dos valores correspondestes as insterrupções, junto com o endereço para a ISR correspondente a ela.

A ISR (interrupt Service Runtime) vai ser ter o conjunto de instruções responsáveis por lidar com a interrupção de hardware gerada pelo controlador USB, após receber novo pacotes USB do controlador teclado. A ISR relacionada ao controlador USB, notifica o sub-sistema USB do kernel, que identifica o dispositivo e chama o driver correto (génerico ou dedicado) associado ao teclado.
Sempre que um dispositivo USB é conectado, o firmware dele envia várias informações para o controlador USB do dispositivo. Essas informações são processadas e utilizadas pelo sub-sistema USB do kernel, para identificar os dispositivos e registrar um ou mais drivers para eles, além de definir outras configurações específicas para eles.
Em seguida, o driver é responsável por coordenar os dados codificados, para o buffer reservado no espaço de memória do kernel. Assim, o kernel pode criar e gerenciar um arquivo de dispositivo de caracter para fornecer uma interface os dados do teclado. Em /dev/input/device-exemplo
Assim, bibliotecas ou aplicações podem fornecer funções para que programas possam ler o buffer do kernel relacionado a um dispositivo de entrada específico por exemplo, e assim obter o máximo de dados transmitidos por eles. Eles podem abrir e ler o conteúdo do arquivo de dispositivo de caracter /dev/input/mouse-exemplo e então ler e interpretar os valores X e Y do mouse, e simular eles, dessa forma conseguindo obter a posição exata da seta do mouse em uma tela com resolução específica.
Os programas geralmente usam APIs para obter o valor da entrada do usuário, do buffer do kernel.
Dessa forma, quando um terminal está em execução, ele basicamente utiliza a função read()
 para entrar em modo de leitura e aguardar dados de entrada do teclado. 
Assim que os dados são recebidos, eles são armazenados no buffer do 
próprio processo e, em seguida, renderizados na interface gráfica.
Funções como input() ou outras para obter os dados de entrada do usuário, são de bibliotecas utilizadas pelos programas, para poder facilitar o desenvolvimento da aplicação.

Essas funções geralmente utilizam uma API para ler o buffer de dados de entrada do kernel, ou utilizam a syscall read() pra ler ele diretamente ele. Assim, elas interpretam os dados brutos e retornam eles para a aplicação. Em alguns casos a API pode ler diretamente os dados a partir do arquivo de dispositivo de caracter, que o kernel fornece.

Em outros casos o terminal pode também ler o buffer do kernel diretamente através da syscall read(), e interpretar os dados brutos dele.
Quando o usuário pressiona "Enter" no terminal, o terminal detecta a ação e envia os dados do seu buffer para o buffer do shell(que é executado como processo um filho do terminal). Assim, o shell fica responsável por interpretar esses dados e processá-los da forma correta.
Ao receber os dados em seu buffer, o shell utiliza read() para ler eles, e ele interpreta o "/n" como sinal de que o comando terminou, e inicia o processamento dele.
Nesse momento, ele verifica se o comando ou os comandos fazem parte do próprio shell, pois se fizerem, o próprio shell irá executa-los no mesmo processo, ou seja, não chamara as syscalls fork() e execve() para criarem um novo processo filho e executarem o comando.
Durante a incialização, o kernel automaticamente cria, configura e gerencia o TTY (Terminal TeleType) no sistema de arquivos da partição raiz "/", e é representado em "/dev/tty1". Ele serve para fornecer uma interface básica de texto e linha de comando para o usuário.
Para isso, o init do sistema é responsável por inicializar esse terminal através da interface que o kernel disponibiliza em "/dev/tty1". Assim como vários outros dispositivos são representados por arquivos especiais em /dev.
O init do sistema inicializa e configura o terminal para o usuário através do comando "getty /dev/tty1", que é responsável por configurar o terminal e exibir a tela de login para o usuário.
A tabela de páginas do processo filho pode herdar recursos e capacidades do processo pai.
Ela pode herdar a tabela de file descriptors abertos pelo processo pai.
FIle descriptors são números inteiros não negativos que representam recursos abertos por um processo. Os processos realizam operações em arquivos, dispositivos ou sockets, através de syscalls que utilizam o valor do file descriptor relacionado ao recurso que o programa quer interagir, para realizarem suas operações. Um programa realiza uma syscall para um dispositivo, arquivo ou socket, dessa forma exemplo: "write(fd, "Hello", 5)", dependendo número relacionado ao file descriptor utilizado, o dado "Hello World" pode ser escrito no buffer do kernel relacionado ao console virtual principal "/dev/tty1", e assim "Hello World" pode ser renderizado no terminal em execução que lê o buffer do kernel relacionado ao console virtual principal, representado em "/dev/tty1".
O kernel mantém uma tabela global de estruturas relacionada a cada file descriptor aberto e usado pelo sistema operacional e processos. As ISRs tratam as syscalls, e podem utilizar o valor do FD que vem junto com a syscall, para localizar a estrutura relacionada ao file descriptor, e chamar a função do driver ou sistema de arquivos, para executar a(s) operações da syscall.
Todo processo possui uma tabela própria de file descriptors abertos e usados por ele. Essa tabela faz parte da estrutura PCB do processo, que é gerenciada pelo kernel.
O valor do FD passado na syscall, corresponde a uma estrutura de dados na tabela global de FDs, gerencia pelo kernel. Cada entrada nessa tabela corresponde a uma estrutura de dados relacionada a um arquivo, dispositivo ou socket aberto. Essa estrutura contém dados que correspondem ao file descriptor.
O kernel se comunica com um dispositivo, chamando as funções do driver correspondente a ele. A ISR do kernel, chama a(s) função(ções) apropriada e disponível para realizar a(s) tarefa(s) da syscall. Para isso, ele localiza a estutura inode do arquivo/dispositivo,  que contém a estrutura file_operations do driver ou sistema de arquivos, assim, a ISR chama a função apropriada, passando a estrutura file e ponteiros para buffers e tamanho de dados dependo da operação. Assim o driver executa a operação fazendo o trabalho necessário para se comunicar o hardware. Então o driver então retorna o resultado ao buffer kernel relacionado ao dispositivo, e assim o kernel pode passar o resultado para uma saída de dados padrão como como o buffer do console virtual principal "/dev/tty1", ou passado para a área de memória utilizada pelo processo para entrada e saída de dados I/O.
A estrutura de dados correspondente a um file descriptor é:
Ponteiro para a estrutura de inode.
Ponteiro para a estrutura de file_operation do driver ou sistema de arquivos.
Informações adicionais como: estado do FD, permissões de acesso e posição de leitura/escrita(offset).
A estrutura inode contém dados que representam o arquivo ou dispositivo no sistema de arquivos. Ele contém metdados e um ponteiro para a estrutura de file_operations.

A estrutura file_operations contém as funções específicas do driver ou sistema de arquivos que kernel utiliza para realizar as operações, como: read(ler dispositivo), write(escrever no dispositivo), ioctl(realizar operações específicas nele), open(abrir device), release(fechar device).

A estrutura file contém dados utilizados pelo kernel como argumentos para chamar e executar funções do driver ou sistema de arquivos. Ele contém as informações do estado atual do recurso. Dados como: flags de acesso e ponteiro para a entrada correspondente na tabela global.
Quando um processo é criado, o kernel já define uma tabela para file descriptors que o processo irá utilizar, e nela ele também define os 3 números de file descriptors básicos para o processo:
0: está mapeado para a entrada padrão de dados, standard input/stdin, que pode ser teclado ou outro dispositivo configurado.
1: está mapeado para a saída padrão do programa, standard output/stdout, que no caso é o terminal.
2: está mapeado para a saída padrão de errors do programa, standard error/stderr, que no caso pode ser o terminal.
O "/dev/tty1" é um arquivo de dispositivo de caracter, o console virtual principal do linux, gerenciado pelo driver virtual dele, que gerencia o buffer de I/O que o kernel usa para passar dados de teclas dígitadas. Os dados de teclas digitadas que o kernel recebeu em seu buffer relacionado ao dispositivo de entrada de dados, nesse caso o teclado, são provenientes do driver do teclado, que executou a função que a ISR chamou para realizar a operação da syscall que programa executou.

