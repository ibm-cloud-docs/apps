---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-27"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creación y utilización de un dominio personalizado
{: #updatingapps}

Los dominios proporcionan la ruta al URL asignado a la organización en {{site.data.keyword.Bluemix_notm}}. Para utilizar un dominio personalizado, debe registrar el dominio personalizado en un servidor DNS público, configurar el dominio personalizado en {{site.data.keyword.Bluemix_notm}}. A continuación, correlacionar el dominio personalizado con el dominio del sistema {{site.data.keyword.Bluemix_notm}} en el servidor DNS público. Después de correlacionar el dominio personalizado con el dominio del sistema, las solicitudes correspondientes al dominio personalizado se direccionan a la aplicación en {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

Puede crear y utilizar un dominio personalizado utilizando la consola o la interfaz de línea de mandatos de {{site.data.keyword.Bluemix_notm}}.

## Utilización de la consola {{site.data.keyword.Bluemix_notm}}

Complete los siguientes pasos para crear un dominio personalizado para su organización utilizando la consola:

1. Vaya a **Gestionar** > **Cuenta** > **Organizaciones de Cloud Foundry**.
2. Pulse el nombre de la organización para la que está creando un dominio personalizado.
3. Pulse el separador **Dominios**.
4. Pulse **Añadir un dominio**, especifique el nombre de dominio y seleccione la región.
5. Confirme sus actualizaciones. Pulse **Añadir**.

Como ejemplo, puede utilizar `*.mycompany.com` para asociar la ruta `www.mybluemix.com` a su app. También puede utilizar `example.mycompany.com` para asociar la ruta `www.example.mybluemix.com` a su app.
{: tip}

Añada la ruta con el dominio personalizado a una aplicación.

1. Pulse el icono **Menú** ![Icono Menú](../icons/icon_hamburger.svg) > **Panel de control** y pulse la fila de la aplicación a la que desee añadir la ruta. Se muestra la página **Visión general**.
2. Desde el menú **Rutas**, seleccione **Editar rutas**.
3. Pulse **Añadir ruta** y especifique la ruta que desea utilizar para la aplicación.
4. Confirme sus actualizaciones pulsando **Guardar**.

## Utilización de la interfaz de línea de mandatos de {{site.data.keyword.Bluemix_notm}}.

1. Cree un dominio personalizado para la organización con el siguiente mandato:

   ```
   ibmcloud app domain-create <your org name> mydomain
   ```

2. Añada la ruta con el dominio personalizado a una aplicación. Para apps de Cloud Foundry, escriba el siguiente mandato:

   ```
   ibmcloud app route-map myapp mydomain -n host_name

   ```

   Para grupos de contenedor, escriba el siguiente mandato:

   ```
   cf ic route map -n host_name -d mydomain mycontainergroup

   ```

Tras configurar su dominio personalizado en {{site.data.keyword.Bluemix_notm}}, correlaciónelo con el dominio del sistema {{site.data.keyword.Bluemix_notm}} en su servidor DNS registrado:

1. Configure un registro 'CNAME' para el nombre de dominio personalizado en su servidor DNS. Los pasos para configurar el registro CNAME varían en función del proveedor de DNS. Por ejemplo, si utiliza GoDaddy, siga las directrices de la [Ayuda sobre dominios ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} de GoDaddy.
2. Correlacione el nombre de dominio personalizado con el punto final seguro para la región {{site.data.keyword.Bluemix_notm}} en la que se ejecuta su aplicación. Utilice los puntos finales de región siguientes para proporcionar la ruta al URL asignado a la organización en {{site.data.keyword.Bluemix_notm}}.

  * US-SOUTH - `secure.us-south.bluemix.net`
  * US-EAST - `secure.us-east.bluemix.net`
  * EU-DE - `secure.eu-de.bluemix.net`
  * EU-GB - `secure.eu-gb.bluemix.net`
  * AU-SYD - `secure.au-syd.bluemix.net`

En un navegador o interfaz de línea de mandatos, escriba el siguiente URL para acceder a la aplicación `myapp`:

```
http://host_name.mydomain

```

Para eliminar una ruta huérfana, ejecute el siguiente mandato:

```
ibmcloud app route-delete domain -n hostname -f
```
{: tip}

En dicho ejemplo, `dominio` es el nombre del dominio y `nombre_host` es el nombre de host de la ruta de la aplicación. Para obtener más información sobre el mandato `ibmcloud app route-delete`, escriba el mandato `ibmcloud app route-delete -h`.
