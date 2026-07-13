#arquitetura-de-software #Algoritmos 
A ideia central: <font color="#de7802">é muito mais fácil e rápido ordenar dois sub-arrays pequenos que já estão ordenados do que ordenar um array grande e bagunçado de uma vez só.</font>
#### O Funcionamento em Duas Fases
O algoritmo funciona de forma recursiva e pode ser dividido em duas etapas principais:
#####  1. Fase de Divisão (Top Down)
O algoritmo pega o array original e o divide consecutivamente ao meio. Ele faz isso repetidas vezes até que o array seja quebrado em sub-arrays que contenham **apenas 1 elemento**.

> **Por que 1 elemento?** Porque um array com apenas um elemento está, conceitualmente, 100% ordenado.

##### 2. Fase de Conquista e Junção (Merge)
O algoritmo começa a reconstruir o array, combinando (_merging_) os sub-arrays unitários de dois em dois, mas já os posicionando de forma ordenada. Ele vai subindo essa estrutura até que todos os pedaços se juntem novamente em um único array totalmente ordenado.
#### Exemplo Visual Prático
Imagine que temos o seguinte array: `[38, 27, 43, 3]`
##### **Fase 1: Divisão**

1. Divide ao meio: `[38, 27]` e `[43, 3]`
2. Divide novamente: `[38]`, `[27]`, `[43]`, `[3]` (Chegamos à base: arrays unitários).

##### **Fase 2: Junção (O processo de Merge)**

Agora, o algoritmo compara os elementos par a par para juntá-los:

1. Compara `38` e `27` $\rightarrow$ junta ordenando: `[27, 38]`
2. Compara `43` e `3` $\rightarrow$ junta ordenando: `[3, 43]`
3. Agora precisamos juntar `[27, 38]` com `[3, 43]`.

##### **Como funciona a junção final:**

O algoritmo usa dois "ponteiros" (indicadores), um no início de cada sub-array, e compara quem é menor:

- Compara `27` (do primeiro) com `3` (do segundo). `3` é menor $\rightarrow$ Novo Array: `[3]`
- Compara `27` com `43`. `27` é menor $\rightarrow$ Novo Array: `[3, 27]`
- Compara `38` com `43`. `38` é menor $\rightarrow$ Novo Array: `[3, 27, 38]`
- O primeiro sub-array acabou. Copia o resto do segundo $\rightarrow$ Novo Array: `[3, 27, 38, 43]`

O array está ordenado.
#### Análise Arquitetural e Complexidade
Como arquiteto de software, o que realmente importa no Merge Sort são os seus comportamentos de infraestrutura e recursos:

- **Complexidade de Tempo( [[O(n log n) - Complexidade Quasilinear]]) :** A árvore de divisão tem uma altura de $\log n$, e em cada nível dessa árvore, o algoritmo precisa passar por todos os $n$ elementos para fazer a junção. O ponto mais forte do Merge Sort é a **previsibilidade**: ele será $O(n \log n)$ se o array estiver totalmente bagunçado, se estiver invertido, ou se já estiver 100% ordenado.
    
- **Complexidade de Espaço ([[O(n) - Complexidade Linear]]):** Esta é a sua maior desvantagem. Para fazer a junção (_merge_), ele não consegue mexer diretamente na mesma memória do array original de forma eficiente; ele precisa criar um array auxiliar temporário do mesmo tamanho dos dados que estão sendo ordenados. Se você estiver ordenando um array de 2GB na memória, precisará de mais 2GB de espaço livre para o processo.
    
- **Estabilidade:** Ele é um algoritmo estável. Se houver dois objetos com a mesma chave de ordenação (por exemplo, dois pedidos com o mesmo valor), o Merge Sort garante que a ordem original deles não será alterada.
#### Onde ele brilha na prática
O Merge Sort é o algoritmo ideal para **External Sorting** (Ordenação Externa).

Se o seu sistema precisa ordenar um arquivo de Log ou uma tabela de banco de dados de **100 GB**, mas o seu servidor só tem **8 GB de memória RAM**, você não pode carregar tudo na memória.

Você pode usar o Merge Sort para quebrar esse arquivo gigante em arquivos menores de 4 GB, ordenar cada um na memória (usando Quick Sort, por exemplo) e depois usar a lógica de _Merge_ do Merge Sort para ler o início de cada arquivo em disco e ir cuspindo o resultado final ordenado diretamente para um arquivo de saída, consumindo pouquíssima RAM durante a junção.

#flashcards/algoritmos-de-ordenação/merge-sort 
Como funciona o algoritmo de ordenação Merge Sort?::O algoritmo quebra um array em vários sub-arrays até que contenham apenas 1 elemento em cada sub-array e depois faz o Merge, juntando e comparando cada elemento unitário de dois em dois já os posicionando de forma ordenada. E vai subindo essa estrutura até que tenha apenas um array totalmente ordenado. Seu melhor e pior caso possuem a mesma complexidade de tempo: **$O(n \log n)$**.