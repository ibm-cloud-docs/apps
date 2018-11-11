---

copyright:
  years: 2018
lastupdated: "2018-11-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Deploying your Mendix app on the {{site.data.keyword.containerlong_notm}}
{: #getting-started}

By default, Mendix applications that target deployment to the {{site.data.keyword.containerlong}} are set up in an evaluation mode. This mode allows the you to start building an application quickly and deploy to the cloud, but doesn't configure data persistence or advanced Kubernetes configurations. This tutorial guides you through configuration of a production environment by setting up a persistent storage volume in Kubernetes with the {{site.data.keyword.cos_full_notm}} service.
{: shortdesc}

## Before you begin
{: #prerequisites}

- Create your Mendix app. See [Creating Mendix apps](/docs/apps/tutorials/tutorial_mendix_getting_started.html) for more information.
- Install the [{{site.data.keyword.dev_cli_notm}} command-line interface (CLI)](/docs/cli/index.html), which includes the {{site.data.keyword.containershort_notm}} CLI.
- Log in to the `ibmcloud` CLI and configure `kubectl` for [access to the Kubernetes cluster](/docs/containers/cs_tutorials.html#cs_cluster_tutorial_lesson3).

## Creating a Cloud Object Storage service instance
{: #cloud-object-storage}

Start from your application's details page and use the following steps:
1. Click **Add Resource**.
2. Select **Storage**, and click **Next**.
3. Next, select the **Cloud Object Storage** option and click **Next**.
4. You're presented with pricing plans for your {{site.data.keyword.cos_full_notm}} instance. Select the pricing plan that best suits your needs, and then click **Create** to create an instance of the {{site.data.keyword.cos_full_notm}} service for use with your Mendix application.

  If you prefer to use an existing instance of the {{site.data.keyword.cos_full_notm}} service, click **Add Resource**, and select the existing instance for your application to use.
  {: tip}

## Creating a storage bucket
{: #storage-bucket}

Once an instance of the {{site.data.keyword.cos_full_notm}} service is associated with your Mendix application, you must create a storage bucket where data can be saved. To create a bucket, click **...** for the {{site.data.keyword.cos_full_notm}} instance, and select **Open Dashboard**.  

The {{site.data.keyword.cos_full_notm}} service dashboard opens in a new window, on the **Buckets** tab. Click **Create Bucket**, and follow the steps to create a bucket by using a unique name. For the purposes of this tutorial, create a bucket called `my-mendix-bucket`.

## Configuring persistent storage
{: #kubernetes-storage}

Next, follow the documentation for [Storing data on {{site.data.keyword.cos_full_notm}}](/docs/containers/cs_storage_cos.html). A `PersistentVolumeClaim` and `PersistentVolume` are created within your Kubernetes cluster, and can be used by the PostGres database instance that is running within your cluster as part of the Mendix application. Be sure to create the `PersistentVolumeClaim` by using the `my-mendix-bucket` bucket as described in the previous step, and review the `PersistentVolumeClaim` name for use in the next step.

## Editing the `postgres-deployment.yaml` file
{: #postgres-deployment}

Once a persistent volume is configured for your Kubernetes cluster, the next step is to modify the PostGres database deployment that is running within your cluster. First, you must edit the files in the Git repository that were created as part of the IBM DevOps toolchain integration step. To find the Git repository, go back to the app details page, and click the Git url link from the **Deployment details** tile.  

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
{: #redeploy}

Once your `postgres-deployment.yaml` file changes are committed back to the repository, a new execution of the DevOps pipeline is automatically triggered. However, it deploys the default application again. You must redeploy the latest version of the Mendix application in order for the latest version of your application to be deployed with the latest persistent volume changes.

To redeploy, go to your application details page, and click **Deploy Application** within the **Deployment details** tile. If the deployment fails inside the DevOps toolchain with an error that indicates that the application's `.mda` file cannot be found, then you must export it from Mendix again. You can export by exporting from the Mendix Modeler desktop application, or by clicking **Edit on Mendix**. Then, within the Mendix web interface, go to the **Environments** section and follow the steps after you click **Create package from teamserver**. Once your application is exported from Mendix, go back to the application's details page and click **Deploy Application** again. The last exported application is deployed to your Kubernetes cluster by using the {{site.data.keyword.cloud_notm}} DevOps toolchain. Once the deployment completes successfully, your application is live and ready for production use.

## Additional information
{: #additional-information}

For more architectural detail on running Mendix applications in Kubernetes environments, review the [Run Mendix on Kubernetes](https://docs.mendix.com/deployment/docker/run-mendix-on-kubernetes) section of the Mendix user documentation.