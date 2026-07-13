Dominar algoritmos de ordenação e busca é fundamental para construir sistemas eficientes. A escolha do algoritmo ideal depende diretamente do volume de dados e das restrições de memória(O(1) vs O(n) de espaço extra).
#### 1. Algoritmos de Ordenação (Sorting) 
Eles organizam os elementos de uma coleção em uma determinada ordem (geralmente crescente ou descrescente).
##### A. Algoritmos Simples (Quadráticos)
Indicados para pequenos volumes de dados devido à simplicidade de implementação.
- [[Bubble Sort]]
- [[Insertion Sort]]
##### B. Algoritmos de Alta Performance (Divisão e Conquista)
São os mais utilizados por trás das bibliotecas padrão (runtimes) das linguagens de programação modernos, devido à eficiência de $O(n \log n)$ no melhor e médio caso.
- [[Merge Sort]]
- [[Quick Sort]]
- [[Heap Sort]]
##### C. Algoritmos Híbridos (O estado da arte)
Os sistemas modernos raramente usam os algoritmos acima de forma "pura". Eles utilizam abordagens híbridas para extrair o melhor de cada cenário.
- [[Tim Sort]]
- [[IntroSort (Introductory Sort)]]
##### D. Algoritmos de Propósito Específico (Tempo Linear)
Existem algoritmos que quebram a barreira de $O(n \log n)$ e conseguem ordenar em tempo linear $O(n)$, mas com uma condição: eles não são algoritmos de comparação.
- [[Counting Sort / Radix Sort]]