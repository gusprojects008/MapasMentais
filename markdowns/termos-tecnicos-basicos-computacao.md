# Glossário de Termos Técnicos em Computação

## Sistemas Operacionais e Processos
- **Kernel**: Núcleo do sistema operacional, responsável pela comunicação entre hardware e software.
- **Bootloader**: Programa inicial que carrega o sistema operacional na inicialização do computador.
- **Firmware**: Software básico armazenado em memória não volátil de dispositivos, que fornece instruções de baixo nível para o hardware.
- **Driver**: Programa que permite que o sistema operacional se comunique com dispositivos de hardware.
- **Threads**: Fluxos de execução independentes dentro de um mesmo processo.
- **Concorrência**: Capacidade de executar múltiplas tarefas em sobreposição temporal.
- **Paralelismo**: Execução simultânea de várias tarefas em diferentes núcleos/processadores.
- **Mutex**: (Mutual Exclusion) mecanismo de sincronização que garante que apenas uma thread acesse um recurso por vez.
- **Deadlock**: Situação em que processos ou threads ficam bloqueados aguardando recursos uns dos outros indefinidamente.
- **Overhead**: Custo adicional de processamento ou memória necessário para gerenciar uma tarefa ou recurso.
- **Escalonador (Scheduler)**: Componente do SO que decide qual processo/thread será executado em cada momento.
- **Context Switch**: Troca do estado de execução entre diferentes processos ou threads.
- **Semáforo (Semaphore)**: Estrutura de controle usada para limitar ou coordenar o acesso a recursos compartilhados.
- **IPC (Inter-Process Communication)**: Métodos para processos trocarem dados (ex.: pipes, filas, memória compartilhada).
- **chroot**: (Change Root) Técnica que altera o diretório raiz de um processo, criando um ambiente isolado semelhante a uma mini-instalação de SO.

## Redes e Comunicação
- **Largura de Banda (Bandwidth)**: Capacidade máxima de transmissão de dados em uma rede.
- **Latência**: Tempo de atraso entre o envio e o recebimento de dados.
- **Pacote (Packet)**: Unidade de dados transmitida pela rede.
- **Protocolo**: Conjunto de regras que define como dados são transmitidos e recebidos (ex.: TCP/IP, HTTP).
- **DHCP (Dynamic Host Configuration Protocol)**: Protocolo que atribui automaticamente endereços IP aos dispositivos na rede.
- **DNS (Domain Name System)**: Sistema que traduz nomes de domínio em endereços IP.
- **Firewall**: Sistema de segurança que controla o tráfego de rede com base em regras predefinidas.
- **CDN (Content Delivery Network)**: É um um grupo de servidores estratégicamente posicionados geograficamente para armazenar conteúdos em cache e fornecê-los para os usuários finais próximos.
- **VPN (Virtual Private Network)**: Rede privada criada sobre a internet pública para aumentar segurança e privacidade.
- **NAT (Network Address Translation)**: Técnica que permite que múltiplos dispositivos compartilhem um único IP público.
- **QoS (Quality of Service)**: Conjunto de técnicas para priorizar e gerenciar tráfego de rede.
- **Throttling**: Limitação intencional da taxa de transferência de dados ou do uso de recursos para evitar sobrecarga.
- **AWS (Amazon Web Services)**: Plataforma de serviços de computação em nuvem da Amazon, incluindo hospedagem, redes, armazenamento e banco de dados.

## Segurança e Criptografia
- **Criptografia**: Técnica de proteger informações por meio de codificação.
- **Chave Simétrica**: Método de criptografia em que a mesma chave é usada para criptografar e descriptografar.
- **Chave Assimétrica**: Método de criptografia que usa um par de chaves (pública e privada).
- **Hash**: Função que gera uma representação única (resumo) de dados.
- **Salt**: Valor aleatório adicionado a senhas antes da aplicação de funções hash para aumentar a segurança.
- **Token**: Credencial digital usada para autenticação ou autorização.
- **2FA (Two-Factor Authentication)**: Autenticação em duas etapas para maior segurança.
- **Exploit**: Código ou técnica que aproveita vulnerabilidades em sistemas.
- **Vulnerabilidade**: Fraqueza em software, hardware ou rede que pode ser explorada.
- **Blockchain**: Estrutura de dados distribuída e imutável usada como registro descentralizado.
- **Malware**: Programas maliciosos, como vírus, trojans e worms.
- **Phishing**: Tentativa de obter informações sensíveis enganando o usuário.
- **Backdoor**: Acesso oculto deixado em um sistema para entrada não autorizada.
- **Sandbox**: Técnica usada para isolar aplicações em um ambiente seguro e controlado para evitar impactos no sistema real.
- **Docker**: Plataforma que utiliza containers para empacotar aplicações e suas dependências, fornecendo isolamento semelhante a máquinas virtuais, mas com menor overhead.

## Programação e Desenvolvimento
- **API (Application Programming Interface)**: Conjunto de rotinas e padrões para integração entre softwares.
- **SDK (Software Development Kit)**: Conjunto de ferramentas e bibliotecas para desenvolvimento de aplicações.
- **IDE (Integrated Development Environment)**: Ambiente integrado com ferramentas de programação, como editor, compilador e debugger.
- **Refatoração**: Reescrita de código para melhorar sua qualidade sem alterar sua funcionalidade.
- **Depuração (Debugging)**: Processo de identificação e correção de erros em programas.
- **Framework**: Estrutura base que facilita o desenvolvimento de softwares.
- **Biblioteca (Library)**: Conjunto de funções prontas para serem usadas por programas.
- **Compilador**: Traduz código-fonte para linguagem de máquina.
- **Interpretador**: Executa código diretamente sem precisar compilar previamente.
- **Garbage Collector**: Mecanismo que gerencia e libera memória automaticamente.
- **Overloading**: Definição de múltiplas funções ou operadores com o mesmo nome mas parâmetros diferentes.
- **Polimorfismo**: Capacidade de objetos assumirem diferentes formas dependendo do contexto.
- **Encapsulamento**: Restrição de acesso direto a partes internas de um objeto, expondo apenas interfaces necessárias.
- **venv (Virtual Environment)**: Ferramenta do Python para criar ambientes isolados, permitindo que projetos usem diferentes versões de bibliotecas sem conflitos.
- **SQL (Structured Query Language)**: Linguagem usada para gerenciamento de bancos de dados relacionais.  
  - **DDL (Data Definition Language)**: Define a estrutura do banco de dados.  
    - `CREATE` (cria tabelas, índices, etc.)  
    - `ALTER` (modifica tabelas existentes)  
    - `DROP` (remove tabelas ou objetos)  
  - **DML (Data Manipulation Language)**: Manipula dados dentro das tabelas.  
    - `INSERT` (insere novos registros)  
    - `UPDATE` (altera registros existentes)  
    - `DELETE` (remove registros)  
  - **DQL (Data Query Language)**: Consultas de dados.  
    - `SELECT` (recupera dados de tabelas)  
  - **DCL (Data Control Language)**: Controle de permissões.  
    - `GRANT` (concede privilégios)  
    - `REVOKE` (revoga privilégios)  
  - **TCL (Transaction Control Language)**: Controle de transações.  
    - `COMMIT` (confirma alterações)  
    - `ROLLBACK` (desfaz alterações)  
    - `SAVEPOINT` (define pontos de restauração)

## Hardware e Arquitetura
- **CPU (Central Processing Unit)**: Unidade central de processamento responsável por executar instruções.
- **GPU (Graphics Processing Unit)**: Processador especializado em cálculos gráficos e paralelos.
- **RAM (Random Access Memory)**: Memória volátil usada para armazenamento temporário de dados em execução.
- **ROM (Read-Only Memory)**: Memória apenas de leitura, geralmente usada para firmware.
- **Cache**: Memória de alta velocidade que armazena dados usados frequentemente.
- **Barramento (Bus)**: Canal de comunicação entre componentes do computador.
- **Overclocking**: Aumento da frequência de operação de um processador além das especificações de fábrica.
- **Hyper-Threading**: Tecnologia que permite que um núcleo de CPU execute múltiplos threads simultaneamente.
- **I/O (Input/Output)**: Operações de entrada e saída de dados de/para dispositivos externos.
- **Virtualização**: Técnica que permite executar múltiplos sistemas operacionais em um mesmo hardware físico.
