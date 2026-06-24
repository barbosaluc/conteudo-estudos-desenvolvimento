A **Complexidade Linear O(n)** representa o cenário onde o tempo de execução (ou o espaço em memória) de um algoritmo cresce na **mesma proporção** em que o volume de dados de entrada (n) aumenta.

Se você dobrar a quantidade de dados, o algoritmo levará o dobro do tempo para rodar.

#### 1. Exemplos Práticos no Código

### O loop `for` simples

O exemplo clássico é percorrer uma lista do início ao fim usando um laço de repetição.
-  Para encontrar o item ou somar os valores, o código precisa olhar cada posição uma vez. 
```java
for (int i = 0; i < pedidos.size(); i++) { 
processar(pedidos.get(i)); 
}
```
#### Busca em uma lista não ordenada (Scan)

Se você precisa encontrar um pedido específico em um Array comum (desordenado), no pior cenário (se o item for o último ou não existir), você terá que olhar todas as n posições.

#### Operações com `Java Streams` / `JavaScript Arrays`

Métodos como `.map()`, `.filter()`, `.forEach()` ou `.anyMatch()` aplicados sobre coleções tradicionais operam internamente em O(n), pois precisam avaliar os elementos um a um.

#### 2. O O(n) no Mundo dos Bancos de Dados

Quando você faz uma consulta `SQL`e o banco de dados não encontra nenhum índice para te ajudar, ele recorre ao **Full Table Scan** (Varredura Completa da Tabela).

- **O que ele faz:** Ele lê a tabela inteira, linha por linha, do início ao fim, para achar o que você pediu.
- **O Perigo:** Se a sua tabela tem 1.000 linhas, é instantâneo. Se o seu `Order-service` crescer e a tabela passar a ter 50 milhões de registros, o banco fará 50 milhões de leituras físicas de disco (I/O). A query vai travar a aplicação.

#### 3. O Impacto na Arquitetura

O O(n) é considerado um comportamento **saudável e aceitável** para a grande maioria das regras de negócio da sua aplicação (processar os itens de um único carrinho de compras, validar um formulário no Angular, etc.), desde que o valor de n seja controlado e pequeno.

O perigo real acontece quando você coloca uma operação O(n), dentro de outra operação O(n). Isso gera o temido O(n²) (Quadrático), que destrói a performance do sistema.