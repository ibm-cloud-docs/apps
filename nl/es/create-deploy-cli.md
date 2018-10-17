---
copyright:

  years: 2018

lastupdated: "2018-10-02"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# Creación y despliegue de apps utilizando la CLI
{: #developing}

Puede utilizar la interfaz de línea de mandatos (CLI) de {{site.data.keyword.Bluemix}} para crear y desplegar su app.
{:shortdesc}

## Antes de empezar
{: #prereqs}

Instale la CLI de {{site.data.keyword.Bluemix_notm}}, el plug-in de la CLI de {{site.data.keyword.dev_cli_notm}} y otras herramientas y plugins recomendados. Para obtener más información, consulte [Iniciación a la CLI de IBM Cloud](/docs/cli/index.html). 

## Creación de su app
{: #create}

Puede crear una app nueva desde cero o crear una app basada en cloud utilizando el código existente. 

### Creación de una app desde cero

1. Ejecute el mandato [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) en el directorio que prefiera.
2. Seleccione **Backend Service / Web App** como tipo de aplicación.
3. Seleccione **Nodo** como tipo de lenguaje.
4. Seleccione **Express.js Basic (Web App)** como el kit de iniciación que va a utilizar.
5. Especifique un nombre para su app y seleccione el grupo de recursos que quiere utilizar (si es necesario). No añada servicios por ahora.
6. Seleccione la opción **IBM DevOps, utilizando Cloud Foundry** para crear la cadena de herramientas de DevOps. Es posible que tenga que configurar las claves SSH para completar este paso.
7. Especifique un nombre de host exclusivo, por ejemplo, `abc-devhost`. Este nombre de host es la ruta de la app, `abc-devhost.mybluemix.net`.

La creación de la app y de la cadena de herramientas puede tardar unos segundos para completarse. Puede supervisar el estado en el indicador de mandatos.

### Creación de una app utilizando código existente

1. Clone la [app de muestra Hello World](https://github.com/IBM-Cloud/node-helloworld) ejecutando el mandato siguiente en el directorio que prefiera.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

2. Vaya al directorio donde ha clonado la app de muestra, y ejecute el mandato [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable).
3. Seleccione continuar sin validar los cambios en GitHub por ahora.
4. Seleccione continuar cuando se le solicite seguir con el lenguaje de nodo que se ha detectado.
5. Seleccione el grupo de recursos que desea utilizar (si es necesario). No añada servicios por ahora.
6. Espere unos segundos a que se cree la app. 
7. Puede elegir fusionar manualmente los archivos de despliegue y configuración que se guardan en el directorio de la app cuando crea la app. O puede omitir este paso por ahora.

## Cree una app y ejecútela localmente
{: #build-run}

Independientemente de la opción que ha utilizado para crear la app, ahora puede crearla y ejecutarla localmente.

1. Vaya al directorio de la aplicación, y asegúrese de que Docker está ejecutándose en el sistema.
2. Ejecute el mandato [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) para crear una app.
3. Ejecute el mandato [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) para empezar a ejecutar la app localmente.
4. Vea su app ejecutándose localmente en `http://localhost:3000` o en un URL similar.
5. Pulse las teclas **Ctrl+C** para detener la app.

También puede utilizar [mandatos compuestos](/docs/cli/idt/commands.html#compound) como `ibmcloud dev build/run` para generar secuencialmente una compilación seguida de una ejecución.
{: tip}

## Cómo añadir un servicio y modificar el código
{: #add-service}

Ahora que su app se puede ejecutar localmente, puede añadir un servicio y modificar código. 

1. Ejecute el mandato [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit).
2. Siga las indicaciones para crear y conectar un nuevo servicio relacionado con datos a la app, como por ejemplo, {{site.data.keyword.cloudant_short_notm}}. Es posible que tenga que seleccionar una región y un plan para el servicio.
3. Puede elegir fusionar manualmente los archivos de despliegue y configuración que se guardan en el directorio de la app cuando crea el servicio. O puede omitir este paso por ahora.
4. Realice un cambio en el código. Por ejemplo, modifique el archivo `/public/index.html` o un archivo similar. Si utiliza la aplicación `ExpressJS` de ejemplo, puede cambiar la cadena `Congratulations!` por algo como `Hello World!`.
5. Guarde los archivos que haya modificado.

## Despliegue en {{site.data.keyword.Bluemix_notm}}
{: #deploy}

Puede desplegar su app {{site.data.keyword.Bluemix_notm}} de una de estas dos maneras, en función de cómo haya configurado su app. 

### Despliegue la app utilizando la cadena de herramientas de DevOps

Si anteriormente ha creado una cadena de herramientas de DevOps para su app, el despliegue de una nueva compilación será tan simple como confirmar y enviar su código al repositorio de la cadena de herramientas. 

1. Ejecute el mandato `git add .`.
2. Ejecute el mandato `git commit -m "made changes"` para confirmar los cambios.
3. Ejecute el mandato `git push origin master` para enviar por push a la rama maestra.
4. Vea la cadena de herramientas de DevOps para su app desde la consola de {{site.data.keyword.Bluemix_notm}}. Puede ver la cadena de herramientas en un navegador web ejecutando el mandato [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) desde el directorio de la app y pulsando **Ver cadena de herramientas**.
5. Ver el conducto dentro de la cadena de herramientas para verificar que se ha iniciado la nueva compilación.

### Despliegue manual de su app

Puede desplegar manualmente su app utilizando el mandato [`deploy`](/docs/cli/idt/commands.html#deploy). Por ejemplo, siga los pasos siguientes para desplegar manualmente su app en Kubernetes.

1. Asegúrese de que ha [creado un clúster de Kubernetes](https://console.bluemix.net/containers-kubernetes/overview).
2. Ejecute el mandato [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy).
3. Cuando se le solicite, confirme el nombre de la imagen del contenedor y del clúster que va a utilizar.
4. Espere unos minutos a que el despliegue se haya completado.

## Visualización de la app
{: #view}

1. Para ver el URL de su app que está ejecutándose en {{site.data.keyword.Bluemix_notm}}, ejecute el mandato [`ibmcloud dev view`](/docs/cli/idt/commands.html#view).
2. Para ver los detalles sobre la cadena de herramientas, servicios y credenciales de su app desde la consola de {{site.data.keyword.Bluemix_notm}}, ejecute el mandato [`ibmcloud dev console`](/docs/cli/idt/commands.html#console). 

