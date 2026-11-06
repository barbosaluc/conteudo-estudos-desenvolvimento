Ou Função com Serviço, é um modelo de computação em nuvem no qual você publica pequenas funções de código, e o provedor cuida da infraestrutura necessária para executá-las.
Essas funções normalmente são acionadas por eventos, com uma requisição HTTP, a chegada de uma mensagem em uma fila ou o envio de um arquivo.
Por exemplo, imagine um aplicativo de fotos:
1. O usuário envia uma imagem para o armazenamento na nuvem.
2. Esse envio dispara uma função.
3. A função cria uma miniatura e a salva.
4. A execução termina, sem que você precise manter um servidor dedicado para essa tarefa.
Você escreve o código e configura o acionamento. O provedor administra os servidores e ajusta a capacidade conforme a demanda. A cobrança geralmente depende da quantidade de execuções e dos recursos consumidos durante elas, embora existam custos adicionais conforme os serviços usados.
FaaS costuma fazer parte do universo [^1]severless. Isso não significa que não existam sevidores: significa que você não precisa administrá-los diretamente. Serverless é um conceito mais amplo; FaaS é uma das formas de implementá-lo.

As principais vantagens são a facilidade de escalar, a menor necessidade de administrar infraestrutura e o bom aproveitamento de recursos para tarefas eventuais. Entre as limitações estão os limites de duração das execuções e a possível demora para iniciar uma função que estava inativa, chamada de cold start. Além disso, dados que precisam persistir devem ficar em um serviço externo, como um banco de dados.
AWS Lambda é um exemplo de FaaS. Esse modelo é especialmente útil para APIs, processamento de arquivos, automações e tarefas disparadas por eventos.

[^1]: É um modelo de computação em nuvem em que você usa serviços e executa código sem precisar administrar servidores. O provedor gerencia a infraestrutura e ajusta os recursos conforme a demanda.
---
#flashcards/cloud/FaaS
Como funciona a FaaS (Function as a Service)?:: Você publica pequenas funções de código, e o provedor cuida da infraestrutura necessária para executá-las. As funções são acionadas por eventos, como um requisição HTTP, a chegada de uma mensagem em uma fila ou envio de um arquivo.
