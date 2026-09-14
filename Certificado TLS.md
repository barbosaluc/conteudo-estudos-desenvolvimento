(Anteriormente chamado de certificado SSH) é um documento digital que funciona como uma carteira de identidade criptográfica para um site ou servidor na internet.

Ele cumpre duas funções na web moderna:

1. Autenticação: Prova para o navegador que o servidor é realmente que diz ser (ex: garante que você está no site verdadeiro do seu banco e não em um clone).
2. Criptografia: Codifica o tráfego entre o cliente e o servidor de forma que ninguém no meio do caminho consiga ler ou alterar dados sensíveis.

### Como funciona o Par de Chaves (Criptografia Assimétrica)

O certificado TLS depende do conceito de criptografica de chave pública:

- Chave pública (Public Key): Fica dentro do certificado e é distribuída abertamente para qualquer pessoa que acesse o site. Qualquer dado codificado por ela só pode ser lido pela chave privada.
- Chave Privada (Private Key): Fica guardada a sete chaves no servidor (ou no Router do OpenShift) e nunca é compartilhada. É ela que decodifica o que a chave pública criptografou.

### Quem garante que o certificado é legitimo? (as CAs)

Qualquer pessoa pode gerar um certificado digital no próprio computador (self-signed certificates). No entanto, para que navegadores e clientes confiem nele, o certificado precisa ser emitido por uma Autoridade Certificadora (Certificate Authority - CA) confiável como _Let's Encrypt_, _DigiCert_ ou _GlobalSign_.

Seu sistema operacional e navegadores já vêm de fábrica com uma lista de CAs confiáveis. Quando você acessa um site via `https://`, o navegador checa se o certificado do site foi assinado por uma dessas CAs.

---

## O Fluxo do TLS Handshake

Quando um cliente tenta acessar um serviço protegido por TLS, ocorre um processo ultrarrápido negociado antes do envio de qualquer dado HTTP:

1. **Client Hello (Início da negociação)**
    - O navegador se conecta ao servidor, envia as versões do TLS que suporta e os algoritmos de criptografia disponíveis (_cipher suites_).
2. **Server Hello & Envio do Certificado**
    - O servidor responde escolhendo os parâmetros de criptografia e enviando seu **certificado TLS público** (que contém sua chave pública e a assinatura da Autoridade Certificadora - CA).
3. **Validação pelo Cliente**
    - O navegador verifica a autenticidade do certificado junto à cadeia de CAs confiáveis e confirma se o nome de domínio bate com a URL acessada.
4. **Geração da Chave Simétrica (Session Key)**
    - Cliente e servidor trocam dados para derivar uma chave temporária única para aquela sessão. A partir desse instante, a comunicação passa a ser completamente cifrada via criptografia simétrica (mais rápida).

---

## Conexão com o OpenShift

Lembrando o contexto do OpenShift e do `Route`:

- **Com Terminação `edge`:** O Router do OpenShift guarda a **chave privada** e o **certificado TLS**. O _TLS Handshake_ é feito diretamente entre o cliente externo e o Router.
- **Com Terminação `passthrough`:** O Router apenas repassa os pacotes brutos, e a aplicação dentro do Pod é quem precisa ter o certificado e a chave privada para realizar o _TLS Handshake_.