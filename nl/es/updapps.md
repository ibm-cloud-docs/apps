---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, custom domain, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Adición y utilización de un dominio personalizado
{: #updatingapps}

Los dominios proporcionan la ruta al URL asignado a la organización en {{site.data.keyword.cloud}}. Los dominios personalizados dirigen las solicitudes para las aplicaciones a un URL propio. Un dominio personalizado puede ser un dominio compartido, un subdominio compartido o un dominio compartido y un host. A menos
que se especifique un dominio personalizado, {{site.data.keyword.cloud_notm}} utiliza un dominio compartido por defecto en la ruta de la aplicación. Puede crear y utilizar un dominio personalizado utilizando la consola o la interfaz de línea de mandatos de {{site.data.keyword.cloud_notm}}.
{:shortdesc}

El dominio compartido predeterminado es `mybluemix.net`, pero `appdomain.cloud` es otra opción de dominio que puede utilizar. Para obtener más información sobre cómo migrar a `appdomain.cloud`, consulte
[Actualización del dominio](/docs/apps/tutorials?topic=creating-apps-update-domain).
{: tip}

Para utilizar un dominio personalizado, debe registrar el dominio personalizado en un servidor DNS público y, a continuación, configurar el dominio personalizado en {{site.data.keyword.cloud_notm}}. Tras ello, debe correlacionar el dominio correlacionado con el dominio del sistema de
{{site.data.keyword.cloud_notm}} en el servidor DNS público. Después de correlacionar el dominio personalizado con el dominio del sistema, las solicitudes correspondientes al dominio personalizado se direccionan a la aplicación en {{site.data.keyword.cloud_notm}}.

## Adición de un dominio personalizado desde la consola de {{site.data.keyword.cloud_notm}}
{: #custom-domain-console}

Siga estos pasos para añadir un dominio personalizado para su organización utilizando la consola:

1. Vaya a **Gestionar > Cuenta** y seleccione **Organizaciones de Cloud Foundry**.
2. Pulse el nombre de la organización para la que está creando un dominio personalizado.
3. Pulse el separador **Dominios** para ver una lista de dominios disponibles.
4. Pulse **Añadir un dominio**, especifique el nombre de dominio y seleccione la región.
5. Confirme las actualizaciones y pulse **Añadir**.

## Adición de la ruta con el dominio personalizado a una aplicación

1. Desde la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"), pulse el icono
**Menú** ![Icono Menú](../../icons/icon_hamburger.svg) y seleccione **Lista de recursos**.
2. En la página **Lista de recursos**, pulse **Apps de Cloud Foundry**.
3. Pulse sobre la aplicación a la que desee añadir la ruta. Aparecerá la página **Visión general** de la app.
4. Seleccione el menú **Rutas** y seleccione **Editar rutas**.
5. Pulse **Añadir ruta** y especifique la ruta que desea utilizar para la aplicación.
6. Confirme sus actualizaciones pulsando **Guardar**.

Como ejemplo, puede utilizar `*.mycompany.com` para asociar la ruta `www.mybluemix.net` a su app. También puede utilizar `example.mycompany.com` para asociar la ruta `www.example.bluemix.net` a su app.
{: tip}

## Adición de un dominio personalizado desde la interfaz de línea de mandatos de {{site.data.keyword.cloud_notm}}
{: #custom-domain-cli}

1. Para apps de Cloud Foundry, conéctese al punto final de API de Cloud Foundry de destino escribiendo el mandato siguiente:
   ```
   ibmcloud target --cf-api <CF_ENDPOINT>
   ```
   
   **Puntos finales de API de Cloud Foundry:**
   * US-SOUTH - `api.us-south.cf.cloud.ibm.com`
   * US-EAST - `api.us-east.cf.cloud.ibm.com`
   * EU-DE - `api.eu-de.cf.cloud.ibm.com`
   * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
   * AU-SYD - `api.au-syd.cf.cloud.ibm.com`
   
2. Cree un dominio personalizado para la organización con el siguiente mandato:
   ```
   ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
   ```

3. Añada la ruta con el dominio personalizado a una aplicación.

   Para apps de Cloud Foundry, escriba el siguiente mandato:
   ```
   ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
   ```
   
## Correlación del dominio personalizado al dominio del sistema
{: #mapcustomdomain}

Tras configurar su dominio personalizado en {{site.data.keyword.cloud_notm}}, correlaciónelo con el dominio del sistema {{site.data.keyword.cloud_notm}} en su servidor DNS registrado:

1. Configure un registro 'CNAME' para el nombre de dominio personalizado en su servidor DNS. Los pasos para configurar el registro CNAME varían en función del proveedor de DNS. Por ejemplo, si utiliza GoDaddy, siga las directrices de la [Ayuda sobre dominios](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") de GoDaddy.
2. Correlacione el nombre de dominio personalizado con el punto final seguro para la región {{site.data.keyword.cloud_notm}} en la que se ejecuta su aplicación. Utilice los puntos finales de región siguientes para proporcionar la ruta al URL asignado a la organización en {{site.data.keyword.cloud_notm}}. Por ejemplo, haga que CNAME apunte a `<custom-domain>.us-east.cf.cloud.ibm.com.`

  **Puntos finales de Cloud Foundry:**
  * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
  * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## Acceso a la aplicación
{: #access-app}

En un navegador, especifique el URL siguiente para acceder a la aplicación, donde
`hostname` es el nombre de host y `mydomain` es el nombre de dominio:
```
http://hostname.mydomain
```

## Eliminación de una ruta huérfana
{: #remove-orphaned-route}

Para eliminar una ruta huérfana, ejecute el siguiente mandato:
```
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: tip}

En dicho ejemplo, `dominio` es el nombre del dominio y `nombre_host` es el nombre de host de la ruta de la aplicación. Para obtener más información sobre el mandato `ibmcloud app route-delete`, escriba el mandato `ibmcloud app route-delete -h`.

## Utilización de un dominio personalizado para apps de Kubernetes
{: #kube-custom-domain}

El subdominio para los nombres de host del servicio IBM Cloud Kubernetes es `containers.appdomain.cloud`. El comodín de subdominio Ingress proporcionado por IBM, `*.<cluster_name>.<region>.containers.mybluemix.net`, está registrado de forma predeterminada para el clúster. El certificado TLS proporcionado por IBM es un certificado comodín, y se puede utilizar para el subdominio comodín. Si desea utilizar un dominio personalizado, debe registrar el dominio personalizado como un dominio comodín como `*.custom_domain.net`. Para utilizar TLS, debe obtener un certificado comodín. Para obtener más información, consulte [Varios dominios dentro del mismo espacio de nombres](/docs/containers?topic=containers-ingress#multi-domains).

Consulte [esta guía de aprendizaje](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes), que le ofrece instrucciones sobre el desarrollo de una aplicación web, su ejecución en local en un contenedor y su posterior despliegue en un clúster de Kubernetes que se ha creado con el servicio IBM Kubernetes. Además, aprenderá a enlazar un dominio personalizado, supervisar el estado del entorno y escalar la aplicación.
