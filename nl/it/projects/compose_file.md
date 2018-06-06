---
copyright:
years: 2015, 2018
lastupdated: "2018-05-21"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Introduzione al file Compose
{: #compose-file}

Per le applicazioni Compose, le seguenti informazioni sono un inventario di quello che normalmente trovi in {{site.data.keyword.Bluemix}}. Quando crei un kit starter, questi file sono creati per te. Se stai migrando un'applicazione per essere ospitata in {{site.data.keyword.Bluemix_notm}}, potresti voler esaminare queste informazioni per evitare potenziali conflitti.
{:shortdesc}

Il file [Compose](https://docs.docker.com/compose/overview/) definisce le informazioni per l'esecuzione delle applicazioni con più contenitori.

Specifica la versione del file Compose utilizzata in modo che sia 2.0 o successiva, ad esempio:
`version: '2'`

Devi anche definire i servizi. Il seguente esempio proviene da un'applicazione Node:

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

I servizi `web` e `mongo` sono definiti e ognuno di essi ha delle configurazioni che sono definite nella [documentazione](https://docs.docker.com/compose/compose-file/compose-file-v2/) di Docker-Compose.

Le configurazioni più rilevanti sono di seguito elencate:

* build: gli attributi context e Dockerfile non sono necessari in questo esempio perché sono i valori predefiniti, ma possono essere sovrascritti in questo formato. L'attributo context definisce il percorso del nome del Dockerfile che è specificato nell'attributo Dockerfile.

* tty: specificando questo attributo, i contenitori possono rimanere in esecuzione e non terminare immediatamente, che è richiesto per il supporto di Docker-Compose.

* command: questo attributo specifica il comando da eseguire all'interno dei contenitori.

* image e container_name: questi attributi specificano i nomi dell'immagine e dei contenitori.
