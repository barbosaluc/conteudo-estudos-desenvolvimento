#### <font color="#e36c09">Encapsulamento</font> - Proteção dos dados através de <font color="#e36c09">getters/setters</font>.
Consiste em agrupar dados (variáveis de instância) e os métodos que operam sobre esses dados dentro de uma única unidade, a classe. Permitindo controlar o acesso direto aos atributos de um objeto, promovendo a ocultação de informação.
#### <font color="#e36c09">Herança</font> - Reutilização de código via ``Extends``.
A herança em Java é um mecanismo que permite que uma classe (chamada de classe filha ou subclasse) herde atributos e métodos de outra classe (chamada de classe mãe ou superclasse).

#### <font color="#e36c09">Polimorfismo</font> - Capacidade de Objetos se comportarem em diferentes formas.
Ele permite que objetos de classes diferentes respondam ao mesmo método de maneiras distintas. Isso é alcançado através de herança e interfaces, possibilitando que uma única chamada de método execute comportamentos diferentes dependendo do tipo de objeto em tempo de execução.
Principais formas de polimorfismo em Java:
- **<font color="#ff0000">Polimorfismo de Sobrecarga</font> (Overloading):** Ocorre quando você tem múltiplos métodos com o mesmo nome na mesma classe, mas com parâmetros diferentes. O compilador decide qual método chamar com base nos argumentos fornecidos.
- **<font color="#ff0000">Polimorfismo de Sobrescrita</font> (Overriding):** Acontece quando uma subclasse fornece uma implementação específica para um método que já está definido em sua superclasse. A JVM (Java Virtual Machine) determina qual método executar em tempo de execução com base no tipo real do objeto.