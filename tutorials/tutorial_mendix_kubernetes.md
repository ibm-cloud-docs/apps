---

copyright:
  years: 2018
lastupdated: "2018-11-06"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Getting started with Mendix Platform on the IBM Kubernetes Service
{: #getting-started}

The Mendix Platform is a low-code development environment and toolset that helps you deliver multi-device applications faster, with fewer development resources, and that run on {{site.data.keyword.cloud}} platform. To learn more about the overall lifecycle of a Mendix application, review the [Mendix Getting Started Guide](/docs/apps/tutorials/tutorial_mendix_getting_started.html).

By default, Mendix applications that are targeting deployment to the IBM Kubernetes service are set up in an evaluation mode. This mode allows the Mendix Developer to start building an application quickly and deploy to the cloud, but doesn't configure data persistence or advanced Kubernetes configurations.

This tutorial guides the user through configuration of a production environment by setting up a persistent storage volume in Kubernetes with the {{site.data.keyword.cos_full_notm}} service.
{: shortdesc}

## Before you begin
{: #prerequisites}

- A Mendix application that targets Kubernetes and was created by using the [Mendix Getting Started Guide](/docs/apps/tutorials/tutorial_mendix_getting_started.html).
- Install the [{{site.data.keyword.dev_cli_notm}} CLI][/docs/cli/index.html], which includes the `kubectl` Kubernetes command line interface. 
- Sign in to the `ibmcloud` CLI and configure `kubectl` for [access to the Kubernetes cluster][/docs/containers/cs_tutorials.html#cs_cluster_tutorial_lesson3].

## Step 1. Create a Cloud Object Storage service instance
{: #cloud-object-storage}

Start from your application's details page and use the following steps:
1. Click **Add Resource**.
2. Select **Storage**, and click **Next**.
3. Next, select the **Cloud Object Storage** option and click **Next**.
4. You're presented with pricing plans for your {{site.data.keyword.cos_full_notm}} instance. Select the pricing plan that best suits your needs, and then click **Create** to create an instance of the {{site.data.keyword.cos_full_notm}} service for use with your Mendix application.

  If you prefer to use an existing instance of the {{site.data.keyword.cos_full_notm}} service, click **Add Resource**, and select the existing instance for your application to use.
  {: tip}

## Step 2. Create a storage bucket
{: #storage-bucket}

Once an instance of the {{site.data.keyword.cos_full_notm}} service is associated with your Mendix application, you must create a storage bucket where data can be saved. To create a bucket, click **...** for the {{site.data.keyword.cos_full_notm}} instance, and select **Open Dashboard**.  

The {{site.data.keyword.cos_full_notm}} service dashboard opens in a new window, on the **Buckets** tab. Click **Create Bucket**, and follow the steps to create a bucket by using a unique name. For the purposes of this tutorial, create a bucket called `my-mendix-bucket`.

## Step 3. Configure Persistent Storage
{: #kubernetes-storage}

Next, follow the documentation for [Storing data on {{site.data.keyword.cos_full_notm}}](/docs/containers/cs_storage_cos.html). A `PersistentVolumeClaim` and `PersistentVolume` are created within your Kubernetes cluster, and can be used by the PostGres database instance that is running within your cluster as part of the Mendix application. Be sure to create the `PersistentVolumeClaim` by using the `my-mendix-bucket` bucket as described in the previous step, and review the `PersistentVolumeClaim` name for use in the next step.

## Step 4. Edit the `postgres-deployment.yaml` file
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

## Step 5. Redeploy
{: #redeploy}

Once your `postgres-deployment.yaml` file changes are committed back to the repository, a new execution of the DevOps pipeline is automatically triggered. However, it deploys the default application again. You must redeploy the latest version of the Mendix application in order for the latest version of your application to be deployed with the latest persistent volume changes.

To redeploy, go to your application details page, and click **Deploy Application** within the **Deployment details** tile. If the deployment fails inside the DevOps toolchain with an error that indicates that the application's `.mda` file cannot be found, then you must export it from Mendix again. You can export by exporting from the Mendix Modeler desktop application, or by clicking **Edit on Mendix**. Then, within the Mendix web interface, go to the **Environments** section and follow the steps after you click **Create package from teamserver**. Once your application is exported from Mendix, go back to the application's details page and click **Deploy Application** again. The last exported application is deployed to your Kubernetes cluster by using the {{site.data.keyword.cloud_notm}} DevOps toolchain. Once the deployment completes successfully, your application is live and ready for production use.

## Additional information
{: #additional-information}

For more architectural detail on running Mendix applications in Kubernetes environments, review the [Run Mendix on Kubernetes](https://docs.mendix.com/deployment/docker/run-mendix-on-kubernetes) section of the Mendix user documentation.