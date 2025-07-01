# como funciona um terminal? e como a cpu executa instruções?

O kernel é o núcleo do sistema operacional, ele é armazenado na partição de boot "/boot" do dispositivo de armazenamento (HD ou SSD).
Ele é compilado e comprimido (bzimage geralmente) para ser carregado mais rápidamente na memória RAM pelo bootloader (grub, syslinux, efiboormgr (para registrar o kernel diretamente na partição EFI), etc...), ele se descomprime sozinho na memória RAM (em código máquina) e assume o controle dando continuidade a inicialização do sistema.

Ele é pré-programado para fornecer instruções e assumir o controle da comunicação entre os softwares e os hardwares do computador. Para isso, ele possui drivers e módulo básicos, sub-sistemas e funções prontas para lidar com os eventos do sistema, que podem ser: interrupções, exeções, timers, eventos de dispositivos, entre outros...

As interrupções são inicialmente identificadas através do um circuito lógico interno da própria CPU, que é responsável por identificar uma sequência específica que indica uma syscall pelo programa,  assim, a CPU verifica o valor da syscall já passada pelas instruções do programa, na tabela IDT inicializada e configurada pelo kernel durante a inicialização, assim a CPU obtém o endereço da ISR associada ao valor da syscall, para assim a ISR resolver a interrupção do programa.

Cada interrupção possui um nível de prioridade específico de acordo com o processador.

Detalhes importantes saber para entender como a CPU executa syscalls ou lida com outros eventos do sistema:

