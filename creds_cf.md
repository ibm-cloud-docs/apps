---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-04"

keywords: apps, credentials, cloud foundry, environment, service, credential, vcap_services

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Adding service credentials to your Cloud Foundry environment
{: #add-credentials-cf}

Learn how to add service credentials to your Cloud Foundry deployment environment. These instructions apply to both [Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf) and [Cloud Foundry Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee).
{: shortdesc}

The default shared domain is `mybluemix.net`, but `appdomain.cloud` is another domain option that you can use. For more information about migrating to `appdomain.cloud`, see [Updating your domain](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).
{: tip}

## Your code + Cloud Foundry
{: #credentials-byoc-cf}

In the Cloud Foundry space in which your application exists, you can define what Cloud Foundry calls a user-provided service. A user-provided service is a stringified JSON stored as though it's a bindable service in the Cloud Foundry space. After you log in and connect to the Cloud Foundry organization and space, complete the following steps to create and bind a service.

1. Create a user-provided service by running the following command:
  ```console
  cf cups customcreds -p '{"username":"Leeroy","password":"Jenkins"}'
  ```
  {: codeblock}

2. Configure your Cloud Foundry application to bind to the user-provided service by adding to the services section:
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - customcreds
  ```

3. Code your application to read the environment for a `VCAP_SERVICES` environment variable, parse it into JSON, and find the credential that you need (node.js-like pseudocode):
  ```
  // get the 'password' from "customcreds" user-provided service
  vcapServices = getEnvironment('VCAP_SERVICES');
  vcapServicesAsJSON = JSON.parse(vcapServices);
  upsArray = vcapServicesAsJSON['user-provided'];
  if (upsArray) {
      for (var i = 0, len = upsArray.length; i < len; i++) {
          if (upsArray[i].name === 'customcreds') {
              return upsArray[i].credentials.password
          }
      }
  }
  ```
{: codeblock}


## Starter kit app + Cloud Foundry
{: #credentials-starterkit-cf}

### How the Cloud Foundry space is prepared

Use the **Configure continuous delivery** feature to deploy your app to your Cloud Foundry space.

If the Cloud Foundry-based service instance is in the same Cloud Foundry space as the deployed Cloud Foundry application, see the [next section](/docs/apps?topic=creating-apps-add-credentials-cf).

If the Cloud Foundry-based service instance is in a different space than the target space for the Cloud Foundry application, see the [following section](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_different).

If the service that you associated with your application is Resource Controller-based, see [Resource Controller](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_controller).

#### The Cloud Foundry-based service is in the same space as the deployed app
{: #cf_resource_same}

If the service that you associated with your application is Cloud Foundry-based, the service is "bindable" in Cloud Foundry. You can see the service in your Cloud Foundry space by connecting your `cf` command line with the correct region + org + space. You can tell if the service is Cloud Foundry-based at the time of service creation, if you were asked in which Cloud Foundry organization and space to create the service.

You can view bound applications by running the following command:
```console
cf services
```
{: codeblock}

Example output:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg3-alertnotificati-1538417831070   alertnotification   authorizedusers                create succeeded
```
{: screen}

#### The Cloud Foundry-based service is in a different space from the deployed app
{: #cf_resource_different}

Cloud Foundry doesn't support "binding" a Cloud Foundry application to a Cloud Foundry service when the application and service aren't in the same Cloud Foundry space. The Cloud Foundry space must be prepared with "user-provided" services, and the following section is applicable.

#### The Resource Controller-based service is associated with your app
{: #cf_resource_controller}

If the service you associated with your application is Resource Controller-based, the service is _not_ "bindable" in Cloud Foundry. You can tell that it is Resource Controller-based at the time of service creation if you were asked in which resource group to create the service. The Cloud Foundry space must be prepared with service credentials so that the application can reference them in code. The preparation is done for you automatically, and you can observe the results of the space preparation by connecting the `cf` command line to your space by running:
```console
cf services
```
{: codeblock}

Example output:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg-cloudant-1538408663553           user-provided
```
{: screen}

Cloud Foundry doesn't allow visibility to the value of any service credentials, encoded or otherwise, to the `cf service` or `cf services` command line. Functionally, a user-provided service is a stringified JSON that is defined as a named "service instance" in your Cloud Foundry space. To see the values, you must first bind an application to the Cloud Foundry service by indicating the service instance name in the app's `manifest.yml` file under the `services` heading. Then, run the app in the Cloud Foundry space, and get the environment of that application by running `cf env $APP_NAME`.

Thankfully, the code that is generated from a starter kit is automatically populated with the correct bindings to retrieve and use the values from the environment that is defined for it in the Cloud Foundry space in which the application runs.

### The starter kit generated code
{: #starterkit-generated-code-cf}

Before you continue, see [Starter kit app + kube](/docs/apps?topic=creating-apps-add-credentials-kube#credentials-starterkit-kube-gencode). Then, apply the following change:

* Although the generated code provides the `deployment.yml`, it isn't applicable for an application that is deployed to Cloud Foundry. Rather, `manifest.yml` _is_ applicable, and its contents are shown to _bind_ to the two services that are created in the Cloud Foundry space:
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - blarg3-alertnotificati-1538417831070
      - blarg-cloudant-1538408663553
  ```
  {: codeblock}

The rest of the documentation from the prior subsection once again applies. The `IBMCloudEnv` library abstracts the retrieval of the values from the environment in which the application runs.

The library abstracts some complexity in retrieving environment values from Cloud Foundry. In Cloud Foundry, a running application is provided with an environment variable named `VCAP_SERVICES` whose value is stringified JSON, and has holds the values for bound service credentials, no matter if the service is a service instance _in_ the Cloud Foundry space or a user-defined service value. The top-level keys in the parsed JSON from `VCAP_SERVICES` environment variable are the Cloud Foundry `label` associated with the services that are Cloud Foundry-based, and the key `user-provided` whose value holds an array of credentials for all of the "user-provided" services.