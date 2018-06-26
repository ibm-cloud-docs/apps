---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-26"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}

# Adding a service to your app
{: #add_service}

When you create an app with {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_console}}, you can add resources from the app overview page. However, you can also provision them directly from the {{site.data.keyword.Bluemix_notm}} catalog, outside the context of your app.
{: shortdesc}

You can request an instance of the resource and use it independently of your app, or you can add the resource instance to your app from the app overview page. You can provision a particular type of resource (a service) directly from the {{site.data.keyword.Bluemix_notm}} catalog.

## Discovering services
{: #discover_services}

You can see all the services that are available in {{site.data.keyword.Bluemix_notm}} in the following ways:

* From the {{site.data.keyword.Bluemix_notm}} console. View the {{site.data.keyword.Bluemix_notm}} catalog.
* From the ibmcloud command line interface. Use the `ibmcloud service offerings` command.
* From your own application. Use the [GET /v2/services Services API ![External link icon](../icons/launch-glyph.svg "External link icon")](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window}.

You can select the service that you need when you develop applications. Once you select it, {{site.data.keyword.Bluemix_notm}} provisions the service. The provisioning process can be different for different types of services. For example, a database service creates a database, and a push notification service for mobile applications generates configuration information.

{{site.data.keyword.Bluemix_notm}} provides the resources of a service to your application by using a service instance. A service instance can be shared across web applications.

You can also use services that are hosted in other regions if those services are available in those regions. These services must be accessible from the internet and have API endpoints. You must manually code your application to use these services in the same way that you code external applications or third-party tools to use {{site.data.keyword.Bluemix_notm}} services. For more information, see [Enabling external applications and third-party tools to use {{site.data.keyword.Bluemix_notm}} services](#accser_external).

## Requesting a new service instance
{: #req_instance}

To request a new service instance, you must use the {{site.data.keyword.Bluemix_notm}} user interface or the {{site.data.keyword.Bluemix_notm}} command line interface.

**Note:** When you specify the service name, avoid characters other than alphabetic or numeric characters because results might be unpredictable.

If you use the {{site.data.keyword.Bluemix_notm}} user interface to request a service instance, complete the following steps:

1. In the {{site.data.keyword.Bluemix_notm}} catalog, click the tile for the service that you want to add. The service details page opens.

2. Type a name in the **Service name** field. A default name is provided. You can change the name in the field, or leave it unchanged.

3. Complete more fields or selections, and then click **CREATE**.

If you use the {{site.data.keyword.Bluemix_notm}} command line interface to request a service instance, complete the following steps:

1. Use the `ibmcloud service offerings` command to find the name and the plan of the service that you require.

2. Use the following command to create a service instance, where service_name is the name of the service, service_plan is the plan of the service, and service_instance is the name that you want to use for this service instance.

```
ibmcloud service create service_name service_plan service_instance
```

3. Use the following command to bind the service instance to an application, where *appname* is the name of the application, and service_instance is the name of the service instance.

```
ibmcloud service bind appname service_instance
```

You can bind a service instance to only those app instances that are in the same space or org. However, you can use service instances from other spaces or orgs in the same way that an external app does. Instead of creating a binding, use the credentials to directly configure your app instance. For more information about how external apps use {{site.data.keyword.Bluemix_notm}} services, see [Enabling external apps to use {{site.data.keyword.Bluemix_notm}} services ![External link icon](../icons/launch-glyph.svg "External link icon")](#accser_external){: new_window}.

## Configuring your application
{: #config}

After you bind a service instance to your application, you must configure your application to interact with the service.

Each service might require a different mechanism for communicating with applications. These mechanisms are documented as part of the service definition for your information when you develop applications. For consistency, the mechanisms are required for your application to interact with the service.

* To interact with database services, use the information that {{site.data.keyword.Bluemix_notm}} provides such as the user ID, password, and the access URI for the application.
* To interact with mobile back-end services, use the information that {{site.data.keyword.Bluemix_notm}} provides such as the application identity (app ID), security information that is specific to the client, and the access URI for the application. The mobile services often work in context with each other so that context information, such as the name of the application developer and the user that uses the application, can be shared across the set of services.
* To interact with web applications or server-side cloud code for mobile applications, use the information that {{site.data.keyword.Bluemix_notm}} provides such as the runtime credentials in the *VCAP_SERVICES* environment variable of the application. The value of the *VCAP_SERVICES* environment variable is the serialization of a JSON object. The variable contains the runtime data that is required to interact with the services that the application is bound to. The format of the data is different for different services. You might need to read the service documentation about what to expect and how to interpret each piece of information.

If a service that you bind to an application crashes, the application might stop running or have errors. {{site.data.keyword.Bluemix_notm}} doesn’t automatically restart the application to recover from these problems. Consider coding your application to identify and recover from outages, exceptions, and connection failures. For more information, see [Apps won't be automatically restarted](/docs/troubleshoot/ts_apps.html#ts_apps_not_auto_restarted).

## Accessing services across {{site.data.keyword.Bluemix_notm}} deployment environments
{: #migrate_instance}

{{site.data.keyword.Bluemix_notm}} offers many deployment options, and you can access a service that is running in one environment from a different environment. For example, if you have a service that is running in Cloud Foundry, you can access that service from an application that is running in a Kubernetes cluster.

### Example: Access a Compose service instance on Cloud Foundry from a Kubernetes pod

Any Compose service instances, such as {{site.data.keyword.composeForMongoDB}} or {{site.data.keyword.composeForRedis}}, are paid instances. After you're comfortable with using your Compose service instance, like {{site.data.keyword.composeForMongoDB}} in Kubernetes, you can import the credentials of the instance provided by Compose in Cloud Foundry.

1. Go to **Credentials** and retrieve your credentials from the instance.

2. Open the `values.yml` file from your charts directory, for example, `chart/project/`.

3. Set the values that are referenced in your service environments. For example, in {{site.data.keyword.composeForMongoDB}}:

  ```
  services:
    mongo:
       url: {uri}
       dbName: {dbname}
       ca: {ca_certificate_base64}
       username: {username}
       password: {password}
       env: production

  ```

4. Open the `bindings.yml` file from your charts directory, for example, `chart/project/`.

5. Add the key-value references that are defined in the `values.yml` file at the end where the `env` block is defined.

  ```
    env:
      - name: MONGO_URL
        value: {{ .Values.services.mongo.url }}
      - name: MONGO_DB_NAME
        value: {{ .Values.services.mongo.name }}
      - name: MONGO_USER
        value: {{ .Values.services.mongo.username }}
      - name: MONGO_PASS
        value: {{ .Values.services.mongo.password }}
      - name: MONGO_CA
        value: {{ .Values.services.mongo.ca }}
  ```

6. In your application, use your environment variables to initiate the service SDK that's provided for you.

  ```javascript
    const serviceManger = require('./services/serivce-manage.js');
    const mongoURL = process.env.MONGO_URL || 'localhost';
    const mongoUser = process.env.MONGO_USER || '';
    const mongoPass = process.env.MONGO_PASS || '';
    const mongoDBName = process.env.MONGO_DB_NAME || 'comments';
    const mongoCA = [new Buffer(process.env.MONGO_CA || '', 'base64')]

    const options = {
        useMongoClient: true,
        ssl: true,
        sslValidate: true,
        sslCA: mongoCA,
        poolSize: 1,
        reconnectTries: 1
    };

    const mongoDBClient = serviceManger.get('mongodb');
  ```

### Secrets (Optional)
{: #migrate_secrets_optional}

Do not expose your credentials in your `deployment.yml` or `values.yml` files. You can use a base64 encoded string or encrypt your credentials with a key. For more information, see [Creating a Secret Using kubectl create secret ![External link icon](../icons/launch-glyph.svg "External link icon")](https://kubernetes.io/docs/concepts/configuration/secret/#creating-your-own-secrets) and [How to encrypt your data ![External link icon](../icons/launch-glyph.svg "External link icon")](https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/)

## Enabling external apps
{: #accser_external}

You might have applications that were created and run outside of {{site.data.keyword.Bluemix_notm}}, or you might use third-party tools. If {{site.data.keyword.Bluemix_notm}} services provide service keys that are accessible from the internet, you can use those services with your local apps or third-party tools.

The following services provide service keys for you to use externally:

* {{site.data.keyword.amashort_old}} <!--Advanced Mobile Access-->
* {{site.data.keyword.alchemyapishort}} <!--AlchemyAPI-->
* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.appseccloudshort}} <!--Application Security on Cloud-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.iotmapinsights_short}} <!--Context Mapping-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.dashdbshort}} <!--dashDB-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.documentconversionshort}} <!--Document Conversion-->
* {{site.data.keyword.iotdriverinsights_short}} <!--Driver Behavior-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.dataworks_short}} <!--IBM&reg; Data Connect-->
* {{site.data.keyword.graphshort}} <!--IBM&reg; Graph-->
* {{site.data.keyword.iotelectronics_full}} <!--IBM&reg; IoT for Electronics-->
* {{site.data.keyword.twittershort}} <!--Insights for Twitter-->
* {{site.data.keyword.iot4auto_short}} <!--IoT for Automotive-->
* {{site.data.keyword.iotinsurance_short}} <!--IoT for Insurance-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.mobileanalytics_short}} <!--Mobile Analytics-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.HybridConnect_short}} <!--Product Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.retrieveandrankshort}} <!--Retrieve and Rank-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.tradeoffanalyticsshort}} <!--Tradeoff Analytics-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

To enable an external app or third-party tool to use a {{site.data.keyword.Bluemix_notm}} service, complete the following steps:

1. Request an instance of the service.
    1. On the Dashboard in the {{site.data.keyword.Bluemix_notm}} user interface, click **Create Resource**. The catalog displays.
    2. From the catalog, select the service that you want by clicking the service tile. The service details page opens.
    3. In the service window, leave the default **Connect to:**: list selection as **Leave unbound**. This selection means that the service isn’t connected to a {{site.data.keyword.Bluemix_notm}} app.
    4. Make any other selections as needed. Then, click **Create**. A service instance is created, and the service Dashboard displays.
2. In the service Dashboard, you can select **Service Credentials** to view or add credentials in JSON format. Select a set of credentials and click **View Credentials** in the Actions column. Use the API key that is displayed as the credentials to connect to the service instance.

Your application that runs outside of {{site.data.keyword.Bluemix_notm}} can now access the {{site.data.keyword.Bluemix_notm}} service.

**Note:** If you want to delete service instances or check the billing information, you must go back to your Dashboard in the user interface to manage the service instances.

## Creating a user-provided service instance
{: #user_provide_services}

You might have services that are managed outside of {{site.data.keyword.Bluemix_notm}}. If you have credentials to access those external services from the internet, you can create {{site.data.keyword.Bluemix_notm}} user-provided service instances to represent and communicate with your external services.

To create a user-provided service instance and bind it to an application, complete the following steps:

1. Create a user-provided service instance by using either the `ibmcloud service user-provided-create` command:
    * To create a general user-provided service instance, use the **-p** option, and separate the parameter names with commas. The `ibmcloud` command line interface then prompts you for each parameter in turn. For example:
        ```
        ibmcloud service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * To create a service instance that drains information to a third-party log management software, use the `-l` option, and specify the destination that the third-party log management software provides. For example:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    If you want to update one or more parameters of the user-provided service instance, use either the `ibmcloud service user-provided-update`.

    * To update a general user-provided service instance, use the **-p** option, and specify the parameter keys and values in a JSON object. For example:

        ```
        ibmcloud service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * To create a service instance that drains information to a third-party log management software, use the `-l` option. For example:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. Bind the service instance to your application by using the `ibmcloud service bind` command. For example:

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

You can now configure your application to use the external services. For information on how to configure your application to interact with a service, see [Configuring your application to interact with a service ![External link icon](../icons/launch-glyph.svg "External link icon")](#config){: new_window}.

