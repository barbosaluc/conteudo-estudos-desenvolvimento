**CDC** significa **Change Data Capture** (Captura de Mudanças de Dados). É um padrão de design de software e um conjunto de tecnologias utilizado para **identificar e capturar inserções, atualizações e exclusões** (INSERTs, UPDATEs e DELETEs) feitas em um banco de dados, notificando outros sistemas sobre essas alterações em tempo real.

Em vez de forçar os outros sistemas a ficarem perguntando ao banco de dados se há algo novo (o que gera lentidão), o CDC transforma o banco em uma fonte de eventos: **aconteceu uma mudança, ela é disparada imediatamente para quem precisa saber.**

### Por que o CDC é necessário? (O Problema do _Polling_)

Antes do CDC, se você precisasse sincronizar o seu banco de dados principal (onde acontecem as vendas) com um motor de busca como o [[Elasticsearch - Banco de dados]] ou um Data Warehouse, a abordagem comum era o _polling_: rodar uma query de tempos em tempos procurando registros com uma coluna `ultima_atualizacao > X`.

Essa abordagem antiga tem problemas graves:

1. <font color="#ff0000">Gera sobrecarga:</font> Fazer queries pesadas no banco de produção a cada poucos segundos consome muita CPU.
2. <font color="#ff0000">Não é tempo real: </font>Se o script roda a cada 10 minutos, seus dados ficam 10 minutos atrasados.
3. <font color="#ff0000">Não detecta deleções:</font>Se um registro for deletado fisicamente (`DELETE`), a query de busca nunca vai encontrá-lo para saber que ele sumiu.

#### Como o CDC funciona na prática?

A forma mais eficiente e moderna de implementar CDC é a baseada em **Logs (Log-based CDC)**.

Todo banco de dados (PostgreSQL, MySQL, Oracle, SQL Server) possui um log de transações interno (chamado de [[Wal - Write-Ahead Logging]] ou _Binary Log_). Esse log registra absolutamente tudo o que acontece no banco antes mesmo de gravar no disco, para garantir a segurança dos dados.

#### Exemplo de um evento de CDC
```JSON
{
  "operacao": "UPDATE",
  "tabela": "clientes",
  "antes": { "id": 42, "nome": "João", "cidade": "São Paulo" },
  "depois": { "id": 42, "nome": "João", "cidade": "Rio de Janeiro" },
  "timestamp": 1774315200000
}
```
### Ferramentas Populares de CDC

- **<font color="#ff0000">Debezium</font>:** É a ferramenta open-source de CDC mais famosa do mercado. Ela roda integrada ao **Apache Kafka** (via Kafka Connect) e possui conectores nativos para extrair dados do PostgreSQL, MySQL, SQL Server, Oracle, etc.
- **<font color="#ff0000">AWS Database Migration Service (DMS):</font>** Serviço gerenciado da Amazon para mover dados continuamente.
- <font color="#ff0000">GoldenGate:</font> Ferramenta corporativa e de alto custo da Oracle.
### Casos de Uso Comuns

- <font color="#ff0000">Atualização de Índices de Busca:</font> Sincronizar o seu banco relacional de produção com o **Elasticsearch** em tempo real.
- <font color="#ff0000">Invalidação de Cache:</font> Sempre que um dado mudar no banco, o CDC avisa a aplicação para limpar ou atualizar aquela chave no Redis.
- <font color="#ff0000">Alimentação de Data Lakes/Data Warehouses: </font>Mover dados de transações de produção para ambientes analíticos (como BigQuery, Snowflake) sem impactar a performance do banco principal.
- <font color="#ff0000">Arquitetura de Microsserviços:</font> Propagar eventos entre microsserviços diferentes para manter a consistência eventual do sistema.

#flashcards/banco-de-dados/CDC
O que é o CDC:: CDC - Change Data Capture (Captura de Mudanças de Dados) utilizado para identifica Inserts, updates e Deletes, e notificar outros sistemas sobre essas alterações em tempo real. A melhor forma de implementar é fazer a leitura dos <font color="#de7802">logs internos dos bancos de dados</font> que registram tudo, antes mesmo de gravar os dados no disco. Todos os bancos de dados possuem esse log.
<!--SR:!2026-07-21,1,210-->