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

# Arquivos de apps Node.js
{: #node-project-files}

Para apps Node.js, as informações a seguir são um inventário do que você normalmente localiza no {{site.data.keyword.Bluemix}}. Ao criar um kit do iniciador, esses arquivos são criados para você. Se você estiver migrando um app para hospedar no {{site.data.keyword.Bluemix_notm}}, poderá desejar revisar essas informações para evitar possíveis conflitos. 
{:shortdesc}

A tabela a seguir lista os diretórios e os arquivos comuns que estão incluídos em um app Node.js gerado.

| Diretório-raiz                                     | Descrição                       |
|:------------------------------------------------|:------------------------------------------|
|`package.json | Arquivo de metadados |
|cli-config.yml | Opções de configuração de CLI |
|manifest.yml | Arquivo de implementação do Cloud Foundry |
|Dockerfile | Dockerfile para comandos `ibmcloud dev run`, `ibmcloud dev deploy` e `docker` |
|Ferramentas do Dockerfile | Dockerfile para `ibmcloud dev build` e `ibmcloud dev test` |
|Docker-compose.yml | Configuração de serviço de aplicativo para o Docker Compose |
|Webpack.config.js | Configuração do webpack para informações relacionadas à construção |
| LICENÇA | Arquivo de licença |
|README.md | Descrição do app |
{: caption="Tabela 1. Conteúdo de um diretório-raiz do app Node.js gerado" caption-side="top"}

| Diretório `./public/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| `./public/swagger.yml` | Especificação do swagger para descrever APIs de REST |
| `./public/index.html` | Marcação da estrutura básica para aplicativos da web |
|`./public/server/server.js` | Arquivo de implementação do servidor |
{: caption="Tabela 2. Conteúdo de um diretório público do app Node.js gerado" caption-side="top"}

| Diretório `./test/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| test-server.js | Teste de integração para o servidor Express |
{: caption="Tabela 3. Conteúdo de um diretório de teste do app Node.js gerado" caption-side="top"}

| Diretório `./.bluemix/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de construção de contêiner |
| deploy.json | Informações de implementação |
| kube_deploy.sh | Script de implementação do Kubernetes |
| pipeline.yml | Definição de pipeline do IBM Cloud |
| toolchain.yml | Definição da cadeia de ferramentas do IBM Cloud |
{: caption="Tabela 4. Conteúdo de um diretório bluemix do app Node.js gerado" caption-side="top"}

| Diretório `./chart/<projectname>/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Gráfico Helm |
| `./chart/<projectname>/values.yaml` | Valores do gráfico Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Modelo de implementação |
| `./chart/<projectname>/templates/service.yaml` | Modelo de serviço |
{: caption="Tabela 5. Conteúdo de um diretório de gráfico do app Node.js gerado" caption-side="top"}
