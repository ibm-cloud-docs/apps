---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Incluindo credenciais na instância virtual ou no ambiente do Docker local
{: #add-credentials-vsi}

Aprenda a incluir as credenciais de serviço na instância de servidor virtual ou no ambiente de implementação
do Docker local.
{: shortdesc}

## Seu código + instância de servidor virtual ou Docker local
{: #credentials-byoc-vsi}

Sob o VSI ou o Docker local, o ambiente é inteiramente seu. Por exemplo, é possível gravar o código como no
exemplo a seguir e fornecer o valor do ambiente da credencial para o aplicativo ao executá-lo.
```
password = getEnvironment('password');
```
{: codeblock}

Em Bash, é possível gravar o código como no exemplo a seguir:
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

No Docker, é possível gravar o código como no exemplo a seguir:
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## Kit do iniciador + VSI (ou Docker local)
{: #credentials-starterkit-vsi}

### Como a instância de servidor virtual é preparada

O ambiente está totalmente sob o seu controle, como se você estivesse executando o aplicativo por meio do seu notebook. Em outras palavras, o Docker local. Como o VSI é efetivamente bare metal da perspectiva do aplicativo
em execução, não existe nenhum _segredo_ (como no Kubernetes) ou _serviço_ (como no Cloud
Foundry).

### O código gerado pelo kit do iniciador
{: #starterkit-generated-code-vsi}

O código gerado por meio de um kit do iniciador tem a biblioteca `IBMCloudEnv` nativa,
que abstrai a recuperação dos valores do ambiente para que o código do aplicativo seja móvel para execução em
diversas implementações de destino. Com o Docker virtual ou local, esse ambiente deve ser preparado com valores que
satisfaçam a biblioteca `IBMCloudEnv` que _não necessariamente_ vêm de variáveis de
ambiente reais.

Para a sua conveniência, as instruções `mappings.json` que são incluídas com a saída gerada
pelo kit do iniciador, têm referências a um arquivo local do qual a biblioteca `IBMCloudEnv` gera os valores que o aplicativo pode usar.

Por exemplo, observe a última linha na seção do arquivo `mappings.json`:
```json
"cloudant_apikey": {
  "searchPatterns": [
    "user-provided:blarg-cloudant-1538408663553:apikey",
    "cloudfoundry:$['cloudant'][0].credentials.apikey",
    "env:service_cloudant:$.apikey",
    "env:cloudant_apikey",
    "file:/server/localdev-config.json:$.cloudant_apikey"
  ]
},
```
{: codeblock}

Se você usar o recurso "Implementar na nuvem" ao criar um app, o arquivo
`/server/localdev-config.json` será removido do repositório GitLab. Por razões de segurança, você não desejará colocar as suas credenciais em um repositório de código-fonte.

Se você usar `git clone` no repositório GitLab criado para iniciar o desenvolvimento ativo,
observe que o arquivo `.gitignore` ignorará especificamente o `server/localdev-config.json` para ajudar a evitar check-ins acidentais de um arquivo que tenha
credenciais sensíveis. No entanto, o VSI _precisa_ desse arquivo, assim como o desenvolvedor que
trabalha em um notebook.

É possível recuperar o arquivo `server/localdev-config.json` concluindo estas etapas:

1. Use `git clone` no repositório GitLab que foi criado automaticamente quando
você usou o recurso "Implementar na nuvem".
2. Instale a CLI do [{{site.data.keyword.cloud_notm}}](/docs/cli/index.html#overview), que inclui o plug-in `dev`.
3. Use a linha de comandos `ibmcloud` para efetuar login no {{site.data.keyword.cloud_notm}}.
4. Execute `ibmcloud dev get-credentials`, que se refere ao arquivo `cli-config.yml`. O arquivo `cli-config.yml` inclui informações sobre qual aplicativo e tarefa de geração tem as
credenciais.

Se algum recurso for removido do aplicativo entre o uso do recurso "Implementar na nuvem" e o
`ibmcloud dev get-credentials`, o arquivo transferido por download `/server/localdev-config.json`
não terá todas as credenciais que o código base `git clone` original pode requerer.
{: tip}

Se você estiver executando o aplicativo em um contêiner do Docker, será possível optar por remover o arquivo `/server/localdev-config.json` completamente e passar as variáveis de ambiente na linha de comandos
do Docker.

Continuando com a seção "cloudant_apikey" por meio do arquivo `mappings.json`, observe o
`env:cloudant_apikey` antes da linha `file...`. Isso significa que uma variável de ambiente denominada `cloudant_apikey` tem precedência sobre o conteúdo do arquivo. Portanto, mesmo se o arquivo estiver presente na imagem do Docker que você construiu (o que não é necessário), será possível
substituir os valores passando-os na linha de comandos do Docker.

Por exemplo:
```console
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}
