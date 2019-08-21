---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-03"

keywords: apps, Mendix, starter kit, developer tools, Mendix app, create mendix app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note .note}

# Creación de apps con Mendix
{: #create-mendix}

Mendix es un entorno de desarrollo con poco código y un conjunto de herramientas que le ayuda a entregar aplicaciones de varios dispositivos que se ejecutan en {{site.data.keyword.cloud}} con mayor rapidez y con menos recursos de desarrollo. Si selecciona un kit de inicio Mendix con poco código, se le guía para configurar su cuenta en Mendix Platform, iniciar el proyecto y seleccionar el destino de despliegue de Cloud Foundry o el clúster de Kubernetes.
{: shortdesc}

## Selección de un kit de inicio
{: #starterkit-mendix}

1. En el [panel de control de {{site.data.keyword.cloud_notm}} App Service](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"), pulse **Iniciación**.
2. Seleccione un kit de inicio de Mendix con poco código de una de las siguientes categorías:
  * [Móvil](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
  * [Watson Web o Mobile App](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
  * [App Web](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
3. Pulse **Crear app**.
4. En la página **Detalles de la app**, asigne un nombre a la app y, si lo desea, especifique etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).
5. Pulse **Crear**.

## Autorización a IBM para crear su proyecto en Mendix y para enlazar cuentas
{: #link-mendix-account}

Si aún no está utilizado Mendix con {{site.data.keyword.cloud_notm}}, se le guiará por la plataforma Mendix para que registre y autorice a {{site.data.keyword.cloud_notm}} a crear un nuevo proyecto en la plataforma Mendix en su nombre. Este proyecto está enlazado a {{site.data.keyword.cloud_notm}}, por lo que los despliegues se dirigen automáticamente a {{site.data.keyword.cloud_notm}}.

1. Si ve este mensaje, pulse **Enlazar cuenta**.
  ```
  "Para completar la creación de la app se necesita una cuenta de usuario de Mendix. ¿Desea enlazar su cuenta ahora?"
  ```
  {: screen}

2. En la página de confirmación de Mendix, seleccione **Acepto la política de privacidad y las condiciones de Mendix** y pulse **Confirmar**.
3. Cuando se le solicite, especifique su dirección de correo electrónico, su contraseña y su país, y luego pulse **Crear**.
4. En la página **Autorizar acceso a la cuenta de Mendix**, pulse **Autorizar**.

Una vez que se haya completado la autorización, el navegador vuelve a la app Mendix que está creando. Se abrirá la página **Seleccionar un destino de despliegue**.

## Selección de un destino de despliegue para la app Mendix
{: #select-deployment}

1. En la página **Seleccionar un destino de despliegue**, seleccione Cloud Foundry o uno de los clústeres de Kubernetes que se ejecutan en {{site.data.keyword.cloud_notm}}. Si la cuenta tiene acceso a {{site.data.keyword.cfee_full_notm}}, puede seleccionar el tipo de desplegador de Cloud Foundry **[nube pública](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** o **[entorno de empresa](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, que puede utilizar para crear y gestionar entornos aislados para alojar apps de Cloud Foundry exclusivamente para su empresa.
2. Opcional. Si no tiene un clúster de Kubernetes, puede crear uno ahora.
3. En la página **Configurar cadena de herramientas**, seleccione su región y grupo de recursos y, a continuación, pulse **Crear**.

Se crea una cadena de herramientas DevOps. La cadena de herramientas integra el proyecto Mendix dentro de la plataforma Mendix en el entorno de {{site.data.keyword.cloud_notm}}. Se despliega una app predeterminada en el destino de despliegue, de modo que pueda verificar que la app se ha desplegado correctamente al finalizar la cadena de herramientas DevOps.

Los despliegues de Mendix Cloud Foundry requieren el servicio de base de datos PostGRES, que no tiene un nivel Lite. Si desea evaluar los kits de inicio de Mendix utilizando una cuenta Lite, puede elegir como destino un clúster de Kubernetes de prueba.
{: tip}

Si ha seleccionado un clúster de Kubernetes para el despliegue, consulte la [guía de aprendizaje de Mendix Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube) para aprender a configurar el clúster para su uso en producción.

## Continuación con el ciclo de vida de desarrollo y de despliegue de Mendix
{: #dev-lifecycle-mendix}

Mendix es un entorno de creación con poco código. El ciclo de vida de desarrollo requiere que abra el proyecto en la app de escritorio Mendix Modeler.

1. Desde la app {{site.data.keyword.cloud_notm}}, pulse **Editar en Mendix**.
2. En el portal web de Mendix, pulse **Editar en Desktop Modeler**.
  La app Mendix se abre en el modelador de escritorio.
3. Edite la app Mendix y guarde los cambios.
4. Utilice el menú **Ejecutar** de la app Mendix Desktop Modeler y seleccione la opción **Ejecutar**.
  El paquete de despliegue se crea y se carga en Mendix. Una vez que se haya creado el paquete de despliegue, puede desplegar la app en {{site.data.keyword.cloud_notm}}.
5. Para desplegar la app Mendix, vuelva a la página **Detalles de app** en {{site.data.keyword.cloud_notm}} y pulse **Desplegar**.
  Esta acción inicia la cadena de herramientas de DevOps de la app, que obtiene el despliegue más reciente de Mendix y lo despliega en el entorno de destino. Una vez finalizado el despliegue, se inicia automáticamente la versión más reciente de la app y pasa a estar disponible.

Todas las apps Mendix se despliegan en {{site.data.keyword.cloud_notm}} pulsando **Configurar entrega continua** en la página **Detalles de app** en {{site.data.keyword.cloud_notm}}. No invoque manualmente cadenas de herramientas de Mendix a través de la interfaz de IBM DevOps. Si se inician manualmente cadenas de herramientas a través de la interfaz de DevOps, es posible que el despliegue falle debido a una falta de los metadatos necesarios que resultan críticos para los despliegues de Mendix. En función del estado de la app, es posible que se produzca un error durante el inicio de la cadena de herramientas de DevOps o un error en la app desplegada.

Si inicia manualmente una cadena de herramientas y se produce un error, puede restaurar la app pulsando **Configurar entrega continua** en la página **Detalles de la app** en {{site.data.keyword.cloud_notm}}. Esta acción desencadena un flujo de DevOps completo para la app Mendix, que incluye los metadatos necesarios.
{: tip}

## Opcional: configuración de {{site.data.keyword.cos_full_notm}} 
{: #mendix-cos}

Es posible que algunos usuarios deseen configurar su app Mendix desplegada para que utilice
{{site.data.keyword.cos_full}} para el almacenamiento persistente y la carga de archivos. {{site.data.keyword.cos_full_notm}} es un servicio de almacenamiento de objetos compatible con S3. Para hacer uso del almacenamiento de archivos compatible con S3, las apps Mendix deben definir las variables de entorno siguientes para acceder a una instancia de {{site.data.keyword.cos_full_notm}}, después de haber configurado la entrega continua:

* `S3_ACCESS_KEY_ID` - la clave S3, que forma parte de las credenciales de {{site.data.keyword.cos_full_notm}}
* `S3_SECRET_ACCESS_KEY` - la clave de secreto S3, que forma parte de las credenciales de {{site.data.keyword.cos_full_notm}}
* `S3_BUCKET_NAME` - el grupo de almacenamiento S3
* `S3_ENDPOINT` - el punto final de almacenamiento S3
* `S3_USE_V2_AUTH` - el valor es `true`

Para obtener más información sobre los grupos y claves de {{site.data.keyword.cos_full_notm}}, consulte la
[Documentación de la API de {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-gs-dev). Para obtener más información sobre los valores de puntos finales regionales y entre regiones, consulte la
[Documentación de {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints). Para obtener más información sobre el soporte de Mendix para almacenamiento compatible con S3, consulte la
[Documentación del paquete de compilación de Mendix](https://github.com/mendix/cf-mendix-buildpack#s3-settings){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo").

### Valores de {{site.data.keyword.cos_full_notm}} para apps de Cloud Foundry
{: cos-cfapps}

Realice estos pasos para los despliegues de Cloud Foundry:

1. Establezca estas variables de entorno en los despliegues de Cloud Foundry utilizando el mandato `cf set-env`:

  ```
    ibmcloud cf set-env <YOUR_APP> S3_ACCESS_KEY_ID <YOUR_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_SECRET_ACCESS_KEY <YOUR_SECRET_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_BUCKET_NAME <YOUR_BUCKET>
    ibmcloud cf set-env <YOUR_APP> S3_ENDPOINT s3.us-south.cloud-object-storage.appdomain.cloud
    ibmcloud cf set-env <YOUR_APP> S3_USE_V2_AUTH true
  ```

2. Después de especificar todos estos valores, vuelva a transferir la app de Cloud Foundry para que se apliquen los nuevos valores.

  ```
    ibmcloud cf restage <YOUR_APP>
  ```

### Valores de {{site.data.keyword.cos_full_notm}} para apps de Kubernetes
{: #cos-kubeapps}

Realice estos pasos para los despliegues de Kubernetes:

1. Establezca las variables de entorno `S3_ACCESS_KEY_ID` y `S3_SECRET_ACCESS_KEY` como valores de secreto de Kubernetes en el clúster. Para obtener más información sobre cómo crear secretos de Kubernetes, consulte la
[Documentación de {{site.data.keyword.containershort_notm}}](/docs/containers?topic=containers-service-binding#adding_app).

2. Además de los valores existentes, especifique las variables de entorno como variables de entorno adicionales en el archivo
`mendix-app.yaml` dentro de la carpeta `chart/<appname>/templates` del repositorio Git. Los nombres de secreto deben coincidir con los nombres que se crearon en el paso anterior.

  ```
    env:
      - name: S3_ACCESS_KEY_ID
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-key"
            key: db-endpoint
      - name: S3_SECRET_ACCESS_KEY
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-secret-key"
            key: db-endpoint
      - name: S3_ENDPOINT
        value: "s3.us-south.cloud-object-storage.appdomain.cloud"
      - name: S3_USE_V2_AUTH
        value: "true"
  ```

3. Una vez que se hayan aplicado los cambios de Kubernetes, vuelva a desplegar la app accediendo a la página
**Detalles de la app** y pulsando **Desplegar**. 

## Pasos siguientes 
{: #next-steps-mendix}

Para desplegar la app en {{site.data.keyword.containerlong_notm}}, configure la app para el despliegue en producción. Para obtener más información, consulte la [guía de aprendizaje de Mendix Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube). 
