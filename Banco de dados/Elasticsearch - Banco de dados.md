#banco-de-dados/conceitos 
O Elasticsearch é um motor de busca e análise de dados distribuído, de código aberto e baseado na biblioteca ``Apache Lucene`` . Foi projeto especificamente para armazenar, buscar e analisar grandes volumes de dados em tempo real.
Diferente de bancos de dados tradicionais, o forte do Elasticsearch não é gerenciar transações financeiras ACID complexas, mas sim encontrar "agulhas em palheiros" de dados textuais e métricas rapidamente.
#### Principais características:
- <font color="#ff0000"><font color="#ff0000"><font color="#ff0000"></font>Busca Full-text</font></font> : Graças ao [[Índice Investido]], ele consegue realizar buscas textuais avançadas, lidando com erros de digitação, sinônimos, busca por proximidade e relevância (scorring).
- <font color="#ff0000">Orientado a documentos (NoSQL)</font> : Ele armazena os dados no formato ``JSON``. Cada registro é um documento que pode ter uma estrutura flexível.
- <font color="#ff0000">Distribuído e altamente escalável</font> : Pode começar com um único nó e expandir para centenas de servidores (cluster). Ele divide os dados automaticamente em pedaços chamados de shards e os distribui/replica entre as máquinas para garantir alta disponibilidade e performance.
- <font color="#ff0000">Schemaless (ou Schema-flexible):</font> Você pode indexar um documento JSON sem definir previamente as colunas e tipos de dados. O Elasticsearch tenta adivinhar o tipo (Dynamic Mapping), embora em produção o recomendado seja definir explicitamente (Explicit Mapping) para otimizar performance.
- <font color="#ff0000">Restful API</font>: Toda a comunicação com o Elasticsearch (inserção, busca, configuração) é feita através de requisições HTTP utilizando verbos padrão (GET, POST, PUT, DELETE), o que o torna compatível com praticamente qualquer linguagem de programação.
### Analogia de Conceitos (SQL vs. Elasticsearch)

Para quem vem do mundo relacional, entender a nomenclatura do Elasticsearch fica mais fácil com este paralelo:

| Banco Relacional (SQL)    | Elasticsearch            | Descrição                                                  |
| ------------------------- | ------------------------ | ---------------------------------------------------------- |
| Banco de Dados (Database) | Cluster / Index          | O agrupamento lógico dos dados.                            |
| Tabela (Table)            | **Index** (Índice)       | Uma coleção de documentos com características semelhantes. |
| Linha/Registro (Row)      | **Document** (Documento) | A unidade básica de informação, expressa em JSON.          |
| Coluna (Column)           | **Field** (Campo)        | Um atributo do documento (ex: "nome", "data_criacao").     |
### Casos de Uso Comuns

1. **Mecanismo de Busca Interno:** Barra de pesquisa de e-commerces (com autocompletar, filtros por facetas/categorias e ordenação por relevância).
2. **Centralização e Análise de Logs (Observabilidade):** Monitorar a saúde de microsserviços e servidores. Ele lê milhões de linhas de logs, indexa tudo e permite identificar erros em tempo real.
3. **Análise de Métricas e BI:** Dashboards analíticos para monitorar segurança (SIEM), transações de negócios ou comportamento de usuários.
### O Ecossistema: Elastic Stack (ELK)

Raramente o Elasticsearch é usado sozinho. Ele costuma fazer parte do que chamamos de **Elastic Stack** (antigo ELK Stack):

- **E**lasticsearch: O cérebro (armazenamento e busca).
- **L**ogstash / **B**eats: Os coletores. O Beats coleta dados na ponta (métricas, logs) e o Logstash os processa, transforma e envia para o Elasticsearch.
- **K**ibana: A interface visual. Uma ferramenta web para criar gráficos, dashboards e navegar nos dados que estão dentro do Elasticsearch.

#flashcards/banco-de-dados/elasticsearch
O que é e como funciona o Elasticsearch::É um motor de busca e análise de dados distribuídos, projetado para armazenar, buscar e análisar grandes volumes de dados em tempo real. Diferente de banco de dados tradicionais, ele armazena os dados em JSON e é orientado a documentos (NoSQL). Toda a comunicação é feita por requisições HTTP, o que o torna compatível com quase todas as aplicações.
<!--SR:!2026-07-10,3,250-->