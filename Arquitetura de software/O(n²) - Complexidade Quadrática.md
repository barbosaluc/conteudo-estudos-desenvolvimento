#Algoritmos #arquitetura 
A **Complexidade Quadrática $O(n^2)$** representa o pior cenário de performance aceitável no dia a dia do desenvolvimento. Ela indica que o tempo de execução de um algoritmo cresce de forma **proporcional ao quadrado** do tamanho dos dados de entrada ($n$).

Se você dobrar a quantidade de dados, o tempo de execução não dobra, ele quadruplica. Se o volume de dados aumentar 10 vezes, o esforço do sistema aumenta 100 vezes.

## 1. De onde ela vem? (O Loop Aninhado)

O cenário mais clássico de um algoritmo $O(n^2)$ é a presença de **dois laços de repetição (`for`) aninhados**, onde o laço interno roda baseado no tamanho do laço externo.
- Para cada item da lista, o código percorre a lista inteira novamente
```java
for (int i = 0; i < n; i++) { 
	for (int j = 0; j < n; j++) { 
	// Operação básica (ex: comparar se i e j são duplicados) } 
	}
```
**O motivo do colapso:** Se a lista tiver 1.000 itens, o loop de fora roda 1.000 vezes, e o de dentro roda mais 1.000 vezes para cada uma delas. Total: **1.000.000 de operações**.
## 2. O Perigo no Mundo Real: Banco de Dados e APIs

Em ambientes de microsserviços e alta concorrência, o $O(n^2)$ costuma se disfarçar e causar estragos graves:

- **O problema do "N+1 Queries" (ORMs):** Quando seu código faz uma busca para listar 100 pedidos ($O(n)$) e, dentro de um loop, faz uma nova chamada ao banco para buscar os itens de cada um desses pedidos. Você acabou de criar um comportamento quadrático de rede e I/O.
    
- **Nested Loops Joins (SQL):** Se você tentar fazer um `JOIN` entre duas tabelas grandes e nenhuma delas tiver índices nas colunas de ligação, o banco de dados será forçado a comparar cada linha da primeira tabela com todas as linhas da segunda tabela.
    

## 3. Como Corrigir ou Evitar o $O(n^2)$?

A principal estratégia de um arquiteto para eliminar o $O(n^2)$ é o **Trade-off de Espaço por Tempo**, geralmente trocando um dos loops por uma estrutura de dados de busca instantânea $O(1)$.

- **A Solução com Mapas (Hashing):** Em vez de usar um segundo `for` para procurar um item correspondente em outra lista, você joga a segunda lista dentro de um `HashMap`. Depois, você faz apenas um loop simples $O(n)$ e busca as correspondências no mapa em $O(1)$. O algoritmo despenca de $O(n^2)$ para **$O(n)$**.

#flashcards/algoritmos/On²
Como funciona a complexidade quadrática $O(n^2)$ ::Ela indica que o tempo de execução de um algoritmo cresce de forma proporcional ao quadrado do tamanho dos dados de entrada (n).
<!--SR:!2026-07-18,5,230-->
Ou seja, se dobrar a quantidade dos dados de entrada, o tempo de execução quadruplica.
<!--SR:!2026-07-05,3,250-->

