---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: apps, mendix, mendix app, deploy, cos, storage bucket, devops toolchain, deploy, kubernetes, kube

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Despliegue de la app Mendix en {{site.data.keyword.containerlong_notm}}
{: #deploy-mendix-kube}

De forma predeterminada, las aplicaciones Mendix que se despliegan en {{site.data.keyword.containerlong}} se configuran en una modalidad de evaluación. Esta modalidad le permite empezar a crear una app rápidamente y desplegarla en la nube, pero no configura la persistencia de datos ni las configuraciones de Kubernetes avanzadas. Esta guía de aprendizaje le guía a través de la configuración de un entorno de producción configurando un volumen de almacenamiento persistente en Kubernetes con el servicio {{site.data.keyword.cos_full_notm}}.
{: shortdesc}

## Antes de empezar
{: #prereqs-mendix-kube}

* Ejecute la app Mendix. Consulte [Creación de apps Mendix](/docs/apps/tutorials?topic=creating-apps-create-mendix) para obtener más información.
* Instale la [interfaz de línea de mandatos (CLI) de {{site.data.keyword.dev_cli_notm}}](/docs/cli?topic=cloud-cli-getting-started), que incluye la CLI de {{site.data.keyword.containershort_notm}}.
* Inicie una sesión en la CLI de `ibmcloud` y configure `kubectl` para el [acceso al clúster de Kubernetes](/docs/containers?topic=containers-cs_cluster_tutorial#cs_cluster_tutorial_lesson3).

## Creación de una instancia del servicio Cloud Object Storage
{: #cos-mendix-kube}

Empiece desde la página **Detalles de la app** y utilice los pasos siguientes:
1. Pulse **Añadir servicio**.
2. Seleccione **Almacenamiento** y pulse **Siguiente**.
3. A continuación, seleccione la opción **Cloud Object Storage** y pulse **Siguiente**.
4. Aparecerán los planes de precios para la instancia de {{site.data.keyword.cos_full_notm}}. Seleccione el plan de precios que mejor se adapte a sus necesidades y luego pulse **Crear** para crear una instancia del servicio {{site.data.keyword.cos_full_notm}} para utilizarla con la app Mendix.

  Si prefiere utilizar una instancia existente del servicio {{site.data.keyword.cos_full_notm}}, pulse **Añadir servicio** y seleccione la instancia existente para que la utilice la app.
  {: tip}

## Creación de un grupo de almacenamiento
{: #storage-bucket-mendix-kube}

Cuando haya asociado una instancia del servicio {{site.data.keyword.cos_full_notm}} a su app Mendix, debe crear un grupo de almacenamiento en el que guardar los datos. Para crear un grupo, pulse **...** para la instancia de {{site.data.keyword.cos_full_notm}} y seleccione **Abrir panel de control**.  

Se abre el panel de control del servicio {{site.data.keyword.cos_full_notm}} en una ventana nueva, en el separador **Grupos**. Pulse **Crear grupo** y siga los pasos para crear un grupo utilizando un nombre exclusivo. En esta guía de aprendizaje creará un grupo llamado `my-mendix-bucket`.

## Configuración del almacenamiento persistente
{: #kube-storage-mendix}

A continuación, siga la documentación correspondiente a [Almacenamiento de datos en {{site.data.keyword.cos_full_notm}}](/docs/containers?topic=containers-object_storage). Se crea `PersistentVolumeClaim` y `PersistentVolume` en el clúster de Kubernetes, que puede utilizar la instancia de la base de datos PostGres que se ejecuta en el clúster como parte de la app Mendix. Asegúrese de crear `PersistentVolumeClaim` utilizando el grupo `my-mendix-bucket`, tal como se describe en el paso anterior y revise el nombre `PersistentVolumeClaim` para utilizarlo en el paso siguiente.

## Edición del archivo `postgres-deployment.yaml`
{: #postgres-deploy-mendix}

Una vez que se haya configurado un volumen persistente para el clúster de Kubernetes, el paso siguiente consiste en modificar el despliegue de la base de datos PostGres que se está ejecutando en el clúster. En primer lugar, debe editar los archivos del repositorio Git que se han creado como parte del paso de integración de la cadena de herramientas de IBM DevOps. Para encontrar el repositorio Git, vuelva a la página **Detalles de la app** y pulse el enlace URL de Git desde el mosaico **Detalles de despliegue**.

Puede clonar el repositorio Git en la máquina local o realizar los cambios siguientes en el editor en línea. Abra el archivo `chart/{app name}/templates/postgres-deployment.yaml` (sustituya `{app name}` por el nombre de su app Mendix). El archivo no tiene entradas `volumeMount` ni `volumes` de forma predeterminada, de modo que todos los datos se almacenan en la memoria dentro del pod de despliegue en ejecución. Debe añadir las entradas `volumeMount` y `volumes` al archivo `deployment.yaml` de Kubernetes para que los datos se guarden en el grupo {{site.data.keyword.cos_full_notm}} y no se pierdan si se reinicia el pod. 

Consulte el siguiente archivo `postgres-deployment.yaml` de ejemplo que incluye las entradas `volumeMount` y `volumes`.  
```yaml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: "{appname}-postgres"
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: "{appname}-postgres"
    spec:
      containers:
        - name: "{appname}-postgres"
          image: postgres:10.1
          ports:
            - containerPort: 5432
          env:
            - name: POSTGRES_DB
              value: db0
            - name: POSTGRES_USER
              value: mendix
            - name: POSTGRES_PASSWORD
              value: mendix
          volumeMounts:
            - mountPath: "/var/lib/postgresql/data"
              name: "mendix-data"
      volumes:
        - name: mendix-data
          persistentVolumeClaim:
            claimName: {pvc-name}
```

Asegúrese de sustituir `{pvc-name}` por el nombre de su `PersistentVolumeClaim` del paso anterior y tenga cuidado en no sobrescribir el nombre de su app, que ya está definido en el archivo dentro del repositorio Git. A continuación, confirme los cambios en el repositorio Git.

## Cómo volver a desplegar
{: #redeploy-mendix-kube}

Cuando los cambios en el archivo `postgres-deployment.yaml` se hayan confirmado en el repositorio, se desencadena automáticamente una nueva ejecución de la interconexión DevOps. Sin embargo, vuelve a desplegar la app predeterminada. Debe volver a desplegar la versión más reciente de la app Mendix para que se despliegue la última versión de la app con los últimos cambios de volumen persistente.

Para volver a realizar el despliegue, vaya a la página **Detalles de la app** y pulse
**Configurar entrega continua** dentro del mosaico **Desplegar la app**. Si el despliegue falla dentro de la cadena de herramientas de DevOps con un error que indica que no se puede encontrar el archivo `.mda` de la app, debe volver a exportarlo desde Mendix. Para ello, exporte desde la app de escritorio de Mendix Modeler o bien pulse **Editar en Mendix**. A continuación, dentro de la interfaz web de Mendix, vaya a la sección **Entornos** y siga los pasos que se indican después de pulsar **Crear paquete desde el servidor de equipo**. Una vez que la app se haya exportado de Mendix, vuelva a la página **Detalles de la app** y pulse **Configurar entrega continua** de nuevo. La última app exportada se despliega en el clúster de Kubernetes utilizando la cadena de herramientas DevOps de {{site.data.keyword.cloud}}. Una vez el despliegue finaliza correctamente, la app está activa y lista para su uso en producción.

## Verificación de que la app se está ejecutando
{: #verify-mendix-kube}

Después de desplegar la app, el conducto de entrega o la línea de mandatos le apunta al URL para la app.

1. Desde la cadena de herramientas de DevOps, pulse **Delivery Pipeline** y luego seleccione **Etapa de despliegue**.
2. Pulse **Ver registros e historial**.
3. En el archivo de registro, busque el URL de la app:

    Al final del archivo de registro, busque la palabra `urls` o `ver`. Por ejemplo, es posible que vea una línea en el archivo de registro parecida a `urls: my-app-devhost.mybluemix.net` o a `Ver el estado de la aplicación en: http://<ipaddress>:<port>/health`.

4. Vaya al URL en el navegador. Si la app se está ejecutando, se muestra un mensaje que incluye `Enhorabuena` o `{"status":"UP"}`.

Si utiliza la línea de mandatos, ejecute el mandato [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para ver el URL de la app. Luego vaya al URL en el navegador.

## Información adicional
{: #more-info-mendix-kube}

Para obtener más información sobre la ejecución de apps Mendix en entornos de Kubernetes, revise la sección
[Ejecutar Mendix en Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo") de la documentación de usuario de Mendix.
