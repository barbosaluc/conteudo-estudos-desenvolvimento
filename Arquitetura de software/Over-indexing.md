Aplicar índices em excesso em uma tabela cria um fenômeno conhecido como **_Over Indexing_, podendo degradar severamente o sistema.**

#### 1. Degradação da Escrita (`INSERT`, `UPDATE` e `DELETE`)

Cada vez que você insere ou altera um registro, o banco de dados não atualiza apenas a tabela principal, ele precisa **atualizar cada um dos índices existentes.**

- Problema: Uma única inserção pode se transformar em 10 operações de escrita se você tiver 9 índices.
- Consequência: Transações ficam lentas, aumentando o tempo de resposta e podendo causar _**timeouts**_ em sistemas de alta concorrência.

#### 2. Consumo excessivo de armazenamento e memória

Índices são estruturas de dados físicas armazenadas no disco.

- Disco: Em tabelas com milhões de registros, os índices podem acabar ocupando **mais espaço que os próprios dados.**
- Memória (Buffer Pool): Para serem rápidos os bancos tentam manter os índices na memória _**RAM.**_ Índices demais expulsam os dados úteis da _**RAM**_, forçando o banco a ler do disco constantemente, o que mata a performance global.

#### 3. O dilema do otimizador de consultas

O banco possui um “Otimizador” que decide qual índice usar para cada query.

- O perigo: Quando há muitos índices parecidos e redundantes, o _**otimizador**_ pode gastar muito tempo apenas planejando a execução (query planning), ou pior, escolher um índice [^1]subótimo, resultando em um consulta mais lenta.
#### 4. Fragmentação de Dados

Muitos índices em colunas que sofrem updates frequentes causam [^2]fragmentação física. Isso exige manutenção constante (como o `REBUILD` de índices no SQL Server ou Oracle) para evitar que o banco fique "inchado" e lento com o passar do tempo.

[^1]: Refere-se a uma solução ou caminho que não é a melhor opção disponível, embora seja funcional.

[^2]: Ocorre quando os dados em discos não estão organizados de forma contínua e eficiente.
