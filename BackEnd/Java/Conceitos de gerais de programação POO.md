#### <font color="#e36c09">Encapsulamento</font> - Proteção dos dados através de <font color="#e36c09">getters/setters</font>.
Consiste em agrupar dados (variáveis de instância) e os métodos que operam sobre esses dados dentro de uma única unidade, a classe. Permitindo controlar o acesso direto aos atributos de um objeto, promovendo a ocultação de informação.
#### <font color="#e36c09">Herança</font> - Reutilização de código via ``Extends``.
A herança em Java é um mecanismo que permite que uma classe (chamada de classe filha ou subclasse) herde atributos e métodos de outra classe (chamada de classe mãe ou superclasse).

#### <font color="#e36c09">Polimorfismo</font> - Capacidade de Objetos se comportarem em diferentes formas.
Ele permite que objetos de classes diferentes respondam ao mesmo método de maneiras distintas. Isso é alcançado através de herança e interfaces, possibilitando que uma única chamada de método execute comportamentos diferentes dependendo do tipo de objeto em tempo de execução.
Principais formas de polimorfismo em Java:
- **<font color="#ff0000">Polimorfismo de Sobrecarga</font> (Overloading):** Ocorre quando você tem múltiplos métodos com o mesmo nome na mesma classe, mas com parâmetros diferentes. O compilador decide qual método chamar com base nos argumentos fornecidos.
- **<font color="#ff0000">Polimorfismo de Sobrescrita</font> (Overriding):** Acontece quando uma subclasse fornece uma implementação específica para um método que já está definido em sua superclasse. A JVM (Java Virtual Machine) determina qual método executar em tempo de execução com base no tipo real do objeto.
#### <font color="#e36c09">Abstração</font>
Abstrair é esconder os detalhes complexos de como algo funciona e mostrar apenas o que é essencial para quem vai usar.
##### Como funciona no Java?
Alcançamos a abstração de duas formas: por classes abstratas ou por interfaces:
1. Classes abstratas
   É uma classe que serve como base, mas que não pode ser instanciada (não pode ``New`` nela). Ela pode conter métodos comuns e métodos abstratos (que são apenas assinaturas, sem código).
2. Interfaces
   É um contrato ainda mais puro. Ela define o que uma classe deve fazer, mas deixa totalmente a cargo da classe decidir como fazer.

#### <font color="#e36c09">Sobrecarga</font> (Overloading)
Polimorfismo de Sobrecarga (Overloading) : Ocorre quando tem múltiplos métodos com o mesmo nome na mesma classe, mas com parâmetros diferentes. O compilador decide qual método chamar com base nos argumentos fornecidos.
#### <font color="#e36c09">Sobrescrita</font> (Overriding)
Polimorfismo de sobrescrita (Overriding) :  Acontece quando uma subclasse fornece uma implementação específica para um método que já está definido em sua superclasse. A [[1.1 JVM (Java virtual Machine)]] determina qual método executar em tempo de execução com base no tipo real do objeto.
#### <font color="#e36c09">Interfaces</font>
Ela define um conjunto de métodos que uma classe deve implementar, mas não fornece nenhuma implementação. Interfaces são compostas exclusivamente por:

- **Métodos abstratos:** Todos os métodos em uma interface são públicos e abstratos por padrão (embora em versões mais recentes do Java, elas possam conter métodos com implementação padrão).
- **Constantes:** Variáveis de instância que são públicas, estáticas e finais por padrão.
#### <font color="#e36c09">Classes abstratas</font>
Uma classe abstrata em Java é um modelo incompleto que serve como base para outras classes. Ela pode conter métodos abstratos (sem implementação) e métodos concretos (com implementação). Classes abstratas não podem ser instanciadas diretamente; elas devem ser estendidas por uma classe concreta, que então fornecerá a implementação para todos os seus métodos abstratos.