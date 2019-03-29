---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, key protection, ACSP client, data protection, protect keys, data, protect, ascp, crypto, keys, cryptography

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protecting your keys and data with cryptographic technology
{: #crypto}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} brings IBM Z cryptography to the cloud. {{site.data.keyword.cloud_notm}} offers the same cryptographic technology that banking and financial services rely on.
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} protect your keys and your data at rest, in use, and in transit at the industry's highest security level – FIPS 140-2 Level 4. {{site.data.keyword.hscrypto}} is the keystore for the [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto?topic=hs-crypto-get-started) service and protect your keys in a hyper secure environment on IBM Z.

## Installing and configuring the ACSP client
{: #crypto_config}

Before you install the Advanced Cryptography Service Provider (ACSP) client, create and provision an instance of the {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} from the [catalog](https://{DomainName}/catalog/services/hyper-protect-crypto-services){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon"). Then, you must install and configure the (ACSP) client in your environment.

1. Download the installation package from the [GitHub repository](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon"). In the **packages** folder, choose the installation package file that is suitable for your operating system and CPU architecture. For example, for Ubuntu on x86, choose `acsp-pkcs11-client_1.5-3.5_amd64.deb`.
2. Install the package to install the ACSP client libraries with the `dpkg` command, for example, `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`.
3. In your {{site.data.keyword.hscrypto}} service instance in {{site.data.keyword.cloud_notm}}, select **Manage** from the navigator.
4. In the manage window, click **Download Config** to download the `acsp_client_credentials.uue` file.
5. Copy the `acsp_client_credentials.uue` file to the `/opt/ibm/acsp-pkcs11-client/config` directory in your local environment.
6. In the `/opt/ibm/acsp-pkcs11-client/config` directory, decode the file with the following command:
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. Extract the client credentials file with the following command:
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. Move the `server-config` files into the default place with the following command:
   ```
   mv server-config/* ./
   ```
   {: codeblock}
9. Rename the client credentials file with the following command:
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. (Optional) Change the group ID of the files with the following command:
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. Enable ACSP to use the proper config for the service instance in the cloud:
    ```
    export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

Now your ACSP client is operational and your {{site.data.keyword.hscrypto}} is ready to use!

## Next steps
{: #next-steps notoc}

An easy way to adopt {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} is to start with the {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}. For more information about the {{site.data.keyword.hsplatform}}, see [Getting Started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}](/docs/services/hypersecure-platform?topic=services/hypersecure-platform-getting-started-with-ibm-cloud-hyper-protect-developer-starter-kits).
