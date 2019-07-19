---

copyright:
  years: 2019
lastupdated: "2019-03-15"

keywords: apps, domain, Kubernetes, Cloud Foundry, cli

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Actualización del dominio
{: #update-domain}

Los dominios proporcionan la ruta al URL asignado a la organización en {{site.data.keyword.cloud}}. Para apps de Cloud Foundry, puede migrar el dominio de `mybluemix.net` a `appdomain.cloud` utilizando la interfaz de línea de mandatos o la consola de
{{site.data.keyword.cloud_notm}}.
{:shortdesc}

## Actualización de dominios desde la consola de {{site.data.keyword.cloud_notm}}
{: #update-domain-console}

El dominio compartido predeterminado es `mybluemix.net`, pero `appdomain.cloud` es otra opción de dominio que puede utilizar.
{: tip}

Siga estos pasos para actualizar el dominio para su organización de Cloud Foundry utilizando la consola:

1. Desde la [consola de {{site.data.keyword.cloud_notm}}
![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}){: new_window}, pulse el icono Menú ![Icono Menú](../icons/icon_hamburger.svg) y seleccione Lista de recursos.
2. En la página **Lista de recursos**, pulse **Apps de Cloud Foundry**.
3. Pulse sobre la aplicación para la cual desee cambiar el dominio. Aparecerá la página **Visión general** de la app.
4. Seleccione el menú **Rutas**, observe cuál es el dominio actual, como `<myapp.mybluemix.net>` y pulse
**Editar rutas**.
5. Seleccione la lista de dominios y, a continuación, pulse sobre el dominio que desee utilizar, como `us-south.cf.appdomain.cloud`.
6. Confirme sus actualizaciones pulsando **Guardar**.
7. Confirme que desea sustituir el dominio anterior y pulse **Eliminar**.
8. Para comprobar que la nueva ruta está funcionando, pulse **Visitar URL de app**.

## Actualización de dominios desde la interfaz de línea de mandatos de {{site.data.keyword.cloud_notm}}
{: #update-domain-cli}

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

2. Añada la ruta con el nuevo dominio a una aplicación escribiendo el mandato siguiente:
   ```
   ibmcloud app route-map APP_NAME DOMAIN -n HOSTNAME
   ```

## Actualización del dominio para apps de Kubernetes
{: #update-domain-kube}

El subdominio para los nombres de host de {{site.data.keyword.containerlong}} es `containers.appdomain.cloud`. El comodín de subdominio Ingress proporcionado por IBM, `*.<cluster_name>.<region>.containers.appdomain.cloud`, está registrado de forma predeterminada para el clúster. El certificado TLS proporcionado por IBM es un certificado comodín, y se puede utilizar para el subdominio comodín. Para obtener más información, consulte [Varios dominios dentro del mismo espacio de nombres](/docs/containers?topic=containers-ingress#multi-domains).
