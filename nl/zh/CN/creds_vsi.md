---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 向虚拟实例或本地 Docker 环境添加凭证
{: #add-credentials-vsi}

了解如何向虚拟服务器实例或本地 Docker 部署环境添加服务凭证。
{: shortdesc}

## 代码 + 虚拟服务器实例或本地 Docker
{: #credentials-byoc-vsi}

在 VSI 或本地 Docker 下，环境完全由您掌控。例如，您可以编写类似以下示例的代码，并在运行应用程序时向其提供凭证的环境值。
```
password = getEnvironment('password');
```
{: codeblock}

您可以使用 Bash 编写类似以下示例的代码：
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

您可以使用 Docker 编写类似以下示例的代码：
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## 入门模板工具包 + VSI（或本地 Docker）
{: #credentials-starterkit-vsi}

### 如何准备虚拟服务器实例

环境完全在您的控制之下，就如同您通过笔记本运行应用程序一样。换言之，就相当于是本地 Docker。从运行中应用程序的角度来看，VSI 实际上是裸机，因此不存在任何_私钥_（如在 Kubernetes 中）或_服务_（如在 Cloud Foundry 中）。

### 入门模板工具包生成的代码
{: #starterkit-generated-code-vsi}

通过入门模板工具包生成的代码具有本机 `IBMCloudEnv` 库，该库将对检索到的环境值进行抽象化处理，以便应用程序代码具有可移植性，能在多个目标部署上运行。对于虚拟或本地 Docker，该环境必须准备好能满足 `IBMCloudEnv` 库的值，但这些值_不一定要_来自实际环境变量。

为了方便起见，入门模板工具包生成的输出中包含的 `mappings.json` 指令引用了一个本地文件，`IBMCloudEnv` 库从该文件中获取应用程序可以使用的值。

例如，请注意 `mappings.json` 文件的以下部分中的最后一行：
```json
"cloudant_apikey": {
  "searchPatterns": [
    "user-provided:blarg-cloudant-1538408663553:apikey",
    "cloudfoundry:$['cloudant'][0].credentials.apikey",
    "env:service_cloudant:$.apikey",
    "env:cloudant_apikey",
    "file:/server/localdev-config.json:$.cloudant_apikey"
  ]
},
```
{: codeblock}

如果在创建应用程序时使用“部署到云”功能，那么会从 GitLab 存储库中除去 `/server/localdev-config.json` 文件。出于安全原因，您并不希望将凭证放在源代码存储库中。

如果您对已创建的 GitLab 存储库使用 `git clone` 来开始积极的开发，请注意 `.gitignore` 文件会特别地忽略 `server/localdev-config.json`，以帮助阻止意外检入具有敏感凭证的文件。但是，VSI _确实_需要该文件，如开发者在笔记本上工作时那样。

您可以通过完成以下步骤来检索 `server/localdev-config.json` 文件：

1. 对使用“部署到云”功能时自动创建的 GitLab 存储库运行 `git clone`。
2. 安装 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html#overview)，其中包含 `dev` 插件。
3. 使用 `ibmcloud` 命令行登录到 {{site.data.keyword.cloud_notm}}。
4. 运行 `ibmcloud dev get-credentials`，它引用的是 `cli-config.yml` 文件。`cli-config.yml` 文件包含有关哪个应用程序和生成作业具有凭证的信息。

如果在使用“部署到云”功能和 `ibmcloud dev get-credentials` 之间从应用程序中除去了任何资源，那么下载的文件 `/server/localdev-config.json` 不会具有原始 `git clone` 代码库可能需要的所有凭证。
{: tip}

如果要在 Docker 容器中运行应用程序，那么可以选择完全除去 `/server/localdev-config.json` 文件，并在 Docker 命令行中传递环境变量。

继续执行 `mappings.json` 文件中的“cloudant_apikey”部分，请注意 `file...` 行前面的 `env:cloudant_apikey`。这意味着名为 `cloudant_apikey` 的环境变量优先于该文件的内容。因此，即使在构建的 Docker 映像中存在该文件（这不是必需的），您也可以通过在 Docker 命令行上传递值来覆盖该文件中的值。

例如：
```console
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}
