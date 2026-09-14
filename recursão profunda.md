Acontece quando uma função recursiva chama a si mesma uma quantidade excessiva de vezes consecutivas antes de alcançar o seu caso base (a condição de parada).
Cada vez que uma função se chama recursivamente, o programa não "descarta" a execução atual: ele precisa salvar o estado atual na memória para saber para onde voltar quando a chamada terminar.
#### O mecanismo da Call Stack (Pilha de Chamadas)
Para entender por que a recursão profunda é um problema, é preciso entender a **Call Stack**:
1. **Frames de Pilha (Stack Frames)**: Sempre que uma função é executada, o sistema cria um frame na memória contendo suas variáveis locais, parâmetros e o endereço de retorno.
2. **Empilhamento**: Em uma chamada recursiva, esses frames vão se acumulando um em cima do outro.
3. **Desempilhamento**: A memória só começa a ser liberada quando a última função atinge o caso base e finalmente começa a retornar seus valores.
Se a recursão for muito "funda" (por exemplo, centenas de milhares de chamadas empilhadas), a memória alocada para a pilha estoura, gerando o famoso erro de **Stack Overflow** (ou <font color="#ff0000">java.lang.StackOverflowError</font> no Java, <font color="#ff0000"><font color="#ff0000"><font color="#ff0000"></font>RecursionError</font></font> no Python).