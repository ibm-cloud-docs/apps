---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-25"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Elección del entorno de alojamiento
{: #hosting}

Si tiene una aplicación existente, puede alojarla en {{site.data.keyword.cloud}} con todos los servicios de infraestructura o de plataforma que necesite.
{:shortdesc}

Con {{site.data.keyword.cloud_notm}}, ya no será necesario hacer grandes inversiones en hardware para probar o ejecutar apps nuevas. En su lugar, nosotros lo gestionamos todos y solo se le cobrará por lo que utilice. El entorno del servicio en la nube es la base de la capa de la infraestructura. Puede elegir una opción única o una combinación de opciones en entornos más complejos. 

Dispone de varias opciones de alojar apps, lo que le proporciona control sobre la infraestructura según sus deseos o necesidades. Puede ejecutar la app de cualquiera de las formas siguientes:

  * Como contenedor Docker en un clúster de Kubernetes
  * Como app de Cloud Foundry
  * Como función sin servidor
  * Como VMware
  * Como máquina virtual
  * En {{site.data.keyword.baremetal_short}} de alto rendimiento 
  
<!--
{{site.data.keyword.baremetal_short}} are single-tenant, physical servers that are dedicated to a single customer. You control almost everything from the server host to the RAM and storage devices. These servers are used with workloads that require compute power over a sustained time, for example, several months.

Some example workloads include e-commerce, ERP, CRM, SCM, and financial services and regulatory applications.

{{site.data.keyword.BluVirtServers_short}} can be deployed as either as public or dedicated instances. With public instances, the resources of the server are shared with other customers, also known as a multi-tenant environment. Private instances dedicate the resources of the physical server to one customer who can have one or more virtual machines on the same server. These servers are ideal for workloads that run for a limited time, for example, a couple of weeks. Some workload examples are development and testing, backup and recovery, and disaster recovery. For more information about server options, see [Bare metal servers versus virtual servers: Choosing the best option for you](https://www.ibm.com/cloud/blog/bare-metal-virtual-servers-works){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
-->

Consulte la tabla siguiente para obtener un resumen de las opciones de cálculo.

| Opción | Descripción | 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) | Combina contenedores de Docker, la tecnología de Kubernetes, una experiencia de usuario intuitiva y una seguridad y aislamiento integrados para automatizar el despliegue, la operación, el escalado y la supervisión de apps contenerizadas en un clúster de hosts de cálculo. |
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) | Crear instancias de varias plataformas de Cloud Foundry aisladas y de nivel empresarial a petición. |
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) | Una plataforma de programación de funciones como servicio (FaaS) basada en Apache OpenWhisk. |
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) | Integrar o migrar de forma rápida y transparente las cargas de trabajo de VMware locales utilizando una infraestructura escalable, segura y de alto rendimiento y la tecnología de virtualización híbrida de VMware líder del sector. |
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) | Servidores virtuales escalables que se adquieren con núcleos dedicados y asignaciones de memoria. |
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-about-bm)  | Servidores de un solo arrendatario mensuales o por hora, dedicados y no compartidos con otros clientes, incluidos los recursos del servidor. |
{: caption="Tabla 1. Opciones de cálculo" caption-side="top"}

