---
copyright:
  years: 2015, 2018
lastupdated: "2018-10-05"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Python 应用程序文件
{: #python-project-files}

对于 Python 应用程序，以下信息列出了通常可在 {{site.data.keyword.Bluemix}} 中找到的内容。创建入门模板工具包时，会创建这些文件。如果要迁移应用程序以在 {{site.data.keyword.Bluemix_notm}} 中进行托管，您可能希望查看这些信息以避免潜在的冲突。
{:shortdesc}

下表列出了生成的 Python 应用程序中包含的常见目录和文件。

|根目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|requirements.txt|必需的 Python 软件包|
|setup.py|Python 安装程序脚本|
|cli-config.yml|CLI 配置选项|
|manifest.yml|Cloud Foundry 部署文件|
|Dockerfile|用于 `ibmcloud dev run`、`ibmcloud dev deploy` 和 `docker` 命令的 Dockerfile|
|`Dockerfile-tools`|用于 `ibmcloud dev build` 和 `ibmcloud dev test` 的 Dockerfile|
|LICENSE|许可证文件|
|README.md|应用程序描述|
{: caption="表 1. 生成的 Python 应用程序根目录的内容" caption-side="top"}

|`./public/` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|swagger.yml|用于描述 REST API 的 Swagger 规范|
|index.html|Web 应用程序的框架标记|
{: caption="表 2. 生成的 Python 应用程序 public 目录的内容" caption-side="top"}

|`./server/` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|`__init__.py`|将目录标记为 Python 软件包目录|
{: caption="表 3. 生成的 Python 应用程序 server 目录的内容" caption-side="top"}

|`./tests/` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|app_tests.py|Python 服务器测试用例|
{: caption="表 4. 生成的 Python 应用程序 tests 目录的内容" caption-side="top"}

|`./.bluemix/` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|container_build.sh|容器构建脚本|
|deploy.json|部署信息|
|kube_deploy.sh|Kubernetes 部署脚本|
|pipeline.yml|IBM Cloud 管道定义|
|toolchain.yml|IBM Cloud 工具链定义|
{: caption="表 5. 生成的 Python 应用程序 bluemix 目录的内容" caption-side="top"}

|`./chart/<projectname>/` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|`./chart/<projectname>/Chart.yaml`|Helm 图表|
|`./chart/<projectname>/values.yaml`|Helm 图表值|
|`./chart/<projectname>/templates/deployment.yaml`|部署模板|
|`./chart/<projectname>/templates/service.yaml`|服务模板|
{: caption="表 6. 生成的 Python 应用程序 chart 目录的内容" caption-side="top"}
