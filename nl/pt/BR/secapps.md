---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# Criando solicitações de assinatura de certificado
{: #ssl_csr}

É possível assegurar seus aplicativos fazendo upload de certificados SSL e restringindo acesso aos aplicativos.
{:shortdesc}

Antes que seja possível fazer upload dos certificados SSL aos quais você está autorizado com o {{site.data.keyword.cloud}}, deve-se criar uma solicitação de assinatura de certificado (CSR) no servidor. Uma CSR é uma mensagem que é enviada a uma autoridade de certificado para solicitar
a assinatura de uma chave pública e as informações associadas. O mais comum é que as CSRs estejam no formato PKCS #10. A CSR inclui uma chave pública e um nome comum, uma organização, uma cidade, um estado, um país e um e-mail. As
solicitações de certificado SSL são aceitas somente com um comprimento da chave CSR de 2048 bits.

## Conteúdos CSR obrigatórios

Para que a CSR seja válida, as informações a seguir devem ser inseridas ao gerar a CSR:

### Nome do país

  Um código com dois dígitos para o país ou a região. Por exemplo, `US` é o código do país para os Estados Unidos. Para outros países ou regiões, verifique a [lista de códigos de país ISO ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.iso.org/obp/ui/#search){:new_window} antes de criar o CSR.

### Estado ou município

  O nome completo sem abreviação do estado ou do município.

### Localidade

  O nome completo da cidade ou do município.

### Organização

  O nome completo dos negócios ou da empresa, conforme registrado legalmente em sua localidade ou nome pessoal. Para
empresas, certifique-se de incluir o sufixo de registro, como Ltd., Inc. ou NV.

### Unidade de Organização

  O nome da filial da sua empresa que está pedindo o certificado, tal como contabilidade ou marketing.

### Nome comum

  O nome completo do domínio (FQDN) para o qual você está solicitando o certificado SSL.

Os métodos para criar uma CSR veriam dependendo de seu sistema operacional. O exemplo a seguir mostra como criar uma CSR usando [a ferramenta de linha de comandos OpenSSL ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](http://www.openssl.org/){:new_window}:

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout
    privatekey.key
```

A implementação OpenSSL SHA-512 depende do suporte
do compilador para o tipo de número inteiro de 64 bits. É possível usar a opção SHA-1 para aplicativos
que possuem problemas de compatibilidade com o certificado SHA-256.
{: tip}

Um
certificado é emitido por uma autoridade de certificação e é assinado digitalmente por
essa autoridade. Depois de criar o CSR, é possível gerar seu certificado SSL em uma autoridade de certificado público.

## Fazendo upload de certificados SSL
{: #ssl_certificate}

É possível aplicar um protocolo de segurança para fornecer privacidade de
comunicação a seu aplicativo a fim de evitar espionagem, violação e falsificação de
mensagens.

Caso o proprietário da conta tenha uma conta de avaliação grátis, deve-se fazer upgrade de sua conta para fazer upload de um certificado.

Antes que seja possível fazer upload dos certificados, deve-se criar uma
solicitação de assinatura de certificado.

Ao usar um domínio customizado para entregar o certificado SSL, use os terminais de região a seguir para fornecer a rota de URL para sua organização no {{site.data.keyword.cloud_notm}}:

* EU-Sul- ` secure.us-south.bluemix.net `
* US-East- ` secure.us-east.bluemix.net `
* EU-DE- ` secure.eu-de.bluemix.net `
* EU-GB- ` secure.eu-gb.bluemix.net `
* AU-SYD- ` secure.au-syd.bluemix.net `

Para fazer upload de um certificado para o seu aplicativo, siga essas etapas.

1. Acesse a lista de recursos.

2. Selecione seu app para abrir a visualização de detalhes do app.

3. Clique nas **Rotas** > **Gerenciar domínios**.

4. Na coluna de ação, clique em **Domínios** no menu de ações adicionais e selecione a sua organização.

5. Clique em **Fazer upload ** na coluna Certificado SSL e selecione seu domínio customizado.

  #### Certificado

    Um documento digital que liga uma chave pública à identidade do proprietário do certificado, o que permite que o proprietário do certificado seja autenticado. Um
certificado é emitido por uma autoridade de certificação e é assinado digitalmente por
essa autoridade.

    Um certificado é geralmente emitido e assinado por uma autoridade de certificação. No entanto, para propósitos de teste e desenvolvimento é possível usar um certificado autoassinado.

    Os
tipos de certificados a seguir são suportados no
{{site.data.keyword.cloud_notm}}:

	* PEM (`pem`, `.crt`, `.cer` e `.cert`)
	* DER (` .der `  ou  ` .cer `)
	* PKCS #7 (`p7b`, `p7r`, `spc`)

  #### Chave privada

    Um padrão algorítmico que é usado para criptografar mensagens que somente a chave pública correspondente pode decriptografar. A chave privada também é usada para decriptografar mensagens que foram criptografadas pela chave pública correspondente. A chave privada é
mantida no sistema do usuário e protegida por uma senha.

    Os tipos de chaves privadas a seguir são suportados no
{{site.data.keyword.cloud_notm}}:

    * PEM (` pem `,  ` .key `)
    * PKCS #8 (` p8 `,  ` pk8 `)

  #### Certificado intermediário

    Um certificado subordinado que é emitido pela autoridade de certificação raiz confiável
(CA) especificamente para emitir certificados do servidor de entidade final. O resultado é uma cadeia de certificados que inicia na
autoridade de certificação raiz confiável, passa pelo certificado intermediário e
termina com o certificado SSL emitido para a organização.

    Use um certificado intermediário para verificar a autenticidade do certificado principal. Os certificados intermédios geralmente são obtidos de um terceiro confiável. Você pode não precisar de um certificado intermediário ao testar seu aplicativo antes de implementá-lo em produção.

  #### Ativar solicitação de certificado de cliente

    Se você ativa essa opção ao fazer upload de um arquivo de armazenamento confiável de certificado de cliente, um usuário que tenta acessar um domínio protegido por SSL é solicitado a fornecer um certificado do lado do cliente. Por exemplo, em um navegador da web, quando um usuário tentar acessar um domínio protegido por SSL, o navegador da web solicitará ao usuário que forneça um certificado de cliente para o domínio. Use a opção de upload de arquivo de **Armazenamento confiável de certificado de cliente** para definir os certificados do lado do cliente que permitem acessar seu domínio customizado.

  O recurso de certificado customizado no gerenciamento de domínio do
{{site.data.keyword.cloud_notm}} depende da
extensão de Indicação de Nome do Servidor (SNI) do protocolo de
Segurança da Camada de Transporte (TLS). O código do cliente que acessa os aplicativos {{site.data.keyword.Bluemix_notm}} que são protegidos pelos certificados customizados deve suportar a extensão SNI na implementação do TLS. Para obter mais informações, consulte [seção 7.4.2 do RFC 4346 ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](http://tools.ietf.org/html/rfc4346#section-7.4.2){:new_window} e [Assegurando dados com TLS](/docs/get-support/appsectls.html).
  {: note}

  #### Armazenamento confiável de certificado de cliente

  O armazenamento confiável de certificado de cliente inclui os certificados de cliente para os usuários aos quais deseja permitir acesso ao seu aplicativo. Faça upload de um arquivo de armazenamento confiável de certificado de cliente para ativar a opção para solicitar um certificado de cliente.

   Os
tipos de certificados a seguir são suportados no
{{site.data.keyword.cloud_notm}}:

      * PEM (pem, .crt, .cer e .cert)
      * PKCS #7 (p7b, p7r, spc)

  É possível configurar a autenticação mútua fazendo upload de um armazenamento confiável de certificado de cliente que inclui uma chave pública em seus metadados.
  {: tip}

Para obter mais informações, veja [Importando SSL Certificates](/docs/infrastructure/ssl-certificates/import-ssl-certificate.html#import-an-ssl-certificate).

Para excluir um certificado ou substituir um certificado existente por um novo, siga essas etapas.

1. Acesse **Gerenciar > Conta** e selecione **Organizações do Cloud Foundry**.
2. Na coluna de ação, selecione **Domínios** no menu de ações adicionais. No menu de ações adicionais para a organização, clique em **Remover da organização**.
