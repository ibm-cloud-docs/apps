---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-29"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migración y alojamiento de apps
{: #hosting}

Si tiene una app existente, puede alojarla en {{site.data.keyword.cloud}} con todos los servicios de infraestructura o de plataforma que necesite. También es posible migrar su app a {{site.data.keyword.cloud_notm}} de forma incremental en lugar de cambiar su app a un entorno de en la nube a la vez.

## Migración de apps
{: #migrating}

Si necesita que su app acceda a sus servicios o datos locales, utilice [{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway?topic=securegateway-getting-started-with-sg#getting-started-with-sg) para establecer una conexión de túnel seguro entre una organización de {{site.data.keyword.cloud_notm}} y su red de fondo empresarial. Para obtener detalles, consulte [Alcanzar el elemento de fondo empresarial con {{site.data.keyword.cloud_notm}} Secure Gateway a través de la consola](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").

Si necesita ayuda con la migración, dispone de [servicios de migración de {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/migration-services){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").

## Alojamiento de apps
{: #ht_hostapp}

En el {{site.data.keyword.cloud_notm}} [catálogo](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"), puede elegir un entorno gestionado como Kubernetes o Cloud Foundry o bien puede alojar su app directamente en un servidor nativo o virtual.

En un despliegue virtual, la mayoría de las operaciones de la app las gestiona {{site.data.keyword.cloud_notm}}. Un despliegue [virtual](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers) es mejor opción si la carga de trabajo está distribuida entre regiones geográficas y desea utilizar un hipervisor de {{site.data.keyword.cloud_notm}} para gestionar los despliegues. Un despliegue [nativo](/docs/bare-metal?topic=bare-metal-bm-getting-started#getting-started) es mejor opción si necesita un acceso directo a un servidor físico dedicado para un mayor rendimiento.

También tiene muchas opciones para:
* Seleccionar el tipo de [almacenamiento](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") adecuado entre almacenamiento en bloque, almacenamiento de archivos o almacenamiento de objetos.
* Seleccionar el tipo de [red](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") que necesite.
* Seleccionar un servicio de [tipo de contenedor](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") para aprovecharse de la tecnología de Kubernetes de {{site.data.keyword.cloud_notm}}.
