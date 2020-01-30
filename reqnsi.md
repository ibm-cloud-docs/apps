---

copyright:
  years: 2015, 2019
lastupdated: "2019-08-23"

keywords: apps, services, add service, application, service, instance, ibmcloud dev edit, vcap_services, credentials

subcollection: creating-apps

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:note: .note}
{:external: target="_blank" .external}

# Adding a service to your app
{: #add-resource}

When you create an app with {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}, you can add services from the App details page. You can also provision them directly from the {{site.data.keyword.cloud_notm}} catalog, outside the context of your app.
{: shortdesc}

You can request an instance of the service and use it independently of your app, or you can add the service instance to your app from the App details page. You can provision a particular type of service directly from the {{site.data.keyword.cloud_notm}} catalog.

## Auto-provisioned services
{: #auto-provision}

If a starter kit specifies required services, {{site.data.keyword.cloud_notm}} automatically creates instances of those services when you create your app. You can also manually create services or select existing service instances to add to your app after creation. You can see a list of service instances that are associated with your app in the **App details** page, along with service credentials in case you need them later.

## Discovering services
{: #discover-resources}

You can see all the services that are available in {{site.data.keyword.cloud_notm}} in the following ways:

* From the {{site.data.keyword.cloud_notm}} console. View the {{site.data.keyword.cloud_notm}} catalog.
* From the command line. Use the `ibmcloud service offerings` command.
* From your own application. Use the [GET /v2/services Services API](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: external}.

You can select the service that you need when you develop apps. Once you select it, {{site.data.keyword.cloud_notm}} provisions the service. The provisioning process can be different for different types of services. For example, a database service creates a database, and a push notification service for mobile apps generates configuration information.

{{site.data.keyword.cloud_notm}} provides the resources of a service to your app by using a service instance. A service instance can be shared across web apps.

You can also use services that are hosted in other regions if those services are available in those regions. These services must be accessible from the internet and have API endpoints. You must manually code your app to use these services in the same way that you code external apps or third-party tools to use {{site.data.keyword.cloud_notm}} services. For more information, see [Connecting services to external apps](/docs/resources?topic=resources-externalapp).

## Requesting a new service instance
{: #request-instance}

To request a new service instance, you must use the {{site.data.keyword.cloud_notm}} user interface or the {{site.data.keyword.cloud_notm}} command line interface.

When you specify the service name, avoid characters other than alphabetic or numeric characters because results might be unpredictable.
{: note}

If you use the {{site.data.keyword.cloud_notm}} user interface to request a service instance, complete the following steps:

1. In the {{site.data.keyword.cloud_notm}} catalog, click the tile for the service that you want to add. The service details page opens.

2. Type a name in the **Service name** field. A default name is provided. You can change the name in the field, or leave it unchanged.

3. Complete more fields or selections, and then click **CREATE**.

If you use the {{site.data.keyword.cloud_notm}} command line interface to request a service instance, download your app locally open the command line, and change to the app directory.

1. Run the following command to add a service to your app. You can select an existing service from one already enabled on your account, or add a service.

  ```bash
  ibmcloud dev edit
  ```
  {: pre}

2. Follow the prompts to select a resource group, and to create and connect a new data-related service to your app, such as Cloudant. You might need to select a region and plan for the service.
3. When the service is created, several files, including credentials, are added to your app directory to help you integrate the service into your app. You can manually merge any files or skip this step for now.

To bind a service instance to an app instance, they must be in the same space or org. However, you can use service instances from other spaces or orgs in the same way that an external app does. Instead of creating a binding, use the credentials to directly configure your app instance. For more information about how external apps use {{site.data.keyword.cloud_notm}} services, see [Enabling external apps to use {{site.data.keyword.cloud_notm}} services](/docs/resources?topic=resources-externalapp#externalapp).

## Configuring your app
{: #configure-app}

After you bind a service instance to your app, you must configure your app to interact with the service.

Each service might require a different mechanism for communicating with apps. These mechanisms are documented as part of the service definition for your information when you develop apps. For consistency, the mechanisms are required for your app to interact with the service.

* To interact with database services, use the information that {{site.data.keyword.cloud_notm}} provides such as the user ID, password, and the access URI for the app.
* To interact with mobile back-end services, use the information that {{site.data.keyword.cloud_notm}} provides. Such as the app identity (app ID), security information that is specific to the client, and the access URI for the app. The mobile services often work in context with each other so that context information, such as the name of the app developer and the user that uses the app, can be shared across the set of services.
* To interact with web apps or server-side cloud code for mobile apps, use the information that {{site.data.keyword.cloud_notm}} provides such as the runtime credentials in the *VCAP_SERVICES* environment variable of the app. The value of the *VCAP_SERVICES* environment variable is the serialization of a JSON object. The variable contains the runtime data that is required to interact with the services that the app is bound to. The format of the data is different for different services. You might need to read the service documentation about what to expect and how to interpret each piece of information.

If a service that you bind to an app crashes, the app might stop running or have errors. {{site.data.keyword.cloud_notm}} doesn’t automatically restart the app to recover from these problems. Consider coding your app to identify and recover from outages, exceptions, and connection failures.

## Accessing services across {{site.data.keyword.cloud_notm}} deployment environments
{: #migrate_instance}

{{site.data.keyword.cloud_notm}} offers many deployment options, and you can access a service that is running in one environment from a different environment. For example, if you have a service that is running in Cloud Foundry, you can access that service from an app that is running in a Kubernetes cluster.

### Example: Access a Cloud Foundry service from a Kubernetes pod

To access a Cloud Foundry service from a pod in a Kubernetes cluster, you must bind the service to your cluster to store the service credentials in a Kubernetes secret. Then, you can make this information available to your app. 
{: shortdesc}

Service credentials that are stored in a Kubernetes secret are base64 encoded and encrypted in etcd by default. 

**Important**: Do not reference or expose your service credentials directly in your deployment YAML file. Deployment YAML files are not designed to hold sensitive data and do not encrypt your service credentials by default. To properly store and access this information, you must use a Kubernetes secret. 

1. [Bind the service to your cluster](/docs/containers?topic=containers-service-binding#bind-services). 
2. To access your service credentials from your app pod, choose between the following options. 
   - Mount the secret as a volume to your pod
   - Reference the secret in environment variables

## Creating a user-provided service instance
{: #user_provide_services}

You might have services that are managed outside of {{site.data.keyword.cloud_notm}}. If you have credentials to access those external services from the internet, you can create {{site.data.keyword.cloud_notm}} user-provided service instances to represent and communicate with your external services.

To create a user-provided service instance and bind it to an app, complete the following steps:

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

    * To create a service instance that drains information to a third-party log management software, use the `-l` option. Specify the destination that the third-party log management software provides. For example:

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

2. Bind the service instance to your app by using the `ibmcloud service bind` command. For example:

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

You can now configure your app to use the external services. For more information about configuring your app to use an external service, see [Configuring your app](/docs/apps?topic=creating-apps-add-resource#configure-app).
