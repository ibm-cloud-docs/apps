---

copyright:
  years: 2016, 2019
lastupdated: "2019-07-17"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app, developer console, app service

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Architectures communes pour les applications en cloud
{: #patterns}

Les kits de démarrage sur {{site.data.keyword.cloud_notm}} vous aident à produire des applications avec une architecture éprouvée. Les applications sont toutes différentes, mais lorsque vous basez votre application sur un pattern d'architecture, il est plus facile d'obtenir rapidement un résultat fiable. Lorsque vous créez une application à partir d'un kit de démarrage, vous choisissez l'un des nombreux types de modèle, en même temps que des composants, tels qu'un environnement d'exécution, pour remplir le modèle.
{:shortdesc}

## Applications Web
{: #web}

Le modèle d'application Web génère des applications qui transmettent du contenu Web (HTML, JavaScript, feuilles de style, par exemple) au serveur Web. {{site.data.keyword.cloud_notm}} inclut plusieurs kits de démarrage d'application Web.

* Basic - Sert un fichier `index.html` statique, une feuille de style par défaut et vide et un fichier JavaScript.
* React - Canevas riche permettant de générer des interfaces utilisateur. Les fichiers source se trouvent dans le répertoire `src/client/app`, sont compilés avec WebPack et sont servis dans le répertoire public.

Vous trouverez des kits de démarrage pour le modèle d'application Web dans la [console de développement {{site.data.keyword.cloud_notm}} App Service](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

## Applications de microservice
{: #microservice}

Les applications de microservice fournissent le fondement de la génération de microservices de back end, y compris un noeud final de santé de base et une API REST. Les applications générées incluent toutes les dépendances requises à la fois pour le microservice proprement dit et pour n'importe quel service cloud associé.

Choisissez un kit de démarrage de micro-service en fonction de vos exigences d'infrastructure et de langage. Vous trouverez des kits de démarrage pour le modèle de microservice dans la [console de développement {{site.data.keyword.cloud_notm}} App Service](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

## Applications mobiles
{: #mobile}

Les applications mobiles sont différents des autres modèles car elles comportent un composant côté client significatif. Le modèle peut inclure une connexion directe aux services mobiles, telle que les notifications push, l'authentification et l'analytique mobile. Les services mobiles sont dénommés système de back end mobile sous forme de services ou encore modèle MBaaS. Ils peuvent également disposer d'une solution Backend-for-frontend dédiée.

{{site.data.keyword.cloud_notm}} offre plusieurs kits de démarrage mobiles pour iOS et Android. Vous trouverez des kits de démarrage pour les modèles mobiles dans la [console de développement {{site.data.keyword.cloud_notm}} Mobile](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

Vous pouvez en outre créer une application mobile en utilisant un kit de démarrage de base et en sélectionnant le type d'application mobile. Pour plus d'informations, voir [Création d'une application mobile](/docs/apps?topic=creating-apps-tutorial-mobile).

## Applications basées sur le langage
{: #languages}

Les kits de démarrage fournis par {{site.data.keyword.cloud_notm}} sont disponibles dans différents langages et infrastructures. Par exemple, les kits de démarrage de microservice de cloud offrent une option Node.js, tandis que les kits de démarrage étroitement liés à l'analyse de données peuvent inclure Python ou Go. Certains langages couramment utilisés dans les kits de démarrage {{site.data.keyword.cloud_notm}} sont présentés.

|Langage de programmation | Description | Infrastructures de développement |
|-----|-----|-----|
|Java | [Java](/docs/runtimes/liberty?topic=liberty-getting-started) est idéal pour la génération des applications de niveau entreprise. Mais les nouvelles fonctionnalités de Java 8, associées à des temps d'exécution de poids plus réduit comme ceux assurés par Liberty et les infrastructures telles Spring Boot font de Java un outil idéal pour la génération des microservices. De plus, Java est un langage de programmation populaire pour les applications Android. | Spring, Liberty, Android |
|Swift | [Swift](/docs/runtimes/swift?topic=Swift-getting-started) est un langage de programmation moderne créé en 2014 qui a été conçu pour remplacer Objective C et Open Source en décembre 2015. Aujourd'hui, il est utilisé pour générer des services iOS, macOS, Web, et des logiciels système sous Linux et macOS utilisant x86, ARM ou z/Architecture. Il écrit comme un langage de script mais est compilé pour obtenir des performances élevées similaires à C avec une faible utilisation du processeur. Ce langage est idéal pour les environnements d'exécution de cloud. Il se sert d'un système de type statique et fort que vous retrouvez dans Java alors que le style fonctionnel et les routines asynchrones correspondent à ce que vous voyez dans JavaScript. Ce langage est performant et la source est compilée en code natif qui utilise la chaîne d'outils de compilateur LLVM. Il peut utiliser des bibliothèques système d'autres langages écrits en C. Swift pouvant être utilisé pour coder à la fois des applications côté client et des applications côté serveur, les développeurs l'utilisent lorsqu'ils ont besoin de faire migrer facilement des fonctions du client vers le serveur et inversement. | Kitura, iOS|
|Node.js | [Node.js](/docs/runtimes/nodejs?topicid=Nodejs-getting-started) est un environnement d'exécution JavaScript qui utilise un modèle d'entrée/sortie non bloquant, géré par événement, qui le rend léger et efficace. Il est extrêmement performant au niveau de la capacité de traitement et de l'évolutivité pour les applications Web, les modèles BFF et les microservices. Le registre de package de Node.js, npm, permet d'accéder à une large collection de modules Open Source. Il fournit une large gamme de fonctionnalités permettant d'accélérer le développement de votre application. | Express|
|Python | [Python](/docs/runtimes/python?topic=Python-getting_started) est un langage de programmation interprété généraliste qui met l'accent sur la lisibilité. Python permet aux programmeurs d'implémenter des fonctions avec moins de lignes de code que d'autres langages. Les fonctions du langage permettent d'écrire du code orienté objets, fonctionnel ou impératif. Python est largement utilisé pour le traitement des tâches en langage naturel. | Flask, Django |
{: caption="Tableau 1. Langages utilisés dans les kits de démarrage" caption-side="top"}
