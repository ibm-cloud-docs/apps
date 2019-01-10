---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creación de una app desde cero
{: #tutorial}

Puede crear una aplicación personalizada desde cero mediante servicios y un tiempo de ejecución. Decida la forma en la que instalar las herramientas que necesita, compile y ejecute la app localmente y despliéguela en la nube.
{: shortdesc}

## Paso 1. Instalar las herramientas
{: #install-tools}

Instale [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html).

Docker se instala como parte de las herramientas de desarrollador. Docker debe estar en ejecución para que funcionen los mandatos de compilación. Debe crear una cuenta de Docker, ejecutar la app de Docker e iniciar la sesión.

## Paso 2. Crear una app desde cero
{: #create-devex}

Cree una app personalizada en el panel de control de {{site.data.keyword.cloud}}:

1. En el panel de control de panel de control de [{{site.data.keyword.cloud}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}), seleccione **Crear** para crear una aplicación personalizada.

  También puede crear una app personalizada en la página [Kits de inicio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/appservice/starter-kits/) en {{site.data.keyword.dev_console}}, seleccione **Crear** para crear una aplicación personalizada.
  {: tip}

2. Especifique el nombre de la app. En esta guía de aprendizaje, utilice `CustomProject`.
3. Especifique un nombre de host exclusivo, por ejemplo, `abc-devhost`. Este nombre de host es la ruta de la app, `abc-devhost.mybluemix.net`
4. Seleccione el idioma y la infraestructura. Es posible que algunos kits de inicio solo estén disponibles en un idioma.
5. Seleccione el plan de precios. Puede utilizar la opción gratuita para esta guía de aprendizaje.
6. Pulse **Crear**.

## Paso 3. Añadir recursos (opcional)
{: #add-services}

Puede añadir recursos para mejorar la app con la potencia cognitiva de Watson, para añadir servicios móviles o servicios de seguridad. Para esta guía de aprendizaje, añada un lugar para gestionar los datos.

1. En la ventana de servicio de la app, pulse **Añadir recurso**.
2. Seleccione el tipo de servicio que desee. Por ejemplo, seleccione **Datos** > **Siguiente** > **Cloudant** > **Siguiente**.
3. Seleccione el plan de precios. Puede utilizar la opción gratuita para esta guía de aprendizaje.
4. Pulse **Crear**.

## Paso 4. Desplegar una cadena de herramientas de DevOps
{: #add-toolchain}

La habilitación de una cadena de herramientas crea un entorno de desarrollo en equipo para la app. Cuando se crea una cadena de herramientas, el servicio de app crea un repositorio Git, donde puede ver el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno de laboratorio Git dedicado y a un conducto de entrega continua. Se personalizan en la plataforma de despliegue que elija, ya sea Kubernetes o Cloud Foundry.

La entrega continua está habilitada para algunas aplicaciones. Puede habilitar la entrega continua para automatizar compilaciones, pruebas y despliegues a través de Delivery Pipeline y GitHub.

1. En la página Detalles de la app, pulse **Desplegar en la nube**.
2. Seleccione un método de despliegue. Configure el método de despliegue de acuerdo con las instrucciones correspondientes al método que elija:
  * Desplegar en un clúster Kubernetes. Cree un clúster de hosts, denominados nodos de trabajador, para desplegar y gestionar contenedores de aplicaciones de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente.
  * Desplegar con Cloud Foundry, donde no necesita gestionar la infraestructura subyacente.
  * Desplegar en una instancia de servidor virtual.

El despliegue de la app en la nube en el último paso crea automáticamente una cadena de herramientas. La cadena de herramientas crea un repositorio Git para la app en el que puede encontrar el código. Para obtener más información, consulte [Creación de cadenas de herramientas](/docs/services/ContinuousDelivery/toolchains_working.html).

## Paso 5. Creación y ejecución de la app localmente
{: #build-run}

También puede compilar la app localmente para probarla antes de enviarla por push a la nube.

1. En la ventana de servicio de la app, pulse **Descargar código** o **Clonar el repositorio** para trabajar con el código localmente.
2. Importe la app a su entorno de desarrollo integrado.
3. Modifique el código.
4. Configure [Autenticación de Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) añadiendo una señal de acceso personal.
5. Inicie sesión en la interfaz de línea de mandatos de {{site.data.keyword.Bluemix}}. Si su organización utiliza inicios de sesión federados, utilice la opción `-sso`.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Establezca los destinos de org y de espacio.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Obtener las credenciales.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Asegúrese de que Docker se esté ejecutando y cree la app en un contenedor de desarrollo local desde el directorio.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Ejecute la app en un contenedor de desarrollo local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Abra el navegador en `http://localhost:3000`. Es posible que el número de puerto sea distinto en función del tiempo de ejecución elegido.

## Paso 6. Desplegar la app
{: #deploy}

### Desplegar una cadena de herramientas de DevOps

Puede desplegar la app en {{site.data.keyword.cloud_notm}} de varias formas, pero una cadena de herramientas de DevOps es la mejor forma de desplegar apps de producción. Con una cadena de herramientas de DevOps, puede automatizar fácilmente despliegues en muchos entornos y añadir rápidamente servicios de supervisión, de registro y de alertas para ayudar a gestionar su app a medida que crece.

Con una cadena de herramientas correctamente configurada, un ciclo de despliegue de compilación empieza automáticamente después de cada fusión en la rama maestra en su repositorio. Todas las cadenas de herramientas creadas a partir de un panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.

También puede desplegar manualmente su app desde su cadena de herramientas de DevOps:

1. En la ventana Detalles de la app, pulse **Ver cadena de herramientas**.
2. Pulse **Conducto de entrega** donde puede iniciar compilaciones, gestionar el despliegue y ver registros e historiales.

Para obtener más información, consulte [Creación y despliegue](/docs/services/ContinuousDelivery/pipeline_build_deploy.html).

### Desplegar utilizando el {{site.data.keyword.dev_cli_short}}

Para desplegar la app en Cloud Foundry, especifique el mandato siguiente:
```
ibmcloud dev deploy
```
{: pre}

Para desplegar la app en un clúster de Kubernetes, especifique el mandato siguiente:
```
ibmcloud dev deploy --target <container>
```
{: pre}

## Paso 7. Verificar que la app se está ejecutando
{: #verify}

Después de desplegar la app, el conducto o la línea de mandatos de DevOps le apunta al URL para la app, por ejemplo `abc-devhost.mybluemix.net`. Vaya a ese URL en el navegador.
