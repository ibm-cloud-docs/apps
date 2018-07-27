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

# Premiers pas avec un fichier Docker Compose
{: #compose-file}

Pour les applications Docker Compose, les informations ci-après répertorient ce que l'on trouve généralement dans {{site.data.keyword.Bluemix}}. Lorsque vous créez un kit de démarrage, ces fichiers sont créés pour vous. Si vous faites migrer une application vers un hôte dans {{site.data.keyword.Bluemix_notm}}, vous souhaiterez peut-être passer en revue ces informations pour éviter tout conflit.
{:shortdesc}

Le fichier [Docker Compose](https://docs.docker.com/compose/overview/) inclut des informations permettant d'exécuter des applications multi-conteneur.

Spécifiez la version 2.0 ou une version ultérieure pour le fichier Docker Compose : `version: '2'`

Vous devez également définir les services. L'exemple suivant est issu d'une application Node :

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

Les services `web` et `mongo` ont été définis et chacun d'entre eux dispose de configurations, lesquelles sont définies dans la [documentation](https://docs.docker.com/compose/compose-file/compose-file-v2/) Docker Compose.

Les configurations les plus pertinentes sont répertoriées ci-dessous :

* `build` : les attributs context et Dockerfile sont inutiles ici car il s'agit des valeurs par défaut pouvant être remplacées sous ce format. L'attribut context définit le chemin d'accès au nom du fichier Dockerfile spécifié dans l'attribut Dockerfile.

* `tty` : en spécifiant cet attribut, les conteneurs peuvent continuer à s'exécuter sans être immédiatement arrêtés, ce qui est requis pour la prise en charge de Docker Compose.

* `command` : cet attribut spécifie la commande à exécuter dans les conteneurs.

* `image` et `container_name` : ces attributs spécifient les noms de l'image et des conteneurs.
