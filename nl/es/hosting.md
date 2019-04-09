---

copyright:
  years: 2017, 2018
lastupdated: "2017-01-26"

---

{:shortdesc: .shortdesc}

# Alojamiento de apps
{: #hosting}

Si tiene una app existente, puede alojarla en IBM Cloud con todos los servicios de infraestructura o de plataforma que necesite. Para las apps existentes, aproveche la infraestructura de {{site.data.keyword.Bluemix_notm}} para alojar apps que ha desarrollado específicamente para {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Migración de apps
{: #ht_hostapp}

Para las apps existentes, puede migrar sus apps a {{site.data.keyword.Bluemix_notm}} de forma incremental, en lugar de desplazarlas completamente al entorno de nube. Primero puede migrar una parte de
su app y conectar a los datos existentes o sistema de registros mediante el
servicio Cloud Integration.

Para sus apps de {{site.data.keyword.Bluemix_notm}}, podría necesitar acceder a los datos o servicios de fondo, como por ejemplo un sistema de registro. En {{site.data.keyword.Bluemix_notm}},
puede utilizar el servicio Secure Gateway para establecer un túnel seguro entre una organización de {{site.data.keyword.Bluemix_notm}} y la red principal de fondo empresarial. El servicio permite a las
apps en {{site.data.keyword.Bluemix_notm}} acceder a los datos y servicios de la red principal de fondo. Para obtener detalles, consulte [Alcanzar el elemento de fondo empresarial con Bluemix Secure Gateway a través de la consola ![icono de enlace externo](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

{{site.data.keyword.Bluemix_notm}} puede alojar su app existente y proporcionar toda la infraestructura que necesita. En el [catálogo](https://console.bluemix.net/catalog/?taxonomyNavigation=apps), puede elegir si aloja la app en un servidor nativo o en un servidor virtual. Un despliegue [nativo](../bare-metal/index.html#about-bare-metal-servers) es mejor opción si necesita un servidor físico dedicado para obtener un mayor rendimiento. Un despliegue [virtual](/vsi/vsi_index.html#provisioning-a-virtual-server) es mejor opción si la carga de trabajo está distribuida entre regiones geográficas y desea utilizar un hipervisor de {{site.data.keyword.Bluemix_notm}} para gestionar los despliegues.

Puede migrar partes de la app a {{site.data.keyword.Bluemix_notm}} todas a la vez o componente por componente. Eche un vistazo a algunos de los servicios que ofrecemos a medida que migra la app.

* Seleccione el tipo de [almacenamiento](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) que sea correcto para usted desde el almacenamiento en bloque, el almacenamiento de archivos o el almacenamiento de objetos.
* Seleccione el tipo de [red](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) que necesita.
* Seleccione un servicio de [contenedores](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) para aprovechar la tecnología de Kubernetes de {{site.data.keyword.Bluemix_notm}}.

## Pasos siguientes
{: #next-steps}

Si el servicio se puede alojar en más de una región, puede seleccionar dónde se aloja la app. Para ello, registre y añada la información de URL personalizado en su app en {{site.data.keyword.Bluemix_notm}}. A continuación, seleccione las regiones donde se aloja la app. Consulte [Actualización de apps](updapps.html) para obtener más información sobre cómo desplegar la app.
