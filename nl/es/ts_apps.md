---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-23"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Resolución de problemas de creación de apps
{: #managingapps}

Entre los problemas generales relacionados con la creación de apps se pueden incluir las apps que no se pueden actualizar y los caracteres de doble byte que no se visualizan. En muchos de los casos, puede solucionar estos problemas siguiendo unos sencillos pasos.
{:shortdesc}

## Hay cambios sin guardar
{: #ts_unsaved_changes}
{: troubleshoot}

Cuando pulse sobre elementos en la página de detalles de apps, es posible que no pueda realizar las acciones. También es posible que se le solicite que guarde los cambios para poder continuar.

Cuando intenta comprobar la app o los servicios en la página de detalles de la app, se muestra el siguiente mensaje de error:
{: tsSymptoms}

`Tiene cambios sin guardar. ¿Está seguro de que desea abandonar esta página?`

Cuando desplace el ratón sobre los campos **INSTANCIAS** o **CUOTA DE MEMORIA** del panel de tiempo de ejecución, los valores cambiarán. Este comportamiento es así por diseño. Sin embargo, se le solicitará que guarde los valores de instancia o de memoria para poder ir a otra página.
{: tsCauses}

Cierre el diálogo de mensaje y pulse **RESTABLECER** en el panel de tiempo de ejecución.
{: tsResolve}

## La migración tras error automática entre regiones de {{site.data.keyword.cloud_notm}} no está disponible
{: #ts_failover}
{: troubleshoot}

No puede utilizar la migración tras error automática entre regiones de {{site.data.keyword.cloud}}. Sin embargo, puede utilizar un proveedor de DNS que dé soporte a la migración tras error entre varias direcciones IP como solución temporal.

Cuando una región de {{site.data.keyword.cloud_notm}} deja de estar disponible, las apps que se ejecutan en dicha región tampoco están disponibles, aunque las mismas apps se estén ejecutando en otra región de {{site.data.keyword.cloud_notm}}.
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} aún no proporciona migración tras error automática entre una región y otra.
{: tsCauses}

Puede utilizar un proveedor de DNS que dé soporte a la migración tras error inteligente entre muchas direcciones ID y configurar manualmente los valores de DNS para habilitar la migración tras error automática entre regiones de {{site.data.keyword.cloud_notm}}. Disponen de esta función los proveedores de DNS NSONE, Akamai y Dyn.
{: tsResolve}

Cuando configure los valores de DNS, debe especificar las direcciones IP públicas de las regiones de {{site.data.keyword.cloud_notm}} en la que se ejecutan sus apps. Para obtener la dirección IP pública de una región de {{site.data.keyword.cloud_notm}}, utilice el mandato `nslookup`. Por ejemplo, puede escribir el siguiente mandato en una ventana de línea de mandatos.
```
nslookup cloud.ibm.com
```
{: codeblock}

## No se puede acceder a los servicios de {{site.data.keyword.cloud_notm}} debido a errores de autorización
{: #ts_vcap}
{: troubleshoot}

Se pueden producir errores de autorización cuando la app accede con un servicio de {{site.data.keyword.cloud_notm}} y las credenciales del servicio están codificadas en la app.

Después de configurar su app para comunicarse con un servicio de {{site.data.keyword.cloud_notm}}, despliega la app en {{site.data.keyword.cloud_notm}}. Sin embargo, no puede utilizar la app para acceder al servicio de {{site.data.keyword.cloud_notm}} y recibe un error de autorización.
{: tsSymptoms}

Las credenciales codificadas de la app podrían no ser correctas. Cada vez que el servicio se vuelve a crear, las credenciales para acceder a él cambian.
{: tsCauses}

En lugar de codificar las credenciales en la app, utilice parámetros de conexión de la variable de entorno VCAP_SERVICES. Los métodos para utilizar los parámetros de conexión de la variable de entorno VCAP_SERVICES varían en función de los lenguajes de programación. Por ejemplo, para las apps Node.js, puede utilizar el siguiente mandato:
{: tsResolve}

```
process.env.VCAP_SERVICES
```

Para obtener más información sobre los mandatos que puede utilizar en otros lenguajes de programación, consulte [Java](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") y [Ruby](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").

## Se han recibido errores 502 de pasarela errónea
{: #ts_502_error}
{: troubleshoot}

Si recibe errores `502 Bad Gateway` al interactuar con apps en {{site.data.keyword.cloud_notm}}, compruebe la página de estado de {{site.data.keyword.cloud_notm}} y, a continuación, tome las medidas apropiadas.

Recibe mensajes de error que empiezan por 502 Bad Gateway. Por ejemplo, puede que vea `502 Bad Gateway: Registered endpoint failed to handle the request.`
{: tsSymptoms}

Los errores de pasarela errónea suelen ocurrir cuando va a un sitio web que utiliza un servidor proxy para almacenar y retransmitir los datos desde el servidor principal que aloja el sitio. Es posible que el servidor principal y el servidor proxy no se conecten correctamente. Por eso, ve el código de error de HTTP 502 en la ventana del navegador. Este código de estado indica que el servidor principal del sitio no ha recibido la implementación de HTTP que se esperaba del servidor proxy.
{: tsCauses}

Otras causas menos habituales de un error de pasarela errónea son caídas del ISP (proveedor de servicios de Internet), configuraciones erróneas de cortafuegos y errores de caché de navegador.

Si sospecha que un servicio de {{site.data.keyword.cloud_notm}} está inactivo, consulte primero la página [Estado de {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/status){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"). Una solución temporal podría ser [utilizar el servicio en otra región de {{site.data.keyword.cloud_notm}}](/docs/resources/connect_external_app?topic=resources-externalapp){: new_window}. Si el estado del servicio es normal, pruebe los pasos siguientes para resolver el problema:
{: tsResolve}

  * Reintente la acción:
    * Para volver a cargar la página, pulse F5 en el teclado o bien pulse **Renovar**. Si este paso no funciona, borre las cookies y la memoria caché del navegador y recargue de nuevo.
    * Utilice otro navegador.
    * Reinicie el direccionador, el módem y el sistema. Rearrancar estos dispositivos puede borrar varios errores que provocan el error 502.
  * Espere y vuelva a intentarlo más adelante. Es posible que se produzcan problemas temporales en el proveedor de servicios de Internet o en los servicios de {{site.data.keyword.cloud_notm}}. Puede esperar a que se resuelvan los problemas temporales.
  * Si el problema todavía existe, póngase en contacto con el equipo de soporte de {{site.data.keyword.cloud_notm}}. Consulte el apartado sobre [Cómo ponerse en contacto con el equipo de soporte de {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") para obtener más información.

## Las apps de Android no pueden recibir {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

En determinadas regiones en las que no se puede acceder a Google, las apps de Android no pueden recibir notificaciones enviadas a través del servicio IBM {{site.data.keyword.mobilepushshort}}. En este caso, un método alternativo consiste en utilizar servicios de terceros.

Enlaza un servicio {{site.data.keyword.mobilepushshort}} con la app de {{site.data.keyword.cloud_notm}} y envía un mensaje a los dispositivos registrados. No obstante, las apps que se desarrollan en Android no pueden recibir notificaciones en determinadas regiones.
{: tsSymptoms}

El servicio IBM {{site.data.keyword.mobilepushshort}} utiliza Google Cloud Messaging (GCM) para enviar notificaciones a apps móviles desarrolladas en Android. Para permitir que las apps de Android reciban notificaciones, se debe poder acceder al servicio Google Cloud Messaging (GCM) en las apps móviles. En regiones en las que las apps Android no pueden acceder al servicio GCM, las apps Android no pueden recibir {{site.data.keyword.mobilepushshort}}.
{: tsCauses}

Como método alternativo, utilice servicios de tercero que no se basen en el servicio GCM, como por ejemplo, [Pushy](https://pushy.me){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"), [getui](http://www.getui.com/){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") y [jpush](https://www.jpush.cn/){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").
{: tsResolve}

## Los caracteres de doble byte no se visualizan correctamente cuando se envían por push apps a {{site.data.keyword.cloud_notm}}
{: #ts_doublebytes}
{: troubleshoot}

Es posible que los caracteres de doble byte no se visualicen correctamente si el soporte de Unicode no está configurado correctamente para el servlet o los archivos JSP.

Cuando se envía una aplicación a {{site.data.keyword.cloud_notm}}, los caracteres de doble byte especificados dentro de la app no se visualizan correctamente.
{: tsSymptoms}

El problema puede ocurrir si el soporte de Unicode no está configurado correctamente para el servlet o los archivos JSP.
{: tsCauses}

Puede utilizar el código siguiente en el servlet o archivo JSP:
{: tsResolve}

  * En el archivo de origen del servlet
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * En el JSP
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## No se pueden desplegar las apps Node.js
{: #ts_nodejs_deploy}
{: troubleshoot}

Es posible que tenga problemas si actualiza una app Node.js o despliega una app Node.js en {{site.data.keyword.cloud_notm}}.

Si actualiza una app Node.js o despliega una app Node.js en {{site.data.keyword.cloud_notm}}, es posible que reciba uno de los siguientes mensajes de error:
{: tsSymptoms}

`Ningún paquete de compilación disponible ha detectado correctamente una app.`

`La instancia (índice 0) no ha podido empezar a aceptar conexiones.`

`No se pueden obtener instancias debido a un error de transferencia.`

A continuación se detallan las causas posibles:
{: tsCauses}

  * No se ha especificado el mandato start.
  * Faltan archivos necesarios para desplegar una app Node.js o bien se encuentran en una carpeta que no es el directorio raíz.

Utilice uno de los métodos siguientes en función de la causa del problema:
{: tsResolve}

  * Especifique el mandato start siguiendo uno de estos métodos:
     * Utilice la interfaz de línea de mandatos de Cloud Foundry. Por ejemplo:
      ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		  ```
      {: codeblock}

    * Utilice el archivo [package.json](https://www.npmjs.com/package/jsonfile){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"). Por ejemplo:
	    ```json
		  {
        ...
  	    "scripts": {
	 		  "start": "node app.js"
 	    }
	    }
	    ```

    * Utilice el archivo `manifest.yml`. Por ejemplo:
	    ```
		  applications:
      name: MyUniqueNodejs01
      ...
      command: node app.js
      ...
      ```

  * Asegúrese de que exista un archivo `package.json` en la app Node.js para que el paquete de compilación Node.js pueda reconocer la app. Asegúrese de que este archivo esté en el directorio raíz de la app.
    El ejemplo siguiente muestra un archivo `package.json` sencillo:
	```json
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

Para ver más sugerencias sobre las apps Node.js, consulte [Consejos para las aplicaciones Node.js](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").

## Aparecen errores de configuración en el archivo `server.xml` después de importar una app {{site.data.keyword.cloud_notm}} Liberty en Eclipse
{: #ts_eclipse}
{: troubleshoot}

Si ve errores de configuración en el archivo `server.xml` después de importar una app {{site.data.keyword.cloud_notm}} Liberty en Eclipse, es posible que tenga que eliminar el archivo `server.xml` del proyecto.

Después de importar una app {{site.data.keyword.cloud_notm}} Liberty en Eclipse, verá errores de configuración en el archivo `server.xml` en la vista Problemas de Eclipse.
{: tsSymptoms}

El paquete de compilación de Liberty utiliza el archivo `server.xml` para configurar la app y genera un archivo `runtime-vars.xml` cuando la app Liberty se envía a {{site.data.keyword.cloud_notm}}. Cuando importa la app en Eclipse, el archivo `runtime-vars.xml` no existe en el entorno local.
{: tsCauses}

Puede resolver este problema eliminando el archivo server.xml del proyecto. El paquete de compilación crea el archivo `server.xml` de forma dinámica cuando se envía la app como una app WAR. Para obtener más información, consulte el apartado [Liberty for Java](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime).
{: tsResolve}

## No se pueden transferir las apps utilizando paquetes de compilación personalizados
{: #ts_bp_compilation}
{: troubleshoot}

Es posible que no pueda desplegar una app en {{site.data.keyword.cloud_notm}} con un paquete de compilación personalizado si los scripts del paquete de compilación no son archivos ejecutables.

Si despliega una app en {{site.data.keyword.cloud_notm}} con un paquete de compilación personalizado, verá el mensaje de error `La aplicación no se ha podido transferir, por lo que no hay instancias que mostrar.`
{: tsSymptoms}

Este problema puede suceder si los scripts, como el script de detección, el script de compilación y el script de liberación, no son ejecutables.
{: tsCauses}

Puede utilizar el mandato [Git update](http://git-scm.com/docs/git-update-index){: new_window} ![icono de enlace externo](../icons/launch-glyph.svg "icono de enlace externo") para cambiar el permiso de cada script por ejecutable. Por ejemplo, puede escribir `git update --chmod=+x script.sh`.
{: tsResolve}

## No puede desplegar una app desde Delivery Pipeline en {{site.data.keyword.cloud_notm}} Continuous Delivery
{: #ts_devops_to_bm}
{: troubleshoot}

 Es posible que no pueda desplegar su app con {{site.data.keyword.deliverypipeline}} en {{site.data.keyword.contdelivery_short}} si el archivo `manifest.yml` no está presente en su app.

 Cuando se despliega una app con {{site.data.keyword.deliverypipeline}} en {{site.data.keyword.contdelivery_short}}, podría visualizarse el mensaje de error `No es posible detectar un tipo de aplicación soportada`.
 {: tsSymptoms}

 Este problema podría deberse a que el conducto necesita un archivo `manifest.yml` para desplegar una app en {{site.data.keyword.cloud_notm}}.
 {: tsCauses}

 Para solucionar este problema, debe crear un archivo `manifest.yml`. Para obtener más información sobre cómo crear un archivo `manifest.yml`, consulte [Manifiesto de aplicación](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).
 {: tsResolve}

## Se ha superado la cuota de almacenamiento
{: #exceed_quota}

Si los trabajos de compilación o de despliegue fallan y ve el siguiente mensaje, puede suprimir las imágenes con los siguientes mandatos de la CLI. `Status: unauthorized: Ha superado su cuota de almacenamiento. Suprima una o varias imágenes, o bien revise su cuota de almacenamiento y su plan de precios.`

* Instale la [CLI de {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) si aún no la tiene.
* Inicie una sesión en {{site.data.keyword.cloud_notm}} mediante el mandato `ibmcloud login` y haga que apunte al espacio en el que se encuentra.
* Obtenga una lista de sus imágenes mediante `ibmcloud cr images`.
* Suprima las imágenes que no utilice con el mandato `ibmcloud cr image-rm <respository>:<tag>`.
* Vuelva a ejecutar el trabajo de compilación o de despliegue que ha fallado.

## Acceso a los registros de Kubernetes
{: #access_kube_logs}

Si la aplicación no se está ejecutando y no puede acceder al punto final de estado, intente examinar los registros del clúster.
* Instale la [CLI de {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) si aún no la tiene.
* Inicie una sesión en {{site.data.keyword.cloud_notm}} mediante el mandato `ibmcloud login` y haga que apunte al espacio en el que se encuentra.
* Obtenga una lista de sus clústeres mediante `ibmcloud cs clusters`,
* Apunte al clúster correspondiente mediante el mandato `ibmcloud cs cluster-config <cluster-name>`.
* Exporte la variable de entorno que aparece en la lista.
* Vea los pods con `kubectl get pods`. Si tiene que instalar `kubectl`, consulte el apartado sobre cómo [Instalar y configurar kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").
* Puede ver los registros en la app con el mandato `kubectl logs <pod-name>.`

## El inicio de `docker` falla con el mensaje "no se ha encontrado el archivo"
{: #docker_not_found}
{: troubleshoot}

Cuando intenta iniciar Docker, aparece el mensaje de error siguiente:
{: tsSymptoms}

```
An error exec: "docker": executable file not found in $PATH was encountered while building the Docker image.
```
{: screen}

El cliente de Docker no está instalado, o está instalado pero no se ha iniciado.
{: tsCauses}

Asegúrese de que [Docker](https://docs.docker.com/install/){: new_window}![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") está instalado e inícielo.
{: tsResolve}

## La compilación de una app falla con un error de Docker
{: #build_error}
{: troubleshoot}

Cuando intenta crear una app con el mandato `ibmcloud dev build`, falla con un error de nombre de usuario o contraseña de Docker. 
{: tsSymptoms}

Se están utilizando credenciales de Docker Hub incorrectas para la autenticación. 
{: tsCauses}

Finalice la sesión de Docker Hub en el cliente de Docker.
{: tsResolve}


