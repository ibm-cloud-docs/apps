---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, credentials, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Adding credentials to your Kubernetes environment
{: #add-credentials-kube}

Learn how to add service credentials to your Kubernetes deployment environment.
{: shortdesc}

You must manually add service credentials to your deployment environment in these scenarios:
 * You bring your own code.
 * You start from a blank starter kit template.
 * You add a service to a starter kit-based app _after_ it was deployed.

## Your code + Kubernetes
{: #credentials-byoc-kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### Code it right

As a precaution, you can code your application to confirm that its environment is complete in your application's main entry point. You don't want to promotion an application into a cluster whose environment isn't complete to cause disruption to your product. The application might refuse to start, and your Kubernetes configuration can automatically prevent such disruptions.

Assume that you have the following two environment variables:
* `SECRET`
* `NOT_SECRET`

For a database, your variables might be `APIKEY` and `DB_URL`, where the former is sensitive and the latter isn't.

In Java, you might want to write something in the main application entry point like:
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

In Node, see a similar example:
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### Prepare the environment

In the Kubernetes `deployment.yml` file, the environment variables or a _reference to a secret in the cluster_ can be defined.

#### Set the deployment to get credentials from the environment

In the section with `kind: Deployment`, add the following example code at an indentation level after `spec.template.spec.containers`:
```yaml
env:
  - name: SECRET
    valueFrom:
      secretKeyRef:
          name: name-secret
          key: KEY_SECRET
  - name: NOT_SECRET
    value: "I'm not a secret"
```
{: codeblock}

* Click **Save**.

Configure the cluster so that the _secretKeyRef_ with the name `name-secret` and key `KEY_SECRET` resolves to a value.

#### Installing prerequisite tools

Use a terminal on your workstation to install the following tools:

1. Install the [{{site.data.keyword.dev_cli_long}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli).
2. Log in by using the `ibmcloud login` command.
3. Connect to your cluster by running `ibmcloud cs cluster-config {your_cluster_name}`.
4. Copy and paste the `export` command to run it from a terminal.

#### Define the secret in the cluster

The {{site.data.keyword.dev_cli_notm}} provides `kubectl`, which you can run because you're connected to your Kubernetes cluster.

To define the resolvable secret, use these `kubectl` commands:
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

Now that the Kubernetes cluster is prepared with a resolvable secret, you can update your application to use the environment variables that are defined in the `deployment.yml` file.

## Starter kit app and Kubernetes
{: #credentials-starterkit-kube}

1. Go to the **App details** page of your app.

2. To create an instance of Cloud Object Storage, select **Add service** > **Storage** > **Cloud Object Storage** > **Lite plan (Free)** > **Create**.

3. Click **Download code** to regenerate your project with the injected code snippets.

4. To access the credentials locally, copy and replace the following files from the newly generated `.zip` file, to your local Git clone to access the credentials. You must still create a Kubernetes secret in your cluster to host the credentials.

   - `chart/{appName}/bindings.yaml` - Generates an environment variable in your Kubernetes cluster that points to your secret.
   - `src/main/resources/localdev-config.json` - Access credentials while you run your app runs locally.
   - `src/main/resources/mappings.json` - A mapping to provide access to the [`env.getProperty()`](/docs/java-spring?topic=java-spring-configuration#accessing-credentials) method to access your environment variables from the code.
   - `manifest.yml` - This file binds your service to your Cloud Foundry application.

  If you later choose to deploy to a Cloud Foundry application with a Resource Controller resource (located in a resource group instead of an organization or space), then you must copy one more file.
  {: note}

5. [View your Kubernetes cluster](https://{DomainName}/containers-kubernetes/clusters){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") with corresponding region (US-South if it was free).

6. Click into your cluster and select **Kubernetes Dashboard** in the upper right to view your cluster dashboard.

7. Scroll down until you see a section that is labeled **Secrets**. You can see a secret for your {{site.data.keyword.cloudant_short_notm}} service instance that uses the following convention `binding-{appName}-{serviceName}-{timestamp}`. In the `chart/{appName}/bindings.yaml` file, you can find the corresponding {{site.data.keyword.cloudant_short_notm}} secret.

8. Now you can create a corresponding one for your Cloud Object Storage instance with the secret name that is already generated in the `chart/{appName}/bindings.yaml`, which looks something like `binding-create-app-ktibr-cloudobjectstor-1538170732311`.

9. Go to the **App details** page in the dashboard and copy the credentials for the Cloud Object Storage instance. See the following example credentials output:
  ```yaml
  {
    "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
    "endpoints": "https://cos-service.bluemix.net/endpoints",
    "resource_instance_id": "crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
  }    
  ```
  {: codeblock}

10. Make sure that your cluster is configured by using `ibmcloud cs cluster-config {your_cluster_name}` and exporting the command in the instructions that follow.

11. Use the `echo` command to place the credentials into a `binding` file.
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. Create the secret with `kubectl create secret generic binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding`. If you go back in to your Kubernetes cluster dashboard, you can see the secret that you created.

  If you're deploying to a Cloud Foundry application, you need to create a user provided service if you're using a Resource Controller instance (if the resource lives in a resource group versus an organization or space). 
  {: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  The name of your user provided service can be found in the `manifest.yml` file with the corresponding instance name.

13. Now you can access your secret through the environment variables through the `env.getProperty` method when your application is running in your Kubernetes cluster.

### How the Kubernetes cluster is prepared

Use the **Configure continuous delivery** feature to deploy your app to your IBM Kubernetes cluster. The feature prepares your Kubernetes cluster with secrets for the credentials of the resources that are associated with your app. You can observe the results of the cluster preparation by completing these steps:

1. Run this command to view the results: `kubectl get secrets`:
  ```
  NAME                                   TYPE                                  DATA      AGE
  binding-blarg-cloudant-1538408663553   Opaque                                1         13m
  bluemix-default-secret                 kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-international   kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-regional        kubernetes.io/dockerconfigjson        1         17d
  default-token-xfd5n                    kubernetes.io/service-account-token   3         17d
  ```
  {: screen}

  You can view [more documentation about secrets](https://kubernetes.io/docs/concepts/configuration/secret/).
  {: tip}

2. Observe that the name of the secret is the resource name.
3. View the verbose information about the secret by using `kubectl get secret binding-blarg-cloudant-1538408663553 -o=yaml`:

  ```
  apiVersion: v1
  data:
    binding: eyJhcGlrZXkiOiI4RFprT3VMVnduVkExWW1HODFnazNQMjZOeThlNWFWbjVhaFpZLVVEOHQ1NCIsImhvc3QiOiI1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJpYW1fYXBpa2V5X2Rlc2NyaXB0aW9uIjoiQXV0byBnZW5lcmF0ZWQgYXBpa2V5IGR1cmluZyByZXNvdXJjZS1rZXkgb3BlcmF0aW9uIGZvciBJbnN0YW5jZSAtIGNybjp2MTpibHVlbWl4OnB1YmxpYzpjbG91ZGFudG5vc3FsZGI6dXMtc291dGg6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzpiZmEzNDJkZC00YjZmLTRkZmUtYTM1YS05MTA4ZmIwZWM1NzE6OiIsImlhbV9hcGlrZXlfbmFtZSI6ImF1dG8tZ2VuZXJhdGVkLWFwaWtleS01MzI3ZWMxZC0wOWE1LTQyMzctOTczNS03ZTAxZmU3NDFiYzciLCJpYW1fcm9sZV9jcm4iOiJjcm46djE6Ymx1ZW1peDpwdWJsaWM6aWFtOjo6OnNlcnZpY2VSb2xlOldyaXRlciIsImlhbV9zZXJ2aWNlaWRfY3JuIjoiY3JuOnYxOmJsdWVtaXg6cHVibGljOmlhbS1pZGVudGl0eTo6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzo6c2VydmljZWlkOlNlcnZpY2VJZC1mNWRhMjMwYy1kNDE0LTQ4NTQtYjE1Yi00MmJmZmRhYWVmNWIiLCJwYXNzd29yZCI6ImY4MjU2ZDJhODYyMjI5NzViZDI3Mjc1MjEzMTY4YTQyNzBhNDZmMmEyOGQ5NDkyMjRhYzFjOTc3NjMwMWNlZTYiLCJwb3J0Ijo0NDMsInVybCI6Imh0dHBzOi8vNTlhYTdiMWEtNWFhYi00ZjJkLTlhNzMtOGMzYjI5NDA4Zjk2LWJsdWVtaXg6ZjgyNTZkMmE4NjIyMjk3NWJkMjcyNzUyMTMxNjhhNDI3MGE0NmYyYTI4ZDk0OTIyNGFjMWM5Nzc2MzAxY2VlNkA1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJ1c2VybmFtZSI6IjU5YWE3YjFhLTVhYWItNGYyZC05YTczLThjM2IyOTQwOGY5Ni1ibHVlbWl4In0=
  kind: Secret
  metadata:
    annotations:
      service-instance-id: 'crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::'
      service-key-id: 5327ec1d-09a5-4237-9735-7e01fe741bc7
    creationTimestamp: 2018-10-01T15:45:02Z
    name: binding-blarg-cloudant-1538408663553
    namespace: default
    resourceVersion: "155591"
    selfLink: /api/v1/namespaces/default/secrets/binding-blarg-cloudant-1538408663553
    uid: f5e7885c-c590-11e8-ad83-8e37f3f3216f
  type: Opaque
  ```
  {: screen}

  The `binding` is the base64-encoded value of the secret. Decoding it reveals that it's just the raw JSON from the `credentials` of the service instance, plus some `iam_...` values:
  ```
  {
    "apikey": "8DZkOuLVwnVA1YmG81gk3P26Ny8e5aVn5ahZY-UD8t54",
    "host": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::",
    "iam_apikey_name": "auto-generated-apikey-5327ec1d-09a5-4237-9735-7e01fe741bc7",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Writer",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/480fd1ec14ac540c5bc37da799a63437::serviceid:ServiceId-f5da230c-d414-4854-b15b-42bffdaaef5b",
    "password": "f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6",
    "port": 443,
    "url": "https://59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix:f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6@59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "username": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix"
  }
  ```
  {: screen}

The Kubernetes secret isn't retrievable by your application code unless the `deployment.yml` declares an `env` value that references the secret. When you use a starter kit, such code is generated automatically.

### The starter kit generated code
{: #credentials-starterkit-kube-gencode}

In this case, you created this application from a starter kit. The code that is generated from a starter kit is made to be portable to run locally, in Cloud Foundry, or in Kubernetes. The library, `IBMCloudEnv`, is used to provide an abstraction layer between the application code and the retrieval of the environment variables that hold the credentials for the service instances.

The code that is created from the starter kit has a dependency for the `IBMCloudEnv` library and produces the following output:

* A `bindings.yml` file, which is included inline in the `deployment.yml` file, with this content:
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  The `secretKeyRef.name` exposes the defined Kubernetes secret to be retrievable by the application as a simple environment variable in the application code.

* The instructions for the `IBMCloudEnv` library are encapsulated in a `mappings.json` file, which is in the starter kit generated code base. The `mappings.json` has individual definitions for each credential:
  ```json
  "cloudant_apikey": {
    "searchPatterns": [
      "user-provided:blarg-cloudant-1538408663553:apikey",
      "cloudfoundry:$['cloudant'][0].credentials.apikey",
      "env:service_cloudant:$.apikey",
      "env:cloudant_apikey",
      "file:/server/localdev-config.json:$.cloudant_apikey"
    ]
  },
  ```
  {: codeblock}

  The `mappings.json` file uses `jsonpath` syntax and the order of the `searchPatterns` array to guide the `IBMCloudEnv` logic.

* Use the following code to retrieve the Cloudant API key (pseudocode):
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

The `IBMCloudEnv` library automatically detects whether your application is running in Kubernetes, Cloud Foundry, or a virtual server instance (treated the same as local docker), and applies the correct `searchPattern` to find the value to return.

Therefore, the `mappings.json` file is to be considered _the definitive list_ of preconfigured and immediately available values that are from the environment in which your app is to run. The values are populated in the environment for the cluster you targeted at the time that you used the **Configure continuous delivery** feature.