O **Insertion Sort** (ou Ordenação por Inserção) é outro algoritmo clássico e muito intuitivo. A melhor forma de mentalizar o seu funcionamento é lembrar de como você **organiza as cartas na mão jogando baralho**:

Você pega uma carta de cada vez, compara com as que já estão na sua mão (que já estão ordenadas) e a **insere** na posição correta, empurrando as cartas maiores para a direita.

## Como o Insertion Sort funciona?

O algoritmo divide virtualmente o array em duas partes: uma **sublista ordenada** (à esquerda) e uma **sublista não ordenada** (à direita). No início, o primeiro elemento é considerado a parte ordenada.

O processo segue estes passos:

1. Começa a partir do segundo elemento (o primeiro elemento não ordenado). Ele é guardado em uma variável temporária, geralmente chamada de **chave** (ou _key_).
2. Compara essa chave com os elementos da sublista ordenada à esquerda (movendo do fim da sublista para o início).
3. Se o elemento ordenado for **maior** que a chave, você move esse elemento uma posição para a direita.
4. Repete o passo 3 até encontrar um elemento menor (ou igual) à chave, ou até chegar ao início da lista.
5. **Insere** a chave na vaga liberada.
6. Avança para o próximo elemento não ordenado.
### Exemplo Prático

Imagine a lista: `[5, 2, 4, 6]`

- **1ª Rodada (Chave = 2):**
    - O `5` é considerado ordenado. A chave é `2`.
    - Compara 5 com 2 $\rightarrow$ 5 > 2, move o 5 para a direita: `[5, 5, 4, 6]`.
    - Chegou ao início. Insere o 2 na primeira posição.
    - Lista atual: `[2, 5, 4, 6]` (Sublista ordenada: `[2, 5]`)
- **2ª Rodada (Chave = 4):**
    - Compara 5 com 4 $\rightarrow$ 5 > 4, move o 5 para a direita: `[2, 5, 5, 6]`.
    - Compara 2 com 4 $\rightarrow$ 2 < 4, para o movimento.
    - Insere o 4 logo após o 2.
    - Lista atual: `[2, 4, 5, 6]` (Sublista ordenada: `[2, 4, 5]`)
- **3ª Rodada (Chave = 6):**
    - Compara 5 com 6 $\rightarrow$ 5 < 6, para imediatamente. O 6 já está no lugar certo.
    - Lista final: `[2, 4, 5, 6]`

## Análise de Complexidade e Características

- **Complexidade de Tempo:**
    - **Pior Caso:** $O(n^2)$ — Ocorre se o array estiver em ordem totalmente inversa.
    - **Caso Médio:** $O(n^2)$ — Para dados distribuídos aleatoriamente.
    - **Melhor Caso:** $O(n)$ — Ocorre se o array **já estiver ordenado**. Ele apenas passa fazendo $n-1$ comparações e nenhuma troca.
- **Complexidade de Espaço:** $O(1)$ — É um algoritmo _In-place_ (consome apenas uma quantidade constante de memória extra para a variável chave).
- **Estabilidade:** **Sim**. Ele preserva a ordem de elementos com chaves iguais.
## Quando o Insertion Sort vale a pena?

Diferente do Bubble Sort, o Insertion Sort **é muito utilizado na prática**, mesmo tendo pior caso quadrático. Ele brilha nos seguintes cenários:

1. **Arrays Pequenos:** Para listas pequenas (geralmente menos de 10 a 20 elementos), o overhead de recursão e divisões de algoritmos como Quick Sort ou Merge Sort faz com que eles sejam mais lentos que o simples Insertion Sort.
    
2. **Dados Quase Ordenados:** Se você recebe um fluxo de dados onde a maioria já está no lugar (por exemplo, adicionar novos registros em um banco que já mantém histórico ordenado), ele roda quase em tempo linear $O(n)$.
    
3. **Algoritmos Híbridos:** Linguagens modernas utilizam algoritmos híbridos em suas bibliotecas padrão. O **Timsort** (usado no Java para `Arrays.sort` de objetos e no Python) e o **IntroSort** (usado no C++) rodam algoritmos robustos (Merge/Quick) para grandes volumes e mudam automaticamente para o Insertion Sort quando as subdivisões ficam pequenas.