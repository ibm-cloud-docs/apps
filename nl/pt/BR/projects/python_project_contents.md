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

# Arquivos de apps Python
{: #python-project-files}

Para apps Python, as informações a seguir são um inventário do que você normalmente localiza no {{site.data.keyword.Bluemix}}. Ao criar um kit do iniciador, esses arquivos são criados para você. Se você estiver migrando um app para hospedar no {{site.data.keyword.Bluemix_notm}}, poderá desejar revisar essas informações para evitar possíveis conflitos.
{:shortdesc}

A tabela a seguir lista os diretórios e os arquivos comuns que estão incluídos em um app Python gerado.

| Diretório-raiz                                     | Descrição                       |
|:------------------------------------------------|:------------------------------------------|
| Requirements.txt | Pacotes Python necessários |
| Setup.py | Script do instalador do Python |
| cli-config.yml | Opções de configuração de CLI |
| manifest.yml | Arquivo de implementação do Cloud Foundry |
| Dockerfile | Dockerfile para comandos `ibmcloud dev run`, `ibmcloud dev deploy` e `docker` |
| Ferramentas do Dockerfile | Dockerfile para `ibmcloud dev build` e `ibmcloud dev test` |
| LICENÇA | Arquivo de licença |
| README.md | Descrição do app |
{: caption="Tabela 1. Conteúdo de um diretório-raiz do app Python gerado" caption-side="top"}

| Diretório `./public/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| Swagger.yml | Especificação do swagger para descrever APIs de REST |
| Index.html | Marcação da estrutura básica para aplicativos da web |
{: caption="Tabela 2. Conteúdo de um diretório público do app Python gerado" caption-side="top"}

| Diretório `./server/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| `__init__.py` | Marcas diretórios como diretórios do pacote Python |
{: caption="Tabela 3. Conteúdo de um diretório do servidor de app Python gerado" caption-side="top"}

| Diretório `./tests/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| App_tests.py | Casos de teste do servidor Python |
{: caption="Tabela 4. Conteúdo de um diretório de testes do app Python gerado" caption-side="top"}

| Diretório `./.bluemix/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de construção de contêiner |
| deploy.json | Informações de implementação |
| kube_deploy.sh | Script de implementação do Kubernetes |
| pipeline.yml | Definição de pipeline do IBM Cloud |
| toolchain.yml | Definição da cadeia de ferramentas do IBM Cloud |
{: caption="Tabela 5. Conteúdo de um diretório bluemix do app Python gerado" caption-side="top"}

| Diretório `./chart/<projectname>/` | Descrição |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Gráfico Helm |
| `./chart/<projectname>/values.yaml` | Valores do gráfico Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Modelo de implementação |
| `./chart/<projectname>/templates/service.yaml` | Modelo de serviço |
{: caption="Tabela 6. Conteúdo de um diretório de gráfico do app Python gerado" caption-side="top"}
