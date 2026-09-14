#arquitetura-de-software #design-patterns 
É um padrão de projeto comportamental cujo objetivo é definir uma família de algoritmos, colocar cada um deles em uma classe separada e tornar seus objetos [^1]intercambiáveis. 
#### 1. O Problema
O padrão aborda cenários em que uma classe precisa executar uma tarefa específica de várias maneiras diferentes.
Um exemplo típico é uma aplicação de navegação que inicialmente calcula apenas rotas de carro. Conforme o sistema evolui, surgem necessidades de calcular rotas a pé, de transporte público e de bicicleta. Se todos esses algoritmos forem mantidos dentro da mesma classe principal, ela se torna gigantesca, difícil de manter e vulnerável a bugs - já que qualquer alteração em um algoritmo pode afetar o restante do código ou gerar conflitos de desenvolvimento.

--------
#### 2. A Solução
O <font color="#de7802">Strategy</font> sugere extrair os diferentes algoritmos da classe principal e isolá-los em classes próprias, chamadas estratégias.
A classe original (chamada <font color="#de7802">contexto</font>) deixa de executar o algoritmo por conta própria e passa a armazenar uma referência para uma das estratégias, delegando o trabalho a ela. O cliente do contexto fica responsável por selecionar e atribuir a estratégia adequada para a situação.

---
#### 3. Estrutura dos Componentes
- Contexto (<font color="#de7802">Context</font>) : Mantém uma referência para um objeto de estratégia e comunica-se com ele exclusivamente por meio da interface de estratégia.
- Interface Estratégia (<font color="#de7802">Strategy</font>) : Interface comum a todas as variações do algoritmo, declarando o método que o contexto utiliza para executá-lo.
- Estratégias Concretas (Concrete <font color="#de7802">Strategies</font>) : Classes que implementam os diferentes algoritmos seguindo a interface comum.
- Cliente (<font color="#de7802">Client</font>) : Instancia a estratégia concreta desejada e a passa para o contexto, podendo trocar a estratégia ativa em tempo de execução via *setter*.

---
#### 4. Analogia ao Mundo Real
Imagine que você precisa ir ao aeroporto. Você pode escolher ir de ônibus, táxi ou bicicleta. Cada meio de transporte representa uma estratégia diferente para alcançar o mesmo objetivo, selecionada por você (o cliente) com base no seu orçamento ou no tempo disponível.

---
#### 5. Prós e Contras
##### Prós :
- <font color="#de7802">Troca em tempo de execução</font> : Permite alterar o algoritmo utilizado por um objeto dinamicamente durante a execução.
- <font color="#de7802">Princípio Aberto/Fechado (SOLID)</font> : Permiti introduzir novas estratégias no programa sem precisar alterar o código do contexto.
- <font color="#de7802">Isolamento de código</font> : Separa os detalhes de implementação de um algoritmo do código de negócio que o utiliza.
- <font color="#de7802">Substitui a herança pela composição </font>: Reduz o acoplamento ao delegar comportamentos a objetos auxiliares em vez de estender classes.
##### Contras :
- <font color="#de7802">Complexidade desnecessária</font> : Se o programa possui poucas variações de algoritmo e elas raramente mudam, criar novas classes e interfaces pode complicar o código sem necessidade.
- <font color="#de7802">Conhecimento pelo cliente</font> : O cliente precisa compreender as diferenças entre as estratégias para conseguir selecionar a mais adequada.

[^1]: Significa que você pode trocar um objeto por outro sem precisar alterar o código da classe que o utiliza.
