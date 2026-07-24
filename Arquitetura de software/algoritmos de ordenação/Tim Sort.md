É um dos algoritmos de ordenação mais eficientes e utilizados no mundo real.
Foi adotado como algoritmo padrão de ordenação em diversas linguagens de programação como o Java (``Arrays.sort``).
Trata-se de um algoritmo híbrido, estável e adaptativo:
- <font color="#de7802">Híbrido</font> : Combina as melhores características do [[Insertion Sort]] e do [[Merge Sort]].
- <font color="#de7802">Estável</font> : Preserva a ordem relativa de elementos com chaves iguais.
- <font color="#de7802">Adaptativo</font> : Aproveita padrões de ordenação já existentes nos dados reais para rodar mais rápido.
### Como funciona (passo a passo)
A ideia central do Timsort é que, no mundo real, conjuntos de dados raramente são 100%  aleatórios - eles quase sempre possuem "``subsequências``" que já estão ordenadas (crescentes ou descrescentes).

```
Vetor Original 
	└── 1. Identifica/Cria "Runs" (Sequências Curtas) 
		└── 2. Ordena os Runs com Insertion Sort 
			└── 3. Intercala os Runs com Merge Sort (+ Galloping) 
				└── Vetor Ordenado
```
#### 1. Definição do `minrun`
O algoritmo começa calculando um parâmetro chamado ``minrun``.
- O ``minrun`` define o tamanho mínimo das subsequências que serão criadas.
- Geralmente, é um número entre 32 e 64.
- A escolha é feita de forma que o tamanho do vetor original dividido pelo ``minrun`` resulte em um número próximo ou igual a uma potência de 2 (o que torna a etapa do Merge extremamente eficiente).
#### 2. Criação e ajuste dos ``Runs``
O Timsort percorre o vetor procurando por ``Runs`` (sequências naturais de dados) :
- <font color="#de7802">Se o Run for decrescente</font> : Ele inverte os elementos para torná-lo crescente.
- <font color="#de7802">Se o Run for menor que minrun</font> : O algoritmo pega elementos adicionais até atingir o tamanho do ``minrun`` e aplica o <font color="#ff0000">Binary Insertion Sort</font> (uma variação do Insertion Sort que usa busca binária para encontrar a posição correta, muito rápida para arrays pequenos).
#### 3. Intercalação (Merge)
Conforme os _runs_ ordenados são identificados e ajustados, eles são colocados em uma pilha de controle. Para garantir que o _merge_ seja equilibrado e eficiente, o Timsort aplica regras estritas sobre o tamanho dos _runs_ no topo da pilha antes de intercalá-los (semelhante ao balanceamento de uma árvore).
#### 4. O Truque de Mestre: Modo Galloping (Galope)
Durante a fase de intercalação (_merge_ de dois _runs_, $A$ e $B$), se o algoritmo percebe que vários elementos consecutivos vêm do mesmo _run_ (por exemplo, 7 elementos seguidos de $A$ são menores que o primeiro de $B$), ele entra no **Modo Galloping**:

- Em vez de comparar elemento por elemento ($O(1)$ a cada passo), ele passa a fazer uma **busca exponencial/binária** para encontrar a posição de inserção.
    
- Isso permite pular blocos inteiros de dados de uma só vez, reduzindo drasticamente o número de comparações.
## Análise de Complexidade


|     Cenário     | Complexidade de Tempo |                          Explicação                           |
|:---------------:|:---------------------:|:-------------------------------------------------------------:|
|   Melhor Caso   |        $O(N)$         | Ocorre quando os dados já estão quase inteiramente ordenados. |
|   Caso Médio    |     $O(N \log N)$     |               Desempenho padrão e consistente.                |
|    Pior Caso    |     $O(N \log N)$     |        Mantém a garantia de desempenho do Merge Sort.         |
| Espaço Auxiliar |        $O(N)$         |  Necessita de memória extra temporária para a intercalação.   |

#flashcards/arquitetura-de-software/algoritmo-ordenacao/timsort 
Como funciona o algoritmo Timsort?
?
É um algoritmo de ordenação híbrido (Merge sort + Insertion Sort) padrão em liguagens com Python e Java.
Como funciona ?
1. Runs: Divide os dados em pequenas sequências ordenadas.
2. Minrun: Define um tamanho mínimo (32-64) e usa Binary Insertion Sort para ordenar
blocos menores que isso.
3. Merge: Combina os runs usando a lógica do Merge Sort, mas com regras de balanceamento.
4. Galloping Mode: Durante o merge, se um bloco é muito maior que outro, ele "pula" elementos via busca binária para acelerar a intercalação.
**Complexidade**
Melhor caso: O(n) (dados já ordenados).
Média / pior caso: O(n log n).
Espaço:  O(n).
**Diferencial Arquitetural**
Projetado para dados do mundo real, que raramente são aleatórios e costumam conter sequências parcialmente ordenadas.