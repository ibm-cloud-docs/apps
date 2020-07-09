---

copyright:
  years: 2015, 2019
lastupdated: "2019-11-13"

keywords: apps, application, ssl, certificates, access, restrict access, create, csr, upload, import

subcollection: apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:external: target="_blank" .external}

# Creating certificate signing requests
{: #ssl_csr}

You can secure your applications by uploading SSL certificates and restricting access to the apps.
{: shortdesc}

## Creating a certificate signing request
{: #create_csr}

Before you can upload the SSL certificates to which you’re entitled with {{site.data.keyword.cloud}}, you must create a certificate signing request (CSR) on your server. A CSR is a message that is sent to a certificate authority to request the signing of a public key and associated information. Most commonly, CSRs are in PKCS #10 format. The CSR includes a public key, a common name, organization, city, state, country, and email. SSL certificate requests are accepted only with a CSR key length of 2048 bits.

The methods for creating a CSR vary depending on your operating system. The following example shows how to create a CSR by using [the OpenSSL command-line tool](https://www.openssl.org/){: external}:

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privatekey.key
```
{: codeblock}

OpenSSL SHA-512 implementation depends on compiler support for 64-bit integer type. You can use the SHA-1 option for apps that have compatibility issues with the SHA-256 certificate.
{: tip}

### Required CSR contents

For the CSR to be valid, the following information must be entered when you create the CSR:

 * **Country name**: A two-digit code for the country or region. For example, `US` is the country code for the United States. For other countries or regions, before you create the CSR, check the [list of ISO country codes](https://www.iso.org/obp/ui/#search){: external}.
 * **State or province**: The full, unabbreviated name of the state or province.
 * **Locality**: The full name of the city or town.
 * **Organization**: The full name of the business or company, as legally registered in your locality, or personal name. For companies, be sure to include the registration suffix, such as Ltd., Inc., or NV.
 * **Organization unit**: The branch name of your company that is ordering the certificate, such as accounting or marketing.
 * **Common name**: The fully qualified domain name (FQDN) for which you’re requesting the SSL certificate. Wildcards are not supported in the common name.

You can use Subject Alternative Names (SAN), but the provided host names must not be issued in other deployed certificates to prevent CN collisions.
{: note}

A certificate is issued by a certificate authority and is digitally signed by that authority. After you create the CSR, you can generate your SSL certificate on a public certificate authority.

## Uploading SSL certificates
{: #ssl_certificate}

You can apply a security protocol to provide communication privacy for your app to prevent eavesdropping, tampering, and message forgery. If you have a Lite account, you must upgrade your account to upload a certificate.

When an expired or expiring certificate must be renewed, and after the new certificate is ready, delete the existing certificate and then add the new one.
{: note}

When you use a custom domain to serve the SSL certificate, use the following region endpoints to provide the URL route for your organization in {{site.data.keyword.cloud_notm}}:

| Region | Endpoint |
| ------ | -------- |
| US-South | `custom-domain.us-south.cf.cloud.ibm.com` |
| US-East | `custom-domain.us-east.cf.cloud.ibm.com` |
| EU-DE | `custom-domain.eu-de.cf.cloud.ibm.com` |
| EU-GB | `custom-domain.eu-gb.cf.cloud.ibm.com` |
| AU-SYD | `custom-domain.au-syd.cf.cloud.ibm.com` | 
{: caption="Table 1. Cloud Foundry custom domain region endpoints" caption-side="top"}

To upload a certificate for your Cloud Foundry app, complete the following steps:

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click **Manage**, and select **Account**.
2. Click **Cloud Foundry orgs**.
3. From the Actions column, click the Actions icon ![More Actions icon](../icons/action-menu-icon.svg), and select **Domains**.
6. Click **Upload** for your custom domain.
7. Select an option, upload the file, and click **Add**.
  
  * Certificate: A digital document that binds a public key to the identity of the certificate owner, which enables the certificate owner to be authenticated. A certificate is issued by a certificate authority and is digitally signed by that authority. A certificate is generally issued and signed by a certificate authority. However, for testing and development purposes, you might use a self-signed certificate.
  * Private key: An algorithmic pattern that is used to encrypt messages that only the corresponding public key can decrypt. The private key is also used to decrypt messages that were encrypted by the corresponding public key. The private key is kept on the user system and is protected by a password.
  * Intermediate certificate (optional): A subordinate certificate that is issued by the trusted root certificate authority (CA) specifically to issue end-entity server certificates. The result is a certificate chain that begins at the trusted root CA, passes through the intermediate certificate, and ends with the SSL certificate issued to the organization. Use an intermediate certificate to verify the authenticity of the main certificate. Intermediate certificates are typically obtained from a trusted third party. You might not require an intermediate certificate when you test your app before you deploy it to production.
  * Enable request of client certificate: When you enable this option, a user who tries to access an SSL protected domain is requested to provide a client-side certificate. For example, in a web browser, when a user tries to access an SSL protected domain, the web browser prompts the user to provide a client certificate for the domain.   
  * Client certificate truststore (optional): Includes the client certificates for the users who you want to allow access to your app. Upload a client certificate truststore file to enable the option to request a client certificate.
  
    You can set up mutual authentication by uploading a client certificate truststore that includes a public key in its metadata.
    {: tip}


