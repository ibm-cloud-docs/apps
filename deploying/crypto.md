---

copyright:
  years: 2018
lastupdated: "2018-3-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protecting your keys and data with cryptographic technology
{: #crypto}

{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} brings System z cryptography to the cloud. The same state-of-the-art cryptographic technology that banks and financial services rely on is now offered to cloud users through {{site.data.keyword.cloud_notm}}.
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} is very useful for iOS developers. It protects your keys and your data at rest, in use, and in transit at the industry highest security level, that is, FIPS 140-2 Level 4. Besides, {{site.data.keyword.hscrypto}} serves as the key store for the [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto/index.html) service and protect your keys in a hyper secure environment on System z.


## Provisioning the service
{: ##crypto_create}

The {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} is an {{site.data.keyword.cloud_notm}} experimental service. To provision it, create an instance of {{site.data.keyword.hscrypto}} from [{{site.data.keyword.cloud_notm}} Experimental Services](https://console.bluemix.net/catalog/labs/){:new_window}. Navigate to the Security catalog and click {{site.data.keyword.hscrypto}}. In the {{site.data.keyword.hscrypto}} catalog page, select **zCrypto Free Plan** and click **Create**.


## Installing and configuring the ACSP client
{: ##crypto_config}

You must install and configure the Advanced Cryptography Service Provider (ACSP) client in your environment.

1. Download the installation package from the [GitHub repository](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:new_window}. In the **packages** folder, choose the installation package file that is suitable for your operation system and CPU architecture. For example, for Ubuntu on x86, choose `acsp-pkcs11-client_1.5-3.5_amd64.deb`.
2. Install the package to install the ACSP client libraries with the `dpkg` command. For example, `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`.
3. In your {{site.data.keyword.hscrypto}} service instance in {{site.data.keyword.cloud_notm}}, select **Manage** from the left navigator.
4. On the "Manage" screen, click the **Download Config** button to download the `acsp_client_credentials.uue` file.
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
10. (Optional:) Change group ID of the files with the following command:
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

An easy way to adopt {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} is to start with the {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}. For more information about the {{site.data.keyword.hsplatform}}, see [Getting Started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}](/docs/services/hypersecure-platform/index.html).
