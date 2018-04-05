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

# Compose-Datei
{: #compose-file}

Für Compose-Projekte stellen die folgenden Informationen einen Bestand der Komponenten dar, die Sie typischerweise in {{site.data.keyword.Bluemix}} finden. Wenn Sie ein Starter-Kit erstellen, werden diese Dateien für Sie erstellt. Wenn Sie eine App migrieren, um sie in {{site.data.keyword.Bluemix_notm}} zu hosten, sollten Sie diese Informationen durchlesen, um potenzielle Konflikte zu vermeiden.
{:shortdesc}

Die [Compose](https://docs.docker.com/compose/overview/)-Datei definiert Informationen zum Ausführen von Anwendungen mit mehreren Containern. 

Sie sollten die Version der verwendeten Compose-Datei als 2.0 oder höher wie folgt angeben:
`version: '2'`

Sie müssen die Services auch definieren. Im Folgenden finden Sie ein Beispiel aus einem Node-Projekt: 
```
services:
  web:
    build:
    	context: <pfad_zur-Dockerfile>
	dockerfile: <name_der_Dockerfile>
    tty: true
    command: npm run start-dev
    image: <imagename>
    container_name: <containername>
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

`web` und `mongo` sind die angegebenen Services, jeweils mit Konfigurationen, die in der Docker-Compose-[Dokumentation](https://docs.docker.com/compose/compose-file/compose-file-v2/) definiert sind. 

Die relevantesten Konfigurationen sind wie folgt aufgelistet: 

* build: Die Attribute 'context' und 'dockerfile' sind hier nicht notwendig, da es sich um die Standardwerte handelt, aber sie können in diesem Format überschrieben werden. Das Attribut 'context' definiert den Pfad zu dem Namen der in dem Attribut 'dockerfile' angegebenen Dockerfile. 

* tty: Indem Sie dieses Attribut angeben, können die Container weiter ausgeführt und müssen nicht sofort beendet werden. Dies ist für die Docker-Compose-Unterstützung erforderlich. 

* command: Dieses Attribut gibt den in den Containern auszuführenden Befehl an. 

* image und container_name: Diese Attribute geben jeweils die Namen des Images und der Container an. 


