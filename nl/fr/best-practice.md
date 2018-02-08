---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

# Qu'est-ce qui caractérise une bonne application ?

Une application générée dans {{site.data.keyword.Bluemix_notm}} peut s'avérer différente d'une application générée d'une autre manière. Ces meilleures pratiques vous aideront à générer la meilleure application pour la plateforme cloud.

## Architecture multi-région
{: #multiregion}

Il est recommandé d'exécuter plusieurs instances afin d'éviter les durées d'indisponibilité pour une région unique, mais pour distribuer une application encore plus robuste, envisagez une architecture multi-région.

## Options de surveillance
{: #monitoring}

{{site.data.keyword.Bluemix_notm}} simplifie la surveillance de votre application grâce à des services comme [Monitoring and Analytics](/docs/services/monana/index.html) et [New Relic ![Icône de lien externe](../icons/launch-glyph.svg)](http://newrelic.com/){: new_window}. Consultez [Surveillance et journalisation](../monitor_log/monitoringandlogging.html#monitoring_logging_bluemix_apps) pour plus d'informations.

## Options de support
{: #support}

Le forfait payant {{site.data.keyword.Bluemix_notm}} offre plusieurs autres types de compte avec un support payant *facultatif*. Quel que soit le type de votre compte, si vous prévoyez de mettre en production une application sur {{site.data.keyword.Bluemix_notm}}, envisagez de vous inscrire à cette option.

Avec ou sans support payant, vous pouvez obtenir de l'aide comme décrit à la rubrique de [support](../get-support/howtogetsupport.html), mais la solution payante offre une garantie contre les incidents imprévisibles.

## Développement d'applications prêtes pour le cloud
{: #cloud-ready-apps}

Si tous les principes ci-après sont respectés dans votre application, l'application est prête pour le cloud et peut être migrée dans {{site.data.keyword.Bluemix_notm}}. Si un principe n'est pas appliqué dans votre application, vous pouvez généralement modifier votre application pour qu'elle le respecte.
{:shortdesc}

### Ne codez pas votre application directement dans une topologie spécifique.

Dans un environnement autre qu'un environnement de cloud, l'application peut utiliser une topologie de déploiement particulière. Cependant, la topologie de l'application peut changer dans les applications en cloud, car les applications et les services prêts pour le cloud autorisent des modifications immédiates à des fins d'évolutivité. Ces modifications incluent la mise à l'échelle dynamique et le redimensionnement manuel du nombre d'instances d'une application.

Construisez votre application de façon à ce qu'elle soit aussi générique et sans état que possible pour éviter qu'elle ne soit affectée par les
modifications à des fins d'évolutivité.

### Ne partez pas du principe que le système de fichiers est permanent.

Parce qu'une application peut être déplacée, supprimée ou dupliquée à tout
moment dans le cloud, ne vous appuyez pas sur les fichiers qui se trouvent dans le système de fichiers. Si une application utilise le système de fichiers local comme cache pour les informations utilisées fréquemment, notamment les journaux d'application, les
informations sont perdues quand l'instance est arrêtée et redémarrée à un autre emplacement ou sur une machine virtuelle différente.

Vous pouvez stocker les informations dans un service, par exemple une base de données SQL ou NoSQL, au lieu de les stocker dans le système de
fichiers local. Dans un environnement de cloud dynamique, il est également essentiel que vos journaux soient disponibles dans un service qui survit aux
instances d'application dans lesquelles les journaux sont générés.

### Ne stockez pas l'état de session dans votre application.

L'état de votre système est défini par vos bases de données et votre espace de stockage
partagé, et non par chaque instance d'application individuelle en cours d'exécution. L'état, quel qu'il soit, limite l'évolutivité d'une application. Essayez de réduire l'impact de l'état de session en le stockant à un emplacement centralisé
sur le serveur.

Si vous ne pouvez pas éliminer l'état de session entièrement, envoyez-le dans un magasin hautement disponible externe à votre serveur
d'applications, par exemple IBM WebSphere Extreme Scale, Redis ou Memcached, ou une base de données externe.

### N'utilisez pas de dépendance d'infrastructure spécifique.

Il s'agit d'un principe général qui se traduit sous différentes formes. Ainsi, ne partez pas du
principe que les services que votre application utilise sont associés à des noms d'hôte ou des adresses IP spécifiques. L'emplacement des services peut changer ou les services peuvent être régénérés dans votre environnement de cloud, les noms d'hôte et les adresses IP peuvent également être modifiés.

L'extraction de dépendances propres à l'environnement dans un ensemble de fichiers de propriétés
constitue une amélioration, mais reste inadaptée. Il est préférable d'utiliser un registre de services externe pour résoudre les noeuds finaux des services
ou de déléguer la fonction de routage complète à un bus de services ou à un équilibreur de charge avec un nom virtuel.

### N'utilisez pas d'API d'infrastructure dans votre application.

Si vous vous appuyez sur une API d'infrastructure spécifique dans votre application, il
est plus complexe de changer l'infrastructure, car une API d'infrastructure peut faire référence à de nombreuses couches différentes dans votre pile de
logiciels.

A la place, vous pouvez vous appuyer sur des produits commerciaux ou open source existants, et laisser les solutions PaaS (Platform as a Service) dans la couche PaaS afin de ne pas les intégrer à votre code d'application.

### N'utilisez pas de protocoles opaques.

N'utilisez pas de protocoles opaques requérant des étapes de configuration supplémentaires afin d'assurer la
résilience.

Les applications reposant sur des protocoles standard sont plus résilientes avec les éléments de configuration délégués à la plateforme. Les protocoles standard sont HTTP, SSL, la base de données standard, la mise en file d'attente et les connexions de service Web.

### Ne vous appuyez pas sur des fonctions propres au système d'exploitation.

Si vous avez déjà utilisé des fonctions propres au système
d'exploitation, vous pouvez résoudre le problème en utilisant des bibliothèques de compatibilité, par exemple Cygwin et Mono. Cygwin est une bibliothèque
de compatibilité qui fournit un ensemble d'outils Linux dans un environnement Windows. Mono est une bibliothèque de compatibilité qui fournit des capacités Windows .NET dans Linux.

Evitez les dépendances propres au
système d'exploitation ; à la place, utilisez des services mis à disposition par l'infrastructure de middleware ou les fournisseurs de services.

### N'installez pas manuellement votre application.

Votre application doit être installée fréquemment à la demande dans l'environnement de cloud
dynamique. Le processus d'installation doit être scripté et fiable, et les données de configuration doivent être externalisées à partir des scripts.

Capturez votre installation d'application sous la forme d'un ensemble uniforme de scripts indépendants du système d'exploitation. Veillez à ce que l'installation d'application reste petite et portable pour qu'elle puisse s'adapter à différentes techniques d'automatisation. De plus, limitez les dépendances requises par l'installation d'application.

Pour plus d'informations sur les applications prêtes pour le cloud, voir [The twelve-factor app ![Icône de lien externe](../icons/launch-glyph.svg)](http://12factor.net/){: new_window}.

