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

# File Compose
{: #compose-file}

Per i progetti Compose, le seguenti informazioni sono un inventario di quello che normalmente trovi in {{site.data.keyword.Bluemix}}. Quando crei un kit starter, questi file sono creati per te. Se stai migrando un'applicazione per essere ospitata in {{site.data.keyword.Bluemix_notm}}, potresti voler esaminare queste informazioni per evitare potenziali conflitti.
{:shortdesc}

Il file [Compose](https://docs.docker.com/compose/overview/) definisce le informazioni per l'esecuzione delle applicazioni con più contenitori.

Devi specificare la versione del file Compose utilizzato in modo che sia 2.0 o successiva, ad esempio:
`version: '2'`

Devi anche definire i servizi. Il seguente è un esempio da un progetto Node:
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

`web` e `mongo` sono i servizi specificati e ognuno di loro ha configurazioni, che sono definite nella [documentazione](https://docs.docker.com/compose/compose-file/compose-file-v2/) Docker-Compose.

Le configurazioni più rilevanti sono di seguito elencate: 

* build: gli attributi contesto e dockerfile non sono qui necessari poiché sono i valori predefiniti, ma possono essere sovrascritti in questo formato. L'attributo di contesto definisce il percorso al nome del Dockerfile specificato nell'attributo dockerfile. 

* tty: specificando questo attributo, i contenitori possono rimanere in esecuzione e non uscire immediatamente. Questo è obbligatorio per il supporto Docker-Compose.

* command: questo attributo specifica il comando da eseguire all'interno dei contenitori.

* image e container_name: questi attributi specificano i nomi dell'immagine e dei contenitori, rispettivamente.


