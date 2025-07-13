# Matemática básica para programadores

Uma das grandes vantagens de sempre ter em mente conceitos matemáticos e computacionais básicos, é capacidade de poder resolver problemas de forma mais rápida, simples e eficiente para a memória e processamento do computador.

Além de auxiliar na criatividade de soluções e funcionalidades complexas e eficientes.

---

## Operadores aritméticos básicos, propósitos e funcionalidades

- **`+`**: Soma 2 números ou elementos, exemplo: `1 + 1` ou `"a" + "b"` e em algumas linguagens: `"a" + 1`.
  - Operação em termos matemáticos: `Parcela + Parcela = Soma/resultado`

- **`-`**: Subtrai um número do outro `1 - 1 = 0`, assim também encontrando a diferença entre eles.
  - Operação em termos matemáticos: `Minuendo - Subtraendo = Diferença/resultado`   

- `*`: Multiplica dois valores, repetindo o primeiro valor quantas vezes indica o segundo. Exemplo: `3 * 4 = 12` (ou seja, 3 somado 4 vezes).
  - Operação em termos matemáticos: `Multiplicando × Multiplicador = Produto/resultado`

- **`/`**: Divide um valor (Dividendo) pela quantidade de vezes do outro (Divisor), dessa forma, encontrando o número/resultado (Quociente) que indique quantas vezes ele pode ser multiplicado pelo segundo valor (Divisor), para chegar no primeiro valor (Dividendo). Exemplo: `10 / 2 = 5 -> 5 * 2 = 10`. Em linguagens de programação, usar "/" Pode gerar número com casas decimais (float), mas usar "//" resulta em um resultado inteiro (sem casa decimais).
  - Operação em termos matemáticos: `Dividendo ÷ Divisor = Quociente/resultado`

---

## Operadores aritméticos e funções matemáticas intermediárias, propósitos e funcionalidades

- **`!`**: Fatorial calcula o produto de todos os inteiros positivos de 1 até `n`. Exemplo: `5! = 5 × 4 × 3 × 2 × 1 = 120`. Muito usado em **combinatória** (contar possibilidades), **recursão**, análise de **complexidade** e problemas de permutação.
  - Operação em termos matemáticos: `n! = n × (n-1) × (n-2) × ... × 1`

- **`log`**: Logaritmo inverte a operação de exponenciação. Retorna o expoente ao qual a base deve ser elevada para se obter um número. Exemplo: `log₂(8) = 3`, pois \(2^3 = 8\). Em programação, usa-se `log` (base `e`), `log10` (base 10), ou `log2` (base 2).

---

### Funções trigonométricas e fundamentos gráficos

Essas funções aparecem com frequência em **animações**, **processamento de sinais**, **física**, **geometria** e **visualização gráfica**.

- **`cos`**: Função cosseno — Relaciona a projeção horizontal de um ponto sobre a circunferência unitária. Exemplo: `cos(0) = 1`, `cos(π/2) = 0`. Usado para calcular ângulos, rotação de vetores e componentes x de movimentos periódicos.

- **`sin`**: Função seno — Relaciona a projeção vertical de um ponto na circunferência unitária. Exemplo: `sin(0) = 0`, `sin(π/2) = 1`. Usado para vibrações, ondas, física e movimento oscilatório.

---

### Plano Cartesiano

O **plano cartesiano** foi proposto por René Descartes e une a geometria com a álgebra, permitindo representar pontos no espaço com coordenadas numéricas (x, y). É a base para sistemas de gráficos, vetores, colisões, transformações geométricas e desenho computacional.

---

### Transformadas de Fourier

As **transformadas de Fourier** (criação de Joseph Fourier) servem para decompor sinais em suas **frequências componentes**. Qualquer onda pode ser expressa como a soma de senos e cossenos.  
Usada em:

- Processamento de sinais (áudio, sensores, rádio).
- Compressão (JPEG, MP3).
- Reconhecimento de padrões (visão computacional).
- Engenharia, eletrônica e matemática aplicada.

---

## Big O Notation

A **notação Big O** descreve o comportamento de um algoritimo em relação ao tempo de execução e desempenho/eficiência à medida que a entrada/processamento de dados cresce. A notação ***Big Oh*** Ignora detalhes como tempo real de execução e foca na **ordem de crescimento** do algoritimo.

| Notação      | Nome             | Exemplo                        |
|--------------|------------------|--------------------------------|
| `O(1)`       | Constante        | Acesso direto em array         |
| `O(log n)`   | Logarítmica      | Busca binária                  |
| `O(n)`       | Linear           | Percorrer uma lista            |
| `O(n log n)` | Quase-linear     | Merge Sort, Quick Sort         |
| `O(n²)`      | Quadrática       | Bubble Sort, nested loops      |
| `O(2^n)`     | Exponencial      | Backtracking, subsets          |

Quanto menor a complexidade, **mais escalável** o algoritmo é para entradas grandes.

---

## Estruturas de Dados: principais tipos, propósitos e funcionalidades

### Arrays (Vetores)
- **Descrição**: Estrutura linear de elementos de tamanho fixo, acessados por índice.
- **Usos**: Acesso rápido (O(1)), armazenamento sequencial, algoritmos que manipulam listas fixas.
- **Limitações**: Tamanho fixo, inserções/remoções custosas (O(n)).

### Listas Ligadas (Linked Lists)
- **Descrição**: Elementos armazenam valor + ponteiro para o próximo (e/ou anterior).
- **Tipos**: 
  - Simples: aponta só para o próximo.
  - Duplamente ligada: aponta para anterior e próximo.
- **Usos**: Inserções/remoções rápidas em qualquer ponto da lista.
- **Limitações**: Acesso sequencial (O(n)).

### Hash Table (Map / Dicionário)
- **Descrição**: Associa chaves a valores usando função de hash.
- **Usos**: Busca e acesso ultra rápidos (O(1) em média).
- **Limitações**: Colisões, pior caso O(n).

### Pilha (Stack)
- **Descrição**: Estrutura LIFO (Last In, First Out).
- **Usos**: Execução de funções, backtracking, algoritmos DFS.
- **Complexidade**: O(1) para inserção e remoção.

### Conjuntos (Set)
- **Descrição**: Coleção de valores únicos, sem ordem específica.
- **Usos**: Verificação de duplicatas, operações matemáticas de união/interseção.

### Fila (Queue)
- **Descrição**: Estrutura FIFO (First In, First Out).
- **Operações**: 
- **Usos**: Algoritmos BFS, buffers, sistemas de espera.
- **Variações**: Fila dupla (deque), prioridade (priority queue).

### Árvores (Trees)
- **Descrição**: Estrutura hierárquica onde cada nó aponta para filhos.
- **Tipos importantes**:
  - Binária
  - Binária de Busca (BST)
  - AVL, Red-Black (autobalanceadas)
  - Trie (prefixos)
- **Usos**: Busca eficiente, organização hierárquica, auto-complete.
- **Complexidade média**: O(log n) busca/inserção em árvores balanceadas.

### Fila de Prioridade (Priority Queue / Heap)
- **Descrição**: Elemento com maior (ou menor) prioridade é removido primeiro.
- **Implementação comum**: Heap binário.
- **Usos**: Algoritmos como Dijkstra, agendamento de tarefas.
- **Complexidade**: Inserção e remoção O(log n).

### Grafos (Graphs)
- **Descrição**: Conjunto de nós (vértices) conectados por arestas.
- **Representações**:
  - Lista de adjacência (eficiente)
  - Matriz de adjacência (simples, mas consome espaço)
- **Tipos**: Dirigido, não-dirigido, ponderado, cíclico, acíclico.
- **Usos**: Redes, caminhos mínimos (Dijkstra, BFS/DFS), IA, web.
