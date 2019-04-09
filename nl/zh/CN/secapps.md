---

copyright:
  years: 2015, 2019
lastupdated: "2019-01-15"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# 创建证书签名请求
{: #ssl_csr}

您可以通过创建和上传 SSL 证书，并限制对应用程序的访问来保护应用程序。
{:shortdesc}

必须在服务器上创建证书签名请求 (CSR)，然后才能通过 {{site.data.keyword.cloud}} 上传您有权使用的 SSL 证书。CSR 是发送到认证中心以请求对公用密钥及其关联信息进行签名的消息。CSR 最常使用的是 PKCS #10 格式。CSR 包含公用密钥以及公共名称、组织、城市、省/直辖市/自治区、国家或地区和电子邮件。仅接受 CSR 密钥长度为 2048 位的 SSL 证书请求。

## 创建 CSR

根据操作系统，创建 CSR 的方法也有所不同。以下示例显示如何使用 [OpenSSL 命令行工具 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://www.openssl.org/){:new_window} 创建 CSR：

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout
    privatekey.key
```
{: codeblock}

OpenSSL SHA-512 实施取决于编译器是否支持 64 位整数类型。您可以将 SHA-1 选项用于与 SHA-256 证书具有兼容性问题的应用程序。
{: tip}

证书由认证中心发放并由该认证中心进行数字签名。创建 CSR 后，可以在公共认证中心生成 SSL 证书。

### 必需的 CSR 内容

要使 CSR 有效，在创建 CSR 时必须输入以下信息：

<dl>
<dt>国家或地区名称</dt>
<dd>表示国家或地区的两位数代码。例如，`US` 是表示美国的国家或地区代码。对于其他国家或区域，请在创建 CSR 前查看 [ISO 国家或地区代码列表 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.iso.org/obp/ui/#search)。
</dd>
<dt>省/自治区/直辖市</dt>
<dd>省/自治区/直辖市的完整非缩写名称。</dd>
<dt>区域</dt>
<dd>城市或城镇的全名。</dd>
<dt>组织</dt>
<dd>在您的区域合法注册的企业或公司的全名或个人姓名。对于公司，请确保包含注册后缀，例如，Ltd.、Inc. 或 NV。</dd>
<dt>组织单元</dt>
<dd>您公司中订购证书的分支的名称，例如，会计或市场营销。</dd>
<dt>公共名称</dt>
<dd>为其请求 SSL 证书的标准域名 (FQDN)。</dd>
</dl>

## 上传 SSL 证书
{: #ssl_certificate}

您可以应用安全协议来为应用程序提供通信隐私，以防止窃听、篡改和消息伪造。如果帐户所有者具有免费轻量帐户，那么必须升级帐户后才能上传证书。

使用定制域来提供 SSL 证书时，请使用以下区域端点来提供 {{site.data.keyword.cloud_notm}} 中您组织的 URL 路径：

* US-South - `custom-domain.us-south.cf.cloud.ibm.com`
* US-East - `custom-domain.us-east.cf.cloud.ibm.com`
* EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
* EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
* AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

要上传应用程序的证书，请完成以下步骤：

1. 在 {{site.data.keyword.cloud_notm}} 控制台中，转至“资源列表”。

2. 选择应用程序以查看其详细信息。

3. 单击**路径** > **管理域**。

4. 在“操作”列中，请单击“操作”图标 ![“更多操作”图标](../icons/action-menu-icon.svg) > **域**。

5. 单击“SSL 证书”列中的**上传**，然后选择定制域：
  
  * 证书：一种数字文档，用于将公用密钥绑定到证书所有者的身份，从而使证书所有者得到认证。证书由认证中心发放并由该认证中心进行数字签名。证书通常由认证中心发放并签名。但是，对于测试和开发用途，您可以使用自签名证书。
  * 专用密钥：一种算法模式，用于对消息进行加密，加密后的消息只能使用对应的公用密钥进行解密。专用密钥还用于解密由对应的公用密钥加密的消息。专用密钥保存在用户系统上，并通过密码进行保护。
  * 中间证书（可选）：一种由可信根认证中心 (CA) 发放的下级证书，专门用于发放最终实体服务器证书。结果是一条证书链，以可信根 CA 开始，接着是中间证书，最后以发放给组织的 SSL 证书结束。使用中间证书来验证主证书的真实性。中间证书通常是从可信的第三方获取的。在将应用程序部署到生产之前对其进行测试时，可能无需中间证书。
  * 启用客户机证书请求：如果启用此选项，那么会要求尝试访问受 SSL 保护的域的用户提供客户机端证书。例如，在 Web 浏览器中，当用户尝试访问受 SSL 保护的域时，Web 浏览器会提示用户提供该域的客户机证书。 

    {{site.data.keyword.cloud_notm}} 域管理中的定制证书功能取决于传输层安全性 (TLS) 协议的服务器名称指示 (SNI) 扩展。访问受定制证书保护的 {{site.data.keyword.cloud_notm}} 应用程序的客户机代码必须在 TLS 实现中支持 SNI 扩展。有关更多信息，请参阅 [RFC 4346 的第 7.4.2 部分 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://tools.ietf.org/html/rfc4346#section-7.4.2){:new_window} 和[使用 TLS 确保数据安全](/docs/get-support/appsectls.html)。
    {: note}
  
  * 客户机证书信任库（可选）：包含您希望允许访问您应用程序的用户的客户机证书。请上传客户机证书信任库文件，以启用此选项来请求客户机证书。
  
    可以通过上传其元数据中包含公用密钥的客户机证书信任库来设置相互认证。
  {: tip}

有关更多信息，请参阅[导入 SSL 证书](/docs/infrastructure/ssl-certificates/import-ssl-certificate.html#import-an-ssl-certificate)。


