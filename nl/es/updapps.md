---

copyright:
  years: 2015, 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Actualización de apps
{: #updatingapps}

Puede utilizar la línea de mandatos o {{site.data.keyword.Bluemix}} Continous Delivery para actualizar las aplicaciones en {{site.data.keyword.Bluemix_notm}}. En muchos casos, incluso para los paquetes de compilación integrados como Node.js, también debe escribir un parámetro -c para especificar el mandato que se sebe utilizar para iniciar la aplicación.
{:shortdesc}

##Creación y utilización de un dominio personalizado
{: #domain}

Para apps de CF y grupos de contenedores, puede utilizar un dominio personalizado en el URL de la aplicación en lugar del dominio del sistema {{site.data.keyword.Bluemix_notm}} predeterminado, que es mybluemix.net.

Los dominios proporcionan la ruta al URL asignado a la organización en {{site.data.keyword.Bluemix_notm}}. Para utilizar un dominio personalizado, debe registrar el dominio personalizado en un servidor DNS público, configurar el dominio personalizado en {{site.data.keyword.Bluemix_notm}} y, a continuación, correlacionar el dominio personalizado con el dominio del sistema {{site.data.keyword.Bluemix_notm}} en el servidor DNS público. Después de correlacionar el dominio personalizado con el dominio del sistema {{site.data.keyword.Bluemix_notm}}, las solicitudes correspondientes al dominio personalizado se direccionan a la aplicación en {{site.data.keyword.Bluemix_notm}}.

Para crear y utilizar un dominio personalizado en {{site.data.keyword.Bluemix_notm}} puede utilizar la interfaz de usuario de {{site.data.keyword.Bluemix_notm}} o la interfaz de línea de mandatos bluemix.

### Si utiliza la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}:

  1. Cree un dominio personalizado para la organización.

	1. Vaya a **Gestionar** &gt; **Cuenta** &gt; **Organizaciones de Cloud Foundry** &gt; **Ver detalles** para su organización. A continuación, pulse **Editar organización de Cloud Foundry** &gt; **Dominios**.

	2. En el separador **DOMINIOS**, pulse **AÑADIR DOMINIO** y escriba el nombre del dominio personalizado y pulse **GUARDAR**.

	**Nota**: por ejemplo, puede utilizar `mycompany.com` para asociar la ruta `www.mycompany.com` a su app. También puede utilizar `example.mycompany.com` para asociar la ruta `www.example.mycompany.com` a su app.

  2. Añada la ruta con el dominio personalizado a una aplicación.

    1. Pulse el icono **Menú** ![Icono Menú](../icons/icon_hamburger.svg) &gt; **Panel de control** y pulse la fila de la aplicación a la que desee añadir la ruta. Se muestra la página **Visión general**.

	2. Desde el menú **Rutas**, seleccione **Editar rutas**.

	3. Pulse **Añadir ruta** y especifique la ruta que desea utilizar para la aplicación.
	4. Pulse **Guardar**.

### Utilice la interfaz de línea de mandatos bluemix:

  1. Cree un dominio personalizado para la organización con el siguiente mandato:

    ```
    bluemix app domain-create <your org name> mydomain
    ```

    *organization_name*: El nombre de la organización.

    *mydomain*: El nombre de dominio personalizado que desea utilizar.

  2. Añada la ruta con el dominio personalizado a una aplicación. Para apps CF, escriba el siguiente mandato:

    ```
    bluemix app route-map myapp mydomain -n host_name
    ```

    Para grupos de contenedor, escriba el siguiente mandato:
     ```
     cf ic route map -n host_name -d mydomain mycontainergroup
     ```

    *myapp*: Para apps de CF, el nombre de su aplicación.

    *mydomain*: El nombre del dominio personalizado, por ejemplo `www.mydomain.mybluemix.net`.

    *host_name*: El nombre de host de la ruta que desea utilizar para la aplicación.

    *mycontainergroup*: Para grupos de contenedores, el nombre del grupo de contenedores.

Tras configurar su dominio personalizado en {{site.data.keyword.Bluemix_notm}}, debe correlacionarlo con el
dominio del sistema {{site.data.keyword.Bluemix_notm}} en su servidor DNS registrado:

  1. Configure un registro 'CNAME' para el nombre de dominio personalizado en su servidor DNS. Los pasos para configurar el registro CNAME varían en función del proveedor de DNS. Por ejemplo, si está utilizando GoDaddy, siga las directrices de la [Ayuda sobre dominios ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window}.
  2. Correlacione el nombre de dominio personalizado con el punto final seguro para la región {{site.data.keyword.Bluemix_notm}} en la que se ejecuta su aplicación. Utilice los puntos finales de región siguientes para proporcionar la ruta al URL asignado a la organización en {{site.data.keyword.Bluemix_notm}}:

    * US-SOUTH: `secure.us-south.bluemix.net`
    * US-EAST: `secure.us-east.bluemix.net`
    * EU-DE: `secure.eu-de.bluemix.net`
    * EU-GB: `secure.eu-gb.bluemix.net`
    * AU-SYD: `secure.au-syd.bluemix.net`

En un navegador o interfaz de línea de mandatos, escriba el siguiente URL para acceder a la aplicación miapp:

```
http://host_name.mydomain
```

**Nota:** Para eliminar una ruta huérfana, utilice el siguiente mandato:

```
bluemix app route-delete domain -n hostname -f
```

*dominio* es el nombre del dominio y *nombre_host* es el nombre de host de la ruta de la aplicación. Para obtener más información sobre el mandato **bluemix app route-delete**, escriba `bluemix app route-delete -h`.

##Despliegues azul-verde
{: #blue_green}

{{site.data.keyword.Bluemix_notm}} da soporte a la técnica de despliegue azul-verde para habilitar la entrega continua y para minimizar los sucesos de tiempo de inactividad.

El *despliegue azul-verde* es una técnica de despliegue con tiempo de inactividad cero que consiste en dos entornos de producción prácticamente idénticos llamados Azul y Verde. Difieren en los artefactos que el desarrollador ha modificado intencionadamente, generalmente en la versión de la aplicación. En cada momento al menos uno de los entornos está activo. Con la técnica de despliegue azul-verde se puede beneficiar de las siguientes ventajas:

* Desarrollo rápido de software, desde la fase final de prueba hasta la fase de producción.
* Despliegue de una nueva versión de una aplicación sin interrumpir el tráfico destinado a la aplicación.
* Retrotracción rápida. Si hay algo que no funciona en uno de los entornos, que pueda conmutar rápidamente al otro entorno.

Si ya ha desplegado una aplicación en {{site.data.keyword.Bluemix_notm}} y desea actualizar la aplicación a una nueva versión, puede utilizar cualquiera de los dos enfoques siguientes para garantizar un despliegue azul-verde.

###Ejemplo: Utilización del mandato bluemix app rename

En este ejemplo, el nombre de la aplicación es Blue. El ejemplo muestra cómo actualizar la versión de *Blue* mediante el mandato **bluemix app rename** sin interrumpir el tráfico destinado a la aplicación. Si lo desea, puede suprimir la versión antigua de *Blue* cuando la versión actualizada esté en vigor.

1. Envíe la app *Blue* a {{site.data.keyword.Bluemix_notm}}.

  ```
  bluemix app push Blue
  ```

  Resultado: La app *Blue* se ejecuta y responde al URL `Blue.mybluemix.net`.

2. Utilice el mandato **bluemix app rename** para cambiar el nombre de la app
*Blue* por *Green*:

  ```
  bluemix app rename Blue Green
  ```

  Obtenga una lista de las apps del espacio actual mediante el mandato **bluemix app list**:

  ```
  ...
  name             requested state   instances   memory   disk   urls
  Green            started           1/1         1G       1G	 Blue.mybluemix.net
  ...
  ```

  Resultado: La app *Green* se ejecuta y responde al URL `Blue.mybluemix.net`.

3. Realice los cambios necesarios y prepare la versión *Blue* actualizada. Envíe la app *Blue* actualizada a {{site.data.keyword.Bluemix_notm}}:

  ```
  bluemix app push Blue
  ```

  Obtenga una lista de las apps del espacio actual mediante el mandato **bluemix app list**:

  ```
  ...
  name             requested state   instances   memory   disk   urls
  Green            started           1/1         1G       1G	 Blue.mybluemix.net
  Blue             started           1/1         1G       1G	 Blue.mybluemix.net
  ...
  ```

  Resultados:
    * Se despliegan dos instancias de la aplicación, *Blue* y *Green*.
	* La app *Green* se ejecuta y responde al URL `Blue.mybluemix.net`.

4. Opcional: Si desea suprimir la versión antigua
(*Green*) de la app, utilice el mandato **bluemix app delete**.

  ```
  bluemix app delete Green -f
  ```

  Obtenga una lista de las rutas del espacio mediante el mandato
**bluemix app route-map**:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Blue
  ...
  ```

  Resultado: La app *Blue* responde al URL `Blue.mybluemix.net`.

###Ejemplo: Utilización del mandato bluemix app route-map

En este ejemplo, *Blue* es la aplicación previamente desplegada y *Green* es la versión actualizada. Este ejemplo muestra cómo actualizar la versión de *Blue* mediante el mandato **bluemix app route-map** sin interrumpir el tráfico destinado a la aplicación. Si lo desea, puede suprimir la versión antigua de *Blue* cuando la versión actualizada esté en vigor.

1. Envíe la app *Blue* a {{site.data.keyword.Bluemix_notm}}.

  ```
  bluemix app push Blue
  ```

  Resultado: La app *Blue* se ejecuta y responde al URL `Blue.mybluemix.net`.

2. Realice los cambios necesarios y prepare la versión *Green*. Envíe la app *Green* a {{site.data.keyword.Bluemix_notm}}:

  ```
  bluemix app push Green
  ```

  Obtenga una lista de las apps del espacio actual mediante el mandato **bluemix app route-map**:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Blue
  Green            mybluemix.net    Green
  ...
  ```

  Resultados:

    * Se despliegan dos instancias de la app, *Blue* y *Green*.
	* La app *Blue* responde al URL `Blue.mybluemix.net`. Y la app *Green* responde al URL `Green.mybluemix.net`.

3. Correlacione la app *Blue* con la app *Green* para que todo el tráfico destinado a `Blue.mybluemix.net` se dirija a la app *Blue* y a la app *Green*.

  ```
  bluemix app route-map Green mybluemix.net -n Blue
  ```

  Obtenga una lista de las rutas del espacio mediante el mandato bluemix app route-map:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Blue, Green
  Green            mybluemix.net    Green
  ...
  ```

  Resultado:

    * Ahora el direccionador de CF envía el tráfico correspondiente a Blue.mybluemix.net. tanto a la app Blue como a la app Green.
	* El direccionador de CF sigue enviando el tráfico correspondiente a Green.mybluemix.net. a la app Green.

4. Cuando verifique que *Green* se está ejecutando según lo esperado, elimine la ruta `Blue.mybluemix.net` de la app *Blue*:

  ```
  bluemix app route-unmap Blue mybluemix.net -n Blue
  ```

  Obtenga una lista de las rutas del espacio mediante el mandato bluemix app route-map:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Green
  Green            mybluemix.net    Green
  ...
  ```

  Resultado: El direccionador de CF deja de enviar tráfico a la app *Blue*. La app *Green* responde a ambos URL: `Green.mybluemix.net` y `Blue.mybluemix.net`.

5. Elimine la ruta `Green.mybluemix.net` a la app *Green*.

  ```
  bluemix app route-unmap Green mybluemix.net -n Green
  ```

  Resultado: El direccionador de CF deja de enviar tráfico a la app *Blue*. La app *Green* responde al URL `Blue.mybluemix.net`.

6. Opcional: Si desea suprimir la versión antigua (*Blue*) de la aplicación, utilice el mandato `bluemix app delete`.

  ```
  bluemix app delete Blue -f
  ```

  Obtenga una lista de las rutas del espacio mediante el mandato bluemix app route-map:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Green
  ...
  ```

  Resultado: La app *Green* responde al URL `Blue.mybluemix.net`.


# Enlaces relacionados
{: #rellinks notoc}

## Enlaces relacionados
{: #general}

[Despliegues azul-verde ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](http://martinfowler.com/bliki/BlueGreenDeployment.html){:new_window}
