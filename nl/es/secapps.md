---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# Creación de solicitudes de firma de certificado
{: #ssl_csr}

Puede proteger las aplicaciones subiendo certificados SSL y limitando el acceso a las aplicaciones.
{:shortdesc}

Para poder cargar los certificados SSL a los que esté autorizado con {{site.data.keyword.cloud}}, debe crear una solicitud de firma de certificado (CSR) en el servidor. Una CSR es un mensaje que se envía a una entidad emisora de certificados para solicitar la firma de una clave pública
y de información asociada. De forma más común, las CSR se encuentran en el formato PKCS número 10. La CSR incluye una clave pública, así como un nombre común, una organización, una ciudad, un estado, un país y un correo electrónico. Las solicitudes de certificados SSL
sólo están aceptadas con una longitud de claves CSR de 2048 bits.

## Contenido necesario de CSR

Para que la CSR sea válida, debe especificarse la siguiente información al generar la CSR:

### Nombre de país

  Un código de dos dígitos correspondiente al país o a la región. Por ejemplo, `US` es el código de país correspondiente a Estados Unidos. Para otros países o regiones, consulte la [lista de códigos de países ISO ![icono de enlace externo](../icons/launch-glyph.svg "icono de enlace externo")](https://www.iso.org/obp/ui/#search){:new_window} antes de crear la CSR.

### Estado o provincia

  El nombre completo no abreviado del estado o de la provincia.

### Localidad

  El nombre completo del pueblo o ciudad.

### Organización

  El nombre completo de la empresa, como esté registrada legalmente en su localidad, o el nombre personal. Para las empresas, asegúrese de incluir el sufijo de registro, como por ejemplo Ltd., Inc. o NV.

### Unidad organizativa

  Nombre de la rama de su empresa que está pidiendo el certificado, como por ejemplo contabilidad o
marketing.

### Nombre común

  Nombre de dominio completo (FQDN) para el que está solicitando el certificado SSL.

Los métodos para crear una CSR varían en función del sistema operativo. El ejemplo siguiente
muestra cómo crear una CSR utilizando [la herramienta de línea de mandatos OpenSSL ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](http://www.openssl.org/){:new_window}:

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout
    privatekey.key
```

La implementación SHA-512 de OpenSSL depende del soporte de compilador para el tipo de entero de 64 bits. Puede utilizar la opción SHA-1 para las aplicaciones que tienen problemas de compatibilidad con el certificado SHA-256.
{: tip}

Un certificado lo emite una entidad emisora de certificados, que lo firma digitalmente. Después de crear la CSR, puede generar el certificado SSL en una entidad emisora de certificados pública.

## Carga de certificados SSL
{: #ssl_certificate}

Puede aplicar un protocolo de seguridad para proporcionar privacidad de comunicación a la aplicación a fin de impedir escuchas no autorizadas, manipulación indebida e interferencia de mensajes.

Si el propietario de su cuenta tiene una cuenta de prueba gratuita, debe actualizar su cuenta para cargar un certificado.

Para poder cargar los certificados, debe crear una
solicitud de firma de certificado.

Si utiliza un dominio personalizado para servir el certificado SSL, utilice los siguientes puntos finales de región para proporcionar la ruta de URL asignada a la organización en {{site.data.keyword.cloud_notm}}:

* US-South - `secure.us-south.bluemix.net`
* US-East - `secure.us-east.bluemix.net`
* EU-DE - `secure.eu-de.bluemix.net`
* EU-GB - `secure.eu-gb.bluemix.net`
* AU-SYD - `secure.au-syd.bluemix.net`

Para cargar un certificado para la aplicación, siga estos pasos.

1. Vaya a la lista de recursos.

2. Seleccione su app para abrir la vista de detalles de la app.

3. Pulse **Rutas** > **Gestionar dominios**.

4. En la columna de acción, pulse **Dominios** en el menú de acciones adicional y seleccione su organización.

5. Pulse **Cargar** en la columna Certificado SSL y seleccione su dominio personalizado.

  #### Certificado

    Documento digital que enlaza una clave pública con la identidad del propietario
del certificado, permitiendo de este modo autenticar al propietario de este certificado. Un certificado lo emite una entidad emisora de certificados, que lo firma digitalmente.

    Por lo general un certificado lo emite y firma una entidad emisora de certificados. Sin embargo, para fines de prueba y desarrollo puede utilizar un certificado autofirmado.

    En {{site.data.keyword.cloud_notm}} se da soporte a los siguientes tipos de certificados:

	* PEM (`pem`, `.crt`, `.cer` y `.cert`)
	* DER (`.der` o `.cer`)
	* PKCS #7 (`p7b`, `p7r`, `spc`)

  #### Clave privada

    Patrón algorítmico utilizado para cifrar mensajes que solo se pueden descifrar con la clave pública correspondiente. La clave privada también se utiliza para descifrar mensajes que se han cifrado mediante la clave pública correspondiente. La clave privada se guarda en el sistema del usuario y se
protege mediante una contraseña.

    En {{site.data.keyword.cloud_notm}} se da soporte a los siguientes tipos de claves públicas:

    * PEM (`pem`, `.key`)
    * PKCS #8 (`p8`, `pk8`)

  #### Certificado intermedio

    Certificado subordinado emitido por la entidad emisora de certificados (CA) raíz de confianza específicamente para emitir certificados del servidor de la entidad final. El resultado es una cadena de certificados que empieza en la entidad emisora de certificados raíz de confianza, pasa por el certificado intermedio y termina con la emisión del certificado SSL a la organización.

    Utilice a un certificado intermedio para verificar la autenticidad del certificado principal. Los certificados intermedios normalmente se obtienen de un tercero de confianza. Es posible que no necesite un certificado intermedio para probar la aplicación antes de desplegarla en producción.

  #### Habilitar solicitud de certificado de cliente

    Si habilita esta opción cargando un archivo de almacén de confianza de certificado de cliente, a los usuarios que intenten acceder un dominio protegido por SSL se les solicitará que especifiquen un certificado del lado del cliente. Por ejemplo en un navegador web, cuando un usuario intenta acceder a un dominio protegido por SSL, el navegador web le solicita que especifique un certificado de cliente para el dominio. Utilice la opción de carga de archivo de **Almacén de confianza de certificado de cliente** para definir los certificados del lado del cliente que permiten acceder al dominio personalizado.

  La característica de certificado personalizado de la gestión del dominio {{site.data.keyword.cloud_notm}} depende de la extensión Indicación de Nombres del Servidor (SNI) del protocolo de seguridad de la capa de transporte (TLS). El código de cliente que accede a las aplicaciones {{site.data.keyword.Bluemix_notm}} que se protegen mediante certificados personalizados deben admitir la extensión SNI de la implementación de TLS. Para obtener más información, consulte [sección 7.4.2 de RFC 4346 ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](http://tools.ietf.org/html/rfc4346#section-7.4.2){:new_window} y [Protección de datos con TLS](/docs/get-support/appsectls.html).
  {: note}

  #### Almacén de confianza de certificado de cliente

  El almacén de confianza de certificado de cliente incluye los certificados de cliente para los usuarios a los que desea permitir el acceso a la aplicación. Cargue un archivo de almacén de confianza de certificado de cliente para habilitar la opción de solicitud de certificado de cliente.

   En {{site.data.keyword.cloud_notm}} se da soporte a los siguientes tipos de certificados:

      * PEM (pem, .crt, .cer y .cert)
      * PKCS #7 (p7b, p7r, spc)

  Puede configurar la autenticación mutua cargando un almacén de confianza de certificado de cliente que incluya una clave pública en sus metadatos.
  {: tip}

Para obtener más información, consulte [Importación de certificados SSL](/docs/infrastructure/ssl-certificates/import-ssl-certificate.html#import-an-ssl-certificate).

Para suprimir un certificado o sustituir un certificado existente con uno nuevo, siga estos pasos.

1. Vaya a **Gestionar > Cuenta** y seleccione **Organizaciones de Cloud Foundry**. 
2. En la columna de acción, seleccione **Dominios** en el menú de acciones adicional. En el menú de acciones adicional de la organización, pulse **Eliminar de la organización**.
