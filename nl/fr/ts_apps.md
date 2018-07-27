---

copyright:

  years: 2015, 2018

lastupdated: "2018-07-09"

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Traitement des incidents liés à la gestion des applications
{: #managingapps}

Des problèmes d'ordre général liés à la gestion des applications peuvent survenir, par exemple, les applications ne peuvent pas être mises à jour ou les caractères codés sur deux octets ne sont pas affichés. Dans de nombreux cas, ces problèmes peuvent être résolus en quelques opérations simples.
{:shortdesc}

## Des modifications n'ont pas été sauvegardées
{: #ts_unsaved_changes}

Lorsque vous cliquez sur des éléments de la page des détails de l'application, il est possible que vous ne puissiez pas effectuer d'action et vous pouvez être invité à sauvegarder vos modifications avant de pouvoir continuer.

Lorsque vous essayez de vérifier votre application ou vos services sur la page des détails de l'application, vous obtenez toujours le message d'erreur suivant :
{: tsSymptoms}

`Des modifications n'ont pas été sauvegardées dans la page nom_appli. Sauvegardez ou annulez les modifications.`

Lorsque vous survolez avec la souris les zones **INSTANCES** ou **QUOTA DE MEMOIRE** dans le panneau du contexte d'exécution, les valeurs changent. Ce comportement est normal. Toutefois, le message d'erreur vous invite à sauvegarder les paramètres de mémoire ou d'instance avant d'accéder à une autre page.
{: tsCauses}

Fermez la fenêtre de message puis cliquez sur **REINITIALISER** dans votre panneau d'exécution.
{: tsResolve}

## Le basculement automatique entre les régions {{site.data.keyword.Bluemix_notm}} n'est pas disponible
{: #ts_failover}

Vous ne pouvez pas utiliser le basculement automatique entre les régions {{site.data.keyword.Bluemix_notm}}. Toutefois, vous pouvez utiliser un fournisseur DNS qui prend en charge le basculement entre plusieurs adresses IP comme solution de contournement.

Lorsqu'une région {{site.data.keyword.Bluemix_notm}} n'est plus disponible, les applications qui sont exécutées dans cette région ne sont plus disponibles non plus, même si les mêmes applications s'exécutent dans une autre région {{site.data.keyword.Bluemix_notm}}.
{: tsSymptoms}

{{site.data.keyword.Bluemix_notm}} ne fournit pas encore le basculement automatique d'une région vers une autre.
{: tsCauses}

Vous pouvez utiliser un fournisseur DNS qui prend en charge le basculement intelligent entre plusieurs adresses IP et configurer manuellement vos paramètres DNS pour activer le basculement automatique entre les régions {{site.data.keyword.Bluemix_notm}}. NSONE, Akamai et Dyn sont des fournisseurs DNS qui proposent cette fonction.
{: tsResolve}

Lorsque vous configurez vos paramètres DNS, vous devez spécifier les adresses IP publiques des régions {{site.data.keyword.Bluemix_notm}} dans lesquelles vos applications s'exécutent. Pour obtenir l'adresse IP publique d'une région {{site.data.keyword.Bluemix_notm}}, utilisez la commande `nslookup`. Vous pouvez, par exemple, entrer la commande suivante dans une fenêtre de ligne de commande.

```
nslookup stage1.mybluemix.net
```

## Impossible de faire passer les applications en mode débogage
{: #ts_debug}

Vous ne pouvez pas activer le mode débogage si votre version de machine virtuelle Java (JVM) est la version 8 ou une version antérieure.

Une fois l'option **Activer le débogage d'application** sélectionnée, les outils tentent de faire passer l'application en mode débogage. Le plan de travail Eclipse entame alors une session de débogage. Lorsque les outils parviennent à activer le mode débogage, le statut de l'application Web affiche `Mise à jour du mode`, `Développement`, et `Débogage`.
{: tsSymptoms}

En revanche, si les outils ne parviennent pas à activer le mode débogage, le statut de l'application Web indique uniquement `Mise à jour du mode` et `Développement`, sans afficher `Débogage`. Les outils peuvent également afficher le message d'erreur suivant dans la vue Console :

```
bluemixMgmgClient - ???? [pool-1-thread-1] .... ERROR --- ClientProxyImpl: Cannot create the websocket connections for MyWebProj
com.ibm.ws.cloudoe.management.client.exception.ApplicationManagementException: javax.websocket.DeploymentException: The HTTP request to initiate the  WebSocket connection failed
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:161)
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl$RunServerTask.run(ClientProxyImpl.java:267)
at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:522)
at java.util.concurrent.FutureTask.run(FutureTask.java:277)
at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1153)
at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
at java.lang.Thread.run(Thread.java:785)
Caused by: javax.websocket.DeploymentException: The HTTP request to initiate the WebSocket connection failed
at  org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:315)
at  com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:158)
... 6 more
Caused by: java.util.concurrent.TimeoutException
at org.apache.tomcat.websocket.AsyncChannelWrapperSecure$WrapperFuture.get(AsyncChannelWrapperSecure.java:505)
at org.apache.tomcat.websocket.WsWebSocketContainer.processResponse(WsWebSocketContainer.java:542)
at org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:296)
... 7 more
[2016-01-15 13:33:51.075] bluemixMgmgClient - ????  [pool-1-thread-1] .... ERROR --- ClientProxyImpl: Cannot create the  websocket connections for MyWebProj
com.ibm.ws.cloudoe.management.client.exception.ApplicationManagementException: javax.websocket.DeploymentException: The HTTP request to initiate the  WebSocket connection failed
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:161)
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl$RunServerTask.run(ClientProxyImpl.java:267)
at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:522)
at java.util.concurrent.FutureTask.run(FutureTask.java:277)
at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1153)
at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
at java.lang.Thread.run(Thread.java:785)
Caused by: javax.websocket.DeploymentException: The HTTP request to initiate the WebSocket connection failed
at org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:315)
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:158)
... 6 more
Caused by: java.util.concurrent.TimeoutException
at org.apache.tomcat.websocket.AsyncChannelWrapperSecure$WrapperFuture.get(AsyncChannelWrapperSecure.java:505)
at org.apache.tomcat.websocket.WsWebSocketContainer.processResponse(WsWebSocketContainer.java:542)
at org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:296)
... 7 autres
```

Les versions de machine virtuelle Java (JVM) suivantes ne peuvent pas établir une session de débogage : IBM JVM 7, IBM JVM 8 et les versions antérieures d'Oracle JVM 8.
{: tsCauses}

Si la machine virtuelle Java (JVM) de votre plan de travail correspond à l'une de ces versions, vous pouvez rencontrer des problèmes lorsque vous créez une session de débogage. La version de machine virtuelle Java de votre plan de travail est généralement celle de la JVM système de votre ordinateur local. Ce n'est pas la même que celle de votre application Java&trade; {{site.data.keyword.Bluemix_notm}} en cours d'exécution. L'application Java {{site.data.keyword.Bluemix_notm}} Java opère presque toujours sur la machine virtuelle Java IBM, et parfois sur la machine virtuelle Java OpenJDK.

Pour vérifier la version Java utilisée par {{site.data.keyword.eclipsetoolsfull}}, procédez comme suit :
{: tsResolve}

  1. Dans IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}, sélectionnez **Aide** > **A propos d'Eclipse** > **Détails de l'installation** > **Configuration**.
  2. Localisez la propriété `eclipse.vm` dans la liste. La ligne suivante est un exemple de propriété `eclipse.vm` :

	```
	eclipse.vm=C:\Program Files\IBM\ibm-java-sdk-80-win-x86_64\bin\..\jre\bin\j9vm\jvm.dll
	```

  3. Sur la ligne de commande, entrez `java -version` depuis le répertoire `bin` de votre installation Java. Les informations de version de votre JVM IBM s'affichent.

Si la machine virtuelle Java de votre plan de travail utilise la JVM 7 ou 8 d'IBM, ou une version antérieure à la JVM 8 d'Oracle 8, procédez comme suit pour passer à la JVM 8 d'Oracle :

  1. Téléchargez et installez Oracle JVM 8. Pour plus d'informations, voir [Java SE Downloads ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://www.oracle.com/technetwork/java/javase/downloads/index.html){: new_window}.
  2. Redémarrez Eclipse.
  3. Vérifiez que la propriété `eclipse.vm` pointe sur votre nouvelle installation de la JVM 8 d'Oracle.


## Impossible de réutiliser le nom des applications supprimées
{: #ts_reuse_appname}

Après avoir supprimé une application, vous ne pouvez réutiliser le nom de cette dernière qu'après en avoir supprimé la route.

Lorsque vous essayez de réutiliser le nom de l'application, vous recevez le message suivant :
{: tsSymptoms}

`Le nom est déjà utilisé par une autre application.`

Lorsqu'une application est supprimée, sa route, autrement dit, son URL, n'est pas automatiquement supprimée et n'est pas disponible pour être réutilisée. Vous devez accéder à l'espace où l'application a été créée afin de supprimer la route et pouvoir réutiliser l'application.
{: tsCauses}

Procédez comme suit pour supprimer la route inutilisée :
{: tsResolve}

  1. Vérifiez si la route appartient à l'espace en cours en entrant la commande suivante :

    ```
    cf routes
    ```

  2. Si la route n'appartient pas à l'espace en cours, basculez vers l'espace ou l'organisation à laquelle elle est rattachée en entrant la commande suivante :

    ```
    cf target -o org_name -s space_name
    ```

  3. Supprimez la route de l'application en entrant la commande suivante :

    ```
    cf delete-route domain_name -n host_name
    ```

  Par exemple :

  ```
  cf delete-route mybluemix.net -n app001
  ```

## Impossible d'extraire les espaces de l'organisation
{: #ts_retrieve_space}

Vous ne pouvez pas créer d'application ou de service si aucun espace n'est associé à votre organisation actuelle.

Lorsque vous tentez de créer une application dans {{site.data.keyword.Bluemix_notm}}, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`BXNUI0515E: Les espaces n'ont pas été extraits. Un problème de connexion réseau est survenu ou votre organisation actuelle n'est pas associée à un espace.`

Cette erreur se produit souvent la première fois que vous tentez de créer une application ou un service à partir du catalogue lorsque aucun espace n'est créé.
{: tsCauses}

Vérifiez que vous avez créé un espace dans votre organisation actuelle. Pour créer un espace, utilisez l'une des méthodes suivantes :
{: tsResolve}

* Dans la barre de menus, cliquez sur **Gérer > Compte > Organisations**. Sélectionnez l'organisation dans laquelle vous désirez créer le compte et cliquez sur **Créer un espace**.
* Dans l'interface de ligne de commande `cf`, entrez `cf create-space <space_name> -o <organization_name>`.

Essayez à nouveau. Si ce message se reproduit, accédez à la page [{{site.data.keyword.Bluemix_notm}} Statut ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://ibm.biz/bluemixstatus){: new_window} pour vérifier si un service ou un composant présente un problème.

## Impossible d'effectuer les actions demandées
{: #ts_authority}

Sans les autorisations d'accès appropriées, vous ne pouvez pas effectuer d'action.

Lorsque vous tentez d'effectuer des actions pour une instance de service ou d'application,  vous ne pouvez pas réaliser les actions demandées et rencontrez l'un des messages d'erreur suivants :
{: tsSymptoms}

`BXNUI0514E: Vous n'êtes pas un développeur dans l'un des espaces de l'organisation <orgName>.`

`Erreur de serveur, code statut : 403, code d'erreur : 10003, message : Vous n'êtes pas autorisé à effectuer l'action demandée.`

Vous ne disposez pas du niveau de droits approprié requis pour effectuer les actions.
{: tsCauses}

Pour obtenir le niveau d'autorisation approprié, utilisez l'une des méthodes suivantes.
{: tsResolve}

* Sélectionnez une autre organisation et un espace où le rôle développeur vous a été attribué.
* Demandez au responsable de l'organisation de vous attribuer le rôle développeur ou de créer un espace, puis de vous y affecter le rôle développeur. Voir [Gestion des organisations et des espaces](/docs/admin/orgs_spaces.html) pour plus d'informations.

## Impossible d'accéder aux services {{site.data.keyword.Bluemix_notm}} en raison d'erreurs d'autorisation
{: #ts_vcap}

Des erreurs d'autorisation peuvent se produite lorsque votre application accède à un service {{site.data.keyword.Bluemix_notm}} si les données d'identification du service sont codées en dur dans votre application.

Une fois que vous avez configuré votre application pour qu'elle communique avec un service {{site.data.keyword.Bluemix_notm}}, vous la déployez dans {{site.data.keyword.Bluemix_notm}}. Toutefois, vous ne pouvez pas utiliser l'application pour accéder au service {{site.data.keyword.Bluemix_notm}} et recevez une erreur d'autorisation.
{: tsSymptoms}

Il se peut que les données d'identification codées en dur dans l'application soient incorrectes. A chaque fois que le service est recréé, les données d'identification permettant d'y accéder changent.
{: tsCauses}

Au lieu de coder en dur les données d'identification dans votre application, utilisez les paramètres de connexion de la variable d'environnement VCAP_SERVICES. Les méthodes d'utilisation des paramètres de connexion de la variable d'environnement VCAP_SERVICES varient selon les langages de programmation. Par exemple, pour les applications Node.js, vous pouvez utiliser la commande suivante :
{: tsResolve}

```
process.env.VCAP_SERVICES
```
Pour plus d'informations sur les commandes que vous pouvez utiliser dans d'autres langages de programmation, voir [Java ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} et [Ruby ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window}.


## Impossible de déployer des applications à l'aide d'IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}
{: #ts_bm_tools_facet}

Lorsqu'une facette non prise en charge est appliquée à votre projet Eclipse, il se peut que vous ne puissiez pas déployer vos applications dans {{site.data.keyword.Bluemix_notm}} à l'aide d'IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}.

Votre application peut être déployée avec succès dans {{site.data.keyword.Bluemix_notm}} à l'aide de l'interface de ligne de commande Cloud Foundry. Toutefois, vous ne pouvez pas déployer l'application dans {{site.data.keyword.Bluemix_notm}} à l'aide d'IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} et le message d'erreur suivante s'affiche : `La facette de projet <facet_name> n'est pas prise en charge.` Exemple :
{: tsSymptoms}
`La facette de projet Cloud Foundry Standalone Application version 1.0 n'est pas prise en charge.`

Les outils IBM Eclipse pour
{{site.data.keyword.Bluemix_notm}} mappent des projets vers les contextes d'exécution
{{site.data.keyword.Bluemix_notm}} par facettes de projet. Les facettes définissent les exigences des projets Java EE dans Eclipse et sont utilisées dans le cadre de la configuration du contexte d'exécution pour que différents contextes d'exécution soient associés à différents projets. Si la facette appliquée au projet n'est pas prise en charge par IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}, vous ne pouvez pas déployer votre application en utilisant IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}.
{: tsCauses}

Vous devez supprimer la facette du projet Eclipse pour pouvoir déployer votre application à l'aide d'IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}.
{: tsResolve}

Pour supprimer la facette, cliquez dans IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}, sur **Projet > Propriétés> Facettes de projet** pour le projet concerné. Décochez ensuite la case correspondant à la facette non prise en charge.

## 502 Des erreurs Passerelle incorrecte sont renvoyées
{: #ts_502_error}

Si des erreurs 502 (passerelle incorrecte) sont générées lors d'une interaction avec des applications dans {{site.data.keyword.Bluemix_notm}}, vérifiez la page de statut {{site.data.keyword.Bluemix_notm}} puis effectuez les actions appropriées.

Vous recevez des messages d'erreur commençant par 502 Bad Gateway. Par exemple, vous pourriez rencontrer le message `502 Passerelle incorrecte : le noeud final enregistré n'a pas pu traiter la demande.`
{: tsSymptoms}

Une erreur de passerelle incorrecte se produit généralement lorsque vous accédez à un site Web qui utilise un serveur proxy pour stocker et relayer les données du serveur principal hébergeant le site. Il se peut que le serveur principal et le serveur proxy ne se connectent pas correctement. Le code d'état HTTP 502 s'affiche alors dans votre fenêtre de navigateur. Ce code d'état indique que le serveur principal du site n'a pas reçu l'implémentation HTTP attendue de la part du serveur proxy.
{: tsCauses}

Motifs moins fréquents d'une erreur de passerelle incorrecte : interruptions du fournisseur d'accès internet, configurations incorrectes du pare-feu et erreurs de cache du navigateur.

Si vous suspectez l'arrêt d'un service {{site.data.keyword.Bluemix_notm}}, consultez d'abord la page [{{site.data.keyword.Bluemix_notm}} Statut ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://ibm.biz/bluemixstatus){: new_window}. Une solution de contournement peut consister à utiliser le service dans une autre région {{site.data.keyword.Bluemix_notm}}. Des informations détaillées sont disponibles dans la section [Utilisation des services dans une autre région ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/reqnsi.html#cross_region_service){: new_window}. Si le statut du service est normal, essayez la procédure suivante pour résoudre le problème :
{: tsResolve}

  * Réessayez l'action :
    * Rechargez la page en appuyant sur la touche F5 de votre clavier ou en cliquant sur le bouton **Actualiser**. Si cette étape ne fonctionne pas, videz le cache de votre navigateur et supprimez les cookies, puis rechargez la page.
    * Utilisez un navigateur différent.
    * Redémarrez votre routeur, votre modem et votre ordinateur. Le réamorçage de ces unités peut éliminer diverses erreurs à l'origine de l'erreur 502.
  * Patientez et essayez à nouveau ultérieurement. Des problèmes temporaires peuvent se produire avec votre fournisseur d'accès Internet ou les services {{site.data.keyword.Bluemix_notm}}. Vous pouvez attendre jusqu'à ce que les problèmes temporaires soient résolus.
  * Si le problème persiste, contactez le support {{site.data.keyword.Bluemix_notm}}. Voir [Contact du support {{site.data.keyword.Bluemix_notm}} ![ Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](/docs/support/index.html#contacting-bluemix-support){: new_window} pour plus d'informations.

## Dépassement du quota de disque
{: #ts_disk_quota}

Si votre espace disque est épuisé, vous pouvez modifier manuellement le quota de disque pour disposer de plus d'espace.

Lorsque votre espace disque devient insuffisant, un message indiquant que le quota de disque est dépassé peut s'afficher. Pour résoudre le problème, vous pouvez tenter d'augmenter votre instance d'application pour obtenir davantage d'espace disque. Par exemple, vous pouvez passer de 256 Mo à 1256 Mo en modifiant le quota de mémoire sur la page de détails de l'application. Cependant, comme le quota de disque est resté le même, vous n'avez pas obtenu plus d'espace disque.
{: tsSymptoms}

Le quota de disque par défaut alloué à une application est de 1 Go. Si vous avez besoin de davantage d'espace disque, vous devez spécifier manuellement le quota de disque.
{: tsCauses}

Utilisez l'une des méthodes suivantes pour spécifier votre quota de disque. Le quota de disque maximal que vous pouvez spécifier est de 2 Go. Si les 2 Go ne sont toujours pas suffisants, essayez un service externe, tel que [Object Store](/docs/services/ObjectStorage/index.html).
{: tsResolve}

  * Dans le fichier manifest.yml, ajoutez l'élément suivant :
    ```
	disk_quota: <disk_quota>
	```
  * Utilisez l'option **-k** avec la commande `cf push` lorsque vous envoyez par commande push votre application à {{site.data.keyword.Bluemix_notm}} :
    ```
	cf push appname -p app_path -k <disk_quota>
	```

## Les applications Android ne peuvent pas recevoir de {{site.data.keyword.mobilepushshort}}
{: #ts_push}

Dans certaines régions où Google n'est pas accessible, les applications Android ne peuvent pas recevoir les notifications que vous envoyez via le service IBM {{site.data.keyword.mobilepushshort}}. Dans ce cas, une solution de contournement consiste à utiliser des services tiers.

Vous liez un service {{site.data.keyword.mobilepushshort}} pour votre application {{site.data.keyword.Bluemix_notm}} et envoyez un message aux unités enregistrées. Toutefois, les applications qui sont développées sous Android ne peuvent pas recevoir vos notifications dans certaines régions.
{: tsSymptoms}

Le service IBM {{site.data.keyword.mobilepushshort}} utilise le service GCM (Google Cloud Messaging) pour diffuser les notifications aux applications mobiles développées sous Android. Les applications mobiles doivent pouvoir accéder au service GCM pour que les applications Android puissent recevoir les notifications. Dans les régions où les applications Android ne peuvent pas accéder au service GCM, ces dernières ne peuvent pas recevoir de notifications {{site.data.keyword.mobilepushshort}}.
{: tsCauses}

Comme solution palliative, utilisez des services de tiers qui ne sont pas basés sur les services GCM, par exemple [Pushy ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://pushy.me){: new_window}, [getui ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://www.getui.com/){: new_window} et [jpush ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.jpush.cn/){: new_window}.
{: tsResolve}

## La limite de services de l'organisation est dépassée
{: #ts_servicelimit}

Si vous utilisez un compte Lite, il se peut que vous ne puissiez pas déployer d'application dans {{site.data.keyword.Bluemix_notm}} si vous avez atteint le nombre maximal de services pour votre organisation.

Lorsque vous tentez de créer une application dans {{site.data.keyword.Bluemix_notm}}, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`BXNUI2032E: La ressource <service_instances> n'a pas été créée. Une erreur est survenue lors du contact de Cloud Foundry pour la création d'une ressource. Message Cloud Foundry : "You have exceeded your organization's services limit."`

Cette erreur survient lorsque le nombre maximal d'instances de service dont vous pouvez disposer pour votre compte est dépassé.
{: tsCauses}

Supprimez les instances de service dont vous n'avez pas besoin ou supprimez la limite portant sur le nombre de services que vous pouvez utiliser.
{: tsResolve}

  * Pour supprimer une instance de service, vous pouvez utiliser la console {{site.data.keyword.Bluemix_notm}} ou l'interface de ligne de commande.

    Pour utiliser la console {{site.data.keyword.Bluemix_notm}} afin de supprimer une instance de service, procédez comme suit :
	  1. Dans le tableau de bord Services, cliquez sur le menu **Actions** du service que vous désirez supprimer.
	  2. Cliquez sur **Supprimer le service**. Vous êtes invité à reconstituer l'application à laquelle l'instance de service était liée.

    Pour utiliser l'interface de ligne de commande pour supprimer une instance de service, procédez comme suit :
	  3. Annulez la liaison de l'instance de service à l'application en entrant `cf unbind-service <appname> <service_instance_name>`.
	  4. Supprimez l'instance de service en entrant `cf delete-service <service_instance_name>`.
	  5. Une fois l'instance de service supprimée, vous pouvez reconstituer l'application à laquelle l'instance de service était liée en entrant `cf restage <appname>`.

  * Pour supprimer la limite de nombre d'instances de service dont vous pouvez disposer, mettez à niveau votre compte Lite vers un compte facturable. Pour plus d'informations, voir [Mise à niveau de votre compte](/docs/account/index.html#upgrade-to-paygo).

## Impossible d'exécuter des fichiers exécutables sur {{site.data.keyword.Bluemix_notm}}
{: #ts_executable}

Il peut s'avérer impossible d'exécuter des fichiers exécutables sur {{site.data.keyword.Bluemix_notm}} si ces fichiers ont été développés et générés dans un environnement différent.

Vous ne parvenez pas à exécuter des fichiers exécutables dans {{site.data.keyword.Bluemix_notm}} lorsque ceux-ci ont été développés et générés dans un environnement différent.
{: tsSymptoms}

Si le contenu à envoyer par commande push dans {{site.data.keyword.Bluemix_notm}} est déjà un fichier exécutable, il a été construit au préalable et n'a pas besoin d'être construit dans {{site.data.keyword.Bluemix_notm}}. Dans ce cas, aucun pack de construction n'est requis pour l'exécution du fichier exécutable dans {{site.data.keyword.Bluemix_notm}}. Vous devez indiquer explicitement à {{site.data.keyword.Bluemix_notm}} qu'aucun pack de construction n'est nécessaire.
{: tsCauses}

Lorsque vous envoyez par commande push le fichier exécutable dans {{site.data.keyword.Bluemix_notm}}, vous devez spécifier la valeur `null-buildpack`, qui indique qu'aucun package de construction n'est requis. Spécifiez la valeur `null-buildpack` avec l'option **-b** dans la commande `cf push` :
{: tsResolve}

```
cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
Exemple :
```
cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```

## La limite mémoire de l'organisation est dépassée
{: #ts_outofmemory}

Si vous utilisez un compte Lite, il se peut que vous ne puissiez pas déployer d'application dans {{site.data.keyword.Bluemix_notm}} si vous avez atteint la limite de mémoire de votre organisation. Vous pouvez réduire la quantité de mémoire que vos applications utilisent ou augmenter le quota de mémoire de votre compte. Le quota de mémoire maximal pour un compte Lite est de 256 Go. Il ne peut être augmenté qu'en passant à un compte facturable.

Lorsque vous déployez une application dans {{site.data.keyword.Bluemix_notm}}, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

Cette erreur survient lorsque la quantité de mémoire restante pour votre organisation est inférieure à la quantité de mémoire requise par l'application à déployer. Le quota de mémoire maximal pour un compte Lite est de 256 Go.
{: tsCauses}

Vous pouvez augmenter le quota de mémoire de votre compte ou diminuer la mémoire que vos applications utilisent.
{: tsResolve}

  * Pour augmenter le quota de mémoire de votre compte, convertissez votre compte Lite en compte facturable. Pour plus d'informations, voir [Mise à niveau de votre compte](/docs/account/index.html#upgrade-to-paygo).
  * Pour réduire la quantité de mémoire consommée par vos applications, utilisez la console {{site.data.keyword.Bluemix_notm}} ou l'interface de ligne de commande `cf`.

    Si vous utilisez la console {{site.data.keyword.Bluemix_notm}}, procédez comme suit :

    1. Sélectionnez votre application dans le tableau de bord. La page des détails de l'application s'ouvre.
    2. Dans le panneau Contexte d'exécution, vous pouvez réduire la limite de mémoire maximale, le nombre d'instances d'application, ou les deux, pour votre application.

    Si vous utilisez l'interface de ligne de commande `cf`, procédez comme suit :

    1. Vérifiez la quantité de mémoire utilisée par vos applications :

	  ```
	  cf apps
	  ```

	  La commande `cf apps` répertorie toutes les applications déployées dans votre espace en cours. Le statut de chaque application est également affiché.

    2. Pour réduire la quantité de mémoire qui est utilisée par votre application, réduisez le nombre d'instances d'application ou la limite de mémoire maximale, ou les deux :

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```

    3. Redémarrez votre application pour que les modifications soient appliquées.

## Les applications ne sont pas redémarrées automatiquement
{: #ts_apps_not_auto_restarted}

Une application n'est pas redémarrée automatiquement lorsqu'un service que vous liez à cette application cesse de fonctionner.

Lorsqu'un service que vous liez à une application tombe en panne, des problèmes tels que des indisponibilités, des exceptions et des échecs de connexion peuvent survenir sur l'application. {{site.data.keyword.Bluemix_notm}} ne redémarre pas automatiquement l'application pour assurer la reprise suite à ces problèmes.
{: tsSymptoms}

Ce comportement est normal dans Cloud Foundry.
{: tsCauses}

Vous pouvez redémarrer manuellement l'application en entrant la commande suivante dans l'interface de ligne de commande :
{: tsResolve}

```
cf push appname -p app_path
```

De plus, vous pouvez coder l'application afin d'identifier les problèmes et d'assurer la reprise après une indisponibilité, une exception ou un échec de connexion.

## Les variables définies par l'utilisateur sont perdues lorsqu'une application est envoyée par commande push
{: #ts_varsnotretained}

Lorsque vous envoyez une application par commande push à {{site.data.keyword.Bluemix_notm}} depuis IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}, les variables que vous spécifiez sont réinitialisées sauf si vous les sauvegardez dans le fichier manifeste.

Les variables que vous spécifiez sont perdues une fois que vous avez envoyé une application par commande push à {{site.data.keyword.Bluemix_notm}} depuis IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}.
{: tsSymptoms}

Les variables que vous spécifiez ne sont sauvegardées que si vous les sauvegardez dans le fichier manifeste.
{: tsCauses}

Lorsque vous envoyez une application par commande push à {{site.data.keyword.Bluemix_notm}} depuis IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}, sélectionnez la case à cocher **Save to the manifest file** dans la page des détails de l'application de l'assistant Application. Ainsi, les variables que vous spécifiez dans l'assistant sont sauvegardées dans le fichier manifeste de votre application. A la prochaine ouverture de l'assistant, elles seront affichées automatiquement.
{: tsResolve}


## Des organisations sont introuvables dans {{site.data.keyword.Bluemix_notm}}
{: #ts_orgs}

Il se peut que vous ne parveniez pas à localiser votre organisation dans {{site.data.keyword.Bluemix_notm}} lorsque vous travaillez sur une région {{site.data.keyword.Bluemix_notm}}.

Vous pouvez vous connecter à la console {{site.data.keyword.Bluemix_notm}}, mais vous ne parvenez pas à envoyer vos applications par commande push à l'aide de l'interface de ligne de commande `cf` ou du plug-in Eclipse.
{: tsSymptoms}

Lorsque vous tentez d'envoyer une application par commande push à {{site.data.keyword.Bluemix_notm}} en utilisant l'interface de ligne de commande `cf`, l'un des messages suivants suivants, qui spécifie le nom de l'organisation, s'affiche :

`Erreur lors de la recherche de l'organisation`

`Organization not found`

Lorsque vous essayez d'envoyer une application par commande push à {{site.data.keyword.Bluemix_notm}} en utilisant le plug-in Eclipse Cloud Foundry, le message d'erreur suivant s'affiche :

`cloudspace not found.`

Ce problème survient car le noeud final d'API de la région avec laquelle vous travaillez n'est pas spécifié et l'organisation que vous recherchez peut se trouver dans une autre région.
{: tsCauses}

Si vous envoyez votre application par commande push à {{site.data.keyword.Bluemix_notm}} en utilisant l'interface de ligne de commande `cf`, entrez la commande `cf api` et spécifiez le noeud final d'API de la région. Par exemple, entrez la commande suivante pour vous connecter à la région {{site.data.keyword.Bluemix_notm}} Europe et Royaume-Uni :
{: tsResolve}

```
cf api https://api.eu-gb.bluemix.net
```

Si vous envoyez votre application par commande push à {{site.data.keyword.Bluemix_notm}} en utilisant les outils Eclipse, vous devez d'abord créer un serveur {{site.data.keyword.Bluemix_notm}} et spécifier le noeud final d'API de la région {{site.data.keyword.Bluemix_notm}} dans laquelle votre organisation a été créée. Pour plus d'informations sur l'utilisation des outils Eclipse, voir [Déploiement d'applications avec IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}](/docs/manageapps/eclipsetools/eclipsetools.html).

## Impossible de créer les routes d'application
{: #ts_hostistaken}

Lorsque vous déployez une application dans {{site.data.keyword.Bluemix_notm}}, la route d'application ne peut pas être créée si le nom d'hôte que vous avez spécifié est déjà utilisé.

Lorsque vous déployez une application dans {{site.data.keyword.Bluemix_notm}}, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`Creating route hostname.domainname ... FAILED Server error, status code: 400, error code: 210003, message: The host is taken: hostname`

Ce problème survient si le nom d'hôte que vous avez spécifié est déjà utilisé.
{: tsCauses}

Le nom d'hôte que vous spécifiez doit être unique dans le domaine que vous utilisez. Pour spécifier un autre nom d'hôte, utilisez l'une des méthodes suivantes :
{: tsResolve}

  * Si vous déployez votre application avec le fichier `manifest.yml`, spécifiez le nom d'hôte dans l'option host.
    ```
    host: host_name
	```
  * Si vous déployez votre application depuis l'invite de commande, utilisez la commande `cf push` avec l'option **-n**.
    ```
    cf push appname -p app_path -n host_name
    ```

## Les applications WAR ne peuvent pas être envoyées à l'aide de la commande cf push
{: #ts_cf_war}

Il est possible que vous ne puissiez pas utiliser la commande `cf push` pour déployer une application Web archivée dans {{site.data.keyword.Bluemix_notm}} si l'emplacement de l'application n'est pas spécifié correctement.

Lorsque vous téléchargez une application WAR dans {{site.data.keyword.Bluemix_notm}} par l'intermédiaire de la commande `cf push`, le message d'erreur suivant s'affiche :
{: tsSymptoms}
`Staging error: cannot get instances since staging failed.`

Ce problème peut se produire si le fichier WAR ou le chemin d'accès à ce fichier n'est pas spécifié.
{: tsCauses}

Utilisez l'option **-p** pour spécifier un fichier WAR ou ajouter un chemin d'accès. Exemple :
{: tsResolve}

```
cf push MyUniqueAppName01 -p app.war
```

```
cf push MyUniqueAppName02 -p "./app.war"
```
Pour plus d'informations sur la commande `cf push`, entrez `cf push -h`.

## Les caractères codés sur deux octets ne s'affichent pas correctement lorsque des applications sont envoyées par commande push vers {{site.data.keyword.Bluemix_notm}}
{: #ts_doublebytes}

Il se peut que les caractères codés sur deux octets ne s'affichent pas correctement si la prise en charge Unicode n'est pas configurée correctement pour le servlet ou les fichiers JSP.

Lorsqu'une application est envoyée par commande push dans {{site.data.keyword.Bluemix_notm}}, les caractères codés sur deux octets spécifiés dans l'application ne s'affichent pas correctement.
{: tsSymptoms}

Le problème peut se produire si la prise en charge Unicode n'est pas configurée correctement pour le servlet ou les fichiers JSP.
{: tsCauses}

Utilisez le code suivant dans votre servlet ou votre fichier JSP :
{: tsResolve}

  * Dans le fichier source servlet
    ```
	response.setContentType("text/html; charset=UTF-8");
	```
  * Dans le fichier JSP
    ```
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```

## Les applications Node.js ne peuvent pas être déployées
{: #ts_nodejs_deploy}

Des problèmes peuvent survenir lorsque vous mettez à jour ou déployez une application Node.js dans {{site.data.keyword.Bluemix_notm}}.

Lorsque vous mettez à jour ou déployez votre application Node.js dans {{site.data.keyword.Bluemix_notm}}, l'un des messages d'erreur suivants peut s'afficher :
{: tsSymptoms}

`Aucune application n'a été détectée par les packs de construction disponibles.`

`L'Instance (index 0) ne peut pas commencer à accepter des connexions.`

`Impossible d'obtenir des instances vu que leur transfert a échoué.`

Causes possibles :
{: tsCauses}

  * La commande de démarrage n'a pas été spécifiée.
  * Des fichiers requis pour déployer une application Node.js sont manquants dans l'application ou résident dans un dossier autre que le répertoire racine.

Utilisez l'une des méthodes suivantes, selon la cause du problème :
{: tsResolve}

  * Spécifiez la commande de démarrage à l'aide d'une des méthodes suivantes :
     * Utilisez l'interface de ligne de commande `cf`. Exemple :
        ```
		cf push MonNoeudJsUnique01 -p chemin_app -c "node app.js"
		```
    * Utilisation du fichier [package.json ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.npmjs.com/package/jsonfile){: new_window}. Exemple :
	    ```
		{
      ...
  	   "scripts": {
	 		 "start": "node app.js"
 	   }
	}
	    ```
    * Utilisez le fichier `manifest.yml`. Exemple :
	    ```
		applications:
  name: MyUniqueNodejs01
  ...
  command: node app.js
  ...
        ```

  * Vérifiez qu'un fichier `package.json` existe dans votre application Node.js pour que le pack de construction Node.js puisse reconnaître l'application. Prenez soin de placer ce fichier dans le répertoire racine de votre application.
    L'exemple suivant représente un fichier `package.json` simple :
	```
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

Pour obtenir des conseils supplémentaires relatifs aux applications Node.js, voir [Tips for Node.js Applications ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window}.

## Des erreurs de configuration figurent dans le fichier `server.xml` après avoir importé une application {{site.data.keyword.Bluemix_notm}} Liberty dans Eclipse
{: #ts_eclipse}

Si vous rencontrez des erreurs de configuration dans le fichier `server.xml` après avoir importé une application {{site.data.keyword.Bluemix_notm}} Liberty dans Eclipse, vous devrez peut-être supprimer du projet le fichier `server.xml`.

Après avoir importé une application {{site.data.keyword.Bluemix_notm}} Liberty dans Eclipse, vous rencontrez des erreurs de configuration dans le fichier `server.xml` dans la vue Erreurs d'Eclipse.
{: tsSymptoms}

Le pack de construction Liberty utilise le fichier `server.xml` pour configurer l'application et génère un fichier `runtime-vars.xml` lorsque l'application Liberty est envoyée par commande push dans {{site.data.keyword.Bluemix_notm}}. Lorsque vous importez l'application dans Eclipse, le fichier `runtime-vars.xml` n'existe pas dans votre environnement local.
{: tsCauses}

Pour résoudre ce problème, supprimez le fichier server.xml du projet. Le pack de construction crée le fichier `server.xml` de manière dynamique lorsque vous envoyez par commande push l'application sous forme d'application WAR. Pour plus d'informations, voir [Liberty for Java](/docs/runtimes/liberty/index.html).
{: tsResolve}

## Les applications ne peuvent pas être transférées à l'aide de packs de construction personnalisés
{: #ts_bp_compilation}

Il se peut que vous ne puissiez pas déployer d'application dans {{site.data.keyword.Bluemix_notm}} à l'aide d'un pack de construction personnalisé si les scripts que ce dernier contient ne sont pas des fichiers exécutables.

Lorsque vous déployez une application dans {{site.data.keyword.Bluemix_notm}} à l'aide d'un pack de construction personnalisé, le message d'erreur `La constitution de l'application a échoué ; par conséquent, il n'y a pas d'instance à afficher` s'affiche.
{: tsSymptoms}

Ce problème peut se produire si des scripts (tels que le script de détection, le script de compilation ou le script de publication) ne sont pas exécutables.
{: tsCauses}

Vous pouvez utiliser la commande [Git update ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://git-scm.com/docs/git-update-index){: new_window} pour faire en sorte que chaque script soit exécutable. Par exemple, vous pouvez entrer `git update --chmod=+x script.sh`.
{: tsResolve}

## Impossible de déployer une application depuis Delivery Pipeline dans {{site.data.keyword.Bluemix_notm}} Continuous Delivery
 {: #ts_devops_to_bm}

 Il se peut que vous ne puissiez pas déployer votre application à l'aide de {{site.data.keyword.deliverypipeline}} dans {{site.data.keyword.contdelivery_short}} si le fichier `manifest.yml` n'est pas présent dans votre application.

 Lorsque vous déployez une application à l'aide de {{site.data.keyword.deliverypipeline}} dans {{site.data.keyword.contdelivery_short}}, il se peut que le message d'erreur `Unable to detect a supported application type` s'affiche.
 {: tsSymptoms}

 Ce problème peut survenir car le pipeline requiert un fichier `manifest.yml` pour déployer une application dans {{site.data.keyword.Bluemix_notm}}.
 {: tsCauses}

 Pour remédier à ce problème, vous devez créer un fichier `manifest.yml`. Pour plus d'informations sur la création du fichier `manifest.yml`, voir [Manifeste d'application](/docs/manageapps/depapps.html#appmanifest).
 {: tsResolve}

## Les applis Meteor ne peuvent pas être envoyées par commande push
{: #ts_meteor}

Il se peut que vous ne puissiez pas envoyer une application Meteor par commande push dans {{site.data.keyword.Bluemix_notm}} si le pack de construction n'est pas spécifié correctement.

Lorsque vous déployez une appli Meteor dans {{site.data.keyword.Bluemix_notm}}, il se peut que le message d'erreur `La constitution de l'application a échoué ; par conséquent, il n'y a pas d'instance à afficher` s'affiche.
{: tsSymptoms}

Ce problème survient car aucun pack de construction n'est fourni pour les applications Meteor. Vous devez utiliser un pack de construction personnalisé.
{: tsCauses}

Afin d'utiliser un pack de construction personnalisé pour les applications Meteor, appliquez l'une des méthodes suivantes :
{: tsResolve}

  * Si vous déployez votre application avec le fichier `manifest.yml`, spécifiez l'adresse URL ou le nom de votre pack de construction personnalisé avec l'option buildpack. Par exemple :
  ```
  buildpack: https://github.com/Sing-Li/bluemix-bp-meteor
  ```
  * Si vous déployez votre application depuis l'invite de commande, utilisez la commande `cf
push` et spécifiez votre pack de construction personnalisé avec l'option **-b**. Exemple :
    ```
	cf push appname -p app_path -b https://github.com/Sing-Li/bluemix-bp-meteor
	```
