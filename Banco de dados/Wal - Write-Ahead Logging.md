#banco-de-dados/conceitos 
Ou Registro de Log Prévio é uma técnica fundamental para garantir a segurança, integridade e durabilidade dos dados em um sistema de banco de dados.
Em termos simples, a regra de ouro do WAL é: **Nenhuma modificação nos dados pode ser gravada de fato nos arquivos do banco antes que o log correspondente a essa mudança tenha sido salvo no disco.**
##### O Problema que o WAL Resolve: A Falha de Energia
Imagine que você está atualizando o saldo bancário de um cliente. Modificar o arquivo principal onde o banco guarda a tabela de contas é uma operação lenta e custosa, porque os dados ficam espalhados pelo disco em estruturas complexas (como árvores B+).

Se o computador **perder a energia exatamente no meio dessa gravação**, o arquivo da tabela ficará corrompido: metade dos dados novos foi escrita e a outra metade não. O banco de dados se torna inutilizável.
##### Como o WAL Funciona?
Para evitar essa lentidão e o risco de corrupção, o banco de dados divide o trabalho em duas etapas, usando o WAL:

```
[Aplicação faz UPDATE]
         │
         ▼
 1. Escreve a mudança no WAL (Log em Disco) ➔ Escrita sequencial (Ultra Rápida)
         │
         ▼
 2. Modifica o dado na Memória RAM (Buffer Pool)
         │
         ▼
[O Banco diz à Aplicação: "Sucesso!"]
         │
         ▼
 3. (Em segundo plano) Transfere o dado da RAM para a Tabela Real no Disco (Checkpointer)
```
1.  <font color="#ff0000">Escrita Sequencial no Log (WAL)</font>: Quando uma alteração é feita (`INSERT`, `UPDATE`, `DELETE`), o banco escreve uma descrição simples dessa mudança no arquivo de WAL (ex: _"A conta 123 mudou de saldo X para Y"_). Escrever no WAL é **extremamente rápido** porque o log é um arquivo do tipo _append-only_ (os dados são apenas anexados no final do arquivo, de forma sequencial, sem precisar caçar posições no disco).
2. <font color="#ff0000">Modificação na Memória (RAM):</font> Assim que o WAL é gravado e salvo com segurança no disco, o banco atualiza o dado na sua memória RAM (o dado na RAM fica marcado como "sujo"). **Nesse momento, a transação é considerada confirmada (Committed)** e o banco avisa à aplicação que deu certo.
3. <font color="#ff0000">Gravação Assíncrona</font> (Checkpoint):** Em segundo plano e sem pressa, um processo do banco (chamado _Checkpointer_) pega os dados alterados que estavam na RAM e os grava definitivamente nos arquivos reais das tabelas no disco.
### Benefícios do WAL

- **Performance Absurda de Escrita:** O banco não precisa esperar uma escrita lenta no disco rígido espalhado para responder ao usuário; ele só escreve sequencialmente no log e responde imediatamente.
- **Garantia ACID (Durabilidade):** O "D" do ACID é garantido pelo WAL. Uma vez que o `COMMIT` retorna, o dado está salvo, não importa se o hardware falhar um milissegundo depois.
- **Base para Outras Tecnologias:** Como vimos antes, o [[CDC - Change Data Capture]] e a replicação de banco de dados para servidores escravos (Read Replicas) funcionam justamente lendo e transmitindo os arquivos de WAL para outros lugares.