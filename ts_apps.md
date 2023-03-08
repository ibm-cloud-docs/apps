---

copyright:
  years: 2015, 2023
lastupdated: "2023-03-08"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: apps

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Troubleshooting for creating apps
{: #managingapps}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created by using the `ibmcloud dev` commands. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the App commands for the "dev" plug-in will be removed to coincide with the starter kit deprecation. To see the list of specific deprecated commands, run `ibmcloud dev` from the {{site.data.keyword.cloud_notm}} CLI. For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
{: deprecated}

General problems with creating applications might include apps that can't be updated, or double-byte characters that aren't displayed. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}

Have a casual question or just want to talk about all things starter kits? Come chat with the development team on [{{site.data.keyword.cloud_notm}} Dev Tools Slack](https://ic-devops-slack-invite.us-south.devops.cloud.ibm.com/){: external}. After you request your invitation, sign in and join the `#ask-your-question` channel.
{: tip}

## Errors when applying Terraform plan using Schematics
{: #terraform-apply-plan-errors}
{: troubleshoot}

Error when creating resource instance: This plan requires a paid account. You can upgrade by adding a credit card to your account or you can select the free plan if it's available.

22: resource "ibm_resource_instance" "cos_instance"

The IBM Cloud Infrastructure credentials could not be validated.

62: resource "ibm_container_cluster" "cluster"

## Exceeded your storage quota for Kubernetes clusters
{: #exceed_quota}

If the build or deploy jobs fail, and you see the following message, you can delete images from your Kubernetes clusters by using CLI commands. `Status: unauthorized: You have exceeded your storage quota. Delete one or more images, or review your storage quota and pricing plan.`

* Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started) if you don't already have it.
* Log in to {{site.data.keyword.cloud_notm}} by using `ibmcloud login`, and point it to the space that you're in.
* List your images by using `ibmcloud cr images`.
* Delete any unused images by using `ibmcloud cr image-rm <respository>:<tag>`.
* Rerun the build or deploy job that failed.

For more information, see [Freeing up used storage and changing service plans or quota limits to stay within given quota limits](/docs/Registry?topic=Registry-registry_quota#registry_quota_freeup).

## Accessing Kubernetes logs
{: #access_kube_logs}

If the app isn't running and you can't access the health endpoint, try looking at the logs in the cluster.
* Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started) if you don't already have it.
* Log in to {{site.data.keyword.cloud_notm}} by using `ibmcloud login`, and point it to the space that you're in.
* List your clusters by using `ibmcloud cs clusters`,
* Point to your corresponding cluster by using `ibmcloud cs cluster-config <cluster-name>`.
* Export the environment variable that is listed.
* View your pods by using `kubectl get pods`. If you need to install `kubectl`, see [Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: external}.
* You can view the logs in your app by using `kubectl logs <pod-name>.`

## Starting `docker` fails with file not found message
{: #docker_not_found}
{: troubleshoot}

When you try to start Docker, the following error message is displayed:
{: tsSymptoms}

```text
An error exec: "docker": executable file not found in $PATH was encountered while the Docker image is building.
```
{: screen}

The Docker client isn't installed, or it's installed but not started.
{: tsCauses}

Ensure [Docker](https://docs.docker.com/install/){: external} is installed, and start it.
{: tsResolve}
