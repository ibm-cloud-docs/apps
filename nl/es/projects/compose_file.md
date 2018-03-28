---
copyright:
years: 2015, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}  

# Archivo Compose
{: #compose-file}

Para proyectos Compose, la siguiente información es una relación de lo que normalmente se encuentra en {{site.data.keyword.Bluemix}}. Cuando se crea un kit de iniciación, estos archivos se crean en su nombre. Si está migrando una app para alojarla en {{site.data.keyword.Bluemix_notm}}, es posible que desee revisar esta información para evitar posibles conflictos.
{:shortdesc}

El archivo [Compose](https://docs.docker.com/compose/overview/) define información para ejecutar aplicaciones en varios contenedores.

Debería especificar una versión del archivo Compose, como mínimo la versión 2.0:
`version: '2'`

También debe definir los servicios. A continuación se muestra un ejemplo de un proyecto Node:
```
services:
  web:
    build:
    	context: <path-to-Dockerfile>
	dockerfile: <name-of-Dockerfile>
    tty: true
    command: npm run start-dev
    image: <image-name>
    container_name: <container-name>
    volumes:
      - .:/app
      - /app/node_modules
    ports:
      - "3000:3000"
    links:
      - mongo
    environment:
      MONGO_URL: "mongo"
      MONGO_DB_NAME: "comments"
      NODE_ENV: "development"
      PORT: 3000
  mongo:
    image: mongo
```

`web` y `mongo` son los servicios que se especifican con sus configuraciones, que se definen en la [documentación](https://docs.docker.com/compose/compose-file/compose-file-v2/) de Docker-Compose.

Las configuraciones más relevantes son las siguientes:

* build: Los atributos context y dockerfile no son necesarios puesto son los valores predeterminados, pero que se pueden sobrescribir en este formato. El atributo context define la vía de acceso al nombre del Dockerfile especificado en el atributo dockerfile.

* tty: Al especificar este atributo, los contenedores pueden permanecer en ejecución y no salir inmediatamente. Esto es necesario para el soporte de Docker-Compose.

* command: Este atributo especifica el mandato a ejecutar dentro de los contenedores.

* image y container_name: estos atributos especifican los nombres de la imagen y el contenedor respectivamente.


