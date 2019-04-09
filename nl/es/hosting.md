---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# Alojamiento de apps
{: #hosting}

Si tiene una app existente, puede alojarla en IBM Cloud con todos los servicios de infraestructura o de plataforma que necesite. También puede aprovechar la infraestructura de {{site.data.keyword.Bluemix_notm}} para alojar apps que ha desarrollado específicamente para {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Migración de apps
{: #ht_hostapp}

Puede migrar sus apps a {{site.data.keyword.Bluemix_notm}} de forma incremental, en lugar de desplazarlas completamente al entorno de nube. Primero puede migrar una parte de
su app y conectar a los datos existentes o sistema de registros mediante el
servicio Cloud Integration.

Para sus apps de {{site.data.keyword.Bluemix_notm}}, podría necesitar acceder a los datos o servicios de fondo, como por ejemplo un sistema de registro. En {{site.data.keyword.Bluemix_notm}},
puede utilizar el servicio Secure Gateway para establecer un túnel seguro entre una
organización de {{site.data.keyword.Bluemix_notm}} y la red principal de fondo empresarial. El servicio permite a las
apps en {{site.data.keyword.Bluemix_notm}} acceder a los datos y servicios de la red principal de fondo. Para obtener detalles, consulte [Alcanzar el elemento de fondo empresarial con Bluemix Secure Gateway a través de la consola ![icono de enlace externo](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

{{site.data.keyword.Bluemix_notm}} puede alojar su app existente y proporcionar toda la infraestructura en {{site.data.keyword.Bluemix_notm}}. En el [catálogo](https://console.bluemix.net/catalog/?taxonomyNavigation=apps), puede elegir si aloja la app en la nube en un servidor nativo, o en un servidor virtual.

Puede migrar partes de la app a {{site.data.keyword.Bluemix_notm}} todas a la vez o componente por componente. Eche un vistazo a algunos de los servicios que ofrecemos a medida que migra la app.

* Seleccione el tipo de [almacenamiento](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) que sea correcto para usted desde el almacenamiento en bloque, el almacenamiento de archivos o el almacenamiento de objetos.
* Seleccione el tipo de [red](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) que necesita.
* Seleccione un servicio de [contenedores](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) para aprovechar la tecnología de Kubernetes de {{site.data.keyword.Bluemix_notm}}.

## Pasos siguientes
{: #next-steps}

Si el servicio se puede alojar en más de una región, puede seleccionar dónde se aloja la app. En [Actualización de apps](updapps.html), puede seleccionar las regiones donde se aloja la app y editar el URL personalizado.
