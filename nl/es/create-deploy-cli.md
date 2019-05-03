---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, create, build, deploy, cli, web app, microservice, deploy cli, deploy command line, build app local, developer tools, ibmcloud dev create

subcollection: creating-apps

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creación y despliegue de apps utilizando la CLI
{: #create-deploy-app-cli}

Puede utilizar la interfaz de línea de mandatos (CLI) de {{site.data.keyword.cloud}} para crear y desplegar su aplicación. 

Puede crear una app de inicio desde cero o habilitar para la nube su código de app existente. 
{: note}

## Antes de empezar
{: #prereqs-app-cli}

Debe instalar la CLI de {{site.data.keyword.cloud_notm}}, el plugin de la CLI de {{site.data.keyword.dev_cli_notm}} y otras herramientas y plugins recomendados. Para obtener más información, consulte [Iniciación a la CLI de IBM Cloud](/docs/cli?topic=cloud-cli-ibmcloud-cli). 

## Creación de una app de inicio desde cero
{: #create-app-cli}

Crear una app desde cero resulta útil si aún no dispone de código existente con el que comenzar y prefiere empezar a partir de una plantilla de inicio de infraestructura o lenguaje.

1. Ejecute el mandato [`ibmcloud dev create`](/docs/cli/idt?topic=cloud-cli-idt-cli#create) en el directorio que prefiera.
2. Seleccione **Backend Service / Web App** como tipo de aplicación.
3. Seleccione **Nodo** como tipo de lenguaje.
4. Seleccione **App Node.js con Express.js (app web)** como kit de inicio que va a utilizar.
5. Especifique un nombre para su app y seleccione el grupo de recursos que quiere utilizar (si es necesario). No añada servicios por ahora.
6. Seleccione la opción **IBM DevOps, utilizando Cloud Foundry** para crear la cadena de herramientas de DevOps. Es posible que tenga que configurar las claves SSH para completar este paso.
  Si define una frase de contraseña para su clave SSH, tendrá que especificar este código.
  {: note}
7. Especifique un nombre de host exclusivo; por ejemplo, `abc-devhost`. Este nombre de host es la ruta de la app; por ejemplo,
`abc-devhost.mybluemix.net`.

El dominio compartido predeterminado es `mybluemix.net`, pero `appdomain.cloud` es otra opción de dominio que puede utilizar. Para obtener más información sobre cómo migrar a `appdomain.cloud`, consulte
[Actualización del dominio](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).
{: tip}

La creación de la app y de la cadena de herramientas puede tardar unos segundos para completarse.

## Generación de activos de despliegue y de habilitación de nube
{: #byoc-cli}

Puede utilizar esta opción si ya dispone de un código base existente y desea generar activos de despliegue y de habilitación de nube para un solo microservicio o una app web mediante [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable). Tenga en cuenta que este mandato está en versión Beta y no se da soporte a todos los lenguajes ni a todas las estructuras de app. En las siguientes instrucciones se describe cómo utilizar esta funcionalidad con un repositorio de ejemplo, pero los pasos son más o menos los mismos para su propio código base.

1. Inicie una sesión en {{site.data.keyword.cloud_notm}} con el mandato `ibmcloud login` y seleccione como destino una organización y un espacio.
2. Clone la [app de muestra Hello World](https://github.com/IBM-Cloud/node-helloworld){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") ejecutando el mandato siguiente en el directorio que prefiera.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. Vaya al directorio donde ha clonado la app de muestra, y ejecute el mandato [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable).
4. Seleccione continuar sin confirmar los cambios por ahora (si es necesario).
5. Seleccione continuar cuando se le solicite seguir con el lenguaje de nodo que se ha detectado.
6. Seleccione el grupo de recursos que desea utilizar (si es necesario). 
7. Seleccione la opción para crear una nueva app de {{site.data.keyword.cloud_notm}} que esté enlazada a este repositorio Git. Consulte las **Notas importantes** para obtener detalles.
8. No añada servicios por ahora.
9. Espere unos segundos hasta que finalicen las operaciones. 
10. Una vez completadas las operaciones, fusione manualmente los archivos de despliegue y de habilitación de nube que se han guardado en el directorio de la app. Fusione los archivos nuevos marcados como `.merge` mediante `git diff` o una herramienta similar.

### Notas importantes
 - Si ya ha creado una app {{site.data.keyword.cloud_notm}} mediante la consola de {{site.data.keyword.cloud_notm}}, siga los pasos 2-5 de la sección anterior en el directorio de la app. Para el paso 6, puede seleccionar la opción para conectar el código local a una app existente.
 - También puede optar por generar archivos de despliegue y de habilitación de nube sin conectarse a una app {{site.data.keyword.cloud_notm}} ejecutando [`ibmcloud dev enable --no-create`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable).
 - Para configurar manualmente una cadena de herramientas y archivos de despliegue, siga [la guía de aprendizaje](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc-kube). Esto puede ser útil si está intentando configurar una cadena de herramientas de Continuous Delivery para más de un microservicio o app web interrelacionados.
 - Si el código base existente aún no está en un repositorio Git, siga los pasos 2-5 de la sección anterior en el directorio de la app. Para el paso 6, puede seleccionar la opción para crear una nueva app de {{site.data.keyword.cloud_notm}} y desplegarla en una cadena de herramientas DevOps (que tiene un repositorio GitLab recién creado).

## Cree una app y ejecútela localmente
{: #build-run-app-cli}

Independientemente de la opción que ha utilizado para crear la app, ahora puede crearla y ejecutarla localmente.

1. Vaya al directorio de la aplicación, y asegúrese de que Docker está ejecutándose en el sistema.
2. Ejecute el mandato [`ibmcloud dev build`](/docs/cli/idt?topic=cloud-cli-idt-cli#build) para crear una app.
3. Ejecute el mandato [`ibmcloud dev run`](/docs/cli/idt?topic=cloud-cli-idt-cli#run) para empezar a ejecutar la app localmente.
4. Vea su app ejecutándose localmente en `http://localhost:3000` o en un URL similar.
5. Pulse las teclas **Ctrl+C** para detener la app.

También puede utilizar [mandatos compuestos](/docs/cli/idt?topic=cloud-cli-idt-cli#compound) como `ibmcloud dev build/run` para generar secuencialmente una compilación seguida de una ejecución.
{: tip}

## Cómo añadir un servicio y modificar el código
{: #resources-app-cli}

Ahora que su app se puede ejecutar localmente, puede añadir un servicio y modificar código. 

1. Ejecute el mandato [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit).
2. Siga las indicaciones para crear y conectar un nuevo servicio relacionado con datos a la app, como por ejemplo, {{site.data.keyword.cloudant_short_notm}}. Es posible que tenga que seleccionar una región y un plan para el servicio.
3. Puede elegir fusionar manualmente los archivos de configuración que se han guardado en el directorio de la app cuando cree el servicio. O puede omitir este paso por ahora.
4. Actualice el código. Por ejemplo, modifique el archivo `/public/index.html` o un archivo similar. Si utiliza la aplicación `ExpressJS` de ejemplo, puede cambiar la cadena `Congratulations!` por algo como `Hello World!`.
5. Guarde los archivos que haya modificado.

## Despliegue en {{site.data.keyword.cloud_notm}}
{: #deploy-app-cli}

Puede desplegar su app {{site.data.keyword.cloud_notm}} de una de estas dos maneras, en función de cómo haya configurado su app. 

### Despliegue la app utilizando la cadena de herramientas de DevOps
Si aún no ha creado una cadena de herramientas de DevOps para la app y la app aún no está en un repositorio Git, puede ejecutar el mandato [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit). Siga las indicaciones para "Configurar DevOps" y despliegue en una nueva cadena de herramientas (y cree un nuevo repositorio GitLab).

Después de crear una cadena de herramientas de DevOps para su app, el despliegue de una nueva compilación será tan simple como confirmar y enviar su código al repositorio de la cadena de herramientas. 

1. Ejecute el mandato `git add .`.
2. Ejecute el mandato `git commit -m "made changes"` para confirmar los cambios.
3. Ejecute el mandato `git push origin master` para enviar por push a la rama maestra.
4. Vea la cadena de herramientas de DevOps para su app desde la consola de {{site.data.keyword.cloud_notm}}. Puede ver detalles de la cadena de herramientas desde la página **Detalles de la app** en la consola de {{site.data.keyword.cloud_notm}} ejecutando el mandato [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) desde el directorio de la app.
5. Ver el conducto dentro de la cadena de herramientas para verificar que se ha iniciado la nueva compilación.

### Despliegue manual de su app

Puede desplegar manualmente su app utilizando el mandato [`deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy). Por ejemplo, siga los pasos siguientes para desplegar manualmente su app en Kubernetes.

1. Asegúrese de haber [creado un clúster de Kubernetes](https://{DomainName}/kubernetes/overview){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").
2. Ejecute el mandato [`ibmcloud dev deploy -t container`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).
3. Cuando se le solicite, confirme el nombre de la imagen del contenedor y del clúster que va a utilizar.
4. Espere unos minutos a que el despliegue se haya completado.

## Visualización de la app
{: #view-app-cli}

1. Para ver el URL de su app que está ejecutándose en {{site.data.keyword.cloud_notm}}, ejecute el mandato [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view).
2. Para ver los detalles sobre la cadena de herramientas, servicios y credenciales de su app desde la consola de {{site.data.keyword.cloud_notm}}, ejecute el mandato [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console). 

**Para notificar problemas o proporcionar comentarios, puede utilizar el
[canal #developer-tools de Slack de {{site.data.keyword.cloud_notm}}
Tech](https://ibm-cloud-tech.slack.com/){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"). Solicite acceso de equipo [aquí](https://slack-invite-ibm-cloud-tech.mybluemix.net/){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").
