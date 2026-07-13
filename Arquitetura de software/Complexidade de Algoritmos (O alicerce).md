A complexidade de algoritmos é medida através da Notação Big O. Ela não mede o tempo em segundos, mas sim o crescimento do número de operações à medida que a quantidade de dados (n) aumenta. 
<font color="#ff0000">A Notação Big O</font> descreve o pior cenário de execução de um algoritmo. Ela responde a pergunta: “Se o meu volume de dados triplicar, quanto tempo a mais o meu sistema vai levar para responder?”
#### 1. As classes de complexidade mais comuns
[[O(1) - Complexidade Constante]]
[[O(log n) - Complexidade Logarítmica]]
[[O(n) - Complexidade Linear]]
[[O(n log n) - Complexidade Quasilinear]]
[[O(n²) - Complexidade Quadrática]]

#### 2. Complexidade de Tempo vs Espaço
Um bom arquiteto avalia dois custos:
1. Time Complexity: Quão rápido o algortimo roda.
2. Space Complexity: Quanta memória RAM ou armazenamento o algoritmo consome durante a execução.
   - Trade-off: Ás vezes, usamos mais memória (cache) para ganhar velocidade (tempo).
Na prática, sempre que escrever um método que manipula listas ou coleções, pergunte-se:
Qual é o Big O disso?
- Se for loop simples: O(n).
- Se for um loop dentro de outro: O(n²).
- Se estiver usando um mapa/dicionário para busca: O(1).