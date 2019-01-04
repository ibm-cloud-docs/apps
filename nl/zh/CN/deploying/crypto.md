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

# 使用加密技术保护密钥和数据
{: #crypto}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} 在云上运用了 IBM Z 密码术。{{site.data.keyword.cloud_notm}} 所提供的加密技术与银行和金融服务所依赖的加密技术相同。
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} 可对静态、使用中和传输中的密钥和数据提供业界最高安全级别（FIPS 140-2 4 级）的保护。{{site.data.keyword.hscrypto}} 是 [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto/index.html) 服务的密钥库，可在 IBM Z 上通过超安全环境来保护您的密钥。

## 安装和配置 ACSP 客户机
{: ##crypto_config}

安装 Advanced Cryptography Service Provider (ACSP) 客户机之前，请通过[目录 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/catalog/services/hyper-protect-crypto-services){:new_window} 创建和供应 {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} 的实例。然后，必须在自己的环境中安装和配置 ACSP 客户机。

1. 从 [GitHub 存储库 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:new_window} 下载安装包。在**包**文件夹中，选择适用于您的操作系统和 CPU 体系结构的安装包文件。例如，对于 Ubuntu on x86，请选择 `acsp-pkcs11-client_1.5-3.5_amd64.deb`。
2. 使用 `dpkg` 命令，安装相应的包来安装 ACSP 客户机库，例如 `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`。
3. 在 {{site.data.keyword.cloud_notm}} 中的 {{site.data.keyword.hscrypto}} 服务实例中，从导航器中选择**管理**。
4. 在“管理”窗口中，单击**下载配置**以下载 `acsp_client_credentials.uue` 文件。
5. 将 `acsp_client_credentials.uue` 文件复制到本地环境的 `/opt/ibm/acsp-pkcs11-client/config` 目录中。
6. 在 `/opt/ibm/acsp-pkcs11-client/config` 目录中，使用以下命令对该文件解码：
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. 使用以下命令解压缩客户机凭证文件：
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. 使用以下命令将 `server-config` 文件移至缺省位置：
   ```
   mv server-config/* ./
   ```
   {: codeblock}
9. 使用以下命令对客户机凭证文件重命名：
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. （可选）使用以下命令更改文件的组标识：
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. 启用 ACSP 以将正确的配置用于云中的服务实例：
    ```
    export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

现在，ACSP 客户机已正常运行，并且 {{site.data.keyword.hscrypto}} 已准备就绪，可供使用！

## 后续步骤
{: ##next-steps}

一种采用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} 的简单方法是使用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}。有关 {{site.data.keyword.hsplatform}} 的更多信息，请参阅 [{{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}} 入门](/docs/services/hypersecure-platform/index.html)。
