---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: apps, mendix, mendix app, deploy, cos, storage bucket, devops toolchain, deploy, kubernetes, kube

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Deploying your Mendix app on the {{site.data.keyword.containerlong_notm}}
{: #deploy-mendix-kube}

By default, Mendix applications that target deployment to the {{site.data.keyword.containerlong}} are set up in an evaluation mode. This mode allows the you to start building an app quickly and deploy to the cloud, but doesn't configure data persistence or advanced Kubernetes configurations. This tutorial guides you through configuration of a production environment by setting up a persistent storage volume in Kubernetes with the {{site.data.keyword.cos_full_notm}} service.
{: shortdesc}

## Before you begin
{: #prereqs-mendix-kube}

* Create your Mendix app. See [Creating Mendix apps](/docs/apps/tutorials?topic=creating-apps-create-mendix) for more information.
* Install the [{{site.data.keyword.dev_cli_notm}} command-line interface (CLI)](/docs/cli?topic=cloud-cli-getting-started), which includes the {{site.data.keyword.containershort_notm}} CLI.
* Log in to the `ibmcloud` CLI and configure `kubectl` for [access to the Kubernetes cluster](/docs/containers?topic=containers-cs_cluster_tutorial#cs_cluster_tutorial_lesson3).

## Creating a Cloud Object Storage service instance
{: #cos-mendix-kube}

Start from your **App details** page, and use the following steps:
1. Click **Add service**.
2. Select **Storage**, and click **Next**.
3. Next, select the **Cloud Object Storage** option and click **Next**.
4. You're presented with pricing plans for your {{site.data.keyword.cos_full_notm}} instance. Select the pricing plan that best suits your needs, and then click **Create** to create an instance of the {{site.data.keyword.cos_full_notm}} service for use with your Mendix app.

  If you prefer to use an existing instance of the {{site.data.keyword.cos_full_notm}} service, click **Add service**, and select the existing instance for your app to use.
  {: tip}

## Creating a storage bucket
{: #storage-bucket-mendix-kube}

Once an instance of the {{site.data.keyword.cos_full_notm}} service is associated with your Mendix app, you must create a storage bucket where data can be saved. To create a bucket, click **...** for the {{site.data.keyword.cos_full_notm}} instance, and select **Open Dashboard**.  

The {{site.data.keyword.cos_full_notm}} service dashboard opens in a new window, on the **Buckets** tab. Click **Create Bucket**, and follow the steps to create a bucket by using a unique name. For the purposes of this tutorial, create a bucket called `my-mendix-bucket`.

## Configuring persistent storage
{: #kube-storage-mendix}

Next, follow the documentation for [Storing data on {{site.data.keyword.cos_full_notm}}](/docs/containers?topic=containers-object_storage). A `PersistentVolumeClaim` and `PersistentVolume` are created within your Kubernetes cluster, and can be used by the PostGres database instance that is running within your cluster as part of the Mendix app. Be sure to create the `PersistentVolumeClaim` by using the `my-mendix-bucket` bucket as described in the previous step, and review the `PersistentVolumeClaim` name for use in the next step.

## Editing the `postgres-deployment.yaml` file
{: #postgres-deploy-mendix}

After a persistent volume is configured for your Kubernetes cluster, the next step is to modify the PostGres database deployment that is running within your cluster. First, you must edit the files in the Git repository that were created as part of the IBM DevOps toolchain integration step. To find the Git repository, return to the **App details** page, and click the Git URL link from the **Deployment details** tile.

You can either clone the Git repository to your local machine, or make the following changes in the online editor. Open up the `chart/{app name}/templates/postgres-deployment.yaml` file (replace `{app name}` with the name of your Mendix app). The file doesn't have any existing `volumeMount` or `volumes` entries by default, so all data is stored in-memory within the running deployment pod. You must add both `volumeMount` and `volumes` entries to the Kubernetes `deployment.yaml` file so that data is saved to the {{site.data.keyword.cos_full_notm}} bucket and isn't lost if the pod restarts. 

See the following sample `postgres-deployment.yaml` that includes the `volumeMount` and `volumes` entries.  
```yaml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: "{appname}-postgres"
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: "{appname}-postgres"
    spec:
      containers:
        - name: "{appname}-postgres"
          image: postgres:10.1
          ports:
            - containerPort: 5432
          env:
            - name: POSTGRES_DB
              value: db0
            - name: POSTGRES_USER
              value: mendix
            - name: POSTGRES_PASSWORD
              value: mendix
          volumeMounts:
            - mountPath: "/var/lib/postgresql/data"
              name: "mendix-data"
      volumes:
        - name: mendix-data
          persistentVolumeClaim:
            claimName: {pvc-name}
```

Be sure to replace `{pvc-name}` with the name of your `PersistentVolumeClaim` from the previous step, and be careful not to overwrite your app's name, which is already set in the file within your Git repository. Then, commit your changes back to the Git repository.

## Redeploying
{: #redeploy-mendix-kube}

After your `postgres-deployment.yaml` file changes are committed back to the repository, a new execution of the DevOps pipeline is automatically triggered. However, it deploys the default app again. You must redeploy the latest version of the Mendix app in order for the latest version of your app to be deployed with the latest persistent volume changes.

To redeploy, go to your **App details** page, and click **Configure continuous delivery** within the **Deploy your app** tile. If the deployment fails inside the DevOps toolchain with an error that indicates that the app's `.mda` file cannot be found, then you must export it from Mendix again. You can export by exporting from the Mendix Modeler desktop app, or by clicking **Edit on Mendix**. Then, within the Mendix web interface, go to the **Environments** section and follow the steps after you click **Create package from teamserver**. After your app is exported from Mendix, return to the **App details** page, and click **onfigure continuous delivery** again. The last exported app is deployed to your Kubernetes cluster by using the {{site.data.keyword.cloud}} DevOps toolchain. Once the deployment completes successfully, your app is live and ready for production use.

## Verifying that your app is running
{: #verify-mendix-kube}

After you deploy your app, the Delivery Pipeline or command line points you to the URL for your app.

1. From your DevOps toolchain, click **Delivery Pipeline**, and then select **Deploy Stage**.
2. Click **View logs and history**.
3. In the log file, find the app's URL:

    At the end of the log file, search for the word `urls` or `view`. For example, you might see a line in the log file that's similar to `urls: my-app-devhost.mybluemix.net` or `View the application health at: http://<ipaddress>:<port>/health`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

## Additional information
{: #more-info-mendix-kube}

For more architectural detail on running Mendix apps in Kubernetes environments, review the [Run Mendix on Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") section of the Mendix user documentation.