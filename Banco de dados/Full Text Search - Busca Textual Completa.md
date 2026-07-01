#banco-de-dados #conceitos-de-bd
É um técnica avança para buscar palavras ou termos dentro de grandes volumes de texto de forma extremamente rápida e inteligente.
Se você tentar buscar um texto usando um operador tradicional como o `LIKE '%termo%'` do SQL, o banco de dados precisará varrer a tabela linha por linha (um _Full Table Scan_). Para tabelas com milhares ou milhões de registros, isso destrói a performance. O FTS resolve esse e vários outros problemas.
#### Como o FTS funciona por baixo dos panos?
O segredo da velocidade do FTS é que ele não busca o texto diretamente na tabela no momento da query. Em vez disso, ele passa o texto por um processo de preparação e cria uma estrutura chamada [[Índice Investido]].
#### O processo de indexação:

1. **Tokenização:** O banco de dados quebra as frases em palavras individuais (tokens).
2. **Normalização (Lowercasing):** Transforma tudo em minúsculas para que "Banco", "banco" e "BANCO" sejam indexados da mesma forma.
3. **Remoção de Stop Words:** Palavras muito comuns que não trazem contexto (como "o", "a", "de", "com", "em") são descartadas para economizar espaço.
4. **Stemming (Radicalização):** Reduz as palavras ao seu radical. Por exemplo, "correndo", "correu" e "corrida" viram apenas "corr". Assim, se você buscar por "correr", encontrará registros que contêm "correndo".
#### As grandes vantagens sobre o ``like``
Além da velocidade absurda em textos longos, o FTS traz recursos de busca que o SQL comum não consegue entregar nativamente:
- **Pesquisa por Relevância (Scoring):** O FTS não retorna apenas "sim" ou "não". Ele calcula um score (pontuação) para cada resultado baseado em fatores como a frequência da palavra no documento versus a frequência no resto do banco (algoritmos como TF-IDF ou BM25). Os resultados mais relevantes aparecem primeiro.
- **Busca Difusa (Fuzzy Match):** Consegue encontrar correspondências mesmo se houver pequenos erros de digitação (ex: buscar "bano" e encontrar "banco").
- **Operadores Booleanos Avançados:** Permite buscas complexas como: `"banco" AND "dados" NOT "financeiro"`.
- **Busca por Proximidade:** Permite buscar por palavras que estejam próximas uma da outra (ex: "banco" a no máximo 3 palavras de distância de "postgres").
### Onde ele é implementado
1. <font color="#e36c09">Bancos de Dados Relacionais (SGBDs)</font>
	Bancos como **PostgreSQL** (usando `tsvector` e `tsquery`), **MySQL** (índices `FULLTEXT`) e **SQL Server** possuem motores de FTS embutidos.
		 <font color="#ff0000">Vantagem</font>: Centralização. Você não precisa de outra ferramenta na sua infraestrutura e mantém a consistência ACID dos dados imediatamente.
	     <font color="#ff0000">Desvantagem</font>: Consome muita CPU e memória do banco principal durante grandes volumes de escrita e indexação.
    
 2. <font color="#e36c09">Motores de Busca Dedicados (NoSQL)</font>
	Ferramentas como **Elasticsearch**, **OpenSearch** e **Meilisearch** são construídas especificamente para isso.
		<font color="#ff0000">Vantagem</font>: Altíssima escalabilidade, ferramentas de análise de texto absurdamente customizáveis, sugestões de digitação (auto-complete) ultra-rápidas e alívio de carga do seu banco de dados principal.
	    <font color="#ff0000">Desvantagem</font>:  Adiciona complexidade à arquitetura, pois você precisa sincronizar os dados do seu banco relacional com o motor de busca (geralmente usando padrões como o Pattern CQRS ou ferramentas de CDC como o Debezium).