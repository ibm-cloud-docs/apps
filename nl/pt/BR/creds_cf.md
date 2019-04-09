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

# Incluindo credenciais no ambiente do Cloud Foundry
{: #add-credentials-cf}

Aprenda a incluir as credenciais de serviço no ambiente de implementação do Cloud Foundry. Estas instruções se aplicam a ambos, [Cloud Foundry Public](/docs/cloud-foundry-public/about-cf.html) e [Cloud Foundry Enterprise Environment](/docs/cloud-foundry-public/cfee.html).
{: shortdesc}

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

Use o recurso **Implementar para nuvem** para implementar o app no espaço do Cloud Foundry.

Se a instância de recurso baseada em Cloud Foundry está no mesmo espaço do Cloud Foundry como o aplicativo
Cloud Foundry implementado, consulte a [próxima seção](/docs/apps/creds_cf.html#cf_resource_same).

Se a instância de recurso baseada em Cloud Foundry está em um espaço diferente do espaço de destino para o aplicativo Cloud Foundry, consulte a [seção a seguir](/docs/apps/creds_cf.html#cf_resource_different).

Se o recurso que você associou ao aplicativo for baseado no Resource Controller, consulte [Resource Controller](/docs/apps/creds_cf.html#cf_resource_controller).

#### O recurso baseado em Cloud Foundry está no mesmo espaço que o app implementado
{: #cf_resource_same}

Se o recurso que você associou ao aplicativo for baseado em Cloud Foundry, o recurso será "de ligação" no Cloud Foundry. É possível ver o serviço no espaço do Cloud Foundry conectando a linha de comandos `cf` com a região correta mais a organização e o espaço. É
possível dizer se o recurso é baseado no Cloud Foundry no momento de sua criação, se a organização e o espaço do Cloud
Foundry nos quais criá-lo foram solicitados a você.

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

#### O recurso baseado em Cloud Foundry está em um espaço diferente do app implementado
{: #cf_resource_different}

O Cloud Foundry não suporta a "ligação" de um aplicativo Cloud Foundry a um serviço do Cloud Foundry quando o aplicativo e o serviço não estão no mesmo espaço do Cloud Foundry. O espaço do Cloud Foundry deve ser preparado com os serviços "fornecidos pelo usuário" e a seção a seguir é aplicável.

#### O recurso baseado no Resource Controller é associado ao app
{: #cf_resource_controller}

Se o recurso que você associou ao aplicativo for baseado em ResourceController (você pode dizer que ele é `ResourceController` com base no horário da criação do recurso, se o grupo de recursos no qual criar o recurso foi solicitado a você), o recurso _não_ será "de ligação" no Cloud Foundry. O espaço do Cloud Foundry deve ser preparado com as credenciais de recurso para que o aplicativo possa referenciá-las no código. A preparação é feita automaticamente e é possível observar os resultados da preparação do espaço conectando a linha de comandos `cf` ao espaço executando:
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

Antes de continuar, consulte [App do kit do iniciador + kube](/docs/apps/creds_kube.html#credentials-starterkit-kube-gencode). Em seguida, aplique a mudança a seguir:

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

**Cuidado**: semelhante ao cuidado expresso na seção referida, a preparação do ambiente _sempre_ é executada para todas as credenciais para todos os recursos associados a um app e todos os `services` são listados no `manifest.yml`, mas _nem todas as referências de credencial_ são colocadas no arquivo `mappings.json`. Nesses casos, é necessário que você mesmo coloque essas referências. Depois
de decidir sobre uma implementação de destino e não precisar da abstração da biblioteca `IBMCloudEnv`, consulte a seção "Seu código + (implementação de destino)" que se ajusta à sua decisão.

**Muita atenção**: alguns kits do iniciador não incluem de forma alguma a referência para a
dependência `IBMCloudEnv`, para `manifest.yml` ou para os arquivos `mappings.json`.
