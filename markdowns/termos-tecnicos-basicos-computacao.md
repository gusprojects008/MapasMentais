# Glossário de Termos Técnicos em Computação

## Sistemas Operacionais e Processos
- **Mutex (Mutual Exclusion)**: Mecanismo de sincronização que garante que apenas uma thread acesse um recurso por vez.
- **Deadlock**: Situação em que processos ou threads ficam bloqueados aguardando recursos uns dos outros indefinidamente.
- **Semáforo (Semaphore)**: Estrutura de controle usada para limitar ou coordenar o acesso a recursos compartilhados.
- **Context Switch**: Troca do estado de execução entre diferentes processos ou threads.
- **Overhead**: Custo adicional de processamento ou memória necessário para gerenciar uma tarefa ou recurso.
- **Escalonador (Scheduler)**: Componente do SO que decide qual processo/thread será executado em cada momento.
- **IPC (Inter-Process Communication)**: Métodos para processos trocarem dados (ex.: pipes, filas, memória compartilhada).
- **chroot (Change Root)**: Técnica que altera o diretório raiz de um processo, criando um ambiente isolado semelhante a uma mini-instalação de SO.
- **Concorrência**: Capacidade de executar múltiplas tarefas em sobreposição temporal.
- **Paralelismo**: Execução simultânea de várias tarefas em diferentes núcleos/processadores.
- **Kernel**: Núcleo do sistema operacional, responsável pela comunicação entre hardware e software.
- **Bootloader**: Programa inicial que carrega o sistema operacional na inicialização do computador.
- **Firmware**: Software básico armazenado em memória não volátil de dispositivos, que fornece instruções de baixo nível para o hardware.
- **Driver**: Programa que permite que o sistema operacional se comunique com dispositivos de hardware.
- **Threads**: Fluxos de execução independentes dentro de um mesmo processo.

### Hooks e Handlers
- **Hooks**: Pontos de extensão em softwares ou sistemas onde é possível inserir código personalizado para alterar ou interceptar comportamentos padrão.
- **Handlers**: Funções ou rotinas responsáveis por tratar eventos específicos, como sinais, interrupções ou requisições de usuários.

### Diretórios Virtuais do Kernel Linux
- **/dev** (Device Filesystem - **devtmpfs**): Contém arquivos especiais que representam dispositivos de hardware (como discos e terminais).
- **/proc** (Process Filesystem - **procfs**): Sistema de arquivos virtual que fornece informações em tempo real sobre processos e recursos do sistema.
- **/sys** (System Filesystem - **sysfs**): Exposição de informações do kernel e dispositivos via sysfs, permitindo configuração e monitoramento.
- **/run** (Runtime Filesystem - geralmente em **tmpfs**): Armazena dados de estado temporário do sistema e de serviços durante a execução.
- **/tmp** (Temporary Filesystem - pode usar **tmpfs** ou disco): Diretório de arquivos temporários acessível a processos do usuário e do sistema.

---

## Redes e Comunicação
- **Largura de Banda (Bandwidth)**: Capacidade máxima de transmissão de dados em uma rede.
- **Latência**: Tempo de atraso entre o envio e o recebimento de dados.
- **CDN (Content Delivery Network)**: Grupo de servidores estrategicamente posicionados geograficamente para armazenar conteúdos em cache e fornecê-los para os usuários finais próximos.
- **Firewall**: Sistema de segurança que controla o tráfego de rede com base em regras predefinidas.
- **NAT (Network Address Translation)**: Técnica que permite que múltiplos dispositivos compartilhem um único IP público.
- **QoS (Quality of Service)**: Conjunto de técnicas para priorizar e gerenciar tráfego de rede.
- **Throttling**: Limitação intencional da taxa de transferência de dados ou do uso de recursos para evitar sobrecarga.
- **AWS (Amazon Web Services)**: Plataforma de serviços de computação em nuvem da Amazon, incluindo hospedagem, redes, armazenamento e banco de dados.
- **DHCP (Dynamic Host Configuration Protocol)**: Protocolo que atribui automaticamente endereços IP aos dispositivos na rede.
- **DNS (Domain Name System)**: Sistema que traduz nomes de domínio em endereços IP.
- **Pacote (Packet)**: Unidade de dados transmitida pela rede.
- **Protocolo**: Conjunto de regras que define como dados são transmitidos e recebidos (ex.: TCP/IP, HTTP).

### Subsistemas de Wi-Fi no Kernel Linux
- **nl80211**:  
  Interface **Netlink IPC** usada para comunicação entre processos e aplicações em espaço de usuário e drivers de dispositivos Wi-Fi.  
  É utilizada para requisitar operações para drivers de dispositivos Wi-Fi, por meio de **sockets Netlink do tipo GENL (Generic Netlink)**, onde é necessário fornecer o ID da família **nl80211** para requisitar as operações suportadas.  
  Exemplos de ferramentas que utilizam `nl80211`:  
  - `iw`  
  - `wpa_supplicant`  
  - `hostapd`  

- **cfg80211**:  
  Núcleo do subsistema de rede sem fio do **kernel Linux**, responsável por gerenciar configurações de dispositivos Wi-Fi e oferecer suporte ao `nl80211`.  
  Ele recebe as requisições vindas do espaço de usuário (via nl80211) e se comunica com o driver do dispositivo Wi-Fi.  
  - Para dispositivos **fullMAC** (que implementam toda a pilha 802.11 no firmware), o `cfg80211` envia diretamente os comandos ao driver.  
  - Para dispositivos **softMAC**, o `cfg80211` repassa as operações para o **mac80211**, que implementa a lógica da camada MAC.  

- **mac80211**:  
  Framework de drivers **softMAC** de dispositivos Wi-Fi.  
  Ele implementa a pilha de protocolos MAC da camada **Data-Link** (802.11), sendo responsável por:  
  - Formatação e encapsulamento de quadros 802.11  
  - Controle de retransmissão  
  - Criptografia e descriptografia de quadros  
  - Gerenciamento de associação, autenticação e roaming  
  - Funções de gestão de potência e QoS  

  #### Exemplos de drivers softMAC (utilizam `mac80211`):
  - **iwlwifi** (Intel)  
  - **ath9k** (Atheros)  
  - **rt2800pci/rt2800usb** (Ralink)  

  #### Exemplos de drivers fullMAC (não utilizam `mac80211`):
  - **brcmfmac** (Broadcom)  
  - **wlcore** (TI WiLink)  
  - **mt76** (MediaTek)  

---

## Segurança e Criptografia
- **Blockchain**: Estrutura de dados distribuída e imutável usada como registro descentralizado.
- **Sandbox**: Técnica usada para isolar aplicações em um ambiente seguro e controlado para evitar impactos no sistema real.
- **Docker**: Plataforma que utiliza containers para empacotar aplicações e suas dependências, fornecendo isolamento semelhante a máquinas virtuais, mas com menor overhead.
- **Criptografia**: Técnica de proteger informações por meio de codificação.
- **Chave Simétrica**: Método de criptografia em que a mesma chave é usada para criptografar e descriptografar.
- **Chave Assimétrica**: Método de criptografia que usa um par de chaves (pública e privada).
- **Hash**: Função que gera uma representação única (resumo) de dados.
- **Salt**: Valor aleatório adicionado a senhas antes da aplicação de funções hash para aumentar a segurança.
- **Token**: Credencial digital usada para autenticação ou autorização.
- **2FA (Two-Factor Authentication)**: Autenticação em duas etapas para maior segurança.
- **Exploit**: Código ou técnica que aproveita vulnerabilidades em sistemas.
- **Vulnerabilidade**: Fraqueza em software, hardware ou rede que pode ser explorada.
- **Malware**: Programas maliciosos, como vírus, trojans e worms.
- **Phishing**: Tentativa de obter informações sensíveis enganando o usuário.
- **Backdoor**: Acesso oculto deixado em um sistema para entrada não autorizada.

---

## Programação e Desenvolvimento
- **SQL (Structured Query Language)**: Linguagem usada para gerenciamento de bancos de dados relacionais.  
  - **DDL (Data Definition Language)**: Define a estrutura do banco de dados.  
    - `CREATE`, `ALTER`, `DROP`  
  - **DML (Data Manipulation Language)**: Manipula dados nas tabelas.  
    - `INSERT`, `UPDATE`, `DELETE`  
  - **DQL (Data Query Language)**: Consultas de dados.  
    - `SELECT`  
  - **DCL (Data Control Language)**: Controle de permissões.  
    - `GRANT`, `REVOKE`  
  - **TCL (Transaction Control Language)**: Controle de transações.  
    - `COMMIT`, `ROLLBACK`, `SAVEPOINT`
- **venv (Virtual Environment)**: Ferramenta do Python para criar ambientes isolados, permitindo que projetos usem diferentes versões de bibliotecas sem conflitos.
- **Garbage Collector**: Mecanismo que gerencia e libera memória automaticamente.
- **Overloading**: Definição de múltiplas funções ou operadores com o mesmo nome mas parâmetros diferentes.
- **API (Application Programming Interface)**: Conjunto de rotinas e padrões para integração entre softwares.
- **SDK (Software Development Kit)**: Conjunto de ferramentas e bibliotecas para desenvolvimento de aplicações.
- **IDE (Integrated Development Environment)**: Ambiente integrado com ferramentas de programação, como editor, compilador e debugger.
- **Refatoração**: Reescrita de código para melhorar sua qualidade sem alterar sua funcionalidade.
- **Depuração (Debugging)**: Processo de identificação e correção de erros em programas.
- **Framework**: Estrutura base que facilita o desenvolvimento de softwares.
- **Biblioteca (Library)**: Conjunto de funções prontas para serem usadas por programas.
- **Compilador**: Traduz código-fonte para linguagem de máquina.
- **Interpretador**: Executa código diretamente sem precisar compilar previamente.
- **Polimorfismo**: Capacidade de objetos assumirem diferentes formas dependendo do contexto.
- **Encapsulamento**: Restrição de acesso direto a partes internas de um objeto, expondo apenas interfaces necessárias.

### Estruturas de Frameworks Populares
- **Django (Python)**  
  - **manage.py**: Script principal para comandos administrativos.  
  - **settings.py**: Arquivo de configuração do projeto.  
  - **urls.py**: Define rotas e URLs.  
  - **views.py**: Contém funções/classes que retornam respostas HTTP.  
  - **models.py**: Define as classes que mapeiam as tabelas do banco de dados.  
  - **templates/**: Armazena arquivos HTML para renderização.  
  - **static/**: Arquivos estáticos (CSS, JS, imagens).

- **Next.js (React com Node.js)**  
  - **pages/**: Contém as páginas do site (cada arquivo vira uma rota).  
  - **public/**: Arquivos estáticos acessíveis diretamente.  
  - **components/**: Componentes React reutilizáveis.  
  - **styles/**: Arquivos CSS ou módulos de estilo.  
  - **api/** (dentro de *pages*): Endpoints de API.  
  - **next.config.js**: Arquivo de configuração do Next.js.

- **React.js (biblioteca JS)**  
  - **src/**: Diretório principal do código-fonte.  
  - **components/**: Componentes reutilizáveis.  
  - **App.js**: Componente raiz da aplicação.  
  - **index.js**: Ponto de entrada da aplicação.  
  - **public/**: Arquivos estáticos como favicon e index.html.

---

## Hardware e Arquitetura
- **Barramento (Bus)**: Canal de comunicação entre componentes do computador.
- **Virtualização**: Técnica que permite executar múltiplos sistemas operacionais em um mesmo hardware físico.
- **Hyper-Threading**: Tecnologia que permite que um núcleo de CPU execute múltiplos threads simultaneamente.
- **I/O (Input/Output)**: Operações de entrada e saída de dados de/para dispositivos externos.
- **CPU (Central Processing Unit)**: Unidade central de processamento responsável por executar instruções.
- **GPU (Graphics Processing Unit)**: Processador especializado em cálculos gráficos e paralelos.
- **RAM (Random Access Memory)**: Memória volátil usada para armazenamento temporário de dados em execução.
- **ROM (Read-Only Memory)**: Memória apenas de leitura, geralmente usada para firmware.
- **Cache**: Memória de alta velocidade que armazena dados usados frequentemente.
- **Overclocking**: Aumento da frequência de operação de um processador além das especificações de fábrica.
 **Virtualização**: Técnica que permite executar múltiplos sistemas operacionais em um mesmo hardware físico.
