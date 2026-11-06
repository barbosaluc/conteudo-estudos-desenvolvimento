#arquitetura-de-software #design-patterns #builder
O Builder (construtor) é um padrão de projeto criacional que permite construir objetos complexos passo a passo. A principal ideia é <font color="#de7802">permitir a produção de diferentes tipos e representações de um objeto utilizando o mesmo código de construção.</font>

### 1. O problema
Construir um objeto complexo frequentemente exige a inicialização trabalhosa de diversos campos e objetos agrupados. Esse processo costuma resultar em duas abordagens problemáticas:
- <font color="#de7802">Subclasses em excessos</font> : Criar subclasses para cada combinação possível de características de um objeto gera uma hierarquia gigante e difícil de manter.
- <font color="#de7802">Construtores gigantes</font> : Definir um construtor com dezenas de parâmetros opcionais obriga chamadas feias e confusas, onde a maioria dos parâmetros acaba recebendo valores nulos ou vazios na maior parte das vezes.
Em vez de fornecer todas as informações de uma vez em um construtor com muitos parâmetros, você configura as partes necessárias e, ao terminar, solicita a criação do objeto.
### 2. A solução
O padrão sugeri extrair o código de construção para fora da classe do objeto movendo-o para objetos separados chamados builders.
<font color="#de7802">O builder oferece um forma de construir objetos complexos passo a passo, evitando construtores com muitos parâmetros.</font>
Ele permite configurar apenas os atributos necessários, definir valores padrão e validar os dados antes de criar o objeto final. Isso torna a criação mais flexível, legível e menos suspeita a erros.
### 3. Principais Componentes
- <font color="#de7802">Interface Builder</font> : Declara as etapas de construção comuns a todas as variações de builders.
- <font color="#de7802">Builders Concretos</font> : Implementam as etapas especificadas na interface e montam o produto. Como builders diferentes podem produzir objetos que não compartilham uma interface comum (ex: um carro e o seu manual de instruções), o produto final é recuperado diretamente do builder concreto que o construiu.
- <font color="#de7802">Produtos</font> : Os objetos complexos resultantes do processo.
- <font color="#de7802">Diretor (opcional)</font> : Define a sequência exata em que as etapas de construção devem ser executas para e reutilizar configurações específicas do produto, escondendo os detalhes da montagem em relação ao cliente. 
- <font color="#de7802">Cliente</font> : Associa um objeto builder a um diretor e obtém o resultado final construído.

### 4. Prós e contras
Prós:
- <font color="#de7802">Construção flexível e passo a passo</font> : Permite construir objetos em etapas, podendo adiar passos ou executá-los de forma recursiva.
- <font color="#de7802">Reutilização</font> <font color="#de7802">de código</font> : Utiliza o mesmo processo de construção da lógica de negócio do produto.
- <font color="#de7802">Princípio de responsabilidade única</font> : Isola o código complexo de construção da lógica de negócio do produto.
Contra:
- <font color="#de7802">Aumento de complexidade</font> : Exige a criação de várias classes e interfaces novas (builders concretos, diretor , interfaces), o que pode complicar o código base do projeto.
