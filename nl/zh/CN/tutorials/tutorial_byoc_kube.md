---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 将您自己的代码部署到 Kubernetes 集群
{: #tutorial-byoc-kube}

了解如何使用现有应用程序存储库在 {{site.data.keyword.cloud}} 中创建应用程序。您可以连接现有 DevOps 工具链或创建 DevOps 工具链，然后持续将应用程序交付到 Kubernetes 集群中的安全容器。本教程将帮助您设置持续集成 DevOps 管道，以便更改可自动构建并一路传播到 Kubernetes 集群中部署的应用程序。
{: shortdesc}

如果您已拥有源代码存储库，其中包含正常工作的后端应用程序的代码库，那么 {{site.data.keyword.cloud_notm}} 可帮助您将此资产组织到构成整个产品广度的所有资产的聚集视图中。使用 DevOps 工具链功能时，{{site.data.keyword.cloud_notm}} 可帮您快速入门并熟练运用可扩展的 DevOps 工作流程。本教程可帮助经验丰富的开发者或 DevOps 工程师获取和配置目标 {{site.data.keyword.cloud_notm}} Kubernetes 集群，以及配置和运行 DevOps 工具链，所有这一切都是在云最佳实践的指导下进行的。

_集群_是一组资源、工作程序节点、网络和存储设备，用于使应用程序保持高可用性。创建集群后，可以在容器中部署应用程序。
{: tip}

## 开始之前
{: #prereqs-byoc-kube}

* 创建应用程序。有关更多信息，请参阅[通过您自己的代码存储库创建应用程序](/docs/apps/tutorials/tutorial_byoc.html#tutorial-byoc)。
* 在 [{{site.data.keyword.cloud_notm}} 控制台 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}){: new_window} 中，单击**菜单**图标 ![“菜单”图标](../../icons/icon_hamburger.svg)，然后选择**容器**以[配置 Kubernetes 集群](/docs/containers/container_index.html#container_index)。
* 要确认应用程序是否在 Docker 中运行，请运行以下命令：
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* 然后，转至您的 URL，例如 `http://localhost/springboothelloworld/sayhello`。按 Ctrl+C 键可停止 Docker 运行。

## 向应用程序添加资源（可选）
{: #resources-byoc-kube}

将服务资源添加到应用程序，然后 {{site.data.keyword.cloud_notm}} 会为您创建服务。对于不同类型的服务，供应过程可能会不同。例如，数据库服务会创建数据库，移动应用程序的推送通知服务会生成配置信息。{{site.data.keyword.cloud_notm}} 通过使用服务实例来为您的应用程序提供服务的资源。一个服务实例可在多个 Web 应用程序之间共享。

此过程会供应服务实例，创建资源密钥（凭证），并将其绑定到应用程序。有关更多信息，请参阅[向应用程序添加服务](/docs/apps/reqnsi.html#add-resource)。

将服务资源添加到应用程序后，您必须将服务的凭证复制到部署环境。有关更多信息，请参阅[向 Kubernetes 环境添加凭证](/docs/apps/creds_kube.html#add_credentials)。

## 准备应用程序以进行部署
{: #deploy-byoc-kube}

在此步骤中，您将 DevOps 工具链连接到应用程序，并将其配置为部署到 {{site.data.keyword.cloud_notm}} Kubernetes 服务中托管的 Kubernetes 集群。

DevOps 工具链足够灵活，允许对 shell 脚本执行的任意阶段进行受管执行。换言之，您可以使用 DevOps 工具链执行几乎任何操作。本部分的范围侧重于在 Kubernetes 集群上部署应用程序，但同时应记住未来针对扩展的 DevOps 和云最佳实践将需要执行哪些措施。

在应用程序、工具链和存储库之间建立链接是迈向组织产品资产的一步。此步骤还可帮助集中了解源存储库与 DevOps 工作流程、运行中应用程序实例以及所有部署目标上的相依服务。

在“连接工具链”页面上，您有以下若干选项：

* 将应用程序连接到现有工具链。
* 将应用程序连接到不包含存储库的现有工具链。然后，日后将该工具链连接到存储库。
* 将应用程序连接到新的工具链。

### 将应用程序连接到现有工具链
{: #connect_toolchain_repo}

如果您有一个或多个 DevOps 工具链已连接到您在应用程序创建期间指定的 Git 存储库，那么这些工具链会显示在**包含存储库**表中。工具链必须配置为从您在应用程序中定义的同一个存储库中检索源。您很可能希望选择其中一个工具链来连接到应用程序。

### 将应用程序连接到不包含存储库的现有工具链
{: #connect_toolchain_notrepo}

如果您有一个或多个 DevOps 工具链已与您的帐户相关联，但未连接到您在应用程序创建期间指定的 Git 存储库，那么这些工具链会显示在**不包含您的存储库**表中。您可以选择其中一个工具链并将其连接到应用程序，但还必须手动将存储库添加到该工具链。

有关将存储库添加到工具链的更多信息，请参阅：

 * [配置 Git Repos and Issue Tracking](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [配置 GitHub](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [配置 GitLab](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### 将应用程序连接到新的工具链
{: #toolchain-byoc-kube-create}

如果要对 DevOps 工具链创建有完全控制权，而不更改代码存储库，请从头开始创建工具链。您还可以创建所有集成来构建应用程序，并将其部署到 Kubernetes 集群。 

1. 在“创建工具链”页面上，单击**构建您自己的工具链**模板。
2. 输入工具链的名称，选择区域和资源组（缺省值），然后单击**创建**。

选择通过新应用程序创建工具链时，会在浏览器的新选项卡中打开 DevOps 仪表板中的[创建工具链](https://{DomainName}/devops/create)页面。在该选项卡中创建并配置工具链后，必须返回到应用程序中的“连接工具链”页面，然后刷新该页面。
{:tip}

如果您不希望从头开始创建 DevOps 工具链，可以使用 [`ibmcloud dev enable` 命令](/docs/cli/idt/commands.html#enable)对现有代码进行云启用。此命令会生成一个 DevOps 工具链模板，您可以将其检入存储库中。然后，将该模板用作 DevOps 工具链创建的内容的指令集。有关更多信息，请参阅 [CLI 文档](/docs/apps/create-deploy-cli.html#byoc-cli)。

## 添加 GitHub 集成
{: #github-byoc-kube}

将 DevOps 工具链配置为集成 GitHub 存储库以允许工具链在存储库中设置 Webhook，以便该存储库中的拉取请求和代码推送操作向工具链发送 POST 操作。 

1. 在 DevOps 工具链模板中，单击**添加工具**。
2. 如果存储库位于公共 GitHub 或企业 GitHub 上，那么选择 **GitHub**。
3. 选择或输入 GitHub 服务器 URL。
4. 可能会显示`在 GitHub 上未授权`消息。如果显示了该消息，请单击**授权**。接下来，在“授权 IBM Cloud 工具链”页面上，单击**授权 IBM Cloud**，然后输入 GitHub 密码。
5. 在“配置集成”页面上，为存储库类型选择**现有**，以便 DevOps 工具链将存储库配置为使用 Webhook，而不对存储库进行任何派生或复制。
6. 输入存储库 URL，例如 `https://github.com/yourrepo/spring-boot-hello-world`。
7. 片刻之后，系统可能会提示您授权 GitHub 授予 DevOps 工具链许可权，以使用 GitHub ReST API 将存储库配置为使用触发工具链所需的 Webhook。
8.  单击**创建集成**。

您可以从存储库设置查看新的 Webhook。

## 添加 Delivery Pipeline
{: #pipeline-byoc-kube}

1. 单击**添加工具**。
2. 选择 **Delivery Pipeline**。
3. 针对管道名称输入 `Continuous Integration`，然后单击**创建集成**。

## 配置管道阶段
{: #pipelineconfig-byoc-kube}

将管道阶段配置为将输入（GitHub 存储库内容）定向到正确的目标。本教程假定您具有的 GitHub 存储库可生成正常工作的 Docker 映像，并且正在使用 IBM Containers Kubernetes 集群，因此您可创建包含输入、shell 脚本和输出的管道阶段以实现此目标。

1. 配置 `build and publish` 管道阶段。
  1. 选择已创建的 Delivery Pipeline，然后单击**添加阶段**。
  2. 单击**输入**选项卡，然后填写相关字段，如下所示：
    * 针对阶段名称输入 `build and publish Docker image`。
    * 针对输入类型选择 **Git 存储库**。
    * 选择 GitHub 存储库。
    * 选择用于持续集成的分支。
  3.  单击**作业**选择卡，然后单击**添加作业“+”**，并填写相关字段，如下所示：
    * 针对作业类型选择**构建**。
    * 针对名称输入 `build and publish`。
    * 针对构建器类型选择 **Container Registry**。
    * 选择 Kubernetes 集群所在的区域。
    * 选择**输入现有 API 密钥**。如果您没有 API 密钥，请参阅[创建 API 密钥](/docs/iam/userid_keys.html#creating-an-api-key)。 
    * 输入容器注册表名称空间，可通过单击**菜单**图标 ![“菜单”图标](../../icons/icon_hamburger.svg)，然后选择**容器** > **注册表** > **名称空间**找到该值。
    * 针对 Docker 映像名称，输入 `continuous`，因为此管道构建阶段用于存储库持续集成分支的持续构建。
    * 通过在第一个 `#!/bin/bash` 行之后添加一行或多行来编辑构建脚本。例如，对于使用 Maven 构建的存储库，可添加类似于以下示例的若干行：

      ```bash
      export JAVA_HOME=/opt/IBM/java8
      # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
      export MAVEN_OPTS="-  
      Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
      mvn -B clean verify
      ```
      {: codeblock}
  4. 单击**保存**。 
2. 通过单击**播放**图标，直至构建成功，以测试 `build and publish` 管道阶段。绿色阶段指示构建成功。 
3. 配置 `deploy to cluster` 管道阶段，以将 Docker 映像部署到 Kubernetes 集群。 
  1. 在 Delivery Pipeline 页面上，单击**添加阶段**。
  2. 单击**输入**选项卡，然后填写相关字段，如下所示：
    * 针对名称输入 `deploy to cluster`。
    * 针对输入类型选择**构建工件**。
    * 针对阶段选择 **Build & Publish Docker Image**。
    * 针对作业选择 **Build & Publish**。
    * 因为这是您的持续集成管道，请接受阶段触发器的缺省选项。
  3. 单击**作业**选择卡，然后单击**添加作业“+”**，并填写相关字段，如下所示：
    * 针对名称输入 `deploy to continuous integration cluster`。
    * 针对部署程序类型选择 **Kubernetes**。
    * 选择 Kubernetes 集群所在的区域。
    * 输入现有 API 密钥。 
  4. 单击**保存**。
4. 通过单击**播放**图标，直至构建成功，以测试 `deploy to cluster` 管道阶段。绿色阶段指示构建成功。

## 验证应用程序是否正在运行
{: #verify-byoc-kube}

应用程序部署完成后，Delivery Pipeline 或命令行会指示您前往应用程序的 URL。

1. 在 DevOps 工具链中，单击 **Delivery Pipeline**，然后选择 **Deploy 阶段**。
2. 单击**查看日志和历史记录**。
3. 在日志文件中，查找应用程序 URL：

    在日志文件末尾，搜索 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在浏览器中转至该 URL。如果应用程序正在运行，那么将显示包含 `Congratulations` 或 `{"status":"UP"}` 的消息。

如果使用的是命令行，请运行 [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) 命令来查看应用程序的 URL。然后，在浏览器中转至该 URL。
