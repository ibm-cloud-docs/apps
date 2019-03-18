---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, deploying apps, containers, Kubernetes, Docker, clusters, DevOps toolchain

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Using containers with Kubernetes
{: #containers-kube}

Get started with {{site.data.keyword.containershort}} by deploying highly available apps in Docker containers that run in Kubernetes clusters. Manage your team development with Git, and then use the DevOps Toolchain to manage the deployment of your app to Kubernetes.
{: shortdesc}

Containers are a standard way to package apps and all their dependencies so that you can seamlessly move the apps between environments. Unlike virtual machines, containers don't bundle the operating system. Only the app code, runtime, system tools, libraries, and settings are packaged inside containers. Containers are more lightweight, portable, and efficient than virtual machines.

See [Getting started with {{site.data.keyword.containershort_notm}}](/docs/containers?topic=containers-container_index) to learn more about the service.

## Configuring deployments
{: #config-deploy}

When you create back-end or web-serving apps, you can deploy them to the {{site.data.keyword.containershort_notm}} service, which uses the Kubernetes environment.

1. Deploy your app to the cloud by setting up an automated cloud pipeline.
2. Click **Configure continous delivery**.
3. Select **IBM Kubernetes Service** as the target. You need to [create a cluster](https://{DomainName}/containers-kubernetes/catalog/cluster/create){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") if you don't already have one.
4. After your deployment is complete, check out your live app in the cloud by getting the URL in the logs from your deploy stage of the delivery pipeline. The last IP address with a port is your app's new home, for example, 169.60.133.124:32355.

## Binding services
{: #bind-services}

As the toolchain is created, the services that you associated with your app are bound to the Kubernetes cluster by using Kubernetes secrets. Secrets are used to manage the service credentials outside of your running app. The app reads the secrets and then retrieves the values that it needs to start running. Binding services enable you to deploy the app to another Kubernetes environment that might be using production level {{site.data.keyword.cloud}} service instances.

If you delete the service or the secrets, you need to manually bind them again or delete and re-create the toolchain.
{: tip}

For more information, see [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon").

## Starting development
{: #dev}

1. Check out your new online Git repository from the toolchain and start working with your code. To see the toolchain, click **View toolchain**.
2. Access the Git repository where the code was created by cloning the repo to your local environment.
3. Open the project with your favorite IDE.

## Building and deploying with a toolchain
{: #bulid-deploy-tc}

The toolchain contains the building stage and the deployment stage.

### Building stage
{: #build-stage}
The building stage is triggered when a `git push` is run on your Git repository. The stage in the pipeline triggers a docker image build and places the image in the container registry.

For more information, see [Getting started with IBM Cloud Container Registry](/docs/services/Registry?topic=registry-index).

### Deployment stage
{: #deploy-stage}

The deployment stage retrieves the latest image from the {{site.data.keyword.registryshort_notm}} and then deploys it into your Kubernetes cluster by using a Helm chart. The Helm chart was added to your app when you deployed to the cloud. Helm charts make it easy to manage the deployment steps of the packaged container image.

For more information, see [Charts](https://docs.helm.sh/developing_charts/){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon").

{{site.data.keyword.cloud_notm}} supports a number of [preconfigured Helm Charts](https://{DomainName}/containers-kubernetes/solutions/helm-charts){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon").

## Checking app security
{: #sec}

{{site.data.keyword.containershort_notm}} supports scanning the packaged container images for security vulnerabilities. Security scanning is essential for supporting enterprise-grade applications.

View the containers [image repository](https://{DomainName}/containers-kubernetes/registry/private){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") to check for potential security vulnerabilities.
