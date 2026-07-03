#conceitos-java
#### Condificionais - if, else if, else, switch
Em Java, as estruturas condicionais permitem que você controle o fluxo de execução do seu programa com base em certas condições. Elas te ajudam a tomar decisões.
``if``
A instrução `if` executa um bloco de código se uma condição especificada for verdadeira.
```java
if (condição) { // código a ser executado se a condição for verdadeira }
```
``else``
A instrução else é usada em conjunto com if. Se a condição do if for falsa, o bloco de código dentro do else será executado.
```java
if (condição) { 
	// código se a condição for verdadeira 
} else { 
	// código se a condição for falsa 
}
```
Você também pode encadear múltiplos if e else if para verificar várias condições em sequência.
``switch``
A instrução switch permite selecionar um entre muitos blocos de código para executar. Ela é útil quando você tem uma variável que pode ter vários valores possíveis.
```java
switch (expressão) 
	{ case valor1: 
	// código se a expressão for igual a valor1 
	break; 
	// importante para sair do switch 
	case valor2: 
	// código se a expressão for igual a valor2 
	break; 
default: 
	// código se nenhum dos casos anteriores for correspondente 
}
```
o break é crucial para evitar que a execução caia para o próximo case. O default é opcional e é executado se nenhum dos outros case corresponder ao valor da expressão. 
#### Laços de repetição
Os laços de repetição (ou loops) são estruturas fundamentais em programação que permitem executar um bloco de código múltiplas vezes. Em Java, temos quatro tipos principais: `for`, `while`,`do-while` e `for-each`.

O laço `for` é ideal quando você sabe de antemão quantas vezes um bloco de código precisa ser executado. Ele possui três partes principais em sua declaração: inicialização, condição de continuação e atualização.
```java
for (inicialização; condição; atualização) {
    // Código a ser repetido
}
```
- **Inicialização:** Executada uma vez no início do loop.
- **Condição:** Verificada antes de cada iteração. Se for `true`, o loop continua; se for `false`, o loop termina.
- **Atualização:** Executada após cada iteração.
``while``
O laço `while` é usado quando a quantidade de iterações não é conhecida previamente, mas depende de uma condição. O bloco de código é executado enquanto a condição for verdadeira.
```java
while (condição) {
    // Código a ser repetido
}
```
A condição é verificada _antes_ de cada iteração. Se a condição for falsa logo de início, o bloco de código dentro do `while` nunca será executado.
``do-while``
Semelhante ao `while`, o `do-while` também executa um bloco de código enquanto uma condição for verdadeira. A principal diferença é que o `do-while` garante que o bloco de código será executado _pelo menos uma vez_, pois a condição é verificada _após_ a execução do bloco.
```java
do {
    // Código a ser repetido
} while (condição);
```
``for-each (Enhanced for loop)``
O laço `for-each` (ou "laço for aprimorado") é uma forma simplificada de iterar sobre elementos de arrays ou coleções (como `ArrayLists`). Ele elimina a necessidade de índices e contadores, tornando o código mais legível.
```java
for (TipoElemento elemento : colecaoOuArray) {
    // Código a ser repetido para cada elemento
}
```
Este laço é muito útil para percorrer todos os itens de uma estrutura de dados sem se preocupar com os detalhes de acesso por índice.
#### break / continue
O controle de execução em laços (loops) permite que você **gerencie o fluxo do programa dentro de blocos de código repetitivos**. As principais ferramentas para isso são:
- **`break`**: Interrompe imediatamente a execução do laço, transferindo o controle para a instrução seguinte ao laço.
-  **`continue`**: Pula a iteração atual do laço e continua com a próxima iteração.
#### try / catch / finally – Tratamento de exceções.
O tratamento de exceções é fundamental para lidar com erros que podem ocorrer durante a execução de um programa. As estruturas `try`, `catch` e `finally` são os pilares desse mecanismo.
``try``
O bloco `try` delimita o código que **potencialmente pode gerar uma exceção**. Se uma exceção ocorrer dentro deste bloco, a execução normal é interrompida, e o controle é transferido para um bloco `catch` correspondente.
``catch``
O bloco `catch` é usado para **capturar e tratar exceções específicas**. Você pode ter múltiplos blocos `catch` para lidar com diferentes tipos de exceções. Quando uma exceção é lançada no bloco `try`, o Java procura por um bloco `catch` que possa manuseá-la.
``finally``
O bloco `finally` contém código que **sempre será executado**, independentemente de uma exceção ter ocorrido ou não no bloco `try`. É comumente usado para liberar recursos, como fechar arquivos ou conexões de rede, garantindo que essas ações sejam realizadas mesmo em caso de erro.
```java
public static void main(String[] args) {
    try {
        // Código que pode gerar uma exceção
        int resultado = 10 / 0; // Isso lançará uma ArithmeticException
        System.out.println("Este texto não será exibido.");
    } catch (ArithmeticException e) {
        // Bloco catch para capturar ArithmeticException
        System.err.println("Erro: Divisão por zero não é permitida.");
        // e.printStackTrace(); // Descomente para ver o rastreamento da pilha
    } catch (Exception e) {
        // Bloco catch genérico para outras exceções
        System.err.println("Ocorreu um erro inesperado: " + e.getMessage());
    } finally {
        // Bloco finally que sempre será executado
        System.out.println("Este bloco finally sempre será executado.");
    }
    System.out.println("Programa continua após o tratamento de exceção.");
    }
    }

```
#### throw / throws – Lançamento e declaração de exceções
O lançamento de exceções é o processo de indicar que uma condição excepcional ocorreu durante a execução do programa. As palavras-chave `throw` e `throws` são usadas para isso, mas com propósitos distintos.
``throw``
A palavra-chave `throw` é usada para **lançar uma exceção explicitamente** em um ponto específico do seu código. Você usa `throw` quando detecta uma condição de erro que deseja sinalizar.
- **Uso:** Dentro de um método ou bloco de código.
- **Propósito:** Criar e lançar uma instância de uma exceção (verificada ou não verificada) para interromper o fluxo normal e transferir o controle para um manipulador de exceções (`try-catch`).
```java
if (valor < 0) {
    throw new IllegalArgumentException("O valor não pode ser negativo.");
}
```
``throws``
A palavra-chave `throws` é usada na **assinatura de um método** para declarar que esse método **pode lançar** uma ou mais exceções. Ela informa aos chamadores do método que eles precisam estar preparados para lidar com essas exceções (sejam elas verificadas ou não).
- **Uso:** Na declaração do método, após a lista de parâmetros.
-  **Propósito:** Propagar a responsabilidade de tratar exceções para o código que chama o método. Se um método declara `throws CheckedException`, o compilador força o chamador a usar um bloco `try-catch` ou a declarar `throws CheckedException` também.
```java
public void lerArquivo(String nomeArquivo) throws FileNotFoundException {
    // Código que pode lançar FileNotFoundException
}
```
##### Diferenças chave de como usar

| Característica        | throw                                                          | throws                                                                           |
| --------------------- | -------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| O quê é               | Uma instrução para lançar uma exceção.                         | Uma declaração na assinatura do método.                                          |
| Onde usar             | Dentro de um método ou bloco de código.                        | Na assinatura do método (após os parâmetros).                                    |
| Propósito             | Lançar explicitamente uma exceção de um ponto específico.      | Declarar que um método pode lançar exceções (passar a responsabilidade).         |
| Gramática             | throw new TipoDeExcecao("mensagem");                           | public void metodo() throws TipoDeExcecao1, TipoDeExcecao2 { ... }               |
| Múltiplas Exceções    | Lança apenas uma exceção por vez.                              | Pode declarar múltiplas exceções separadas por vírgula.                          |
| Checked vs. Unchecked | Pode lançar tanto exceções verificadas quanto não verificadas. | Geralmente usado para declarar exceções verificadas (que precisam ser tratadas). |
