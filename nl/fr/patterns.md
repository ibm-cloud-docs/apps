---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Architectures communes pour les applications en cloud
{: #patterns}

Les kits de démarrage sur {{site.data.keyword.cloud_notm}} vous aident à produire des applications avec une architecture éprouvée. Les applications sont toutes différentes, mais lorsque vous basez votre application sur un pattern d'architecture, il est plus facile d'obtenir rapidement un résultat fiable. Lorsque vous créez un projet à partir d'un kit de démarrage, vous choisissez l'un des nombreux types de pattern, en même temps que des composants, tels qu'un environnement d'exécution, pour remplir le pattern.
{:shortdesc}

## Application Web
{: #web}

Le modèle d'application Web génère des projets qui servent du contenu Web, HTML, JavaScript, par exemple, et des feuilles de style au serveur Web. Il existe plusieurs kits de démarrage d'application Web. 

* Basic - Sert un fichier `index.html` statique, une feuille de style par défaut et vide et un fichier JavaScript. 
* React - Canevas riche permettant de générer des interfaces utilisateur. Les fichiers source se trouvent dans le répertoire `src/client/app`, sont compilés avec WebPack et sont servis dans le répertoire public. 

Vous trouverez des kits de démarrage pour le modèle d'application Web dans le [tableau de bord de développeur de service d'application {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## BFF (Backend for Frontend)
{: #bff}

BFF (Backend for Frontend) permet de créer un code de back end qui expose des données métier et des services d'une manière qui répond aux attentes des utilisateurs pour un canal d'application spécifique, par exemple, mobile ou Web. Par exemple, les utilisateurs d'un appareil mobile pourront utiliser le contrôle vocal, tandis les utilisateurs qui consomment votre application via un navigateur Web préféreront cliquer et pointer. Vous pouvez générer deux architectures BFF, l'une pour un appareil mobile incluant des services, tels que [{{site.data.keyword.conversationfull}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/conversation.html), et l'autre pour le Web comportant une interface utilisateur plus sophistiquée. 

Dans {{site.data.keyword.cloud_notm}}, vous pouvez générer une architecture BFF avec une approche de programmation polyglotte. Vous pouvez utiliser Node.js, Swift, Java ou Python et les exécuter dans un modèle avec des services de conteneur ou utiliser des fonctions sans serveur. 

L'architecture BFF gère la persistance de données, la mise en cache et l'intégration à des services de valeur supérieure, tels que [{{site.data.keyword.ibmwatson}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson), [{{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot), [{{site.data.keyword.weather_short}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps) et [{{site.data.keyword.sparks}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps).

L'architecture BFF expose une API en utilisant le plus souvent un modèle REST, mais vous pouvez concevoir votre propre architecture BFF pour qu'elle fonctionne à partir d'une architecture de messagerie à l'aide de {{site.data.keyword.messagehub}}.

Vous avez le choix entre plusieurs kits de démarrage d'architecture BFF selon vos exigences en matière de langage et d'infrastructure. Vous trouverez des kits de démarrage pour le modèle BFF dans le [tableau de bord de développeur de service d'application {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Microservice
{: #microservice}

Les projets de microservice fournissent le fondement de la génération de microservices de back end, y compris un noeud final de santé de base et une API REST. Les projets générés contiennent toutes les dépendances requises à la fois pour le microservice proprement dit et pour n'importe quel service cloud associé.

Vous avez le choix entre plusieurs kits de démarrage microservice selon vos exigences en matière de langage et d'infrastructure. Vous trouverez des kits de démarrage pour le modèle de microservice dans le [tableau de bord de développeur de service d'application {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Mobile
{: #mobile}

Les projets mobiles sont différents des autres modèles car ils comportent un composant côté client significatif. Le modèle peut inclure une connexion directe aux services mobiles, tels que les notifications push, l'authentification et l'analytique mobile, appelée système de back end mobile sous forme de services, ou peut avoir une architecture [Backend for Frontend](#bff) dédiée.   

{{site.data.keyword.cloud_notm}} offre plusieurs kits de démarrage mobile pour iOS, Swift, Android et Cordova. Vous trouverez des kits de démarrage pour le modèle mobile dans le [tableau de bord de développeur mobile {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/mobile/dashboard).

## Langages
{: #languages}

Les kits de démarrage fournis par {{site.data.keyword.cloud_notm}} sont disponibles dans différents langages et dans diverses infrastructures. Par exemple, les kits de démarrage de microservice de cloud offrent une option Node.js, tandis que les kits de démarrage étroitement liés à l'analyse de données peuvent inclure Python ou Go. Certains langages couramment utilisés dans les kits de démarrage {{site.data.keyword.cloud_notm}} sont présentés. 


|Langage de programmation | Description | Infrastructures de développement |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) dispose de fonctionnalités qui ont fait leur preuve pour générer des applications destinées aux entreprises, mais les nouvelles fonctionnalités de Java 8, associées à des temps d'exécution de poids plus réduit comme ceux assurés par Liberty et les infrastructures telles Spring Boot, font de Java un outil également parfaitement adapté à la génération des microservices.  De plus, Java est un langage de programmation populaire pour les applications Android. | Spring, Liberty, Android |
|Swift | [Swift](../runtimes/swift/getting-started.html) est un langage de programmation moderne créé par Apple en 2014 et qui a été conçu pour remplacer l'utilisation d'Objective-C et d'Open Source à compter de décembre 2015. Aujourd'hui, il est utilisé pour générer des services iOS, macOS, Web, et des logiciels système sous Linux et macOS utilisant  x86, ARM ou z/Architecture. Il écrit comme un langage de script mais est compilé pour obtenir des performances élevées similaires à C avec de faibles temps de traitement, ce qui le rend idéal pour les environnements d'exécution de cloud. Il se sert d'un système de type statique et fort que vous retrouvez dans Java alors que le style fonctionnel et les routines asynchrones correspondent à ce que vous voyez dans JavaScript. Il est très performant, et le source est compilé en code natif à l'aide de la chaîne d'outils de compilateur LLVM et peut facilement utiliser des bibliothèques de système étranger écrites en C. Etant donné que Swift peut être utilisé pour coder à la fois des applications côté client et des applications côté serveur, les développeurs l'utilisent lorsqu'ils ont besoin de faire migrer facilement des fonctions du client vers le serveur et inversement. | Kitura, iOS|
|Node.js | [Node.js](../runtimes/nodejs/getting-started.html) est un environnement d'exécution JavaScript qui utilise un modèle d'entrée/sortie non bloquant, géré par événement, qui le rend léger, efficace et extrêmement performant au niveau de la capacité de traitement et de l'évolutivité pour les applications Web, les modèles BFF et les microservices. L'écosystème de package Node.js, npm, permet d'accéder à une large collection de modules open source, fournissant une large gamme de fonctionnalités pour accélérer le développement de votre application. | Express|
|JavaScript|JavaScript crée des effets interactifs sur des pages Web. JavaScript, ainsi que HTML et CSS, constitue la page de la plupart des pages Web. Lorsqu'il est encapsulé avec un plug-in Cordova, le code JavaScript peut bénéficier pleinement des fonctions natives des appareils. Les développeurs ayant des compétences Web peuvent facilement créer des applications mobiles, et si besoin, le code d'application peut être réutilisé dans les environnements Web et mobile. |Cordova|
|Python | [Python](../runtimes/python/getting-started.html) est un langage de programmation interprété généraliste qui met l'accent sur la lisibilité. Python permet aux programmeurs d'implémenter des fonctions avec moins de lignes de code que d'autres langages. Les fonctions du langage permettent d'écrire du code orienté objets, fonctionnel ou impératif. Python est largement utilisé pour le traitement des tâches en langage naturel. | Flask, Django|

