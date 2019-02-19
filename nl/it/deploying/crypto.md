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

# Protezione di chiavi e dati con tecnologia crittografica
{: #crypto}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} porta la crittografia IBM Z nel cloud. {{site.data.keyword.cloud_notm}} offre la stessa tecnologia crittografica su cui si basano i servizi bancari e finanziari.
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} protegge le tue chiavi e i tuoi dati inattivi, in uso e in transito al livello di sicurezza più elevato del settore – FIPS 140-2 Livello 4. {{site.data.keyword.hscrypto}} è il keystore per il servizio [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto/index.html#get-started) e protegge le tue chiavi in un ambiente altamente sicuro su IBM Z.

## Installazione e configurazione del client ACSP
{: ##crypto_config}

Prima di installare il client ACSP (Advanced Cryptography Service Provider), crea ed esegui il provisioning di un'istanza di {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} dal [catalogo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/catalog/services/hyper-protect-crypto-services){:new_window}. Quindi, dovrai installare e configurare il client (ACSP) nel tuo ambiente.

1. Scarica il pacchetto di installazione dal [repository GitHub ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:new_window}. Nella cartella **packages**, scegli il file del pacchetto di installazione adatto al tuo sistema operativo e all'architettura della CPU. Ad esempio, per Ubuntu su x86, scegli `acsp-pkcs11-client_1.5-3.5_amd64.deb`.
2. Installa il pacchetto per installare le librerie client ACSP con il comando `dpkg`, ad esempio, `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`.
3. Nella tua istanza del servizio {{site.data.keyword.hscrypto}} in {{site.data.keyword.cloud_notm}}, seleziona **Manage** dal programma di navigazione.
4. Nella finestra di gestione, fai clic su **Download Config** per scaricare il file `acsp_client_credentials.uue`.
5. Copia il file `acsp_client_credentials.uue` nella directory `/opt/ibm/acsp-pkcs11-client/config` del tuo ambiente locale.
6. Nella directory `/opt/ibm/acsp-pkcs11-client/config`, decodifica il file con il seguente comando:
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. Estrai il file delle credenziali del client con il seguente comando:
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. Sposta il file `server-config` nella posizione predefinita con il seguente comando:
   ```
   mv server-config/* ./
   ```
   {: codeblock}
9. Rinomina il file delle credenziali del client con il seguente comando:
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. (Facoltativo) Modifica l'ID gruppo dei file con il seguente comando:
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. Abilita ACSP per utilizzare la configurazione corretta per l'istanza del servizio nel cloud:
    ```
    export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

Ora il tuo client ACSP è operativo e {{site.data.keyword.hscrypto}} è pronto per l'uso.

## Passi successivi
{: ##next-steps}

Un modo semplice per adottare {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} è iniziare con {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}. Per ulteriori informazioni su {{site.data.keyword.hsplatform}}, vedi [Introduzione a {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}](/docs/services/hypersecure-platform/index.html).
