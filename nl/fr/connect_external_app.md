---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-05"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{: tip: .tip}

# Connexion de services à des applications externes
{: #externalapp}

Vous pouvez disposer d'applications créées et exécutées en dehors de {{site.data.keyword.Bluemix_notm}}, mais également utiliser des outils tiers. Si des services {{site.data.keyword.Bluemix_notm}} fournissent des clés de service accessibles depuis Internet, vous pouvez utiliser ces services dans vos applications locales ou dans des outils tiers.

Les services suivants vous fournissent des clés de service pour un usage externe :

* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

Pour autoriser une application externe ou un outil tiers à utiliser un service {{site.data.keyword.Bluemix_notm}}, procédez comme suit :

1. Créez une instance du service.
    1. Cliquez sur **Catalogue**.
    2. Dans le catalogue, sélectionnez le service de votre choix en cliquant sur la vignette correspondante. 
    3. Sélectionnez l'emplacement et une organisation et un espace ou un groupe de ressources, puis cliquez sur **Créer**.
2. Sur la page des détails du service, sélectionnez **Données d'identification du service** pour afficher ou ajouter des données d'identification au format JSON.  
    * Pour créer de nouvelles données d'identification, sélectionnez **Nouvelles données d'identification** et si vous le souhaitez, ajoutez des paramètres de configuration manuellement ou importez un fichier au format JSON, puis cliquez sur **Ajouter**. Sélectionnez **Afficher les données d'identification** pour sauvegarder les données d'identification vous permettant de vous connecter à votre application externe. 
    * Sélectionnez un ensemble de données d'identification et cliquez sur **Afficher les données d'identification** dans la colonne Actions s'ils existent déjà.  
3. Utilisez la clé d'API affichée comme données d'identification pour vous connecter à l'instance de service.

Votre application qui s'exécute en dehors de {{site.data.keyword.Bluemix_notm}} peut désormais accéder au
service {{site.data.keyword.Bluemix_notm}}.

Si vous souhaitez supprimer des instances de service ou consulter les informations de facturation, vous devez revenir à votre tableau de bord dans l'interface utilisateur afin de gérer les instances de service.
{: tip}
