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

# Java 应用程序文件
{: #java-project-files}

对于 Java 应用程序，以下信息列出了通常可在 {{site.data.keyword.Bluemix}} 中找到的内容。创建入门模板工具包时，会创建这些文件。如果要迁移应用程序以在 {{site.data.keyword.Bluemix_notm}} 中进行托管，您可能希望查看这些信息以避免潜在的冲突。
{:shortdesc}

## Spring
{: #spring-project-files}

下表列出了生成的 Java Spring 应用程序中包含的目录和文件。

| `./` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|pom.xml|maven pom 文件|
|cli-config.yml|CLI 配置选项|
|manifest.yml|Cloud Foundry 部署文件|
|Dockerfile|用于 `ibmcloud dev run`、`ibmcloud dev deploy` 和 `docker` 命令的 Dockerfile|
|Dockerfile-tools|用于 `ibmcloud dev build` 和 `ibmcloud dev test` 的 Dockerfile|
|LICENSE|许可证文件|
|README.md|应用程序描述|
{: caption="表 1. 生成的 Java Spring 应用程序根目录的内容" caption-side="top"}

|`./src/main/java/` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|`./src/main/test/application/SBApplication.java`|主 Spring 应用程序|
|`./src/main/test/application/HealthEndpointTest.java`|测试|
|`./src/main/java/application/rest/HealthApplication.java`|运行状况端点|
|`./src/main/java/application/rest/v1/Example.java`|示例代码|
|`./src/main/java/resources/application-local.properties`|Spring 属性|
{: caption="表 2. 生成的 Java Spring 应用程序 /java/ 目录的内容" caption-side="top"}

|`./.bluemix/` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|container_build.sh|容器构建脚本|
|deploy.json|部署信息|
|kube_deploy.sh|Kubernetes 部署脚本|
|pipeline.yml|IBM Cloud 管道定义|
|toolchain.yml|IBM Cloud 工具链定义|
{: caption="表 3. 生成的 Java Spring 应用程序 ./.bluemix/ 目录的内容" caption-side="top"}

| `./chart/<projectname>/` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml`|Helm 图表|
| `./chart/<projectname>/values.yaml`|Helm 图表值|
| `./chart/<projectname>/templates/deployment.yaml`|部署模板|
| `./chart/<projectname>/templates/hpa.yaml`|HPA 模板|
| `./chart/<projectname>/templates/service.yaml`|服务模板|
{: caption="表 4. 生成的 Java Spring 应用程序 ./chart/<projectname>/templates/ 目录的内容" caption-side="top"}

| `./manifests/` 目录 |描述
|
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml |Kubernetes 服务和部署 yaml|
{: caption="表 5. 生成的 Java Spring 应用程序 ./manifests/ 目录的内容" caption-side="top"}

## Liberty
{: #liberty-project-files}

下表列出了生成的 Java Liberty 应用程序中包含的目录和文件。

| `./` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|pom.xml|maven pom 文件|
|cli-config.yml|CLI 配置选项|
|manifest.yml|Cloud Foundry 部署文件|
|Dockerfile|用于 `ibmcloud dev run`、`ibmcloud dev deploy` 和 `docker` 命令的 Dockerfile|
|`Dockerfile-tools`|用于 `ibmcloud dev build` 和 `ibmcloud dev test` 命令的 Dockerfile|
|LICENSE|许可证文件|
|README.md|应用程序描述|
{: caption="表 6. 生成的 Java Liberty 应用程序根目录的内容" caption-side="top"}

|`./src/main` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
|`./src/main/java/application/rest/HealthApplication.java`|运行状况端点|
|`./src/main/java/application/rest/v1/Example.java`|示例代码|
|`./src/main/liberty/config/jvm.options`|JVM 选项|
|`./src/main/liberty/config/jvmbx.options`|Java 度量值代理程序配置|
|`./src/main/liberty/config/server.env`|环境变量|
|`./src/main/liberty/config/server.xml`|服务器配置|
|`./src/main/webapp/WEB-INF/beans.xml`|CDI bean 配置|
|`./src/main/webapp/WEB-INF/ibm-web-ext.xml`|IBM Web 应用程序配置|
|`./src/main/test/it/HealthEndpointTest.java`|测试|
{: caption="表 7. 生成的 Java Liberty 应用程序 ./src/main/ 目录的内容" caption-side="top"}

| `./.bluemix/` 目录 |描述
|
|:------------------------------------------------|:------------------------------------------|
| container_build.sh |容器构建脚本|
| deploy.json |部署信息|
| kube_deploy.sh |Kubernetes 部署脚本|
| pipeline.yml |IBM Cloud 管道定义|
| toolchain.yml |IBM Cloud 工具链定义|
{: caption="表 8. 生成的 Java Liberty 应用程序 ./bluemix/ 目录的内容" caption-side="top"}

| `./chart/<projectname>/` 目录|描述
|
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` |Helm 图表|
| `./chart/<projectname>/values.yaml` |Helm 图表值|
| `./chart/<projectname>/templates/deployment.yaml` |部署模板|
| `./chart/<projectname>/templates/hpa.yaml` |HPA 模板|
| `./chart/<projectname>/templates/service.yaml` |服务模板|
{: caption="表 9. 生成的 Java Liberty 应用程序 ./chart/<projectname>/ 目录的内容" caption-side="top"}

| `./manifests/` 目录 |描述
|
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml |Kubernetes 服务和部署 yaml|
{: caption="表 10. 生成的 Java Liberty 应用程序 ./manifests/ 目录的内容" caption-side="top"}
