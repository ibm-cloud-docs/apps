---

copyright:
  years: 2015, 2017, 2018
lastupdated: "2018-05-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Comprobación del estado de su app
{: #manageapps}

Su panel de control en la consola de {{site.data.keyword.Bluemix}} proporciona información de resumen de la aplicación que ha creado. La información de resumen incluye el nombre, el icono, el URL, el tiempo de ejecución, el estado de ejecución y las instancias de servicios vinculadas a la app.
{:shortdesc}

## Estado de su app
{: #status}

Desde su panel de control, puede ver el estado de cada aplicación. En la columna de estado para cada aplicación, puede ver si las instancias de app están en ejecución.

<dl>
<dt>
<strong>
Detenido o Desconocido (gris)
</strong>
</dt>
<dd>
La app se ha detenido o el estado es desconocido. El icono gris indica que la app está detenida o que se desconoce su estado.
</dd>
<dt>
<strong>
En ejecución (verde)
</strong>
</dt>
<dd>
La app está ejecutándose. El icono verde indica que la app se ha iniciado y se están ejecutando todas las instancias.
</dd>
<dt>
<strong>
_Número_ en ejecución (amarillo)
</strong>
</dt>
<dd>
La app se ha iniciado pero no se están ejecutando todas las instancias. El icono amarillo indica que se están ejecutando menos del 100% de las instancias. El número de instancias que se están ejecutando y el número de instancias que no se han podido visualizar.
</dd>
<dt>
<strong>
No se está ejecutando (rojo)
</strong>
</dt>
<dd>
La app no se está ejecutando. El icono rojo indica que la app se ha iniciado, pero que no hay ninguna instancia en ejecución.
</dd>
</dl>

## Visualización del panel de control de detalles de su app
{: #viewingapps}

Puede ver más información sobre una app pulsando el nombre en su panel de control. A continuación, puede ver la página de Visión general de la app.

En la página Visión general de apps, cuando se despliega una app, puede iniciar, detener, reiniciar o en el caso de aplicaciones web, modificar el número de instancias y la cantidad de memoria utilizada por la app. Para las aplicaciones web, {{site.data.keyword.Bluemix_notm}} no escala automáticamente su app en función de su carga, por lo que deberá gestionarlo usted mismo.

Si se realiza una actualización, las apps se pueden volver a desplegar. El mecanismo por el que se actualiza la app es el mismo que se utiliza cuando se despliega originalmente. {{site.data.keyword.Bluemix_notm}} detiene
todas las instancias en ejecución y las reemplaza por instancias nuevas de forma automática.
