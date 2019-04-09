---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-29"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Qu'est-ce qui caractérise une bonne application ?
{: #best-practice}

Créez votre application dans {{site.data.keyword.cloud}} pour bénéficier de tout ce qu'un cloud peut offrir. Les meilleures pratiques décrites ci-après vous aideront à développer des applications prêtes pour le cloud.
{: shortdesc}

## Créez une application indépendante de la topologie

Dans un environnement autre qu'un environnement de cloud, votre application peut utiliser une topologie de déploiement particulière. Cependant, la topologie de l'application peut changer dans les applications en cloud, car les applications et les services prêts pour le cloud autorisent des modifications immédiates à des fins d'évolutivité. Ces modifications incluent la mise à l'échelle dynamique et le redimensionnement manuel du nombre d'instances d'une application.

Construisez votre application de façon à ce qu'elle soit aussi générique et sans état que possible pour éviter qu'elle ne soit affectée par les modifications à des fins d'évolutivité.

## Partez du principe que le système de fichiers local n'est pas permanent

Etant donné qu'une application peut être déplacée, supprimée ou dupliquée dans le cloud, ne vous fiez pas aux fichiers consignés dans le système de fichiers. Si une application utilise le système de fichiers local comme cache pour les informations utilisées fréquemment (notamment les journaux d'application), les informations sont perdues lorsque l'instance est arrêtée et redémarrée à un autre emplacement ou sur une autre machine virtuelle.

Vous pouvez stocker les informations dans un service, par exemple une base de données SQL ou NoSQL, au lieu de les stocker dans le système de fichiers local. Dans un environnement de cloud dynamique, il est également essentiel que vos journaux soient disponibles dans un service qui survit aux instances d'application dans lesquelles les journaux sont générés.

## Exclusion de l'état de session de votre application

L'état de votre système est défini par vos bases de données et votre espace de stockage partagé, et non par chaque instance d'application individuelle en cours d'exécution. L'état, quel qu'il soit, limite l'extensibilité d'une application. Essayez de réduire l'impact de l'état de session en le stockant à un emplacement centralisé sur le serveur.

Si vous ne pouvez pas éliminer l'état de session entièrement, envoyez-le dans un magasin hautement disponible externe à votre serveur d'applications, Les magasins peuvent être IBM WebSphere eXtreme Scale, Redis, Memcached, ou encore une base de données externe.

## Utilisez un registre de services externe pour résoudre les noeuds finaux de service

Ne partez pas du principe que les services que votre application utilise sont associés à des noms d'hôte ou des adresses IP spécifiques. L'emplacement des services peut changer ou les services peuvent être régénérés dans votre environnement de cloud, les noms d'hôte et les adresses IP peuvent également être modifiés.

L'extraction de dépendances propres à l'environnement dans un ensemble de fichiers de propriétés constitue une amélioration, mais reste inadaptée. Il est préférable d'utiliser un registre de services externe pour résoudre les noeuds finaux des services ou de déléguer la fonction de routage complète à un bus de services ou à un équilibreur de charge avec un nom virtuel.

## Créez votre application sous une architecture multi-régions
{: #multiregion}

Vous pouvez exécuter plusieurs instances afin d'éviter des indisponibilités dans une région unique. Pour mettre à disposition une application encore plus robuste, pensez à utiliser une architecture multi-région.

## Prenez soin de surveiller vos applications
{: #monitoring}

{{site.data.keyword.Bluemix_notm}} simplifie la surveillance de votre application grâce à des services comme [New Relic ![Icône de lien externe](../icons/launch-glyph.svg)](http://newrelic.com/){: new_window}.

## Bénéficiez des options de support
{: #support}

Le forfait payant {{site.data.keyword.Bluemix_notm}} offre plusieurs autres types de compte avec un support payant facultatif. Quel que soit le type de votre compte, si vous prévoyez de mettre en production une application sur {{site.data.keyword.Bluemix_notm}}, envisagez de vous inscrire à cette option.

Avec ou sans support payant, vous pouvez obtenir de l'aide comme décrit à la rubrique [support](/docs/get-support/howtogetsupport.html), afin de vous prémunir contre les problèmes imprévisibles.

## Evitez les API d'infrastructure dans votre application

Si vous vous appuyez sur une API d'infrastructure spécifique dans votre application, il
est plus complexe de changer l'infrastructure, car une API d'infrastructure peut faire référence à de nombreuses couches différentes dans votre pile de
logiciels.

A la place, vous pouvez vous appuyer sur des produits commerciaux ou open source existants, et laisser les solutions PaaS (Platform as a Service) dans la couche PaaS afin de ne pas les intégrer à votre code d'application.

## Utilisez des protocoles standard

N'utilisez pas de protocoles opaques requérant des étapes de configuration supplémentaires afin d'assurer la résilience.

Les applications reposant sur des protocoles standard sont plus résilientes lorsque les éléments de configuration sont délégués à la plateforme. Les protocoles standard sont HTTP, SSL, la base de données standard, la mise en file d'attente et les connexions de service Web.

## Utilisez des bibliothèques de compatibilité au lieu des fonctions spécifiques au système d'exploitation

Si vous avez déjà utilisé des fonctions propres au système d'exploitation, vous pouvez résoudre le problème en utilisant des bibliothèques de compatibilité, par exemple Cygwin et Mono. Cygwin est une bibliothèque de compatibilité qui fournit un ensemble d'outils Linux dans un environnement Windows. Mono est une bibliothèque de compatibilité qui fournit des outils Windows .NET dans Linux.

Evitez les dépendances propres au système d'exploitation ; à la place, utilisez des services mis à disposition par l'infrastructure de middleware ou les fournisseurs de services.

## Rédigez le script de votre processus d'installation

Votre application doit être installée fréquemment à la demande dans l'environnement de cloud dynamique. Le processus d'installation doit être scripté et fiable, et les données de configuration doivent être externalisées à partir des scripts.

Capturez votre installation d'application sous la forme d'un ensemble uniforme de scripts indépendant du système d'exploitation. Veillez à ce que l'installation de votre application reste petite et portable pour qu'elle puisse s'adapter à différentes techniques d'automatisation. De plus, limitez les dépendances requises par l'installation d'application.

Pour plus d'informations sur les applications prêtes pour le cloud, voir [The twelve-factor app ![Icône de lien externe](../icons/launch-glyph.svg)](http://12factor.net/){: new_window}.


