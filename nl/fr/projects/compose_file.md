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

# Fichier Compose
{: #compose-file}

Pour les projets Compose, les informations ci-après répertorient ce que l'on trouve généralement dans {{site.data.keyword.Bluemix}}. Lorsque vous créez un kit de démarrage, ces fichiers sont créés pour vous. Si vous faites migrer une application vers un hôte dans {{site.data.keyword.Bluemix_notm}}, vous souhaiterez peut-être passer en revue ces informations pour éviter tout conflit.
{:shortdesc}

Le fichier [Compose](https://docs.docker.com/compose/overview/)d définit des informations permettant d'exécuter des applications multi-conteneur. 

Vous devez spécifier la version 2.0 ou une version ultérieure pour le fichier Compose utilisé, par exemple, `version: '2'`

Vous devez également définir les services. Voici un exemple de projet de noeud :
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

`web` et `mongo` sont les services spécifiés et chacun d'eux comportent des configurations, qui sont définies dans la [documentation Docker-Compose](https://docs.docker.com/compose/compose-file/compose-file-v2/).

Les configurations les plus pertinentes sont répertoriées ci-dessous :

* build : les attributs context et dockerfile sont inutiles ici car il s'agit des valeurs par défaut, mais ils peuvent être remplacés dans ce format. L'attribut context définit le chemin d'accès au nom du fichier Dockerfile spécifié dans l'attribut dockerfile. 

* tty : avec cet attribut, les conteneurs peuvent rester actifs et ne pas se terminer immédiatement. Cet attribut est requis pour le support Docker-Compose. 

* command : cet attribut spécifie la commande à exécuter dans les conteneurs. 

* image et container_name : ces attributs spécifient les noms de l'image et des conteneurs, respectivement. 


