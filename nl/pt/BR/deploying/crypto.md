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

# Protegendo suas chaves e os dados com a tecnologia criptográfica
{: #crypto}

O {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} traz a criptografia IBM Z para a nuvem. O {{site.data.keyword.cloud_notm}} oferece a mesma tecnologia criptográfica da qual os serviços bancários e financeiros dependem.
{:shortdesc}

O {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} protege suas chaves e dados inativos, em uso e em trânsito no nível de segurança mais alto da indústria - FIPS 140-2 Nível 4. O {{site.data.keyword.hscrypto}} é o keystore do serviço [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto/index.html) e protege suas chaves em um ambiente de hipersegurança no IBM Z.

## Instalando e configurando o cliente ACSP
{: ##crypto_config}

Antes de instalar o cliente Advanced Cryptography Service Provider (ACSP), crie e provisione uma instância do {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} por meio do catálogo do [ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/hyper-protect-crypto-services){:new_window}. Em seguida, deve-se instalar e configurar o cliente (ACSP) em seu ambiente.

1. Faça download do pacote de instalação por meio do [Repositório GitHub ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:new_window}. Na pasta de **pacotes**, escolha o arquivo de pacote de instalação que for adequado para seu sistema operacional e arquitetura de CPU. Por exemplo, para Ubuntu on x86, escolha `acsp-pkcs11-client_1.5-3.5_amd64.deb`.
2. Instale o pacote para instalar as bibliotecas do cliente ACSP com o comando `dpkg`, por exemplo, `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`.
3. Na instância de serviço do {{site.data.keyword.hscrypto}} no {{site.data.keyword.cloud_notm}}, selecione **Gerenciar** no navegador.
4. Na janela de gerenciamento, clique em **Fazer download da configuração** para fazer download do arquivo `acsp_client_credentials.uue`.
5. Copie o arquivo `acsp_client_credentials.uue` para o diretório `/opt/ibm/acsp-pkcs11-client/config` em seu ambiente local.
6. No diretório `/opt/ibm/acsp-pkcs11-client/config`, decodifique o arquivo com o comando a seguir:
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. Extraia o arquivo de credenciais do cliente com o comando a seguir:
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. Mova os arquivos `server-config` para o local padrão com o comando a seguir:
   ```
   mv server-config/ * ./
   ```
   {: codeblock}
9. Renomeie o arquivo de credenciais do cliente com o comando a seguir:
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. (Opcional) Mude o ID do grupo dos arquivos com o comando a seguir:
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. Ative o ACSP para usar a configuração adequada da instância de serviço na nuvem:
    ```
    export ACSP_P11 = /opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

Agora seu cliente ACSP está operacional e seu {{site.data.keyword.hscrypto}} está pronto para usar!

## Próximas Etapas
{: ##next-steps}

Uma maneira fácil de adotar o {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} é iniciar com o {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}. Para obter mais informações sobre o {{site.data.keyword.hsplatform}}, consulte [Introdução ao {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}](/docs/services/hypersecure-platform/index.html).
