---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-03"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Traitement des incidents liés à la création d'applications
{: #managingapps}

Des problèmes d'ordre général liés à la création d'applications peuvent survenir, par exemple, les applications ne peuvent pas être mises à jour ou les caractères codés sur deux octets ne sont pas affichés. Dans de nombreux cas, ces problèmes peuvent être résolus en quelques opérations simples.
{:shortdesc}

## Des modifications n'ont pas été sauvegardées
{: #ts_unsaved_changes}
{: troubleshoot}

Lorsque vous cliquez sur des éléments de la page des détails de l'application, il est possible que vous ne puissiez pas effectuer d'action. Vous pouvez également être invité à sauvegarder vos modifications avant de pouvoir continuer.

Lorsque vous essayez de vérifier votre application ou vos services sur la page des détails de l'application, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`You have unsaved changes. Are you sure you want to leave this page?`

Lorsque vous survolez avec la souris les zones **INSTANCES** ou **QUOTA DE MEMOIRE** dans le panneau du contexte d'exécution, les valeurs changent. Ce comportement est normal. Toutefois, vous êtes invité à sauvegarder les paramètres de mémoire ou d'instance avant d'accéder à une autre page.
{: tsCauses}

Fermez la fenêtre de message puis cliquez sur **REINITIALISER** dans votre panneau d'exécution.
{: tsResolve}

## Le basculement automatique entre les régions {{site.data.keyword.cloud_notm}} n'est pas disponible
{: #ts_failover}
{: troubleshoot}

Vous ne pouvez pas utiliser le basculement automatique entre les régions {{site.data.keyword.cloud}}. Toutefois, vous pouvez utiliser un fournisseur DNS qui prend en charge le basculement entre plusieurs adresses IP comme solution de contournement.

Lorsqu'une région {{site.data.keyword.cloud_notm}} n'est plus disponible, les applications qui sont exécutées dans cette région ne sont plus disponibles non plus, même si les mêmes applications s'exécutent dans une autre région {{site.data.keyword.cloud_notm}}.
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} ne fournit pas encore le basculement automatique d'une région vers une autre.
{: tsCauses}

Vous pouvez utiliser un fournisseur DNS qui prend en charge le basculement intelligent entre plusieurs adresses IP et configurer manuellement vos paramètres DNS pour activer le basculement automatique entre les régions {{site.data.keyword.cloud_notm}}. Les fournisseurs DNS avec cette fonction incluent NSONE, Akamai et Dyn.
{: tsResolve}

Lorsque vous configurez vos paramètres DNS, vous devez spécifier les adresses IP publiques des régions {{site.data.keyword.cloud_notm}} dans lesquelles vos applications s'exécutent. Pour obtenir l'adresse IP publique d'une région {{site.data.keyword.cloud_notm}}, utilisez la commande `nslookup`. Vous pouvez, par exemple, entrer la commande suivante dans une fenêtre de ligne de commande.
```
nslookup cloud.ibm.com
```
{: codeblock}

## Impossible de réutiliser le nom des applications supprimées
{: #ts_reuse_appname}
{: troubleshoot}

Après avoir supprimé une application, vous ne pouvez réutiliser le nom de cette dernière qu'après en avoir supprimé la route.

Lorsque vous essayez de réutiliser le nom de l'application, le message suivant s'affiche :
{: tsSymptoms}

`The name is already used by another app.`

Lorsqu'une application est supprimée, sa route, autrement dit, son URL, n'est pas automatiquement supprimée et n'est pas disponible pour être réutilisée. Vous devez accéder à l'espace où l'application a été créée afin de supprimer la route et pouvoir réutiliser l'application.
{: tsCauses}

Procédez comme suit pour supprimer la route inutilisée :
{: tsResolve}

  1. Vérifiez si la route appartient à l'espace en cours en entrant la commande suivante :
    ```
    ibmcloud cf routes
    ```
    {: codeblock}

  2. Si la route n'appartient pas à l'espace en cours, basculez vers l'espace ou l'organisation à laquelle elle est rattachée en entrant la commande suivante :
    ```
    ibmcloud cf target -o org_name -s space_name
    ```
    {: codeblock}

  3. Supprimez la route de l'application en entrant la commande suivante :
    ```
    ibmcloud cf delete-route domain_name -n host_name
    ```
    {: codeblock}

  Par exemple :
  ```
  ibmcloud cf delete-route cf.cloud.ibm.com -n app001
  ```
  {: codeblock}

## Impossible d'extraire les espaces de l'organisation
{: #ts_retrieve_space}
{: troubleshoot}

Vous ne pouvez pas créer d'application ou de service si aucun espace n'est associé à votre organisation actuelle.

Lorsque vous tentez de créer une application dans {{site.data.keyword.cloud_notm}}, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`BXNUI0515E: The spaces in the org weren't retrieved. Either a network connection problem occurred, or your current organization does not have a space associated with it.`

Cette erreur se produit souvent la première fois que vous tentez de créer une application ou un service à partir du catalogue lorsque aucun espace n'est créé.
{: tsCauses}

Vérifiez que vous avez créé un espace dans votre organisation actuelle. Pour créer un espace, appliquez l'une des méthodes suivantes :
{: tsResolve}

* Dans la barre de menus, cliquez sur **Gérer > Compte** et sélectionnez **Organisations Cloud Foundry**. Cliquez sur le nom de l'organisation dans laquelle vous souhaitez créer l'espace puis cliquez sur **Ajouter un espace**.
* Dans l'interface de ligne de commande Cloud Foundry, entrez `cf create-space <space_name> -o <organization_name>`.

Essayez à nouveau. Si ce message se reproduit, accédez à la page [{{site.data.keyword.cloud_notm}} Statut ](http://ibm.biz/bluemixstatus){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") pour vérifier si un service ou un composant présente un problème.

## Impossible d'effectuer les actions demandées
{: #ts_authority}
{: troubleshoot}

Sans les autorisations d'accès appropriées, vous ne pouvez pas effectuer d'action.

Lorsque vous tentez d'effectuer des actions pour une instance de service ou d'application, vous ne pouvez pas réaliser les actions demandées et rencontrez l'un des messages d'erreur suivants :
{: tsSymptoms}

`BXNUI0514E: You are not a developer for any of the spaces in the <orgName> organization.`

`Server error, status code: 403, error code: 10003, message: You are not authorized to perform the requested action.`

Vous ne disposez pas du niveau de droits approprié requis pour effectuer les actions.
{: tsCauses}

Pour obtenir le niveau d'autorisation approprié, utilisez l'une des méthodes suivantes.
{: tsResolve}

* Sélectionnez une autre organisation et un espace où le rôle Développeur vous a été attribué.
* Demandez au responsable de l'organisation de vous attribuer le rôle Développeur ou de créer un espace, puis de vous affecter le rôle Développeur. Voir [Gestion des organisations et des espaces](/docs/iam?topic=iam-cfaccess#cfaccess) pour plus d'informations.

## Impossible d'accéder aux services {{site.data.keyword.cloud_notm}} en raison d'erreurs d'autorisation
{: #ts_vcap}
{: troubleshoot}

Des erreurs d'autorisation peuvent se produite lorsque votre application accède à un service {{site.data.keyword.cloud_notm}} si les données d'identification du service sont codées en dur dans votre application.

Une fois que vous avez configuré votre application pour qu'elle communique avec un service {{site.data.keyword.cloud_notm}}, vous la déployez dans {{site.data.keyword.cloud_notm}}. Toutefois, vous ne pouvez pas utiliser l'application pour accéder au service {{site.data.keyword.cloud_notm}} et recevez une erreur d'autorisation.
{: tsSymptoms}

Il se peut que les données d'identification codées en dur dans l'application soient incorrectes. A chaque fois que le service est recréé, les données d'identification permettant d'y accéder changent.
{: tsCauses}

Au lieu de coder en dur les données d'identification dans votre application, utilisez les paramètres de connexion de la variable d'environnement VCAP_SERVICES. Les méthodes d'utilisation des paramètres de connexion de la variable d'environnement VCAP_SERVICES varient selon les langages de programmation. Par exemple, pour les applications Node.js, vous pouvez utiliser la commande suivante :
{: tsResolve}

```
process.env.VCAP_SERVICES
```

Pour plus d'informations sur les commandes que vous pouvez utiliser dans d'autres langages de programmation, voir [Java](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") et[Ruby](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

## Erreurs 502 Bad Gateway (passerelle incorrecte)
{: #ts_502_error}
{: troubleshoot}

Si des erreurs `502 Bad Gateway` (passerelle incorrecte) sont générées lors d'une interaction avec des applications dans {{site.data.keyword.cloud_notm}}, vérifiez la page de statut {{site.data.keyword.cloud_notm}} puis effectuez les actions appropriées.

Vous recevez des messages d'erreur commençant par 502 Bad Gateway. Par exemple, vous pourriez rencontrer le message `502 Bad Gateway: Registered endpoint failed to handle the request.`
{: tsSymptoms}

Une erreur de passerelle incorrecte se produit généralement lorsque vous accédez à un site Web qui utilise un serveur proxy pour stocker et relayer les données du serveur principal hébergeant le site. Il se peut que le serveur principal et le serveur proxy ne se connectent pas correctement. Le code d'état HTTP 502 s'affiche alors dans votre fenêtre de navigateur. Ce code d'état indique que le serveur principal du site n'a pas reçu l'implémentation HTTP attendue de la part du serveur proxy.
{: tsCauses}

Motifs moins fréquents d'une erreur de passerelle incorrecte : interruptions du fournisseur d'accès internet, configurations incorrectes du pare-feu et erreurs de cache du navigateur.

Si vous suspectez l'arrêt d'un service {{site.data.keyword.cloud_notm}}, consultez d'abord la page [{{site.data.keyword.cloud_notm}} Statut ](http://ibm.biz/bluemixstatus){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"). L'[utilisation du service dans une autre région {{site.data.keyword.cloud_notm}}](/docs/resources/connect_external_app#externalapp){: new_window} peut être une solution palliative. Si le statut du service est normal, essayez la procédure suivante pour résoudre le problème :
{: tsResolve}

  * Réessayez l'action :
    * Rechargez la page en appuyant sur la touche F5 de votre clavier ou en cliquant sur le bouton **Actualiser**. Si cette étape ne fonctionne pas, videz le cache de votre navigateur et supprimez les cookies, puis rechargez la page.
    * Utilisez un navigateur différent.
    * Redémarrez votre routeur, votre modem et votre ordinateur. Le réamorçage de ces unités peut éliminer diverses erreurs à l'origine de l'erreur 502.
  * Patientez et essayez à nouveau ultérieurement. Des problèmes temporaires peuvent se produire avec votre fournisseur d'accès Internet ou les services {{site.data.keyword.cloud_notm}}. Vous pouvez attendre jusqu'à ce que les problèmes temporaires soient résolus.
  * Si le problème persiste, contactez le support {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir la rubrique présentant comment [contacter le support {{site.data.keyword.cloud_notm}}](/docs/support/index.html#contacting-bluemix-support){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

## Dépassement du quota de disque
{: #ts_disk_quota}
{: troubleshoot}

Si votre espace disque est épuisé, vous pouvez modifier manuellement le quota de disque pour disposer de plus d'espace.

Lorsque votre espace disque devient insuffisant, un message indiquant que le quota de disque est dépassé peut s'afficher. Pour résoudre le problème, vous pouvez tenter d'augmenter votre instance d'application pour obtenir davantage d'espace disque. Par exemple, vous pouvez passer de 256 Mo à 1 256 Mo en modifiant le quota de mémoire sur la page de détails de l'application. Cependant, comme le quota de disque est resté le même, vous n'avez pas obtenu plus d'espace disque.
{: tsSymptoms}

Le quota de disque par défaut alloué à une application est de 1 Go. Si vous avez besoin de davantage d'espace disque, vous devez spécifier manuellement le quota de disque.
{: tsCauses}

Utilisez l'une des méthodes suivantes pour spécifier votre quota de disque. Le quota de disque maximal que vous pouvez spécifier est de 2 Go. Si les 2 Go ne sont toujours pas suffisants, essayez un service externe, tel que [Object Store](/docs/services/cloud-object-storage?topic=cloud-object-storage-for-developers#for-developers).
{: tsResolve}

  * Dans le fichier `manifest.yml`, ajoutez l'élément suivant :
  ```yaml
	disk_quota: <disk_quota>
	```
  * Utilisez l'option **-k** avec la commande `ibmcloud cf push` lorsque vous envoyez par commande push votre application à {{site.data.keyword.cloud_notm}} :
    
  ```
	ibmcloud cf push appname -p app_path -k <disk_quota>
	```
  {: codeblock}

## Les applications Android ne peuvent pas recevoir de {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

Dans certaines régions où Google n'est pas accessible, les applications Android ne peuvent pas recevoir les notifications que vous envoyez via le service IBM {{site.data.keyword.mobilepushshort}}. Dans ce cas, une solution de contournement consiste à utiliser des services tiers.

Vous liez un service {{site.data.keyword.mobilepushshort}} pour votre application {{site.data.keyword.cloud_notm}} et envoyez un message aux unités enregistrées. Toutefois, les applications qui sont développées sous Android ne peuvent pas recevoir vos notifications dans certaines régions.
{: tsSymptoms}

Le service IBM {{site.data.keyword.mobilepushshort}} utilise le service GCM (Google Cloud Messaging) pour diffuser les notifications aux applications mobiles développées sur Android. Les applications mobiles doivent pouvoir accéder au service GCM pour que les applications Android puissent recevoir les notifications. Dans les régions où les applications Android ne peuvent pas accéder au service GCM, ces dernières ne peuvent pas recevoir de notifications {{site.data.keyword.mobilepushshort}}.
{: tsCauses}

Comme solution palliative, utilisez des services de tiers qui ne sont pas basés sur les services GCM, par exemple [Pushy ](https://pushy.me){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"), [getui ](http://www.getui.com/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") et [jpush ](https://www.jpush.cn/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").
{: tsResolve}

## La limite de services de l'organisation est dépassée
{: #ts_servicelimit}
{: troubleshoot}

Si vous utilisez un compte Lite, il se peut que vous ne puissiez pas créer d'application dans {{site.data.keyword.cloud_notm}} si vous avez atteint le nombre maximal de services pour votre organisation.

Lorsque vous tentez de créer une application dans {{site.data.keyword.cloud_notm}}, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`BXNUI2032E: La ressource <service_instances> n'a pas été créée. Une erreur est survenue lors du contact de Cloud Foundry pour la création d'une ressource. Message Cloud Foundry : "You have exceeded your organization's services limit."`

Cette erreur survient lorsque le nombre maximal d'instances de service dont vous pouvez disposer pour votre compte est dépassé.
{: tsCauses}

Supprimez les instances de service dont vous n'avez pas besoin ou supprimez la limite portant sur le nombre de services que vous pouvez utiliser.
{: tsResolve}

  * Pour supprimer une instance de service, vous pouvez utiliser la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande.

    Pour utiliser la console {{site.data.keyword.cloud_notm}} afin de supprimer une instance de service, procédez comme suit :
	  1. Dans la liste de ressources, cliquez sur le menu **Actions** du service à supprimer.
	  2. Cliquez sur **Supprimer le service**. Vous êtes invité à reconstituer l'application à laquelle l'instance de service était liée.

    Pour utiliser l'interface de ligne de commande pour supprimer une instance de service, procédez comme suit :
	  3. Annulez la liaison entre l'instance de service et une application. Entrez `cf unbind-service <appname> <service_instance_name>`.
	  4. Supprimez l'instance de service. Entrez `cf delete-service <service_instance_name>`.
	  5. Une fois l'instance de service supprimée, vous pouvez souhaiter reconstituer l'application à laquelle l'instance de service était liée. Entrez `cf restage <appname>`.

  * Pour supprimer la limite de nombre d'instances de service dont vous pouvez disposer, mettez à niveau votre compte Lite vers un compte facturable. Pour plus d'informations, voir [Mise à niveau de votre compte](/docs/account?topic=account-accounts#upgrade-to-paygo).

## Impossible d'exécuter les fichiers exécutables sur {{site.data.keyword.cloud_notm}}
{: #ts_executable}
{: troubleshoot}

Il peut s'avérer impossible d'exécuter des fichiers exécutables sur {{site.data.keyword.cloud_notm}} si ces derniers ont été développés et générés dans un autre environnement.

Vous ne parvenez pas à exécuter des fichiers exécutables dans {{site.data.keyword.cloud_notm}} lorsqu'ils ont été développés et générés dans un autre environnement.
{: tsSymptoms}

Si le contenu à envoyer par commande push dans {{site.data.keyword.cloud_notm}} est déjà un fichier exécutable, il a été construit au préalable et n'a pas besoin d'être construit dans {{site.data.keyword.cloud_notm}}. Dans ce cas, aucun pack de construction n'est requis pour l'exécution du fichier exécutable dans {{site.data.keyword.cloud_notm}}. Vous devez indiquer explicitement à {{site.data.keyword.cloud_notm}} qu'aucun pack de construction n'est nécessaire.
{: tsCauses}

Lorsque vous envoyez par commande push le fichier exécutable dans {{site.data.keyword.cloud_notm}}, vous devez spécifier la valeur `null-buildpack`, qui indique qu'aucun pack de construction n'est requis. Indiquez une valeur `null-buildpack` en utilisant l'option **-b** avec la commande `ibmcloud cf push` :
{: tsResolve}

```
ibmcloud cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
{: codeblock}

Par exemple :
```
ibmcloud cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```
{: codeblock}

## La limite mémoire de l'organisation est dépassée
{: #ts_outofmemory}
{: troubleshoot}

Si vous utilisez un compte Lite, il se peut que vous ne puissiez pas déployer d'application dans {{site.data.keyword.cloud_notm}} si vous avez atteint la limite de mémoire de votre organisation. Vous pouvez réduire la quantité de mémoire que vos applications utilisent ou augmenter le quota de mémoire de votre compte. Le quota de mémoire maximal pour un compte Lite est de 256 Go. Il ne peut être augmenté qu'en passant à un compte facturable.

Lorsque vous déployez une application dans {{site.data.keyword.cloud_notm}}, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`FAILED Erreur de serveur, code statut : 400, code d'erreur : 100005, message : vous avez dépassé la limite mémoire de votre organisation.`

Cette erreur survient lorsque la quantité de mémoire restante pour votre organisation est inférieure à la quantité de mémoire requise par l'application à déployer. Le quota de mémoire maximal pour un compte Lite est de 256 Go.
{: tsCauses}

Vous pouvez augmenter le quota de mémoire de votre compte ou diminuer la mémoire que vos applications utilisent.
{: tsResolve}

  * Pour augmenter le quota de mémoire de votre compte, mettez à niveau votre compte Lite vers un compte payant. Pour plus d'informations, voir [Mise à niveau de votre compte](/docs/account?topic=account-accounts#upgrade-to-paygo).
  * Pour réduire la quantité de mémoire consommée par vos applications, utilisez la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande Cloud Foundry.

    Si vous utilisez la console {{site.data.keyword.cloud_notm}}, procédez comme suit :

    1. Sélectionnez votre application dans la liste de ressources. La page des détails de l'application s'ouvre.
    2. Dans le panneau Contexte d'exécution, vous pouvez réduire la limite de mémoire maximale, le nombre d'instances d'application, ou les deux, pour votre application.

    Si vous utilisez l'interface de ligne de commande, procédez comme suit :

    1. Vérifiez la quantité de mémoire utilisée par vos applications :
  	  ```
	    ibmcloud cf list
	    ```
      {: codeblock}

	    La commande `ibmcloud cf list` répertorie toutes les applications déployées dans votre espace actuel. Le statut de chaque application est également affiché.

    2. Pour réduire la quantité de mémoire qui est utilisée par votre application, réduisez le nombre d'instances d'application ou la limite de mémoire maximale, ou les deux :
	    ```
	    ibmcloud cf push appname -p app_path -i instance_number -m memory_limit
      ```
      {: codeblock}

    3. Redémarrez votre application pour que les modifications soient appliquées.

## Les applications ne sont pas redémarrées automatiquement
{: #ts_apps_not_auto_restarted}
{: troubleshoot}

Une application n'est pas redémarrée automatiquement lorsqu'un service que vous liez à cette application cesse de fonctionner.

Lorsqu'un service que vous liez à une application tombe en panne, des problèmes tels que des indisponibilités, des exceptions et des échecs de connexion peuvent survenir sur l'application. {{site.data.keyword.cloud_notm}} ne redémarre pas automatiquement l'application pour assurer la reprise suite à ces problèmes.
{: tsSymptoms}

Ce comportement est normal dans Cloud Foundry.
{: tsCauses}

Vous pouvez redémarrer manuellement une application qui est déjà déployée en entrant la commande suivante dans l'interface de ligne de commande :
{: tsResolve}

```
ibmcloud cf restart <APPNAME>
```
{: codeblock}

De plus, vous pouvez coder l'application afin d'identifier les problèmes et d'assurer la reprise après une indisponibilité, une exception ou un échec de connexion.

<!-- begin STAGING ONLY -->

## {{site.data.keyword.cloud_notm}} Live Sync Debug ne démarre pas à partir de la ligne de commande
{: #ts_no_debug}
{: troubleshoot}

Vous avez activé la fonction {{site.data.keyword.cloud_notm}} Live Sync Debug pour votre application en utilisant la ligne de commande mais vous ne pouvez pas accéder à l'interface Debug.

Vous avez activé la fonction de débogage pour votre application en définissant la variable d'environnement **BLUEMIX_APP_MGMT_ENABLE**. Cependant, vous ne pouvez pas accéder à l'interface utilisateur Debug à partir de `app_url/bluemix-debug/manage`.
{: tsSymptoms}

La fonction de débogage ne peut pas être activée dans les situations suivantes :
{: tsCauses}

  * Lorsque le fichier `manifest.yml` contient l'attribut command
  * Lorsque vous utilisez l'option **-c** pour transmettre une application à {{site.data.keyword.cloud_notm}}

Utilisez une des options suivantes pour résoudre le problème :
{: tsResolve}

  * Il est recommandé d'utiliser le pack de construction IBM Node.js pour démarrer l'application. Pour plus d'informations, voir la section relative à la commande Startup de la rubrique relative au [déploiement d'une application Node.js dans {{site.data.keyword.cloud_notm}}](/docs/runtimes/nodejs?topic=Nodejs-startup_commmand#startup_commmand).
  * Désactivez la commande pour votre application existante en modifiant l'attribut command dans votre fichier `manifest.yml` en command: null ou en éditant votre commande push afin d'inclure `-c null`.
  * Retirez l'attribut **command** du fichier `manifest.yml`. Supprimez ensuite l'application actuelle d'{{site.data.keyword.cloud_notm}} et envoyez à nouveau l'application par commande push.

<!-- end STAGING ONLY -->

## Des organisations sont introuvables dans {{site.data.keyword.cloud_notm}}
{: #ts_orgs}
{: troubleshoot}

Il se peut que vous ne parveniez pas à localiser votre organisation dans {{site.data.keyword.cloud_notm}} lorsque vous travaillez sur une région {{site.data.keyword.cloud_notm}}.

Vous pouvez vous connecter à la console {{site.data.keyword.cloud_notm}}, mais vous ne parvenez pas à envoyer vos applications par commande push à l'aide de l'interface de ligne de commande Cloud Foundry.
{: tsSymptoms}

Lorsque vous tentez d'envoyer une application par commande push à {{site.data.keyword.cloud_notm}} en utilisant l'interface de ligne de commande Cloud Foundry, l'un des messages d'erreur suivants spécifiant le nom de l'organisation s'affiche :

`Error finding org`

`Organization not found`

Ce problème survient car le noeud final d'API de la région avec laquelle vous travaillez n'est pas spécifié et l'organisation que vous recherchez peut se trouver dans une autre région.
{: tsCauses}

Si vous envoyez votre application par commande push à {{site.data.keyword.cloud_notm}} en utilisant l'interface de ligne de commande Cloud Foundry, entrez la commande `cf api` et spécifiez le noeud final d'API de la région. Par exemple, entrez la commande suivante pour vous connecter à la région {{site.data.keyword.cloud_notm}} Europe et Royaume-Uni :
{: tsResolve}

```
cf api https://api.eu-gb.cf.cloud.ibm.com
```
{: codeblock}


## Impossible de créer les routes d'application
{: #ts_hostistaken}
{: troubleshoot}

Lorsque vous déployez une application dans {{site.data.keyword.cloud_notm}}, la route d'application ne peut pas être créée si le nom d'hôte que vous avez spécifié est déjà utilisé.

Lorsque vous déployez une application dans {{site.data.keyword.cloud_notm}}, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`Creating route hostname.domainname ... FAILED Server error, status code: 400, error code: 210003, message: The host is taken: hostname`

Ce problème survient si le nom d'hôte que vous avez spécifié est déjà utilisé.
{: tsCauses}

Le nom d'hôte que vous spécifiez doit être unique dans le domaine que vous utilisez. Pour spécifier un autre nom d'hôte, utilisez l'une des méthodes suivantes :
{: tsResolve}

  * Si vous déployez votre application avec le fichier `manifest.yml`, spécifiez le nom d'hôte dans l'option host.
    ```yaml
    host: host_name
	  ```

  * Si vous déployez votre application depuis l'invite de commande, utilisez la commande `ibmcloud cf push` avec l'option **-n**.
    ```
    ibmcloud cf push appname -p app_path -n host_name
    ```
    {: codeblock}

## Les applications WAR ne peuvent pas être envoyées à l'aide de la commande ibmcloud cf push
{: #ts_cf_war}
{: troubleshoot}

Il se peut que vous ne puissiez pas utiliser la commande `ibmcloud cf push` pour déployer dans {{site.data.keyword.cloud_notm}} une application Web archivée si l'emplacement de l'application n'est pas spécifié correctement.

Lorsque vous téléchargez une application WAR dans {{site.data.keyword.cloud_notm}} à l'aide de la commande `ibmcloud cf push`, le message d'erreur suivant s'affiche :
{: tsSymptoms}
`Staging error: cannot get instances since staging failed.`

Ce problème peut se produire si le fichier WAR ou le chemin d'accès à ce fichier n'est pas spécifié.
{: tsCauses}

Utilisez l'option **-p** pour spécifier un fichier WAR ou ajouter un chemin d'accès. Exemple :
{: tsResolve}

```
ibmcloud cf push MyUniqueAppName01 -p app.war
```
{: codeblock}

```
ibmcloud cf push MyUniqueAppName02 -p "./app.war"
```
{: codeblock}

Pour plus d'informations sur la commande `ibmcloud cf push`, entrez `ibmcloud cf push -h`.

## Les caractères codés sur deux octets ne s'affichent pas correctement lorsque des applications sont envoyées par commande push vers {{site.data.keyword.cloud_notm}}
{: #ts_doublebytes}
{: troubleshoot}

Il se peut que les caractères codés sur deux octets ne s'affichent pas correctement si la prise en charge Unicode n'est pas configurée correctement pour le servlet ou les fichiers JSP.

Lorsqu'une application est envoyée par commande push dans {{site.data.keyword.cloud_notm}}, les caractères codés sur deux octets spécifiés dans l'application ne s'affichent pas correctement.
{: tsSymptoms}

Le problème peut se produire si la prise en charge Unicode n'est pas configurée correctement pour le servlet ou les fichiers JSP.
{: tsCauses}

Utilisez le code suivant dans votre servlet ou votre fichier JSP :
{: tsResolve}

  * Dans le fichier source servlet
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * Dans l'élément JSP
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## Les applications Node.js ne peuvent pas être déployées
{: #ts_nodejs_deploy}
{: troubleshoot}

Des problèmes peuvent survenir lorsque vous mettez à jour ou déployez une application Node.js dans {{site.data.keyword.cloud_notm}}.

Lorsque vous mettez à jour ou déployez votre application Node.js dans {{site.data.keyword.cloud_notm}}, l'un des messages d'erreur suivants peut s'afficher :
{: tsSymptoms}

`An app was not successfully detected by any available buildpack.`

`Instance (index 0) failed to start accepting connections.`

`Cannot get instances since staging failed.`

Causes possibles :
{: tsCauses}

  * La commande de démarrage n'a pas été spécifiée.
  * Des fichiers requis pour déployer une application Node.js sont manquants dans l'application ou résident dans un dossier autre que le répertoire racine.

Utilisez l'une des méthodes suivantes, selon la cause du problème :
{: tsResolve}

  * Spécifiez la commande de démarrage à l'aide d'une des méthodes suivantes :
     * Utilisez l'interface de ligne de commande Cloud Foundry. Exemple :
      ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		  ```
      {: codeblock}

    * Utilisez le fichier [package.json ](https://www.npmjs.com/package/jsonfile){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"). Exemple :
	    ```json
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
	```json
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

Pour obtenir des conseils supplémentaires relatifs aux applications Node.js, voir [Tips for Node.js Applications ](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

## Des erreurs de configuration figurent dans le fichier `server.xml` après avoir importé une application {{site.data.keyword.cloud_notm}} Liberty dans Eclipse
{: #ts_eclipse}
{: troubleshoot}

Si vous rencontrez des erreurs de configuration dans le fichier `server.xml` après avoir importé une application {{site.data.keyword.cloud_notm}} Liberty dans Eclipse, vous devrez peut-être supprimer du projet le fichier `server.xml`.

Après avoir importé une application {{site.data.keyword.cloud_notm}} Liberty dans Eclipse, vous rencontrez des erreurs de configuration dans le fichier `server.xml` dans la vue Erreurs d'Eclipse.
{: tsSymptoms}

Le pack de construction Liberty utilise le fichier `server.xml` pour configurer l'application et génère un fichier `runtime-vars.xml` lorsque l'application Liberty est envoyée par commande push dans {{site.data.keyword.cloud_notm}}. Lorsque vous importez l'application dans Eclipse, le fichier `runtime-vars.xml` n'existe pas dans votre environnement local.
{: tsCauses}

Pour résoudre ce problème, supprimez le fichier server.xml du projet. Le pack de construction crée le fichier `server.xml` de manière dynamique lorsque vous envoyez par commande push l'application sous forme d'application WAR. Pour plus d'informations, voir [Liberty for Java](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime).
{: tsResolve}

## Les applications ne peuvent pas être transférées à l'aide de packs de construction personnalisés
{: #ts_bp_compilation}
{: troubleshoot}

Il se peut que vous ne puissiez pas déployer d'application dans {{site.data.keyword.cloud_notm}} à l'aide d'un pack de construction personnalisé si les scripts que ce dernier contient ne sont pas des fichiers exécutables.

Lorsque vous déployez une application dans {{site.data.keyword.cloud_notm}} à l'aide d'un pack de construction personnalisé, le message d'erreur `The application failed to stage, so there are no instances to display` s'affiche.
{: tsSymptoms}

Ce problème peut se produire si des scripts (tels que le script de détection, le script de compilation ou le script de publication) ne sont pas exécutables.
{: tsCauses}

Vous pouvez utiliser la commande [Git update ](http://git-scm.com/docs/git-update-index){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") pour faire en sorte que chaque script soit exécutable. Par exemple, vous pouvez entrer `git update --chmod=+x script.sh`.
{: tsResolve}

## Impossible de déployer une application depuis Delivery Pipeline dans {{site.data.keyword.cloud_notm}} Continuous Delivery
{: #ts_devops_to_bm}
{: troubleshoot}

 Il se peut que vous ne puissiez pas déployer votre application à l'aide de {{site.data.keyword.deliverypipeline}} dans {{site.data.keyword.contdelivery_short}} si le fichier `manifest.yml` n'est pas présent dans votre application.

 Lorsque vous déployez une application à l'aide de {{site.data.keyword.deliverypipeline}} dans {{site.data.keyword.contdelivery_short}}, il se peut que le message d'erreur `Unable to detect a supported application type` s'affiche.
 {: tsSymptoms}

 Ce problème peut survenir car le pipeline requiert un fichier `manifest.yml` pour déployer une application dans {{site.data.keyword.cloud_notm}}.
 {: tsCauses}

 Pour remédier à ce problème, vous devez créer un fichier `manifest.yml`. Pour plus d'informations sur la création du fichier `manifest.yml`, voir [Manifeste d'application](/docs/cloud-foundry/deploy-apps.html#appmanifest).
 {: tsResolve}

## Les applis Meteor ne peuvent pas être envoyées par commande push
{: #ts_meteor}
{: troubleshoot}

Il se peut que vous ne puissiez pas envoyer une application Meteor par commande push dans {{site.data.keyword.cloud_notm}} si le pack de construction n'est pas spécifié correctement.

Lorsque vous déployez une application Meteor dans {{site.data.keyword.cloud_notm}}, le message d'erreur suivant peut s'afficher : `The application failed to stage, so there are no instances to display.`
{: tsSymptoms}

Ce problème survient car aucun pack de construction n'est fourni pour les applications Meteor. Vous devez utiliser un pack de construction personnalisé.
{: tsCauses}

Afin d'utiliser un pack de construction personnalisé pour les applications Meteor, appliquez l'une des méthodes suivantes :
{: tsResolve}

  * Si vous déployez votre application avec le fichier `manifest.yml`, spécifiez l'adresse URL ou le nom de votre pack de construction personnalisé avec l'option buildpack. Par exemple :
  ```yaml
  buildpack: https://github.com/Sing-Li/bluemix-bp-meteor
  ```

  * Si vous déployez votre application depuis l'invite de commande, utilisez la commande `ibmcloud cf push` et spécifiez votre pack de construction personnalisé avec l'option **-b**. Par exemple :
  ```
	ibmcloud cf push appname -p app_path -b https://github.com/Sing-Li/bluemix-bp-meteor
	```
  {: codeblock}

## Dépassement de votre quota de stockage
{: #exceed_quota}

Si les travaux de génération ou de déploiement échouent et que le message suivant est généré, vous pouvez supprimer vos images en utilisant les commandes CLI suivantes. `Status: unauthorized: You have exceeded your storage quota. Delete one or more images, or review your storage quota and pricing plan.`

* Installez l'[interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) si ce n'est pas déjà fait.
* Connectez-vous à {{site.data.keyword.cloud_notm}} en utilisant `ibmcloud login` et faites en sorte qu'il désigne l'espace dans lequel vous vous trouvez.
* Répertoriez vos images en utilisant `ibmcloud cr images`.
* Supprimez toute image non utilisée en utilisant `ibmcloud cr image-rm <respository>:<tag>`.
* Exécutez à nouveau le travail de génération ou de déploiement ayant échoué.

## Accès aux journaux Kubernetes
{: #access_kube_logs}

Si l'application n'est pas en cours d'exécution et que vous ne pouvez pas accéder au noeud final de santé, consultez les journaux du cluster.
* Installez l'[interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) si ce n'est pas déjà fait.
* Connectez-vous à {{site.data.keyword.cloud_notm}} en utilisant `ibmcloud login` et faites en sorte qu'il désigne l'espace dans lequel vous vous trouvez.
* Répertoriez vos clusters en utilisant `ibmcloud cs clusters`,
* Désignez votre cluster correspondant en utilisant `ibmcloud cs cluster-config <cluster-name>`.
* Exportez la variable d'environnement répertoriée.
* Affichez vos pods en utilisant `kubectl get pods`. Si vous avez besoin d'installer kubectl, voir [Install and Set Up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").
* Vous pouvez afficher les journaux dans votre application en utilisant `kubectl logs <pod-name>.`


## Echec du démarrage de `docker` avec le message "file not found"
{: #docker_not_found}
{: troubleshoot}

Lorsque vous tentez de démarrer Docker, le message d'erreur suivant s'affiche :
{: tsSymptoms}

```
An error exec: "docker": executable file not found in $PATH was encountered while building the Docker image.
```
{: screen}

Le client Docker n'est pas installé ou est installé mais n'est pas démarré.
{: tsCauses}

Vérifiez que [Docker](https://docs.docker.com/install/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") est installé puis démarrez-le.
{: tsResolve}


## Echec de la génération d'une application avec une erreur Docker
{: #build_error}
{: troubleshoot}

Lorsque vous tentez de générer une application avec la commande `ibmcloud dev build`, cette opération échoue suite à une erreur de nom d'utilisateur/mot de passe Docker. 
{: tsSymptoms}

Des données d'identification Docker Hub incorrectes ont été utilisées pour l'authentification. 
{: tsCauses}

Déconnectez Docker Hub dans le client Docker.
{: tsResolve}


