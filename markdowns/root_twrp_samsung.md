# ROOT e TWRP no Samsung
- ## Conceitos abordados:
- * [Stock ROMs](##O que é uma Stock ROM)
- * [ROOT](##ROOT)
- * [Custom recovery (TWRP)](##Custom Recovery)
- ---
- ## O que é uma Stock ROM?
- Uma Stock ROM é conjunto de vários arquivos binários ".img/.bin" que compõem e formam o seu sistema operacional, incluindo drivers e firmwares de fábrica.
- A Stock ROM é desenvolvida e instalada pela própria fabricante do seu dispositivo, pois ela é construida e organizada para se adequar perfeitamente as configurações de hardware do seu dispositivo e o esquema de particionamento do dispositivo de armazenamento dele.
-
- Usar comando ADB para fazer pull e push entre o sistema de arquivo do android e computador.
  Ou usar "adb backup".
  
  Por meio delas vamos ter uma maior noção e compreensão sobre o que nós estamos fazendo, e com o que estamos lidando.
  
  Reduzindo a medo que geralmente as pessoas possuem sobre as operações de modificação do celular, como root e customização do recovery com TWRP.
  
  
  Esses arquivo de .img e .bin possuem muitas funções e responsabilidades, eles são responsáveis por gerenciar e fornecerem as funcionalidades que os dispositivos de hardware possuem, além de fornecerem os componentes básicos e cruciais para o funcionamento do smartphone.
  
  Alguns arquivo .img comuns são:
  
  recovery.img: Arquivo responsável por fornecer ao usuário uma interface para fazer o gerenciamento básico do dispositivo, como opções para redefinação para padrões de fábrica, restauração, testes de gráficos/apps, entre outras opções.
  
  boot.img: Arquivo que carrega o kernel e ramdisk (initramfs) padrão para fábricante, eles geralmente são modificados e implementam e fornecem funcionalidades específicas para o dispositivo.
  
  vendor.img: Possui Drivers e firmwares carregáveis para os diferentes componentes e dispositivos presentes no dispositivo.
  
  vbmeta.img: Responsável por fazer a verificação de bootloader e imagens "flasheadas" nas partições do dispositivo.
  
  system.img: Fornece os binários e utilitários utilizados pelo sistema operacional.