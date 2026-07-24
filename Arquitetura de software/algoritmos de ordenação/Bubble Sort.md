O Bubble Sort (ou ordenação por flutuação) é um dos algoritmos de ordenação mais simples e intuitivos. O nome "Bubble" (bolha) vem da lógica do algoritmo: os maiores elementos "flutuam" para o final da lista a cada iteração.
##### Como o Bubble Sort funciona?
O algoritmo funciona por meio de comparações e trocas diretas. Ele percorre a lista várias vezes, comparando sempre dois elementos adjacentes (lados a lado).
1. Compara o primeiro elemento com o segundo.
2. Se o primeiro for maior que o segundo, ele trocam de lugar.
3. Avança para o próximo par (segundo com o terceiro) e repete a comparação.
4. Ao final da primeira passagem completa pela lista, o maior elemento terá "flutuado" até a última posição.
5. O processo é repetido para o restante da lista (excluindo os elementos que já estão nas posições finais corretas) até que nenhuma troca seja necessária em uma passada completa.
### Exemplo Prático

Imagine a lista: `[5, 1, 4, 2]`

- **1ª Passagem:**
    - Compara 5 e 1 $\rightarrow$ 5 > 1, troca. Lista: `[1, 5, 4, 2]`
    - Compara 5 e 4 $\rightarrow$ 5 > 4, troca. Lista: `[1, 4, 5, 2]`
    - Compara 5 e 2 $\rightarrow$ 5 > 2, troca. Lista: `[1, 4, 2, 5]` _(O 5 chegou ao fim)_
- **2ª Passagem:**
    - Compara 1 e 4 $\rightarrow$ 1 < 4, não troca.
    - Compara 4 e 2 $\rightarrow$ 4 > 2, troca. Lista: `[1, 2, 4, 5]` _(O 4 chegou ao seu lugar)_
- **3ª Passagem:**
    - Compara 1 e 2 $\rightarrow$ 1 < 2, não troca. Como nenhuma troca foi feita nesta rodada, o algoritmo sabe que a lista está ordenada e para.
## Análise de Complexidade e Características

- **Complexidade de Tempo:**
    - **Pior Caso:** $O(n^2)$ — Ocorre quando a lista está em ordem inversamente ordenada.
    - **Caso Médio:** $O(n^2)$ — Para listas com distribuições aleatórias.
    - **Melhor Caso:** $O(n)$ — Ocorre se a lista já estiver ordenada. Para isso, o código precisa de uma flag de otimização que verifica se houve alguma troca na primeira passada.
- **Complexidade de Espaço:** $O(1)$ — É um algoritmo _In-place_ (ordena na própria memória original, sem precisar de uma lista auxiliar).
    
- **Estabilidade:** **Sim**, é um algoritmo estável. Se houver dois elementos iguais (ex: dois números 5), eles manterão a ordem relativa que tinham antes da ordenação.
## Quando usar o Bubble Sort?

 **quase nunca em ambientes de produção**. Devido à sua complexidade quadrática $O(n^2)$, ele se torna extremamente lento à medida que o volume de dados cresce. Algoritmos como o _Quick Sort_ ou _Merge Sort_ são muito mais eficientes.

No entanto, ele é excelente para fins **educacionais** (para entender o conceito de loops, ponteiros e ordenação básica) ou para cenários onde a lista é muito pequena e a simplicidade do código importa mais do que a performance pura.