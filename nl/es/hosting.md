---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migración y alojamiento de apps
{: #hosting}

Si tiene una app existente, puede alojarla en {{site.data.keyword.Bluemix}} con todos los servicios de infraestructura o de plataforma que necesite. También es posible migrar su app a {{site.data.keyword.Bluemix_notm}} de forma incremental en lugar de cambiar su app a un entorno de en la nube a la vez.

## Migración de apps
{: #migrating}

Si necesita que su app acceda a sus servicios o datos locales, utilice [{{site.data.keyword.SecureGatewayfull}}](../services/SecureGateway/secure_gateway.html) para establecer una conexión de túnel seguro entre una organización de {{site.data.keyword.Bluemix_notm}} y su red de fondo empresarial. Para obtener detalles, consulte [Alcanzar el elemento de fondo empresarial con {{site.data.keyword.Bluemix_notm}} Secure Gateway a través de la consola ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg).

Si necesita ayuda con la migración, [IBM Cloud Migration Services](https://www.ibm.com/cloud/migration-services){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") está disponible.

## Alojamiento de apps
{: #ht_hostapp}

En el [catálogo](https://console.bluemix.net/catalog/?taxonomyNavigation=apps){: new_window} de {{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"), elija un entorno gestionado como Kubernetes o Cloud Foundry. También puede alojar su app directamente en un servidor virtual o nativo.

En un despliegue virtual, la mayoría de las operaciones de la app las gestiona {{site.data.keyword.Bluemix_notm}}. Un despliegue [virtual](../vsi/vsi_about.html) es mejor opción si la carga de trabajo está distribuida entre regiones geográficas y desea utilizar un hipervisor de {{site.data.keyword.Bluemix_notm}} para gestionar los despliegues. Un despliegue [nativo](../bare-metal/index.html) es mejor opción si necesita un acceso directo a un servidor físico dedicado para un mayor rendimiento.

También tiene muchas opciones para:
* Seleccionar el tipo de [almacenamiento](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} de ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") adecuado para su almacenamiento de bloques, almacenamiento de archivos u Object Storage.
* Seleccionar el tipo de [red](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") que necesite.
* Seleccionar un servicio de [tipo de contenedor](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") para aprovecharse de la tecnología de Kubernetes de {{site.data.keyword.Bluemix_notm}}.
