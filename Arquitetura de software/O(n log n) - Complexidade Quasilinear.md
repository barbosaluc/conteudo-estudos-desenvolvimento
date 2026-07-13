#Algoritmos #arquitetura
Representa o “padrão ouro” que permite organizar e reestruturar grandes volumes de dados. Ela é um meio-termo técnico: é um pouco mais lenta do que a complexidade linear O(n), mas é infinitamente superior à complexidade quadrática O(n²).

Se você precisa ordenar uma lista de dados antes de processá-la, o seu objetivo deve ser atingir essa complexidade.
#### O termo Quasilinear

O termo existe porque o algoritmo multiplica uma força linear (n) por uma força logaritmica (log n). Para entender na prática, pense na estratégica Dividir Para Conquistar:

- O log n (dividir): O algoritmo quebra o problema original (uma lista grande) ao meio repetidas vezes até ter vários pedaços minúsculos.
- O n (conquistar/juntar): O algoritmo passa por esses pedaços para combiná-los novamente de forma ordenada.
#### 1. O Exemplo clássico: Ordenação Avançada

Se você usar o método nativa de ordenação, como no java <font color="#ff0000">Collections.sort()</font> , por baixo dos panos eles utilizam algoritmos como o <font color="#ff0000">Merge Sort</font>, <font color="#ff0000">Quick Sort</font> ou <font color="#ff0000">TimSort. </font> 
Todos ele operam em O (n log n).
#### 2. A diferença contra o O(n²)

Antigamente, algoritmos iniciantes de ordenação como o <font color="#f79646">Bubble Sort</font> varriam a lista com um `FOR` dentro de outro O(n²). Veja quando o volume de dados do sistema cresce:

| <font color="#f79646">Elementos (n</font>) | <font color="#f79646">Quadrático O(n²) - ruim</font> | <font color="#f79646">Quasilinear O(n log n) -bom</font> |
| ------------------------------------------ | ---------------------------------------------------- | -------------------------------------------------------- |
| 1.000                                      | 1.000.000 operações                                  | ~10.000 operações                                        |
| 10.000                                     | 100.000.000 operações                                | ~130.000 operações                                       |
| 1.000.000                                  | 1.000.000.000.000 operações                          | ~20.000.000 operações\|                                  |
Impacto na prática: Para ordenar 1 milhão de pedidos, o algoritmo ruim faz 1 trilhão de operações. O algoritmo O(n log n) resolve o mesmo problema com apenas 20 milhões de operações.
### 3. Onde são aplicados no dia a dia

- <font color="#ff0000">Banco de dados (Ordenação em disco)</font> : Quando executa a query ORDER BY em uma coluna que não possuí índice, o banco de dados precisa carregar esses dados e ordená-los na memória/disco. Ele usará O(n log n) para fazer isso.
- <font color="#ff0000">Processamento de Mensagens:</font> Agrupar grandes volumes de eventos ou mensagens chave antes de salvá-los em lote.
- <font color="#ff0000">Algortimos de Grafos Complexos</font> : Vários algoritmos que calculam caminhos ou conexões precisam ordenar as arestas/pesos antes de começar, adotando essa complexidade na sua primeira fase.

#flashcards/algoritmos/O-n-log-n
Como funciona o algoritmo de complexidade quasilinear O(n log n)?::O termo quasilinear existe porque o termo multiplica uma força linear (n) por uma força logaritmica (log n), na prática, o (log n) quebra o problema original (uma lista) repetidas vezes até ter vários pedaços minúsculos.           O (n) o algoritmo passa por esses pedaços para combiná-los novamente de forma ordenada. 