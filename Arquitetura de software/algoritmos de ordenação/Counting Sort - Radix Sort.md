#arquitetura-de-software/algoritmo-ordenacao 
São <font color="#de7802">algoritmos de ordenação não comparativos.</font>
## Counting Sort (Ordenação por contagem)

O Counting Sort funciona contando a frequência de cada valor presente no array e usando essas contagens para determinar a posição exata de cada elemento na saída.
**Requisito essencial:** Os elementos devem ser inteiros pertencentes a um intervalo conhecido e limitado (de $0$ até $K$).
#### Passo a Passo

1. **Contagem:** Cria-se um array auxiliar `count` de tamanho $K+1$. Varre-se o array original incrementando a frequência de cada número.
    
2. **Soma Acumulada:** Transforma-se o array `count` em posições acumuladas (`count[i] = count[i] + count[i-1]`). Isso indica até qual índice no array final cada valor deve ir.
    
3. **Construção da Saída:** Mapeia-se o array original de trás para frente (garantindo **estabilidade**) colocando os elementos no array ordenado de acordo com as posições do `count`.
#### Complexidade e Propriedades
- **Tempo:** $\mathcal{O}(n + K)$, onde $n$ é o número de elementos e $K$ é o tamanho do intervalo de valores.
- **Espaço Auxiliar:** $\mathcal{O}(n + K)$.
- **Estabilidade:** **Estável** (mantém a ordem relativa de elementos de mesmo valor).
- **Limitação:** Se $K$ for muito maior que $n$ (ex: ordenar `[1, 1000000]`), a eficiência cai drasticamente e consome memória excessiva.
## Radix Sort (Ordenação por Raízes/Dígitos)
O Radix Sort resolve o problema de grandes intervalos do Counting Sort ordenando os elementos **dígito a dígito** (ou caractere a caractere), do dígito menos significativo (LSD) para o mais significativo (MSD).

**Requisito essencial:** O algoritmo de ordenação interno usado em cada dígito **precisa ser estável** (o Counting Sort é a escolha padrão).
#### Passo a Passo

1. Identifica-se o número máximo de dígitos dos elementos.
2. Para cada posição de dígito (unidades, dezenas, centenas...):
    - Aplica-se o **Counting Sort** considerando apenas o dígito atual.
    - Graças à estabilidade do Counting Sort, a ordenação dos dígitos anteriores é preservada à medida que avançamos para os mais significativos.
#### Exemplo Visual (LSD)

Array inicial: `[170, 045, 075, 090, 802, 024, 002, 066]`

1. **Ordena pelas Unidades:** `[170, 090, 802, 002, 024, 045, 075, 066]`
2. **Ordena pelas Dezenas:** `[802, 002, 024, 045, 066, 170, 075, 090]`
3. **Ordena pelas Centenas:** `[002, 024, 045, 066, 075, 090, 170, 802]` _(Ordenado!)_

### Comparativo Direto

| **Característica** | **Counting Sort**                           | **Radix Sort**                                          |
| ------------------ | ------------------------------------------- | ------------------------------------------------------- |
| **Abordagem**      | Contagem direta de frequências              | Ordenação por posições/dígitos                          |
| **Melhor uso**     | Intervalos pequenos ($K \approx n$)         | Números grandes com tamanho de dígitos $d$ fixo/pequeno |
| **Sub-algoritmo**  | Não utiliza                                 | Utiliza um algoritmo estável (geralmente Counting Sort) |
| **Desvantagem**    | Ineficiente para grande variação de valores | Depende do formato/tamanho dos dígitos                  |