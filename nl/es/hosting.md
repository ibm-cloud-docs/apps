---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migración y alojamiento de apps
{: #hosting}

Si tiene una app existente, puede alojarla en {{site.data.keyword.cloud}} con todos los servicios de infraestructura o de plataforma que necesite. También es posible migrar su app a {{site.data.keyword.cloud_notm}} de forma incremental en lugar de cambiar su app a un entorno de en la nube a la vez.

## Migración de apps
{: #migrating}

Si necesita que su app acceda a sus servicios o datos locales, utilice [{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway/index.html) para establecer una conexión de túnel seguro entre una organización de {{site.data.keyword.cloud_notm}} y su red de fondo empresarial. Para obtener detalles, consulte [Alcanzar el elemento de fondo empresarial con {{site.data.keyword.cloud_notm}} Secure Gateway a través de la consola ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

Si necesita ayuda con la migración, dispone de [servicios de migración de {{site.data.keyword.cloud_notm}}![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/migration-services){: new_window}.

## Alojamiento de apps
{: #ht_hostapp}

En el {{site.data.keyword.cloud_notm}} [catálogo ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window}, puede elegir un entorno gestionado como Kubernetes o Cloud Foundry o bien puede alojar su app directamente en un servidor nativo o virtual.

En un despliegue virtual, la mayoría de las operaciones de la app las gestiona {{site.data.keyword.cloud_notm}}. Un despliegue [virtual](/docs/vsi/vsi_about.html) es mejor opción si la carga de trabajo está distribuida entre regiones geográficas y desea utilizar un hipervisor de {{site.data.keyword.cloud_notm}} para gestionar los despliegues. Un despliegue [nativo](/docs/bare-metal/index.html#getting-started) es mejor opción si necesita un acceso directo a un servidor físico dedicado para un mayor rendimiento.

También tiene muchas opciones para:
* Seleccionar el tipo de [almacenamiento ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} adecuado entre almacenamiento en bloque, almacenamiento de archivos o almacenamiento de objetos.
* Seleccionar el tipo de [red ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} que necesite.
* Seleccionar un servicio de [tipo de contenedor ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} para aprovecharse de la tecnología de Kubernetes de {{site.data.keyword.cloud_notm}}.
