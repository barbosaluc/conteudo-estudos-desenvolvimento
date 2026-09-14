#arquitetura-de-software/algoritmo-ordenacao/heap-sort
O **Heap Sort** é um algoritmo de ordenação baseado em uma estrutura de dados chamada **Heap** (ou árvore heap). Ele é eficiente, realiza a ordenação **em memória (in-place)** e possui complexidade [[O(n log n) - Complexidade Quasilinear]] no pior caso.
Antes de entender o algoritmo, é importante compreender o que é um Heap.
#### O que é um Heap?

Um **Heap** é uma árvore binária completa que obedece uma propriedade específica.

Existem dois tipos:
- **Max Heap:** o pai é sempre maior ou igual aos filhos.
- **Min Heap:** o pai é sempre menor ou igual aos filhos.
Como o Heap Sort normalmente ordena em ordem crescente, ele utiliza um **Max Heap**.
Exemplo:
```
          90
        /    \
      70      60
     /  \    /  \
   40   50 20   10
   
   Observe que todos os pais são maiores que seus filhos
```
--------------------------------------------------------------------------
### Como um Heap é armazenado?
Não é necessário criar uma árvare.
O Heap é armazenado em um vetor.
```
Índice:   0   1   2   3   4   5   6

Vetor:   [90,70,60,40,50,20,10]
```
As relações são calculadas pelos índices:
```
Pai(i)      = (i - 1) / 2

Filho Esq   = 2*i + 1

Filho Dir   = 2*i + 2
```
Exemplo : 
```
Índice 1 = 70

Filho esquerdo:
2*1+1 = 3 → 40

Filho direito:
2*1+2 = 4 → 50
```
---
### Ideia do Heap Sort
O algoritmo funciona em duas fases:
#### 1. Construir um Max Heap
```
Imagine o vetor:
[4, 10, 3, 5, 1]
Ele ainda não é um heap, precisamos reorganizá-lo.
Depois da construção:
        10
      /    \
     5      3
    / \
   4   1
No vetor:
[10,5,3,4,1]
Agora o maior elemento está na raiz.
```
#### 2. Ordenação
Agora repetimos:
1. Troca a raiz pelo último elemento.
2. O maior elemento fica na posição correta.
3. Diminui o Heap.
4. Reorganiza o Heap.
```
passo 1
Heap:
[10,5,3,4,1]
troca
10 ↔ 1
resultado:
[1,5,3,4,10]
O 10 já está ordenado.
```
Reorganiza
```
      1
    /   \
   5     3
  /
 4
```
Como 5 é maior :
```
      5
    /   \
   1     3
  /
 4
```
Agora compara 1 com 5 :
```
      5
    /   \
   4     3
  /
 1
```
vetor :
```
[5,4,3,1,10]
```
Próxima troca:
troca :
```
5 ↔ 1
[1,4,3,5,10]
```
reorganiza :
```
      4
    /   \
   1     3
Como 3 é menor que 4 :
[4,1,3,5,10]
```
Continua e depois das próximas trocas :
```
[3,1,4,5,10]

↓

[1,3,4,5,10]
```
---
### A função mais importante : Heapify
Ela garante que um nó satisfaça a propriedade do Heap.
```
Heapify(vetor, tamanho, i)

maior = i

esquerda = 2*i + 1
direita  = 2*i + 2

se esquerda existe e vetor[esquerda] > vetor[maior]
    maior = esquerda

se direita existe e vetor[direita] > vetor[maior]
    maior = direita

se maior != i

    troca(vetor[i], vetor[maior])

    Heapify(vetor, tamanho, maior)
```
A chamada recursiva é necessária porque, após uma troca, a subárvore abaixo também pode deixar de obedecer à propriedade do heap.
### Complexidade
|Caso|Complexidade|
|---|---|
|Melhor|**O(n log n)**|
|Médio|**O(n log n)**|
|Pior|**O(n log n)**|
|Memória extra|**O(1)** (versão iterativa/in-place)|

---
#### Vantagens
- Excelente desempenho garantido: **O(n log n)**.
- Ordena no próprio vetor (in-place).
- Não depende da distribuição dos dados.
- Não sofre degradação para **O(n²)**.
#### Desvantagens
- Não é **estável** (elementos iguais podem mudar de ordem).
- Na prática, costuma ser mais lento que o [[Quick Sort]] devido ao maior número de acessos não sequenciais à memória.
- É mais complexo de implementar do que algoritmos simples como [[Insertion Sort]] ou Selection Sort. 
---
#flashcards/algoritmos-de-ordenação/heap-sort 
Como funciona o algoritmo de ordenação?::É baseado em uma estrutura de dados chamada Heap (ou Árvore Heap), em todos os casos possui complexidade quasilinear O(n log n). Ná prática é mais lento que o <font color="#de7802">Quick Sort</font>.
<!--SR:!2026-08-03,3,250-->