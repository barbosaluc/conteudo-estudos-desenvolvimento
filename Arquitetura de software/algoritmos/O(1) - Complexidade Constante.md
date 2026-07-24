É o nível máximo de eficiência que um algoritmo pode alcançar. Ela representa o cenário onde o tempo necessário para executar uma tarefa é independente do tamanho da entrada de dados. Não importa se você tem 10 itens ou 10 bilhões de itens, o número de operações que o computador realiza será o mesmo.
#### 1. Conceito

Dizer que um algoritmo é O(1) não significa que leva exatamente 1 milisegundo ou 1 segundo. Significa que, não importa se você tem **10 itens** ou **10 bilhões** de itens, o número de operações que o computador realiza é o mesmo.

#### 2. Porque é o favorito da Arquitetura?

Quando desejamos sistemas de alta escala, o objetivo é aproximar as operações crítcas do O(1) por três motivos:

1. **Previbilidade**: Você sabe exatamente quanto recurso de CPU será gasto, facilitando o cálculo de custos de infraestrutura.
2. **Escalabilidade Infinita**: O sistema não degrada conforme o banco de dados cresce.
3. **Latência Baixa**: Essencial para experiências de usuário em tempo real.

#### 3. Aplicaçao no contexto (Banco de Dados)

Quando faz a consulta `SELECT * FROM tabelas WHERE id = 123` em uma coluna com Índice único `(Primary Key)`, o banco utiliza estruturas de dados que permite localizar o registro de forma quase constante (ou logarítmica muito baixa). Sem o índice, o banco teria que fazer um `Full Table Scan`, que é O(n).
O problema de aplicar índices em excesso:
[[Over-indexing]]