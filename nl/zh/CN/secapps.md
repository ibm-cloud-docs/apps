---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-03"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 创建证书签名请求
{: #ssl_csr}

您可以通过上传 SSL 证书并限制对应用程序的访问来保护应用程序。
{:shortdesc}

必须在服务器上创建证书签名请求 (CSR)，然后才能通过 {{site.data.keyword.Bluemix}} 上传您有权使用的 SSL 证书。

CSR 是发送到认证中心以请求对公用密钥及其关联信息进行签名的消息。CSR 最常使用的是 PKCS #10 格式。CSR 包含公用密钥以及公共名称、组织、城市、省/直辖市/自治区、国家或地区和电子邮件。仅接受 CSR 密钥长度为 2048 位的 SSL 证书请求。

## 必需的信息

要使 CSR 有效，在生成 CSR 时必须输入以下信息：

### 国家或地区名称

  表示国家或地区的两位数代码。例如，“US”表示美国。对于其他国家或地区，请在创建 CSR 前检查 [ISO 国家或地区代码列表 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.iso.org/obp/ui/#search){:new_window}。

### 省/自治区/直辖市

  省/自治区/直辖市的完整非缩写名称。

### 区域

  城镇或城市的全名。

### 组织

  在您的区域合法注册的企业或公司的全名或个人姓名。对于公司，请确保包含注册后缀，例如，Ltd.、Inc. 或 NV。

### 组织单元

  订购证书的公司的分支名称，例如，会计或市场营销。

### 公共名称

  为其请求 SSL 证书的标准域名 (FQDN)。

根据操作系统，创建 CSR 的方法也有所不同。以下示例显示如何使用 [OpenSSL 命令行工具 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://www.openssl.org/){:new_window} 创建 CSR：

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout
    privatekey.key
```

OpenSSL SHA-512 实施取决于编译器是否支持 64 位整数类型。您可以将 SHA-1 选项用于与 SHA-256 证书具有兼容性问题的应用程序。
{: tip}

证书由认证中心发放并由该认证中心进行数字签名。创建 CSR 后，可以在公共认证中心生成 SSL 证书。

## 上传 SSL 证书
{: #ssl_certificate}

您可以应用安全协议来为应用程序提供通信隐私，以防止窃听、篡改和消息伪造。

对于 {{site.data.keyword.Bluemix_notm}} 中帐户所有者已具有现买现付或预订套餐的每个组织，可以上传证书四次。对于帐户所有者具有免费试用帐户的每个组织，必须升级帐户后才能上传证书。

在上传证书之前，必须创建证书签名请求。

使用定制域时，要提供 SSL 证书，请使用以下区域端点来提供在 {{site.data.keyword.Bluemix_notm}} 中分配给您组织的 URL 路径：

* US-South：secure.us-south.bluemix.net
* US-East：secure.us-east.bluemix.net
* EU-DE：secure.eu-de.bluemix.net
* EU-GB：secure.eu-gb.bluemix.net
* AU-SYD：secure.au-syd.bluemix.net


要上传应用程序的证书，请执行以下操作：

1. 转至仪表板。

2. 选择应用程序以打开应用程序详细信息视图。

3. 单击**路径** > **管理域**。

4. 在“操作”列中，从组织的“其他操作”菜单中选择**域**。

5. 对于定制域，单击“SSL 证书”列中的**上传**。

6. 浏览以上传证书、专用密钥，以及中间证书或客户机证书（这两项是可选的）。要启用客户机证书信任库，必须上传客户机证书信任库文件，此文件定义了对定制域所允许的用户访问权。

  #### 证书

    一种数字文档，用于将公用密钥绑定到证书所有者的标识，从而使证书所有者得到认证。证书由认证中心发放并由该认证中心进行数字签名。

    证书通常由认证中心发放并签名。但是，对于测试和开发用途，您可以使用自签名证书。

    {{site.data.keyword.Bluemix_notm}} 中支持以下类型的证书：

	* PEM（pem、.crt、.cer 和 .cert）
	* DER（.der 或 .cer）
	* PKCS #7（p7b、p7r 和 spc）

  #### 专用密钥

    一种算法模式，用于对消息进行加密，加密后的消息只能使用对应的公用密钥进行解密。专用密钥还用于解密由对应的公用密钥加密的消息。专用密钥保存在用户系统上，并通过密码进行保护。

    {{site.data.keyword.Bluemix_notm}} 中支持以下类型的专用密钥：

    * PEM（pem 和 .key） 
    * PKCS #8（p8 和 pk8）

  #### 中间证书

    一种由可信根认证中心 (CA) 发放的下级证书，专门用于发放最终实体服务器证书。结果是一条证书链，以可信根 CA 开始，接着是中间证书，最后以发放给组织的 SSL 证书结束。

    您应该使用中间证书来验证主证书的真实性。中间证书通常是从可信的第三方获取的。在将应用程序部署到生产之前对其进行测试，可能无需中间证书。

  #### 启用客户机证书请求

    如果通过上传客户机证书信任库文件启用了此选项，那么会要求尝试访问受 SSL 保护的域的用户提供客户机端证书。例如，在 Web 浏览器中，当用户尝试访问受 SSL 保护的域时，Web 浏览器会提示用户提供该域的客户机证书。使用**客户机证书信任库**文件上传选项可定义您允许访问定制域的客户机端证书。

  **注：**{{site.data.keyword.Bluemix_notm}} 域管理中的定制证书功能取决于传输层安全性 (TLS) 协议的服务器名称指示 (SNI) 扩展。因此，用于访问受定制证书保护的 {{site.data.keyword.Bluemix_notm}} 应用程序的客户机代码必须在 TLS 实现中支持 SNI 扩展。有关更多信息，请参阅 [RFC 4346 的第 7.4.2 部分 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://tools.ietf.org/html/rfc4346#section-7.4.2){:new_window} 和[使用 TLS 确保数据安全](/docs/get-support/appsectls.html)。

  #### 客户机证书信任库

  客户机证书信任库是包含客户机证书的文件，供您希望允许访问您应用程序的用户使用。如果启用此选项来请求客户机证书，请上传客户机证书信任库文件。

   {{site.data.keyword.Bluemix_notm}} 中支持以下类型的证书：

      * PEM（pem、.crt、.cer 和 .cert）
      * PKCS #7（p7b、p7r 和 spc）

  可以通过上传其元数据中包含公用密钥的客户机证书信任库来设置相互认证。
  {: tip}

有关更多信息，请参阅[导入 SSL 证书](/docs/infrastructure/ssl-certificates/import-ssl-certificate.html#import-an-ssl-certificate)。

要删除证书或将现有证书替换为新证书，请转至**管理** > **帐户** > **Cloud Foundry 组织**。然后，在“操作”列中，从“其他操作”菜单中选择**域**。在组织的其他操作菜单中，单击**从组织中除去**。
