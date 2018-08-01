---

copyright:
  years: 2018
lastupdated: "2018-07-23"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 将容器与 Kubernetes 配合使用
{: #containers}

通过在 Kubernetes 集群中运行的 Docker 容器中部署高可用性应用程序，开始使用 {{site.data.keyword.containershort}}。使用 Git 来管理团队开发，然后使用 DevOps 工具链来管理如何将应用程序部署到 Kubernetes。
{: shortdesc}

容器是打包应用程序及其所有依赖项的标准方法，以便您可以在环境之间无缝移动应用程序。与虚拟机不同的是，容器并不捆绑操作系统。容器内仅打包应用程序代码、运行时、系统工具、库和设置。容器相比虚拟机更轻巧、可移植性更强、更高效。

请参阅 [{{site.data.keyword.containershort_notm}} 入门](/docs/containers/container_index.html#container_index)以了解有关该服务的更多信息。

## 配置部署
{: #config-deploy}

创建后端或 Web 服务应用程序后，可以将其部署到使用 Kubernetes 环境的 {{site.data.keyword.containershort_notm}} 服务。

1. 通过设置自动化云管道，将应用程序部署到云上。
2. 单击**部署到云**。
3. 选择 Kubernetes 作为目标。如果您还没有集群，那么需要[创建集群 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/containers-kubernetes/catalog/cluster/create){:new_window}。
4. 部署完成后，通过从 Delivery Pipeline 的部署阶段获取日志中的 URL，检查您的在线应用程序是否已在云中。最后一个带端口的 IP 地址是应用程序的新主页，例如 169.60.133.124:32355。

## 绑定服务
{: #bind-services}

创建工具链后，与应用程序关联的服务将使用 Kubernetes 私钥绑定到 Kubernetes 集群。私钥用于管理运行的应用程序外部的服务凭证。应用程序会读取私钥，然后检索开始运行所需的值。通过绑定服务，您可以将应用程序部署到可能正在使用生产级别 {{site.data.keyword.cloud_notm}} 服务实例的其他 Kubernetes 环境。

![查看工具链](images/kubesecrets.png)

如果删除了服务或私钥，您需要重新手动绑定这些项，或者删除并重新创建工具链。
{: tip}

有关更多信息，请参阅[私钥 ![外部链接图标](../../icons/launch-glyph.svg " 外部链接图标")](https://kubernetes.io/docs/concepts/configuration/secret/){:new_window}。

## 开始开发
{: #dev}

1. 查看工具链中新的在线 Git 存储库，然后开始使用代码。要查看工具链，请单击**查看工具链**。
2. 通过将创建代码所在的 Git 存储库克隆到本地环境来访问该存储库。
3. 使用您最喜欢的 IDE 打开项目。

## 使用工具链进行构建和部署
{: #bulid-deploy-tc}

工具链包含构建阶段和部署阶段。

![查看工具链](images/deploytoolchain.png)

### 构建阶段
{: #build-stage}
在 Git 存储库上运行 `git push` 时，会触发构建阶段。管道中的该阶段会触发 Docker 映像构建，并将该映像放入容器注册表中。

有关更多信息，请参阅 [IBM Cloud Container Registry 入门](/docs/services/Registry/index.html#index)。

### 部署阶段
{: #deploy-stage}

部署阶段从 {{site.data.keyword.registryshort_notm}} 中检索最新映像，然后使用 Helm 图表将其部署到 Kubernetes 集群中。部署到云时，Helm 图表已添加到应用程序中。通过 Helm 图表，可以轻松管理已打包容器映像的部署步骤。

有关更多信息，请参阅[图表 ![外部链接图标](../../icons/launch-glyph.svg " 外部链接图标")](https://docs.helm.sh/developing_charts/){:new_window}。

{{site.data.keyword.cloud_notm}} 支持若干[预配置的 Helm 图表 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/containers-kubernetes/solutions/helm-charts){:new_window}。

## 检查应用程序安全性
{: #sec}

{{site.data.keyword.containershort_notm}} 支持扫描打包的容器映像以查找安全漏洞。安全扫描对于支持企业级应用程序至关重要。

查看容器[映像存储库 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/containers-kubernetes/registry/private){:new_window}，以检查是否有潜在的安全漏洞。
