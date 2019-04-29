---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-04"

keywords: apps, credentials, cloud foundry, environment, service, credential, vcap_services

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Incluindo credenciais no ambiente do Cloud Foundry
{: #add-credentials-cf}

Aprenda a incluir as credenciais de serviço no ambiente de implementação do Cloud Foundry. Estas instruções se aplicam a ambos, [Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf) e [Cloud Foundry Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee).
{: shortdesc}

O domínio compartilhado padrão é `mybluemix.net`, mas o `appdomain.cloud` é outra opção de domínio que você pode usar. Para obter mais informações sobre como migrar para o `appdomain.cloud`, consulte [Atualizando seu domínio](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).
{: tip}

## Seu código + Cloud Foundry
{: #credentials-byoc-cf}

No espaço do Cloud Foundry em que o aplicativo existe, é possível definir o que o Cloud Foundry chama de um serviço fornecido pelo usuário. Um serviço fornecido pelo usuário é um JSON em sequência armazenado como se fosse um serviço de ligação no espaço do Cloud Foundry. Depois de efetuar login e se conectar à organização e ao espaço do Cloud Foundry, conclua as etapas a seguir para criar e ligar um serviço.

1. Crie um serviço fornecido pelo usuário executando o comando a seguir:
  ```console
  cf cups customcreds -p '{"username":"Leeroy","password":"Jenkins"}'
  ```
  {: codeblock}

2. Configure o aplicativo Cloud Foundry para se ligar ao serviço fornecido pelo usuário incluindo na seção de serviços:
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - customcreds
  ```

3. Codifique o aplicativo para ler o ambiente para uma variável de ambiente `VCAP_SERVICES`,
analisá-lo no JSON e localizar a credencial necessária (node.js-like pseudocode):
  ```
  // get the 'password' from "customcreds" user-provided service
  vcapServices = getEnvironment('VCAP_SERVICES');
  vcapServicesAsJSON = JSON.parse(vcapServices);
  upsArray = vcapServicesAsJSON['user-provided'];
  if (upsArray) {
      for (var i = 0, len = upsArray.length; i < len; i++) {
          if (upsArray[i].name === 'customcreds') {
              return upsArray[i].credentials.password
          }
      }
  }
  ```
{: codeblock}


## App do kit do iniciador + Cloud Foundry
{: #credentials-starterkit-cf}

### Como o espaço do Cloud Foundry é preparado

Use o recurso **Configurar entrega contínua** para implementar seu app em seu espaço do Cloud Foundry.

Se a instância de serviço baseada no Cloud Foundry estiver no mesmo espaço do Cloud Foundry que o aplicativo Cloud Foundry implementado, consulte a [próxima seção](/docs/apps?topic=creating-apps-add-credentials-cf).

Se a instância de serviço baseada no Cloud Foundry estiver em um espaço diferente do espaço de destino para o aplicativo Cloud Foundry, consulte a [seção a seguir](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_different).

Se o serviço que você associou ao seu aplicativo for baseado no Resource Controller, consulte [Resource Controller](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_controller).

#### O serviço baseado no Cloud Foundry está no mesmo espaço que o app implementado
{: #cf_resource_same}

Se o serviço que você associou ao seu aplicativo for baseado no Cloud Foundry, o serviço será "ligável" ao Cloud Foundry. É possível ver o serviço no espaço do Cloud Foundry conectando a linha de comandos `cf` com a região correta mais a organização e o espaço. É possível dizer se o serviço é baseado no Cloud Foundry no momento da criação dele, se foi perguntado a você em qual organização e espaço do Cloud Foundry criar o serviço.

É possível visualizar os aplicativos ligados executando o comando a seguir:
```console
cf services
```
{: codeblock}

Saída de exemplo:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg3-alertnotificati-1538417831070   alertnotification   authorizedusers                create succeeded
```
{: screen}

#### O serviço baseado no Cloud Foundry está em um espaço diferente do app implementado
{: #cf_resource_different}

O Cloud Foundry não suporta a "ligação" de um aplicativo Cloud Foundry a um serviço do Cloud Foundry quando o aplicativo e o serviço não estão no mesmo espaço do Cloud Foundry. O espaço do Cloud Foundry deve ser preparado com os serviços "fornecidos pelo usuário" e a seção a seguir é aplicável.

#### O serviço baseado no Resource Controller está associado ao seu app
{: #cf_resource_controller}

Se o serviço que você associou ao seu aplicativo for baseado no Resource Controller, o serviço _não_ será "ligável" ao Cloud Foundry. É possível dizer se o serviço é baseado no Resource Controller no momento da criação dele, se foi perguntado a você em qual grupo de recursos criar o serviço. O espaço do Cloud Foundry deve ser preparado com credenciais de serviço para que o aplicativo possa referenciá-las no código. A preparação é feita automaticamente e é possível observar os resultados da preparação do espaço conectando a linha de comandos `cf` ao espaço executando:
```console
cf services
```
{: codeblock}

Saída de exemplo:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg-cloudant-1538408663553           user-provided
```
{: screen}

O Cloud Foundry não permite visibilidade para o valor de nenhuma credencial de serviço, codificada ou não, para a linha de comandos `cf service` ou `cf services`. Funcionalmente, um serviço fornecido pelo usuário é um JSON em sequência definido como uma "instância de serviço" nomeada no espaço do Cloud Foundry. Para
ver os valores, deve-se primeiro ligar um aplicativo ao serviço do Cloud Foundry indicando o nome da instância de serviço no arquivo `manifest.yml` do app sob o título `services`. Em seguida, execute o app no espaço do Cloud Foundry e obtenha o ambiente desse aplicativo executando `cf env $APP_NAME`.

Felizmente, o código que é gerado por meio de um kit do iniciador é preenchido automaticamente com as ligações corretas para recuperar e usar os valores do ambiente definido para ele no espaço do Cloud Foundry no qual o aplicativo é executado.

### O código gerado pelo kit do iniciador
{: #starterkit-generated-code-cf}

Antes de continuar, consulte [App do kit do iniciador + kube](/docs/apps?topic=creating-apps-add-credentials-kube#credentials-starterkit-kube-gencode). Em seguida, aplique a mudança a seguir:

* Embora o código gerado forneça o `deployment.yml`, ele não é aplicável para um aplicativo que é implementado no Cloud Foundry. Em vez disso, `manifest.yml` _é_ aplicável e seu conteúdo é mostrado como _ligação_ para os dois serviços que são criados no espaço do Cloud Foundry:
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - blarg3-alertnotificati-1538417831070
      - blarg-cloudant-1538408663553
  ```
  {: codeblock}

O restante da documentação da subseção anterior se aplica novamente. A biblioteca `IBMCloudEnv` abstrai a recuperação dos valores do ambiente no qual o aplicativo é executado.

A biblioteca abstrai alguma complexidade na recuperação dos valores do ambiente do Cloud Foundry. No Cloud
Foundry, um aplicativo em execução é fornecido com uma variável de ambiente denominada `VCAP_SERVICES`
cujo valor é JSON em sequência e retém os valores para ligar as credenciais de serviço, não importando se o
serviço é uma instância de serviço _no_ espaço do Cloud Foundry ou um valor de serviço definido pelo usuário. As
chaves de nível superior no JSON analisado por meio da variável de ambiente `VCAP_SERVICES` são a
`label` do Cloud Foundry associada aos serviços baseados em Cloud Foundry e a chave
`user-provided`, cujo valor retém uma matriz de credenciais para todos os serviços "fornecidos pelo usuário".
