#conceitos-de-bd 
Pense no índice remissivo que fica no final de um livro.

Se você quiser encontrar todas as páginas do livro que mencionam "chocolate", você não folheia o livro inteiro página por página (isso seria o `LIKE` ou um _Full Table Scan_). Você vai direto na letra **C** no final do livro, acha a palavra "chocolate" e vê a lista de páginas: _págs. 45, 67, 120_.

O índice invertido faz exatamente isso, mas em vez de páginas, ele mapeia as palavras para os IDs dos documentos (ou IDs das linhas da sua tabela) onde elas aparecem.

#### O passo a passo da Construção 
Imagine que temos três linhas (documentos) guardadas na nossa tabela de produtos do banco de dados:
- **Doc 1:** "Café torrado em grãos"
- **Doc 2:** "Grãos de bico orgânico"
- **Doc 3:** "Café expresso gourmet"

Antes de montar o índice, o motor de busca aplica os filtros de tratamento de texto (tokenização, Stop Words e Stemming). O resultado desse processamento limpo fica assim:

| Documento | Texto Original           | Termos Processados (Tokens)  |
| --------- | ------------------------ | ---------------------------- |
| Doc 1     | "Café torrado em grãos"  | `café`, `torrad`, `grã`      |
| Doc 2     | "Grãos de bico orgânico" | `grã`, `bic`, `orgânic`      |
| Doc 3     | "Café expresso gourmet"  | `café`, `express`, `gourmet` |
(Note que "em" e "de" sumiram porque são stop words, e palavras como "torrado/grãos" foram reduzidas ao radical).
#### A "inversão" do índice
O banco de dados pega essa estrutura e a inverte. Em vez de o documento apontar para as palavras, a palavra passa a apontar para os documentos.

| Termo (Chave) | Lista de Ocorrências (Postings List) |
| ------------- | ------------------------------------ |
| café          | Doc 1, Doc 3                         |
| grã           | Doc 1, Doc 2                         |
| orgânic       | Doc 2                                |
## Como o banco faz a busca instantânea?

Quando um usuário digita na barra de pesquisa: **"café em grãos"**, o motor de busca faz o seguinte:

1. Trata a busca do usuário com o mesmo processo (remove "em", aplica o radical), resultando nos termos: `café` e `grã`.
    
2. Faz um "look-up" (busca direta por chave) no índice invertido:
    
    - Ele olha `café` $\rightarrow$ Retorna Doc 1, Doc 3
    - Ele olha `grã` $\rightarrow$ Retorna Doc 1, Doc 2

3. Se a busca for do tipo `AND` (contendo os dois termos), o banco faz uma operação matemática de **interseção** entre as duas listas de IDs:
    
    - `[1, 3]` $\cap$ `[1, 2]` = **`[1]`**
        
O banco de dados sabe instantaneamente que **apenas o Doc 1** possui as duas palavras, sem precisar ler nenhuma linha de texto das tabelas. Ele buscou direto em estruturas de memória otimizadas (geralmente em  [[Árvores de decisão (B-Trees e Índices)]] ou estruturas de dados baseadas em FST).

É por isso que, não importa se você tem 100 ou 100 milhões de documentos, o tempo para encontrar o termo no índice invertido é praticamente o mesmo (complexidade próxima de [[O(1) - Complexidade Constante]] ou [[O(log n) - Complexidade Logarítmica]]).

#flashcards/banco-de-dados/índice-invertido
O que é um índice invertido?:: Estrutura que permite mapear palavras ou termos aproximados, facilitando a busca.
<!--SR:!2026-07-04,3,250-->
