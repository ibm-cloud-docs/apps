---
copyright:

  years: 2018

lastupdated: "2018-11-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# 部署虚拟服务器
{: #vsi-deploy}

您可以使用 {{site.data.keyword.cloud}} [App Service ![外部链接图标](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} 将应用程序部署到多种类型的环境中，包括虚拟服务器实例。虚拟服务器实例会模拟裸机机器，是将内部部署工作负载移动到云上时常见的部署选择。
{: shortdesc}

与其他配置相比，虚拟服务器实例可以为所有工作负载类型提供更好的透明度、可预测性和自动化功能。与裸机服务器相结合，还可以创建出独特的工作负载组合。例如，可以使用运行基于 Debian Linux 的操作系统的裸机和 GPU 配置来创建高性能的数据库逻辑或机器学习。

供应和部署虚拟服务器实例的过程可能很复杂和耗时。使用 {{site.data.keyword.cloud_notm}} App Service，您就可以快速地启动和运行虚拟服务器实例了。

## 开始之前
{: #prereqs}

请升级到“现买现付”帐户。要使用虚拟实例，必须为经典基础架构启用 {{site.data.keyword.cloud_notm}} 帐户。要升级帐户，请转至控制台中的**管理** > **计费和使用情况** > **计费**。

**重要信息：**服务未绑定到虚拟服务器实例。您无法向虚拟服务器中的应用程序添加服务。

## 创建和部署应用程序
{: #create-deploy}

App Service 会为您供应虚拟服务器实例，装入包含您的应用程序的映像，创建 DevOps 工具链，并为您启动第一个部署周期。

1. [创建应用程序](index.html#createapp)。 
2. 在应用程序详细信息页面中，单击**部署到云**。
3. 选择**部署到虚拟服务器**以及运行服务器的区域。

## 部署过程的运作方式

要完成虚拟服务器部署过程，需要了解该过程所包含的几项关键技术（Terraform、管道启用和 API 密钥管理（Git 操作））以及工具链流程。 

### 通过 Terraform 部署

在动态创建的虚拟实例中，可以通过 [Terraform ![外部链接图标](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} 部署任何 App Service 入门模板工具包。Terraform 是一种开放式源代码“基础架构即代码”框架。 

### 启用管道部署

当您创建入门模板工具包来使用 {{site.data.keyword.cloud_notm}} [App Service ![外部链接图标](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} 时，系统会启用虚拟服务器实例。在创建应用程序后，可以选择要在何处部署应用程序。启用了入门模板工具包，以支持使用 Continuous Delivery 工具链进行部署。入门模板工具包可用于 Kubernetes、Cloud Foundry 以及 Virtual Server 实例。该工具链包含源代码存储库和部署管道。

虚拟服务器选项分阶段进行。首先，准备应用程序代码并将其存储在 GitLab Git 存储库中。源代码用于创建包含管道的工具链。可定义管道来构建代码，并将代码打包成 Debian 软件包管理器格式。然后，Terraform 供应一个虚拟实例。最后，在运行中虚拟映像内部署、安装和启动应用程序，并验证其运行状况。

管道使用一组用户帐户属性和一个新的 SSH 密钥对来部署到基础架构。这些属性会自动传递到工具链中，但出于安全原因，不会存储在 Git 源代码中。

要查看这些环境属性，请完成以下步骤。 

1. 在“应用程序详细信息”页面中，单击**查看工具链**。
2. 单击 **Delivery Pipeline** 磁贴。
3. 单击**阶段配置**图标，然后单击构建阶段上的**配置阶段**。
4. 单击**环境属性**选项卡来查看属性。要了解可用的属性，请参阅下表。

  |属性|描述
|
  |---|---|
  | `TF_VAR_ibm_sl_api_key` | [基础架构 API 密钥](#iaas-key)来自经典基础架构控制台。|
  | `TF_VAR_ibm_sl_username` | 用于标识经典基础架构帐户的[基础架构用户名](#user-key) |
  | `TF_VAR_ibm_cloud_api_key` | {{site.data.keyword.cloud_notm}} [平台 API 密钥](#platform-key)用于确保能够进行服务创建。|
  | `PUBLIC_KEY` | [公用密钥](#public-key)，可定义该密钥来允许对虚拟服务器实例的访问。|
  | `PRIVATE_KEY` | [专用密钥](#public-key)，可定义该密钥来允许对虚拟服务器实例的访问。**注**：必须使用 `\n` 换行符样式格式。|
  | `VI_INSTANCE_NAME` | 自动为虚拟服务器实例生成的名称 |
  | `GIT_USER` | 如果将 [Terraform 状态](#tform-state)设置为存储 apply 命令的状态，那么需要 GitLab 用户名。|
  | `GIT_PASSWORD` | 如果将 [Terraform 状态](#tform-state)设置为存储 apply 命令的状态，那么需要 GitLab 密码。|
  {: caption="表 1. 为启用管道而更改的环境变量" caption-side="top"}

#### 基础架构 API 密钥
{: #iaas-key}

Terraform 需要基础架构 API 密钥来创建经典基础架构资源。在部署期间，会自动获取该密钥。要手动检索该密钥，请完成以下步骤。 

1. 转至经典基础架构[用户列表 ![外部链接图标](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window}。您也可以单击**菜单** > **经典基础架构** > **帐户** > **用户列表**。
2. 查找创建工具链的用户的详细信息，单击“API 密钥”列中的**查看**或单击**生成**。这两个步骤都会在窗口中显示 API 密钥。
3. 复制 API 密钥并替换工具链配置 `TF_VAR_ibm_sl_api_key` 中的值。

#### 经典基础架构用户名
{: #user-key}

在部署期间，还会自动获取并使用经典基础架构用户名。要手动获取该用户名，请完成以下步骤。

1. 转至经典基础架构[用户列表 ![外部链接图标](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window}。您也可以单击**菜单** > **经典基础架构** > **帐户** > **用户列表**。
2. 单击您想要其创建工具链的用户。
3. 向下滚动到 **VPN 用户名**属性。
4. 剪切并粘贴此值，然后替换工具链配置 `TF_VAR_ibm_sl_username`。

#### 平台 API 密钥
{: #platform-key}

为了在 Terraform 中创建平台级别的服务（如数据库和 Compose 服务），系统会自动获取平台 API 密钥，并将其存储为管道中的环境变量。要手动检索平台密钥，请完成以下步骤。

1. 在 [API 密钥 ![外部链接图标](../icons/launch-glyph.svg)](https://console.bluemix.net/iam/#/apikeys) 页面中，单击**管理** > **安全性** > **平台 API 密钥**。
2. 单击**创建**。
3. 输入名称和描述，然后单击**创建**。
4. 窗口打开时，单击**显示**以查看密钥。
5. 将密钥复制并粘贴到剪贴板上，或下载密钥。
6. 使用生成的值替换工具链配置 `TF_VAR_ibm_cloud_api_key` 中的值。

#### 公共和专用密钥
{: #public-key}

为了使工具链能够将 Debian 打包安装到虚拟服务器实例中，部署基础架构会自动生成专用和公用 SSH 密钥对，以用于将 Git 内容传输到实例。

要手动执行此操作，请执行以下步骤：
1. 在客户机中，使用以下指示信息来创建[公用和专用密钥对 ![外部链接图标](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}。
2. 转至[基础架构 SSH 密钥视图 ![外部链接图标](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window}。您也可以单击**菜单** > **经典基础架构** > **设备** > **管理** > **SSH 密钥**。
3. 单击**添加**。
4. 将先前创建的公用密钥的内容复制并粘贴到密钥内容中。
5. 为密钥指定名称，然后单击**添加**。

专用密钥必须在一行上。将换行符替换为 `\n`。请参阅以下示例。
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

#### 启用 Terraform 状态
{: #tform-state}

Terraform 支持存储 Terraform `apply` 命令的状态。此状态文件会第二次运行 `apply` 命令，以确定是否有任何 Terraform 配置文件发生更改。状态会存储在应用程序和配置均为自动设置的 Git 存储库中。

为了启用状态存储，`GIT_USER` 和 `GIT_PASSWORD` 会自动配置为工具链环境变量中的属性。如果需要访问这些值，请执行以下步骤：

1. 在工具链视图中，通过代码工具访问 Git 存储库。
2. 在 GIT Lab 中，单击**概要文件图标**，然后单击**设置**。
3. 单击**帐户**，复制用户名并替换 `GIT_USER` 值。
4. 单击**访问令牌**。
5. 定义令牌名称，选择作用域，然后单击**创建个人访问令牌**。
6. 单击`您的新个人访问令牌`字段中的**复制**，然后替换工具链属性中的 `GIT_PASSWORD` 值。

Terraform 状态存储在称为 `terraform` 的分支中，即使发生更改，也不会触发管道运行。

### 启用 Git 操作
{: #git-repo}

在将应用程序部署到 {{site.data.keyword.cloud_notm}} 时，会创建一个 GitLab 存储库来托管代码，以便管理源代码。您可以使用 Git 操作，让团队通过合作来交付对应用程序的更改。下面列出了此存储库中包含的文件夹以及对文件夹内容的说明。

#### Debian 文件夹
{: #debian-folder}

`debian` 文件夹包含将应用程序打包成 [Debian 软件包所需的配置。![外部链接图标](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window}

#### Terraform 文件夹
{: #terraform-folder}

`terraform` 文件夹包含“基础架构即代码”配置，可用于供应基础架构资源。文件 `main.tf` 是更改 Terraform 配置选项的主要来源。

```json
resource "ibm_compute_vm_instance" "vm1" {
    hostname = "${var.vi_instance_name}"
    domain = "example.com"
    os_reference_code = "DEBIAN_8_64"
    datacenter = "${var.datacenter}"
    network_speed = 100
    hourly_billing = true
    private_network_only = false
    cores = 1
    memory = 1024
    disks = [25]
    local_disk = false
    ssh_key_ids = [
        "${ibm_compute_ssh_key.ssh_key_gip.id}"
    ]
}
```

此外，还可以使用 Terraform 供应裸机服务器。有关更多信息，请参阅 [IBM Terraform Provider 文档 ![外部链接图标](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} 和 [IBM Terraform Provider GIT 存储库 ![外部链接图标](../icons/launch-glyph.svg)](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}。

`variables.tf` 可用于更改您想要用于创建虚拟实例的数据中心。要查看平台上已定义数据中心的列表，请参阅[数据中心 ![外部链接图标](../icons/launch-glyph.svg)](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}。

缺省情况下，会为 Washington 和 `wdc04` 配置 Terraform 文件。
```json
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### 了解工具链阶段
{: #toolchain-stages}

工具链会显示一个简单管道中的基础架构和应用程序部署。将“基础架构即代码”部分划分到一个管道中，而将应用程序部署划分到另一个管道中。

工具链流程有五个阶段。

1. “构建阶段”会克隆 Git 存储库，并将代码打包成 Debian 软件包。
2. “Terraform 规划阶段”会准备 Terraform 计划。
  ```console
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. “Terraform 应用阶段”会应用 Terraform 配置，并一直等到虚拟服务器的 IP 地址可用。

  ```console
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. “部署、安装、启动阶段”会将第一阶段构建的 Debian 软件包移动到运行中的虚拟服务器上，然后安装并启动该软件包。
5. “运行状况检查阶段”会验证运行状况端点在应用程序上是否可用，然后完成管道。

启动应用程序后，要访问应用程序，请查看“运行状况检查阶段”的日志。单击日志中列出的 URL 链接，这将显示应用程序的 IP 地址和端口。
