---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 将您自己的代码部署到 Kubernetes 集群
{: #tutorial}

了解如何使用现有应用程序存储库在 {{site.data.keyword.cloud}} 中创建应用程序。您可以连接现有 DevOps 工具链或创建 DevOps 工具链，然后持续将应用程序交付到 Kubernetes 集群中的安全容器。本教程将帮助您设置持续集成 DevOps 管道，以便更改可自动构建并一路传播到 Kubernetes 集群中部署的应用程序。
{: shortdesc}

如果您已拥有源代码存储库，其中包含正常工作的后端应用程序的代码库，那么 {{site.data.keyword.cloud_notm}} 可帮助您将此资产组织到构成整个产品广度的所有资产的聚集视图中。使用 DevOps 工具链功能时，{{site.data.keyword.cloud_notm}} 可帮您快速入门和熟悉运用可扩展的 DevOps 工作流程。本教程可帮助经验丰富的开发者或 DevOps 工程师获取和配置目标 {{site.data.keyword.cloud_notm}} Kubernetes 集群，以及配置和运行 DevOps 工具链，所有这一切都是在云最佳实践的指导下进行的。

_集群_是一组资源、工作程序节点、网络和存储设备，用于使应用程序保持高可用性。创建集群后，可以在容器中部署应用程序。
{: tip}

## 开始之前
{: #prereqs}

* 执行[通过您自己的代码存储库创建应用程序](/docs/apps/tutorials/tutorial_byoc.html)中的步骤以创建应用程序。
* 在 [{{site.data.keyword.cloud_notm}} 仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}){: new_window} 中，单击**菜单**图标 ![“菜单”图标](../../icons/icon_hamburger.svg)，然后选择**容器**以[配置 Kubernetes 集群](/docs/containers/container_index.html)。
* 要确认应用程序是否在 Docker 中运行，请运行以下命令：
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* 然后，访问 URL，例如 `http://localhost/springboothelloworld/sayhello`。   
按 `Ctrl+C` 键可停止 Docker 运行。

## 可选。向应用程序添加资源
{: #add_resources}

将服务资源添加到应用程序，然后 {{site.data.keyword.cloud_notm}} 会为您创建服务。对于不同类型的服务，供应过程可能会不同。例如，数据库服务会创建数据库，移动应用程序的推送通知服务会生成配置信息。{{site.data.keyword.cloud_notm}} 通过使用服务实例来为您的应用程序提供服务的资源。一个服务实例可在多个 Web 应用程序之间共享。

此过程会供应服务实例，创建资源密钥（凭证），并将其绑定到应用程序。有关更多信息，请参阅[向应用程序添加服务](/docs/apps/reqnsi.html)。

### 将服务凭证复制到环境

将服务资源添加到应用程序后，请注意，该服务的凭证会显示在**凭证**框中。您必须将凭证复制到部署环境。

有关将凭证复制到环境的更多信息，请参阅[向 Kubernetes 环境添加凭证](/docs/apps/creds_kube.html)。


## 使用 DevOps 工具链准备应用程序以进行部署
{: #connect_toolchain}

在此步骤中，您将 DevOps 工具链连接到应用程序，并将其配置为部署到 {{site.data.keyword.cloud_notm}} Kubernetes 服务中托管的 Kubernetes 集群。

DevOps 工具链足够灵活，允许对 shell 脚本执行的任意阶段进行受管执行。换句话说，您可以使用 DevOps 工具链执行几乎任何操作。本部分的范围侧重于在 Kubernetes 集群上部署应用程序，但同时应记住未来针对扩展的 DevOps 和云最佳实践将需要执行哪些措施。

在应用程序、工具链和存储库之间建立链接是迈向组织产品资产的一步。此步骤还可帮助集中了解源存储库与 DevOps 工作流程、运行中应用程序实例以及所有部署目标上的相依服务。

在“连接工具链”页面中，您有以下若干选项：

* 将应用程序连接到现有工具链。
* 将应用程序连接到不包含存储库的现有工具链。然后，日后将该工具链连接到存储库。
* 将应用程序连接到新的工具链。

### 将应用程序连接到现有工具链
{: #connect_toolchain_repo}

如果您有一个或多个 DevOps 工具链已连接到您在应用程序创建期间指定的 Git 存储库，那么这些工具链会显示在**包含存储库**表中。工具链必须配置为从您在应用程序中定义的同一个存储库中检索源。您很可能希望选择其中一个工具链来连接到应用程序。

### 将应用程序连接到不包含存储库的现有工具链
{: #connect_toolchain_notrepo}

如果您有一个或多个 DevOps 工具链已与您的帐户相关联，但未连接到您在应用程序创建期间指定的 Git 存储库，那么这些工具链会显示在标注为**不包含您的存储库**的表中。您可以选择其中一个工具链并将其连接到应用程序，但还必须手动将存储库添加到该工具链。

有关将存储库添加到工具链的更多信息，请参阅：

 * [配置 Git Repos and Issue Tracking](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [配置 GitHub](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [配置 GitLab](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### 将应用程序连接到新的工具链
{: #create_toolchain}

您可以通过以下选项将应用程序连接到新的工具链：
* 如果您不希望从头开始创建 DevOps 工具链，可以使用 [`ibmcloud dev enable` 命令](/docs/cli/idt/commands.html#enable)对现有代码进行云启用。此命令会生成一个 DevOps 工具链模板，您可以将其检入存储库中。然后，将该模板用作 DevOps 工具链创建的内容的指令集。有关更多信息，请参阅 [CLI 文档](/docs/apps/create-deploy-cli.html#byoc)。
* 在控制台中从头开始创建 DevOps 工具链。如果要对 DevOps 工具链创建有完全控制权，而不更改代码存储库，请从头开始创建工具链。有关更多信息，请参阅[从头开始创建 DevOps 工具链](#create_toolchain_scratch)。

#### 从头开始创建 DevOps 工具链
{: #create_toolchain_scratch}

如果要从头开始创建工具链并将其连接到应用程序，请完成以下步骤。您还可以创建所有集成来构建应用程序，并将其部署到 Kubernetes 集群。DevOps 工具链功能提供了模板，而这些步骤说明了如何从头开始设置 DevOps 工具链。

选择通过新应用程序创建工具链后，会在浏览器的新选项卡中打开 [DevOps 仪表板](https://{DomainName}/devops/)中的[创建工具链](https://{DomainName}/devops/create)页面。在该选项卡中创建并配置工具链后，必须返回到应用程序中的**连接工具链**页面，然后刷新该页面。
{:tip}

1. 在**创建工具链**页面上，单击**构建您自己的工具链**模板。
2. 在**构建您自己的工具链**页面上，输入工具链的名称，选择区域和资源组（缺省值），然后单击**创建**。

这将创建不包含预配置工具或集成的空工具链。通过完成其余步骤，继续配置并测试新的工具链。

## 添加 GitHub 集成

您可以使用以下步骤为 DevOps 工具链配置 GitHub 集成：

1. 在 DevOps 工具链模板中，单击**添加工具**。
2. 选择 **GitHub**（如果存储库确实位于公共 GitHub 或企业 GitHub 上）。
3. 在 GitHub 的**配置集成**页面上，完成以下步骤：
  * 选择（或输入）**GitHub 服务器** URL。
  * 如果看到“在 GitHub 上未授权”消息，请单击**授权**。接下来，在**授权 IBM Cloud 工具链**页面上，单击**授权 IBM Cloud**。然后，输入 GitHub 密码。
  * 在**配置集成**页面上，为**存储库类型**选择**现有**，以便 DevOps 工具链将存储库配置为使用 Webhook，而_不_对存储库进行任何派生或复制。
  * 输入**存储库 URL**。（例如，`https://github.com/yourrepo/spring-boot-hello-world`）。
  * 稍等片刻，系统可能会提示您授权 GitHub 授予 DevOps 工具链许可权，以使用 GitHub ReST API 将存储库配置为使用触发工具链所需的 Webhook。
  * 单击**创建集成**。

您已配置此 DevOps 工具链，其中包含 GitHub 存储库的集成。执行此操作将允许工具链在存储库中设置 Webhook，以便该存储库中的拉取请求和代码推送操作会触发对工具链的 POST 操作。您可以检查存储库的设置来查看新的 Webhook。

## 添加 Delivery Pipeline 以构建、测试和部署应用程序

Delivery Pipeline 是执行工作的位置。

1. 单击**添加工具**。
2. 选择 **Delivery Pipeline**。
3. 在 Delivery Pipeline 的**配置集成**页面上，完成以下步骤：
 * 对于管道名称，输入“Continuous Integration”。
 * 单击**创建集成**。

您已创建空的交付管道。接下来，可定义管道阶段以将输入（GitHub 存储库内容）定向到其目标。本教程假定您具有的 GitHub 存储库可生成正常工作的 Docker 映像并且是将 IBM Containers Kubernetes 集群设定为目标，因此您可创建包含输入、shell 脚本和输出的管道各阶段以实现此目标。

### 配置“Build and Publish”管道阶段

1. 单击已创建的 Delivery Pipeline。
2. 在 Delivery Pipeline 页面上，单击**添加阶段**。
3. 在**阶段配置**页面的**输入**选项卡上，填写相关字段，如下所示：
  * 对于阶段名称，输入 **Build & Publish Docker Image**。
  * **输入类型**：选择 **Git 存储库**。
  * **Git 存储库**：选择您的 GitHub 存储库。
  * **分支**：选择用于持续集成的分支。
4. 单击**作业**选项卡，然后填写相关字段，如下所示：
  * 单击**添加作业“+”**图标，然后选择**构建**作为作业类型。
  * 输入名称，例如 **Build & Publish**。
  * **构建器类型**：选择**容器注册表**。
  * **IBM Cloud 区域**：选择 Kubernetes 集群所在的区域。
  * **API 密钥**：选择**输入现有 API 密钥**。如果您没有密钥或不知道 API 密钥，那么可以通过打开单独的浏览器窗口并浏览至**管理** > **安全性** > **平台 API 密钥**来[获取 API 密钥](https://{DomainName}/iam/#/apikeys)。请确保将此密钥保存在安全的位置。
  * **帐户名称**：输入 API 密钥时，此字段会自动填写。
  * **容器注册表名称空间**：输入[容器注册表名称空间](https://{DomainName}/containers-kubernetes/registry/namespaces)（可以通过单击**菜单**图标 ![“菜单”图标](../../icons/icon_hamburger.svg)，然后选择**容器** > **注册表** > **名称空间**来找到该值）。
  * **Docker 映像名称**：输入 **continuous**，因为此管道构建阶段用于存储库持续集成分支的持续构建。
  * **构建脚本**：请注意 shell 脚本。此脚本缺少针对_您的_存储库的应用程序构建指示信息。您需要在第一个 `#!/bin/bash` 行之后添加一行或多行。例如，对于使用 Maven 构建的存储库，可添加类似于以下示例的若干行：

    ```bash
    export JAVA_HOME=/opt/IBM/java8
    # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
    export MAVEN_OPTS="-Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
    mvn -B clean verify
    ```
    {: codeblock}
5. 单击**保存**。您的“Build and Publish”管道阶段现在会显示在工具链中。

### 测试“Build and Publish”管道阶段

单击**播放**图标，直至构建成功。该阶段变为绿色时，您即知道该阶段工作正常，并且脚本输出会确认您的预期。此阶段的目标是将 Docker 映像发布到映像注册表。如果脚本没有显示足够的内容让您相信该阶段工作正常，那么可以通过单击**菜单**图标 ![“菜单”图标](../../icons/icon_hamburger.svg)，然后选择**容器** > **注册表** > **专用存储库**来查看映像注册表以确认发布。然后，确认是否列出了以 `/continuous` 名称结尾的存储库。（请记住，这是映像名称。）

### 配置“Deploy to Cluster”管道阶段

到目前为止，您已将 Docker 映像发布到专用 Docker 映像注册表。现在该创建一个阶段，用于将该映像部署到 Kubernetes 集群。

1. 在 Delivery Pipeline 页面上，单击**添加阶段**。
2. 在**阶段配置**页面的**输入**选项卡上，填写相关字段，如下所示：
  * **名称**：输入 **Deploy**。
  * **输入类型**：选择**构建工件**。
  * **阶段**：选择 **Build & Publish Docker Image**。
  * **作业**：选择 **Build & Publish**。
  * **阶段触发器**：这是您的持续集成管道，因此请选择缺省触发器**运行作业，然后上一个阶段即完成**。
3. 单击**作业**选项卡，然后填写相关字段，如下所示：
  * 单击**添加作业“+”**图标，然后选择**部署**作为作业类型。
  * 输入名称，例如 **Deploy to Continuous Integration Cluster**。
  * **部署程序类型**：选择 **Kubernetes**。
  * **IBM Cloud 区域**：选择 Kubernetes 集群所在的区域。
  * **API 密钥**：选择**输入现有 API 密钥**。如果您没有密钥或不知道 API 密钥，那么可以通过打开单独的浏览器窗口并浏览至**管理** > **安全性** > **平台 API 密钥**来[获取 API 密钥](https://{DomainName}/iam/#/apikeys)。请确保将此密钥保存在安全的位置。
  * 接受其余的缺省设置。
4. 单击**保存**。您的“Deploy”管道阶段现在会显示在工具链中。

### 测试“Deploy to Cluster”管道阶段

单击**播放**图标，直至构建成功。该阶段变为绿色时，您即知道该阶段工作正常，并且脚本输出会确认您的预期。您可以查看该阶段的日志。在日志末尾附近，找到运行中应用程序的可单击链接。但是，只有_您_才知道您的应用程序的上下文根和路径。请附加正确的路径以确认它是否在运行。
