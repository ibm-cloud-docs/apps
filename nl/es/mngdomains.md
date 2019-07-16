---

copyright:
  years: 2019
lastupdated: "2019-06-03"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom domain, dns, domainname, domain name, endpoint, update, migrate

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Gestión de los dominios
{: #update-domain}

Los dominios proporcionan la ruta al URL asignado a la organización en {{site.data.keyword.cloud}}. Los dominios personalizados dirigen las solicitudes para las aplicaciones a un URL propio. Un dominio personalizado puede ser un dominio compartido, un subdominio compartido o un dominio compartido y un host. A menos
que se especifique un dominio personalizado, {{site.data.keyword.cloud_notm}} utiliza un dominio compartido por defecto en la ruta de la app. El proceso para gestionar sus dominios depende del destino de despliegue, como
{{site.data.keyword.containershort}}, Cloud Foundry y otros.
{:shortdesc}

Para utilizar un dominio personalizado, debe registrar el dominio personalizado en un servidor DNS público y, a continuación, configurar el dominio personalizado en {{site.data.keyword.cloud_notm}}. Tras ello, debe correlacionar el dominio correlacionado con el dominio del sistema de
{{site.data.keyword.cloud_notm}} en el servidor DNS público. Después de correlacionar el dominio personalizado con el dominio del sistema, las solicitudes correspondientes al dominio personalizado se direccionan a la app en {{site.data.keyword.cloud_notm}}.

## Cambio del dominio para apps de Kubernetes
{: #update-domain-kube}

El subdominio para los nombres de host de {{site.data.keyword.containershort_notm}} es `containers.appdomain.cloud`. El comodín de subdominio Ingress proporcionado por IBM, `*.<cluster_name>.<region>.containers.appdomain.cloud`, está registrado de forma predeterminada para el clúster. El certificado TLS proporcionado por IBM es un certificado comodín, y se puede utilizar para el subdominio comodín. Para obtener más información, consulte [Varios dominios dentro del mismo espacio de nombres](/docs/containers?topic=containers-ingress#multi-domains).

## Utilización de un dominio personalizado para apps de Kubernetes
{: #custom-domain-kube}

Si desea utilizar un dominio personalizado, debe registrar el dominio personalizado como un dominio comodín, como `*.custom_domain.net`. Para utilizar TLS, debe obtener un certificado comodín. Para obtener más información, consulte [Varios dominios dentro del mismo espacio de nombres](/docs/containers?topic=containers-ingress#multi-domains).

Consulte [esta guía de aprendizaje](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes), que le ofrece instrucciones sobre el desarrollo de una app web, su ejecución en local en un contenedor y su posterior despliegue en un clúster de Kubernetes que se ha creado con el servicio IBM Kubernetes. Además, la guía de aprendizaje le mostrará cómo enlazar un dominio personalizado, supervisar el estado del entorno y escalar la app.

## Cambio del dominio para apps de Cloud Foundry
{: #update-domain-cf}

Para apps de Cloud Foundry, puede cambiar el dominio de `mybluemix.net` a `appdomain.cloud` utilizando la interfaz de línea de mandatos o la consola de
{{site.data.keyword.cloud_notm}}. Para obtener más información sobre cómo cambiar el dominio a `appdomain.cloud`, consulte
[Actualización del dominio](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

El dominio compartido predeterminado es `mybluemix.net`, pero `appdomain.cloud` es otra opción de dominio que puede utilizar.
{: tip}

## Utilización de un dominio personalizado para apps de Cloud Foundry
{: #custom-domain-cf}

Para las apps de Cloud Foundry, puede crear y utilizar un dominio personalizado utilizando la consola o la interfaz de línea de mandatos de {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Adición y utilización de un dominio personalizado](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains).
