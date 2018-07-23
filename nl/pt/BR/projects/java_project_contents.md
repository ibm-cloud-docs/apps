---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-22"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Arquivos de app Java
{: #java-project-files}

Para apps Java, as informações a seguir são um inventário do que você normalmente localiza no {{site.data.keyword.Bluemix}}. Ao criar um kit do iniciador, esses arquivos são criados para você. Se você estiver migrando um app para hospedar no {{site.data.keyword.Bluemix_notm}}, poderá desejar revisar essas informações para evitar possíveis conflitos.
{:shortdesc}

## Spring
{: #spring-project-files}

A tabela a seguir lista os diretórios e os arquivos que estão incluídos em um app Java Spring gerado.

| Diretório `./`                                  | Descrição                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | O arquivo maven pom |
| cli-config.yml | Opções de configuração de CLI |
| manifest.yml | Arquivo de implementação do Cloud Foundry |
| Dockerfile | Dockerfile para comandos `ibmcloud dev run`, `ibmcloud dev deploy` e `docker` |
| Ferramentas do Dockerfile | Dockerfile para `ibmcloud dev build` e `ibmcloud dev test` |
| LICENÇA | Arquivo de licença |
| README.md | Descrição do app |
{: caption="Tabela 1. Conteúdo de um diretório-raiz do app Java Spring gerado" caption-side="top"}

| Diretório `./src/main/java/` | Descrição                       |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/test/application/SBApplication.java` | O aplicativo Spring principal |
| `./src/main/test/application/HealthEndpointTest.java` | Testes |
| `./src/main/java/application/rest/HealthApplication.java` | Endpoint de funcionamento |
| `./src/main/java/application/rest/v1/Example.java` | O código de exemplo |
| `./src/main/java/resources/application-local.properties` | Propriedades de Spring |
{: caption="Tabela 2. Conteúdo de um diretório /java/ do app Java Spring gerado" caption-side="top"}

| Diretório `./.bluemix/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de construção de contêiner |
| deploy.json | Informações de implementação |
| kube_deploy.sh | Script de implementação do Kubernetes |
| pipeline.yml | Definição de pipeline do IBM Cloud |
| toolchain.yml | Definição da cadeia de ferramentas do IBM Cloud |
{: caption="Tabela 3. Conteúdo de um diretório ./.bluemix/ do app Java Spring gerado" caption-side="top"}

|Diretório `./chart/<projectname>/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Gráfico Helm |
| `./chart/<projectname>/values.yaml` | Valores do gráfico Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Modelo de implementação |
| `./chart/<projectname>/templates/hpa.yaml` | Modelo HPA |
| `./chart/<projectname>/templates/service.yaml` | Modelo de serviço |
{: caption="Tabela 4. Conteúdos de um diretório ./chart/<projectname>/templates/ do app Java Spring gerado" caption-side="top"}

| Diretório `./manifests/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Serviço e implementação do & Kubernetes yaml |
{: caption="Tabela 5. Conteúdo de um diretório ./manifests/ do app Java Spring gerado" caption-side="top"}

## Liberty
{: #liberty-project-files}

A tabela a seguir lista os diretórios e os arquivos incluídos em um app Java Liberty gerado.

| Diretório `./`                                  | Descrição                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | O arquivo maven pom |
| cli-config.yml | Opções de configuração de CLI |
| manifest.yml | Arquivo de implementação do Cloud Foundry |
| Dockerfile | Dockerfile para comandos `ibmcloud dev run`, `ibmcloud dev deploy` e `docker` |
| Ferramentas do Dockerfile | Dockerfile para os comandos `ibmcloud dev build` e `ibmcloud dev test` |
| LICENÇA | Arquivo de licença |
| README.md | Descrição do app |
{: caption="Tabela 6. Conteúdo de um diretório-raiz do app Java Liberty gerado" caption-side="top"}

| Diretório `./src/main` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/java/application/rest/HealthApplication.java` | Endpoint de funcionamento |
| `./src/main/java/application/rest/v1/Example.java` | O código de exemplo |
| `./src/main/liberty/config/jvm.options` | Opções de JVM |
| `./src/main/liberty/config/jvmbx.options` | Configuração do agente de métricas Java |
| `./src/main/liberty/config/server.env` | `Variáveis de ambiente |
| `./src/main/liberty/config/server.xml` | Configuração do servidor |
| `./src/main/webapp/WEB-INF/beans.xml` | Configuração de bean CDI |
| `./src/main/webapp/WEB-INF/ibm-web-ext.xml` | Configuração de app da web IBM |
| `./src/main/test/it/HealthEndpointTest.java` | Testes |
{: caption="Tabela 7. Conteúdo de um diretório ./src/main/ do app Java Liberty gerado" caption-side="top"}

| Diretório `./.bluemix/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de construção de contêiner |
| deploy.json | Informações de implementação |
| kube_deploy.sh | Script de implementação do Kubernetes |
| pipeline.yml | Definição de pipeline do IBM Cloud |
| toolchain.yml | Definição da cadeia de ferramentas do IBM Cloud |
{: caption="Tabela 8. Conteúdo de um diretório ./bluemix/ do app Java Liberty gerado" caption-side="top"}

|Diretório `./chart/<projectname>/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Gráfico Helm |
| `./chart/<projectname>/values.yaml` | Valores do gráfico Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Modelo de implementação |
| `./chart/<projectname>/templates/hpa.yaml` | Modelo HPA |
| `./chart/<projectname>/templates/service.yaml` | Modelo de serviço |
{: caption="Tabela 9. Conteúdos de um diretório ./chart/<projectname>/ do app Java Liberty gerado" caption-side="top"}

| Diretório `./manifests/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Serviço e implementação do & Kubernetes yaml |
{: caption="Tabela 10. Conteúdo de um diretório ./manifests/ do app Java Liberty gerado" caption-side="top"}
