---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 在 {{site.data.keyword.containerlong_notm}} 上部署 Mendix 应用程序
{: #deploy-mendix-kube}

缺省情况下，会使用评估方式对部署目标为 {{site.data.keyword.containerlong}} 的 Mendix 应用程序进行设置。在评估方式下，您可以快速地开始构建应用程序并将其部署到云，但不能配置数据持久性或设置高级 Kubernetes 配置。本教程会介绍如何使用 {{site.data.keyword.cos_full_notm}} 服务在 Kubernetes 中设置持久存储卷，从而指导您完成生产环境的配置。
{: shortdesc}

## 开始之前
{: #prereqs-mendix-kube}

- 创建 Mendix 应用程序。有关更多信息，请参阅[创建 Mendix 应用程序](/docs/apps/tutorials/tutorial_mendix_getting_started.html#create-mendix)。
- 安装 [{{site.data.keyword.dev_cli_notm}} 命令行界面 (CLI)](/docs/cli/index.html#overview)，其中包含 {{site.data.keyword.containershort_notm}} CLI。
- 登录到 `ibmcloud` CLI，然后配置 `kubectl` 以便[访问 Kubernetes 集群](/docs/containers/cs_tutorials.html#cs_cluster_tutorial_lesson3)。

## 创建 Cloud Object Storage 服务实例
{: #cos-mendix-kube}

首先，打开应用程序的详细信息页面，然后完成以下步骤：
1. 单击**添加资源**。
2. 选择**存储**，然后单击**下一步**。
3. 接下来，选择 **Cloud Object Storage** 选项，然后单击**下一步**。
4. 此时将显示 {{site.data.keyword.cos_full_notm}} 实例的价格套餐。选择最适合您需求的价格套餐，然后单击**创建**来创建 {{site.data.keyword.cos_full_notm}} 服务实例，以供您的 Mendix 应用程序使用。

  如果想要使用 {{site.data.keyword.cos_full_notm}} 服务的现有实例，请单击**添加资源**，然后选择现有实例，以供您的应用程序使用。
  {: tip}

## 创建存储区
{: #storage-bucket-mendix-kube}

将 {{site.data.keyword.cos_full_notm}} 服务实例与 Mendix 应用程序相关联后，必须创建一个用于保存数据的存储区。要创建存储区，请单击 {{site.data.keyword.cos_full_notm}} 实例的 **...**，然后选择**打开仪表板**。  

{{site.data.keyword.cos_full_notm}} 服务仪表板会在新窗口中打开。在**存储区**选项卡上，单击**创建存储区**，然后按照相应步骤，使用唯一名称来创建存储区。对于本教程，请创建一个名为 `my-mendix-bucket` 的存储区。

## 配置持久存储
{: #kube-storage-mendix}

接下来，按照[在 {{site.data.keyword.cos_full_notm}} 上存储数据](/docs/containers/cs_storage_cos.html#object_storage)文档中的说明来执行操作。在 Kubernetes 集群中创建 `PersistentVolumeClaim` 和 `PersistentVolume`，以供集群内作为 Mendix 应用程序一部分运行的 PostGres 数据库实例来使用。请确保使用上一步创建的 `my-mendix-bucket` 存储区来创建 `PersistentVolumeClaim`，然后查看 `PersistentVolumeClaim` 名称，以便在下一步中使用。

## 编辑 `postgres-deployment.yaml` 文件
{: #postgres-deploy-mendix}

为 Kubernetes 集群配置持久卷后，下一步是修改在集群内运行的 PostGres 数据库部署。首先，必须编辑 Git 存储库中作为 IBM DevOps 工具链集成步骤一部分创建的文件。要查找 Git 存储库，请返回到应用程序详细信息页面，然后单击**部署详细信息**磁贴中的 Git URL 链接。  

您可以将 Git 存储库克隆到本地计算机，也可以通过在线编辑器来进行以下更改。打开 `chart/{app name}/templates/postgres-deployment.yaml` 文件（将 `{app name}` 替换为您 Mendix 应用程序的名称）。缺省情况下，该文件没有任何现存的 `volumeMount` 或 `volumes` 条目，因此所有数据都存储在运行中部署 pod 的内存中。您必须将 `volumeMount` 和 `volumes` 条目都添加到 Kubernetes `deployment.yaml` 文件中，您的数据才能保存到 {{site.data.keyword.cos_full_notm}} 存储区中，即便 pod 重新启动，也不会丢失。 

请参阅以下 `postgres-deployment.yaml` 样本，其中包含 `volumeMount` 和 `volumes` 条目。  
```yaml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: "{appname}-postgres"
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: "{appname}-postgres"
    spec:
      containers:
        - name: "{appname}-postgres"
          image: postgres:10.1
          ports:
            - containerPort: 5432
          env:
            - name: POSTGRES_DB
              value: db0
            - name: POSTGRES_USER
              value: mendix
            - name: POSTGRES_PASSWORD
              value: mendix
          volumeMounts:
            - mountPath: "/var/lib/postgresql/data"
              name: "mendix-data"
      volumes:
        - name: mendix-data
          persistentVolumeClaim:
            claimName: {pvc-name}
```

确保将 `{pvc-name}` 替换为上一步中的 `PersistentVolumeClaim` 名称，并注意不要覆盖您的应用程序名称，因为该名称已在 Git 存储库内的文件中进行设置。然后，将您的更改提交回 Git 存储库。

## 重新部署
{: #redeploy-mendix-kube}

将 `postgres-deployment.yaml` 文件更改提交回存储库后，会自动触发新的 DevOps 管道执行程序。不过，这样会重新部署缺省应用程序。您必须重新部署最新版 Mendix 应用程序，您要部署的最新版应用程序才能具有最新的持久卷更改。

要进行重新部署，请转至应用程序详细信息页面，然后单击**部署详细信息**磁贴内的**部署应用程序**。如果部署在 DevOps 工具链内部失败，并且错误指示找不到应用程序的 `.mda` 文件，那么必须重新从 Mendix 导出应用程序。您可以从 Mendix Modeler 桌面应用程序中导出，也可以单击**在 Mendix 上编辑**来导出。接下来，在 Mendix Web 界面内，转至**环境**部分，单击**从团队服务器创建包**，然后执行相应的步骤。从 Mendix 导出应用程序后，返回到应用程序的详细信息页面，再次单击**部署应用程序**。最后导出的应用程序将通过 {{site.data.keyword.cloud}} DevOps 工具链部署到 Kubernetes 集群中。部署成功完成后，即可在生产环境中使用您的应用程序。

## 验证应用程序是否正在运行
{: #verify-mendix-kube}

应用程序部署完成后，Delivery Pipeline 或命令行会指示您前往应用程序的 URL。

1. 在 DevOps 工具链中，单击 **Delivery Pipeline**，然后选择 **Deploy 阶段**。
2. 单击**查看日志和历史记录**。
3. 在日志文件中，查找应用程序 URL：

    在日志文件末尾，搜索 `urls` 或 `view`。例如，您可能会在日志文件中看到类似于以下内容的行：`urls: my-app-devhost.cloud.ibm.com` 或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在浏览器中转至该 URL。如果应用程序正在运行，那么将显示包含 `Congratulations` 或 `{"status":"UP"}` 的消息。

如果使用的是命令行，请运行 [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) 命令来查看应用程序的 URL。然后，在浏览器中转至该 URL。

## 其他信息
{: #more-info-mendix-kube}

有关在 Kubernetes 环境中运行 Mendix 应用程序的更多架构详细信息，请查看 Mendix 用户文档的 [Run Mendix on Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes) 部分。
