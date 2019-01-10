---
copyright:
years: 2015, 2018
lastupdated: "2018-07-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Cómo empezar a trabajar con un archivo Docker Compose
{: #compose-file}

Para las apps Docker Compose, la siguiente información es un inventario de lo que normalmente se encontrará en {{site.data.keyword.Bluemix}}. Cuando se crea un kit de inicio, estos archivos se crean en su nombre. Si está migrando una app para alojarla en {{site.data.keyword.Bluemix_notm}}, es posible que desee revisar esta información para evitar posibles conflictos.
{:shortdesc}

El archivo [Docker Compose](https://docs.docker.com/compose/overview/) define información para ejecutar aplicaciones en varios contenedores.

Especifique la versión del archivo Docker Compose que se utiliza, que debe ser 2.0 o posterior:
`version: '2'`

También debe definir los servicios. El ejemplo siguiente es de una app de nodo:

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

Los servicios `web` y `mongo` están definidos y cada uno de ellos tiene configuraciones, que se definen en la [documentación](https://docs.docker.com/compose/compose-file/compose-file-v2/) de Docker Compose.

Las configuraciones más relevantes son las siguientes:

* `build`: los atributos context y dockerfile no son necesarios puesto que son los valores predeterminados, pero que se pueden sobrescribir en este formato. El atributo context define la vía de acceso al nombre del Dockerfile que se especifica en el atributo dockerfile.

* `tty`: si especifica este atributo, los contenedores pueden seguir ejecutándose y no salir inmediatamente, lo que es necesario para el soporte de Docker Compose.

* `command`: este atributo especifica el mandato que se va a ejecutar dentro de los contenedores.

* `image` y `container_name`: estos atributos especifican los nombres de la imagen y de los contenedores.
