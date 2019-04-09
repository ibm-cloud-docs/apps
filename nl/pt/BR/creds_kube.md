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
{:note: .note}

# Incluindo credenciais no ambiente do Kubernetes
{: #add-credentials-kube}

Aprenda a incluir as credenciais de serviço no ambiente de implementação do Kubernetes.
{: shortdesc}

Deve-se incluir manualmente as credenciais de serviço no ambiente de implementação nestes cenários:
 * Ao trazer seu próprio código.
 * Ao iniciar por meio de um modelo de kit do iniciador em branco.
 * Ao incluir um serviço em um app baseado em kit do iniciador _depois_ que ele foi implementado.

## Seu código + Kubernetes
{: #credentials-byoc-kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### Codifique-o corretamente

Como precaução, é possível codificar o aplicativo para confirmar que seu ambiente está completo no ponto de
entrada principal do aplicativo. Você não deseja promover um aplicativo em um cluster cujo ambiente não está completo
para causar interrupção no produto. O aplicativo pode se recusar a iniciar e sua configuração do Kubernetes pode impedir
automaticamente essas interrupções.

Suponha que você tenha as duas variáveis de ambiente a seguir:
* `SECRET`
* `NOT_SECRET`

Para um banco de dados, as variáveis podem ser `APIKEY` e `DB_URL`, em
que a primeira é sensível e a última não.

Em Java, talvez você queira gravar algo no ponto de entrada do aplicativo principal, como:
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

Em Nó, consulte um exemplo semelhante:
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### Preparar o ambiente

No arquivo `deployment.yml` do Kubernetes, as variáveis de ambiente ou uma _referência a um segredo no cluster_ podem ser definidas.

#### Configure a implementação para obter as credenciais do ambiente

Na seção com `kind: Deployment`, inclua o código de exemplo a seguir em um nível de indentação após `spec.template.spec.containers`:
```yaml
env:
  - name: SECRET
    valueFrom:
      secretKeyRef:
          name: name-secret
          key: KEY_SECRET
  - name: NOT_SECRET
    value: "I'm not a secret"
```
{: codeblock}

* Clique em **Salvar**.

Configure o cluster para que o _secretKeyRef_ com o nome `name-secret` e a
chave `KEY_SECRET` seja resolvido para um valor.

#### Instalando as ferramentas obrigatórias

Use um terminal em sua estação de trabalho para instalar as ferramentas a seguir:

1. Instale a CLI do [{{site.data.keyword.dev_cli_long}} ](/docs/cli/index.html).
2. Efetue login usando o comando `ibmcloud login`.
3. Conecte-se ao cluster executando `ibmcloud cs cluster-config {your_cluster_name}`.
4. Copie e cole o comando `export` para executá-lo por meio de um terminal.

#### Defina o segredo no cluster

O {{site.data.keyword.dev_cli_notm}} fornece o `kubectl`, que pode ser executado
porque você está conectado ao cluster do Kubernetes.

Para definir o segredo resolvível, use esses comandos `kubectl`:
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

Agora que o cluster do Kubernetes está preparado com um segredo resolvível, é possível atualizar o aplicativo para
usar as variáveis de ambiente definidas no arquivo `deployment.yml`.

## App do kit do iniciador + Kubernetes
{: #credentials-starterkit-kube}

1. Acesse a página **Detalhes do app** do app.
2. Para criar uma instância do Cloud Object Storage, selecione **Incluir recurso** >
**Armazenamento** > **Cloud Object Storage** > **plano Lite (grátis)** > **Criar**.
3. Clique em `Fazer download do código` para gerar novamente o projeto com os fragmentos do
código injetado.
4. Para acessar as credenciais localmente, copie e substitua os arquivos a seguir por meio do arquivo
`.zip` recém-gerado, para que o clone Git local acesse as credenciais. Deve-se ainda criar um segredo do Kubernetes no cluster para hospedar as credenciais.

	- `chart/{appName}/bindings.yaml`: gera uma variável de ambiente no cluster do
Kubernetes que aponta para o segredo.
	- `src/main/resources/localdev-config.json`: credenciais de acesso enquanto o app é executado localmente.
  - `src/main/resources/mappings.json`: um mapeamento para fornecer acesso ao método
[`env.getProperty()`](/docs/java-spring/configuration.html#accessing-credentials)
para acessar as variáveis de ambiente por meio do código..
  - `manifest.yml`: esse arquivo liga o serviço ao aplicativo Cloud Foundry.

Se posteriormente você escolher implementar em um aplicativo Cloud Foundry com um recurso do Resource Controller (localizado em um grupo de recursos em vez de uma organização ou espaço), você deverá copiar mais um
arquivo.
{: note}

5. [Visualize](https://cloud.ibm.com/containers-kubernetes/clusters) o cluster do
Kubernetes com a região correspondente (Sul dos EUA se ela era grátis).
6. Clique no cluster e selecione **Painel do Kubernetes** na parte superior direito
para visualizar o painel do cluster.
7. Role para baixo até que você veja uma seção intitulada **Segredos**. É possível ver um
segredo para a instância de serviço do {{site.data.keyword.cloudant_short_notm}} que usa a seguinte convenção `binding-{appName}-{serviceName}-{timestamp}`. No arquivo `chart/{appName}/bindings.yaml` é possível
localizar o segredo do {{site.data.keyword.cloudant_short_notm}} correspondente.
8. Agora é possível criar uma instância correspondente para a instância do Cloud Object Storage com o nome
secreto que já foi gerado no `chart/{appName}/bindings.yaml` e que se parece com `binding-create-app-ktibr-cloudobjectstor-1538170732311`.
9. Acesse a página **Detalhes do app** no painel e copie as credenciais para a instância
do Cloud Object Storage. Consulte a saída de credenciais de exemplo a seguir:
```yaml
{
  "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
  "endpoints": "https://cos-service.bluemix.net/endpoints",
  "resource_instance_id": "crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
}    
```
{: codeblock}

10. Certifique-se de que o cluster esteja configurado usando `ibmcloud cs cluster-config
{your_cluster_name}` e exportando o comando nas instruções a seguir.
11. Use o comando `echo` para colocar as credenciais em um arquivo `binding`.
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. Crie o segredo com o `kubectl create secret generic
binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding`. Se você voltar para o painel do
cluster do Kubernetes, será possível ver o segredo que você criou.

Se estiver implementando em um aplicativo do Cloud Foundry, será necessário criar um serviço fornecido pelo
usuário se você estiver usando uma instância do Resource Controller (se o recurso residir em um grupo de recursos em vez
de em uma organização ou espaço). 
{: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  O nome do serviço fornecido pelo usuário pode ser localizado no arquivo `manifest.yml` com o nome da instância correspondente.

13. Agora será possível acessar o segredo por meio das variáveis de ambiente usando o método
`env.getProperty` quando o aplicativo estiver em execução no cluster do Kubernetes.

### Como o cluster do Kubernetes é preparado

Use o recurso **Implementar para nuvem** para implementar o app no cluster do IBM Containers Kubernetes. O
recurso prepara o cluster do Kubernetes com segredos para as credenciais dos recursos associados ao app. É
possível observar os resultados da preparação do cluster concluindo estas etapas:

1. Execute este comando para visualizar os resultados: `kubectl get secrets`:
  ```
  NAME                                   TYPE                                  DATA      AGE
  binding-blarg-cloudant-1538408663553   Opaque                                1         13m
  bluemix-default-secret                 kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-international   kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-regional        kubernetes.io/dockerconfigjson        1         17d
  default-token-xfd5n                    kubernetes.io/service-account-token   3         17d
  ```
  {: screen}

  É possível visualizar [mais documentação
sobre segredos](https://kubernetes.io/docs/concepts/configuration/secret/).
  {: tip}

2. Observe que o nome do segredo é o nome do recurso.
3. Visualize as informações detalhadas sobre o segredo usando `kubectl get secret
binding-blarg-cloudant-1538408663553 -o=yaml`:

  ```
  apiVersion: v1
  data:
    binding: eyJhcGlrZXkiOiI4RFprT3VMVnduVkExWW1HODFnazNQMjZOeThlNWFWbjVhaFpZLVVEOHQ1NCIsImhvc3QiOiI1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJpYW1fYXBpa2V5X2Rlc2NyaXB0aW9uIjoiQXV0byBnZW5lcmF0ZWQgYXBpa2V5IGR1cmluZyByZXNvdXJjZS1rZXkgb3BlcmF0aW9uIGZvciBJbnN0YW5jZSAtIGNybjp2MTpibHVlbWl4OnB1YmxpYzpjbG91ZGFudG5vc3FsZGI6dXMtc291dGg6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzpiZmEzNDJkZC00YjZmLTRkZmUtYTM1YS05MTA4ZmIwZWM1NzE6OiIsImlhbV9hcGlrZXlfbmFtZSI6ImF1dG8tZ2VuZXJhdGVkLWFwaWtleS01MzI3ZWMxZC0wOWE1LTQyMzctOTczNS03ZTAxZmU3NDFiYzciLCJpYW1fcm9sZV9jcm4iOiJjcm46djE6Ymx1ZW1peDpwdWJsaWM6aWFtOjo6OnNlcnZpY2VSb2xlOldyaXRlciIsImlhbV9zZXJ2aWNlaWRfY3JuIjoiY3JuOnYxOmJsdWVtaXg6cHVibGljOmlhbS1pZGVudGl0eTo6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzo6c2VydmljZWlkOlNlcnZpY2VJZC1mNWRhMjMwYy1kNDE0LTQ4NTQtYjE1Yi00MmJmZmRhYWVmNWIiLCJwYXNzd29yZCI6ImY4MjU2ZDJhODYyMjI5NzViZDI3Mjc1MjEzMTY4YTQyNzBhNDZmMmEyOGQ5NDkyMjRhYzFjOTc3NjMwMWNlZTYiLCJwb3J0Ijo0NDMsInVybCI6Imh0dHBzOi8vNTlhYTdiMWEtNWFhYi00ZjJkLTlhNzMtOGMzYjI5NDA4Zjk2LWJsdWVtaXg6ZjgyNTZkMmE4NjIyMjk3NWJkMjcyNzUyMTMxNjhhNDI3MGE0NmYyYTI4ZDk0OTIyNGFjMWM5Nzc2MzAxY2VlNkA1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJ1c2VybmFtZSI6IjU5YWE3YjFhLTVhYWItNGYyZC05YTczLThjM2IyOTQwOGY5Ni1ibHVlbWl4In0=
  kind: Secret
  metadata:
    annotations:
      service-instance-id: 'crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::'
      service-key-id: 5327ec1d-09a5-4237-9735-7e01fe741bc7
    creationTimestamp: 2018-10-01T15:45:02Z
    name: binding-blarg-cloudant-1538408663553
    namespace: default
    resourceVersion: "155591"
    selfLink: /api/v1/namespaces/default/secrets/binding-blarg-cloudant-1538408663553
    uid: f5e7885c-c590-11e8-ad83-8e37f3f3216f
  type: Opaque
  ```
  {: screen}

  `binding` é o valor codificado em Base64 do segredo. Decodificá-lo revela que ele é apenas o
JSON bruto das `credentials` da instância de recurso, mais alguns valores `iam_...` :
  ```
  {
    "apikey": "8DZkOuLVwnVA1YmG81gk3P26Ny8e5aVn5ahZY-UD8t54",
    "host": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::",
    "iam_apikey_name": "auto-generated-apikey-5327ec1d-09a5-4237-9735-7e01fe741bc7",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Writer",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/480fd1ec14ac540c5bc37da799a63437::serviceid:ServiceId-f5da230c-d414-4854-b15b-42bffdaaef5b",
    "password": "f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6",
    "port": 443,
    "url": "https://59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix:f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6@59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "username": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix"
  }
  ```
  {: screen}

O segredo do Kubernetes não é recuperável pelo código do aplicativo, a menos que o `deployment.yml` declare um valor `env` que faça referência ao segredo. Ao
usar um kit do iniciador, esse código será gerado automaticamente.

### O código gerado pelo kit do iniciador
{: #credentials-starterkit-kube-gencode}

Nesse caso, você criou esse aplicativo por meio de um kit do iniciador. O código gerado por meio de um kit
do iniciador é feito para ser móvel para executar localmente no Cloud Foundry ou em Kubernetes. A biblioteca,
`IBMCloudEnv`, é usada para fornecer uma camada de abstração entre o código do aplicativo e a
recuperação das variáveis de ambiente que retêm as credenciais para os recursos (instâncias de serviço).

O código criado por meio do kit do iniciador tem uma dependência para a biblioteca `IBMCloudEnv` e produz a saída a seguir:

* Um arquivo `bindings.yml`, que é incluído sequencial no arquivo `deployment.yml`, com esse conteúdo:
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  O `secretKeyRef.name` expõe o segredo do Kubernetes definido para que seja recuperável pelo
aplicativo como uma variável de ambiente simples no código do aplicativo.

* As instruções para a biblioteca `IBMCloudEnv` são encapsuladas em um arquivo
`mappings.json`, que está no código base gerado pelo kit do iniciador. O `mappings.json` tem definições individuais para cada credencial:
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

  O arquivo `mappings.json` usa a sintaxe `jsonpath` e a ordem da matriz
`searchPatterns` para orientar a lógica `IBMCloudEnv`.

* Use o código a seguir para recuperar a chave de API do Cloudant (pseudocódigo):
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

A biblioteca `IBMCloudEnv` detecta automaticamente se o aplicativo está em execução no
Kubernetes, no Cloud Foundry ou em uma instância de servidor virtual (tratados da mesma forma que o Docker local) e
aplica o `searchPattern` correto para localizar o valor a ser retornado.

Portanto, o arquivo `mappings.json` deve ser considerado _a lista definitiva_ dos
valores pré-configurados e imediatamente disponíveis que são do ambiente no qual o app deve ser executado. Os valores
são preenchidos no ambiente para o cluster que você destinou no momento em que usou o recurso **Implementar na
nuvem**.

**Cuidado**: no momento da criação desta documentação, a preparação do ambiente
_sempre_ é executada para todas as credenciais para todos os recursos associados a um app, mas
_nem todas as referências `env`_ são colocadas no arquivo `bindings.yml`
ou no arquivo `mappings.json`. Nesses casos, você mesmo deve colocar essas referências. Se você já
decidiu sobre uma implementação de destino e não precisa da abstração da biblioteca `IBMCloudEnv`, consulte a seção
"Seu código + (implementação de destino)" que se ajusta à sua decisão.

Alguns kits do iniciador não incluem de forma alguma a referência para a dependência `IBMCloudEnv`, para `manifest.yml` ou para os arquivos `mappings.json`.
{: note}
