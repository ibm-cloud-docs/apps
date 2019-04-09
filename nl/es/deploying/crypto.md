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

# Proteger las claves y los datos con tecnología criptográfica
{: #crypto}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} lleva la criptografía de IBM Z a la nube. {{site.data.keyword.cloud_notm}} ofrece la misma tecnología criptográfica en la que se basan los servicios bancarios y financieros.
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} protege sus claves y sus datos en reposo, en uso y en tránsito en el nivel se seguridad más alto del sector – FIPS 140-2 Nivel 4. {{site.data.keyword.hscrypto}} es el almacén de claves para el servicio de [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto/index.html) y protege sus claves en un entorno híper seguro en IBM Z.

## Instalación y configuración del cliente de ACSP
{: ##crypto_config}

Antes de instalar el cliente ACSP (Advanced Cryptography Service Provider), cree y suministre una instancia de {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} desde el [catálogo de ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/services/hyper-protect-crypto-services){:new_window}. A continuación, debe instalar y configurar el cliente (ACSP) en el entorno.

1. Descargue el paquete de instalación desde el [repositorio de GitHub ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:new_window}. En la carpeta **packages**, elija el archivo de paquete de instalación que sea adecuado para el sistema operativo y la arquitectura de CPU. Por ejemplo, para Ubuntu en x86, elija `acsp-pkcs11-client_1.5-3.5_amd64.deb`.
2. Instale el paquete para instalar las bibliotecas de cliente de ACSP con el mandato `dpkg`, por ejemplo, `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`.
3. En la instancia de servicio de {{site.data.keyword.hscrypto}} en {{site.data.keyword.cloud_notm}}, seleccione **Gestionar** desde el navegador.
4. En la ventana de gestión, pulse **Descargar configuración** para descargar el archivo `acsp_client_credentials.uue`.
5. Copie el archivo `acsp_client_credentials.uue` al directorio `/opt/ibm/acsp-pkcs11-client/config` en su entorno local.
6. En el directorio `/opt/ibm/acsp-pkcs11-client/config`, descodifique el archivo con el mandato siguiente:
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. Extraiga el archivo de credenciales del cliente con el mandato siguiente:
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. Mueva los archivos `server-config` al lugar predeterminado con el mandato siguiente:
   ```
   mv server-config/* ./
   ```
   {: codeblock}
9. Cambie el nombre del archivo de credenciales del cliente con el mandato siguiente:
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. (Opcional) Cambie el ID de grupo de los archivos con el mandato siguiente:
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. Habilite ACSP para que utilice la configuración adecuada para la instancia de servicio en la nube:
    ```
    export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

Ahora el cliente de ACSP está operativo y su {{site.data.keyword.hscrypto}} está listo para su uso.

## Pasos siguientes
{: ##next-steps}

Una forma fácil de adoptar {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} es empezar con el {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}. Para obtener más información sobre el {{site.data.keyword.hsplatform}}, consulte [Iniciación a {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}](/docs/services/hypersecure-platform/index.html).
