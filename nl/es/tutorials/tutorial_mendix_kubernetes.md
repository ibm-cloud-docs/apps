---

copyright:
  years: 2018
lastupdated: "2018-11-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Despliegue de la app Mendix en {{site.data.keyword.containerlong_notm}}
{: #getting-started}

De forma predeterminada, las aplicaciones Mendix que se despliegan en {{site.data.keyword.containerlong}} se configuran en una modalidad de evaluación. Esta modalidad le permite empezar a crear una aplicación rápidamente y desplegarla en la nube, pero no configura la persistencia de datos ni las configuraciones de Kubernetes avanzadas. Esta guía de aprendizaje le guía a través de la configuración de un entorno de producción configurando un volumen de almacenamiento persistente en Kubernetes con el servicio {{site.data.keyword.cos_full_notm}} .
{: shortdesc}

## Antes de empezar
{: #prerequisites}

- Ejecute la app Mendix. Consulte [Creación de apps Mendix](/docs/apps/tutorials/tutorial_mendix_getting_started.html) para obtener más información.
- Instale la [interfaz de línea de mandatos (CLI) de {{site.data.keyword.dev_cli_notm}}](/docs/cli/index.html), que incluye la CLI de {{site.data.keyword.containershort_notm}}.
- Inicie una sesión en la CLI de `ibmcloud` y configure `kubectl` para el [acceso al clúster de Kubernetes](/docs/containers/cs_tutorials.html#cs_cluster_tutorial_lesson3).

## Creación de una instancia del servicio Cloud Object Storage
{: #cloud-object-storage}

Empiece desde la página de detalles de la aplicación y siga los pasos siguientes:
1. Pulse **Añadir recurso**.
2. Seleccione **Almacenamiento** y pulse **Siguiente**.
3. A continuación, seleccione la opción **Cloud Object Storage** y pulse **Siguiente**.
4. Aparecerán los planes de precios para la instancia de {{site.data.keyword.cos_full_notm}}. Seleccione el plan de precios que mejor se adapte a sus necesidades y luego pulse **Crear** para crear una instancia del servicio {{site.data.keyword.cos_full_notm}} para utilizarla con la aplicación Mendix.

  Si prefiere utilizar una instancia existente del servicio {{site.data.keyword.cos_full_notm}}, pulse **Añadir recurso** y seleccione la instancia existente para que la utilice la aplicación.
  {: tip}

## Creación de un grupo de almacenamiento
{: #storage-bucket}

Cuando haya asociado una instancia del servicio {{site.data.keyword.cos_full_notm}} a su aplicación Mendix, debe crear un grupo de almacenamiento en el que guardar los datos. Para crear un grupo, pulse **...** para la instancia de {{site.data.keyword.cos_full_notm}} y seleccione **Abrir panel de control**.  

Se abre el panel de control del servicio {{site.data.keyword.cos_full_notm}} en una ventana nueva, en el separador **Grupos**. Pulse **Crear grupo** y siga los pasos para crear un grupo utilizando un nombre exclusivo. En esta guía de aprendizaje creará un grupo llamado `my-mendix-bucket`.

## Configuración del almacenamiento persistente
{: #kubernetes-storage}

A continuación, siga la documentación correspondiente a [Almacenamiento de datos en {{site.data.keyword.cos_full_notm}}](/docs/containers/cs_storage_cos.html). Se crea `PersistentVolumeClaim` y `PersistentVolume` en el clúster de Kubernetes, que puede utilizar la instancia de la base de datos PostGres que se ejecuta en el clúster como parte de la aplicación Mendix. Asegúrese de crear `PersistentVolumeClaim` utilizando el contenedor `my-mendix-bucket`, tal como se describe en el paso anterior y revise el nombre `PersistentVolumeClaim` para utilizarlo en el paso siguiente.

## Edición del archivo `postgres-deployment.yaml`
{: #postgres-deployment}

Una vez que se ha configurado un volumen persistente para el clúster de Kubernetes, el paso siguiente consiste en modificar el despliegue de la base de datos PostGres que se está ejecutando en el clúster. En primer lugar, debe editar los archivos del repositorio Git que se han creado como parte del paso de integración de la cadena de herramientas de IBM DevOps. Para encontrar el repositorio Git, vuelva a la página de detalles de la app y pulse el enlace URL de Git desde el mosaico **Detalles de despliegue**.  

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
{: #redeploy}

Cuando los cambios en el archivo `postgres-deployment.yaml` se hayan configurado en el repositorio, se desencadena automáticamente una nueva ejecución de la interconexión DevOps. Sin embargo, vuelve a desplegar la aplicación predeterminada. Debe volver a desplegar la versión más reciente de la aplicación Mendix para que se despliegue la última versión de la aplicación con los últimos cambios de volumen persistente.

Para volver a desplegar, vaya a la página de detalles de la aplicación y pulse **Desplegar aplicación** en el mosaico **Detalles de despliegue**. Si el despliegue falla dentro de la cadena de herramientas de DevOps con un error que indica que no se puede encontrar el archivo `.mda` de la aplicación, debe volver a exportarlo desde Mendix. Para ello, exporte desde la aplicación de escritorio de Mendix Modeler o bien pulse **Editar en Mendix**. A continuación, dentro de la interfaz web de Mendix, vaya a la sección **Entornos** y siga los pasos que se indican después de pulsar **Crear paquete desde el servidor de equipo**. Una vez que la aplicación se haya exportado desde Mendix, vuelva a la página de detalles de la aplicación y pulse **Desplegar aplicación** de nuevo. La última aplicación exportada se despliega en el clúster de Kubernetes utilizando la cadena de herramientas DevOps de {{site.data.keyword.cloud_notm}}. Una vez el despliegue finaliza correctamente, la aplicación está activa y lista para su uso en producción.

## Información adicional
{: #additional-information}

Para obtener más información sobre la ejecución de aplicaciones Mendix en entornos de Kubernetes, revise la sección [Ejecutar Mendix en Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes) de la documentación de usuario de Mendix.
