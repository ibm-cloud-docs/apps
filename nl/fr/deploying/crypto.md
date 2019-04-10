---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, key protection, ACSP client, data protection

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protection de vos clés et de vos données à l'aide de la technologie de cryptographie
{: #crypto}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} permet d'utiliser la cryptographie IBM Z dans le cloud. {{site.data.keyword.cloud_notm}} propose la même technologie cryptographique que celle utilisée par les services bancaires et financiers.
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} protège vos clés et vos données inactives, utilisées et en transit en utilisant le niveau de sécurité le plus élevé du marché, FIPS 140-2 Niveau 4. {{site.data.keyword.hscrypto}} constitue le magasin de clés du service [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto?topic=hs-crypto-get-started) qui protège vos clés dans un environnement extrêmement sécurisé sur IBM Z.

## Installation et configuration du client ACSP
{: #crypto_config}

Avant d'installer le client ACSP (Advanced Cryptography Service Provider), créez et mettez à disposition une instance d'{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} à partir du [catalogue ](https://{DomainName}/catalog/services/hyper-protect-crypto-services){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe"). Vous devez ensuite installer et configurer le client (ASCP) dans votre environnement.

1. Téléchargez le package d'installation à partir du [référentiel GitHub ](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe"). Dans le dossier **packages**, choisissez le fichier du package d'installation adapté à votre système d'exploitation et à votre architecture d'unité centrale. Par exemple, pour Ubuntu sur x86, choisissez `acsp-pkcs11-client_1.5-3.5_amd64.deb`.
2. Installez le package afin d'installer les bibliothèques client ACSP avec la commande `dpkg`, par exemple, `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`.
3. Dans votre instance de service {{site.data.keyword.hscrypto}} d'{{site.data.keyword.cloud_notm}}, sélectionnez **Gérer** dans le navigateur.
4. Dans la fenêtre de gestion, cliquez sur **Télécharger configuration** pour télécharger le fichier `acsp_client_credentials.uue`.
5. Copiez le fichier `acsp_client_credentials.uue` dans le répertoire `/opt/ibm/acsp-pkcs11-client/config` de votre environnement local.
6. Dans le répertoire `/opt/ibm/acsp-pkcs11-client/config`, décodez le fichier avec la commande suivante :
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. Extrayez le fichier des données d'identification client à l'aide de la commande suivante :
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. Déplacez les fichiers `server-config` à l'emplacement par défaut à l'aide de la commande suivante :
   ```
   mv server-config/* ./
   ```
   {: codeblock}
9. Renommez le fichier des données d'identification client à l'aide de la commande suivante :
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. (Facultatif) Changez l'ID de groupe des fichiers à l'aide de la commande suivante :
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. Faites en sorte qu'ACSP puisse utilise la configuration appropriée pour l'instance de service du cloud :
    ```
    export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

Votre client ACSP est désormais opérationnel et votre instance {{site.data.keyword.hscrypto}} est prête à être utilisée !

## Etapes suivantes
{: #next-steps notoc}

Pour adopter {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} de manière simple, il suffit de commencer en utilisant des éléments {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}. Pour plus d'informations sur les éléments {{site.data.keyword.hsplatform}}, voir [Initiation à {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}](/docs/services/hypersecure-platform?topic=services/hypersecure-platform-getting-started-with-ibm-cloud-hyper-protect-developer-starter-kits).
