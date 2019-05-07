---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-23"

keywords: apps, deploying apps, containers, kubernetes, docker, clusters, devops toolchain, deployment, kube

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Utilización de contenedores con Kubernetes
{: #containers-kube}

Empiece con {{site.data.keyword.containershort}} desplegando apps de alta disponibilidad en contenedores Docker que se ejecutan en clústeres de Kubernetes. Gestione el desarrollo en equipo con Git y, a continuación, utilice la Cadena de herramientas de DevOps para gestionar el despliegue de la app en Kubernetes.
{: shortdesc}

Los contenedores son una forma estándar de empaquetar apps y todas sus dependencias para poder moverlas entre entornos sin complicaciones. A diferencia de las máquinas virtuales, los contenedores no empaquetan el sistema operativo. Solo el código de app, el tiempo de ejecución, las herramientas del sistema, las bibliotecas y los valores se empaquetan dentro de los contenedores. Los contenedores son más ligeros, portátiles y eficientes que una máquina virtual.

Consulte [Iniciación a {{site.data.keyword.containershort_notm}}](/docs/containers?topic=containers-getting-started) para obtener más información sobre el servicio.

## Configuración de despliegues
{: #config-deploy}

Al crear apps de fondo o de servicio web, puede desplegarlas en el servicio de {{site.data.keyword.containershort_notm}}, que utiliza el entorno de Kubernetes.

1. Despliegue la app en la nube configurando un conducto de nube automatizado.
2. Pulse **Configurar entrega continua**.
3. Seleccione **Servicio de IBM Kubernetes** como destino. Debe [crear un clúster](https://{DomainName}/kubernetes/catalog/cluster/create){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo") si aún no tiene ninguno.
4. Una vez que se haya completado el despliegue, compruebe la app activa en la nube obteniendo el URL en los registros de la etapa de despliegue del conducto de entrega. La última dirección IP con un puerto es la nueva página de inicio de la app, por ejemplo, 169.60.133.124:32355.

## Enlace de servicios
{: #bind-services}

A medida que se crea la cadena de herramientas, los servicios que asocia a su app están enlazados al clúster de Kubernetes utilizando los secretos de Kubernetes. Los secretos se utilizan para gestionar las credenciales de servicio fuera de la app en ejecución. La app lee los secretos y, a continuación, recupera los valores que necesita para empezar a ejecutarse. El enlace de servicios le permite desplegar la app en otro entorno de Kubernetes que podría estar utilizando instancias de servicio {{site.data.keyword.cloud}} de nivel de producción.

Si suprime el servicio o los secretos, debe enlazarlos de nuevo manualmente o suprimir y volver a crear la cadena de herramientas.
{: tip}

Para obtener más información, consulte [Secretos](https://kubernetes.io/docs/concepts/configuration/secret/){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo").

## Iniciando desarrollo
{: #dev}

1. Consulte el nuevo repositorio de Git en línea desde la cadena de herramientas y empiece a trabajar con el código. Para ver la cadena de herramientas, pulse **Ver cadena de herramientas**.
2. Acceda al repositorio Git en el que se ha creado el código clonando el repositorio en el entorno local.
3. Abra el proyecto con su IDE favorito.

## Creación y despliegue con una cadena de herramientas
{: #bulid-deploy-tc}

La cadena de herramientas contiene la etapa de creación y la etapa de despliegue.

### Etapa de creación
{: #build-stage}
La etapa de creación se desencadena cuando se ejecuta un `git push` en el repositorio Git. La etapa del conducto desencadena una compilación de imágenes de docker y coloca la imagen en el registro del contenedor.

Para obtener más información, consulte [Iniciación a IBM Cloud Container Registry](/docs/services/Registry?topic=registry-getting-started).

### Etapa de despliegue
{: #deploy-stage}

La etapa de despliegue recupera la imagen más reciente del {{site.data.keyword.registryshort_notm}} y, a continuación, la despliega en el clúster de Kubernetes utilizando un diagrama de Helm. El diagrama de Helm se ha añadido a la app cuando se desplegó en la nube. Los diagramas de Helm facilitan la gestión de los pasos de despliegue de la imagen de contenedor empaquetada.

Para obtener más información, consulte [Diagramas](https://docs.helm.sh/developing_charts/){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo").

{{site.data.keyword.cloud_notm}} da soporte a un número de [diagramas de Helm preconfigurados](https://{DomainName}/kubernetes/solutions/helm-charts){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo").

## Comprobación de la seguridad de la app
{: #sec}

{{site.data.keyword.containershort_notm}} da soporte al escaneo de las imágenes de contenedor empaquetadas para las vulnerabilidades de seguridad. El escaneo de seguridad es esencial para dar soporte a las aplicaciones de nivel empresarial.

Vea el [repositorio de imágenes](https://{DomainName}/kubernetes/registry/main/private){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo") de los contenedores para comprobar si hay vulnerabilidades de seguridad potenciales.
