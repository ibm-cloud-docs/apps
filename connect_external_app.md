---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-05"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{: tip: .tip}

# Connecting services to external apps
{: #externalapp}

You might have applications that were created and run outside of {{site.data.keyword.Bluemix_notm}}, or you might use third-party tools. If {{site.data.keyword.Bluemix_notm}} services provide service keys that are accessible from the internet, you can use those services with your local apps or third-party tools.

The following services provide service keys for you to use externally:

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

To enable an external app or third-party tool to use an {{site.data.keyword.Bluemix_notm}} service, complete the following steps:

1. Create an instance of the service.
    1. Click **Catalog**.
    2. From the catalog, select the service that you want by clicking the service tile. 
    3. Select the location and org and space or resource group, and then click **Create**.
2. From the service details page, select **Service Credentials** to view or add credentials in JSON format. 
    * To create new credentials, select **New credential** and optionally add configuration parameters manually or import a file in JSON format, then click **Add**. Select **View credentials** to save the credentials to connect to your external app.
    * Select a set of credentials and click **View credentials** in the Actions column if they already exist. 
3. Use the API key that is displayed as the credentials to connect to the service instance.

Your application that runs outside of {{site.data.keyword.Bluemix_notm}} can now access the {{site.data.keyword.Bluemix_notm}} service.

If you want to delete service instances or check the billing information, you must go back to your Dashboard in the user interface to manage the service instances.
{: tip}
