---

copyright:
  years: 2015, 2023
lastupdated: "2023-02-03"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: apps

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Troubleshooting for creating apps
{: #managingapps}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created, and the starter kits will be removed from the catalog. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the App commands for the "dev" plug-in will be removed to coincide with the starter kit deprecation. To see the list of specific deprecated commands, run `ibmcloud dev` from the {{site.data.keyword.cloud_notm}} CLI. For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
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

## Cannot deploy my app from a starter kit that is deprecated
{: #deprecated-starter-ts}
{: troubleshoot}

When I try to deploy an app that I created from a starter kit, the following message is displayed:
{: tsSymptoms}

```text
Starter Kit De-Registered The starter kit associated with this app has been de-registered. The ability to download code and deploy is disabled.
```

This message occurs if you previously created an app from a starter kit that has since been deprecated, and you haven’t deployed the app yet. Because the corresponding Git repo is archived, you cannot download or generate the code or deploy that app.
{: tsCauses}

* Delete the app, and create a new one from a starter kit that isn't deprecated.
* Or, if you already deployed the app and want to keep it, you can only add services to it. Because your code is already deployed, then your repo for that app is already set up.
{: tsResolve}

## Web browser says my downloaded .zip file might be dangerous
{: #dangerous-file}
{: troubleshoot}

When I click **Download code** while I'm creating my app, the following message occurs, along with a **Discard** button:
{: tsSymptoms}

```text
<filename>.zip is not commonly downloaded and may be dangerous.
```

This message from your browser occurs most commonly when you try to download scripts, executables, and compressed files. When you click **Download code,** you're downloading a .zip file that contains the files for your app. The .zip file is safe for you to download.
{: tsCauses}

Click the arrow that's next to the **Discard** button, and then select **Keep**. The file is saved to your local drive.
{: tsResolve}

## My apps are hosted in different domains
{: #domains-ts}
{: troubleshoot}

Some of my apps are hosted in the `mybluemix.net` domain, but others are hosted in the `appdomain.cloud` domain.

My existing apps are hosted in the `mybluemix.net` domain, but my newer apps are hosted in the `appdomain.cloud` domain.
{: tsSymptoms}

A new host name option `*.appdomain.cloud` is available on cloud.ibm.com.

Previously, the `mybluemix.net` domain was used for hosting apps in various deployment targets, such as {{site.data.keyword.containerlong_notm}}. Any apps that you have hosted on `mybluemix.net` are not impacted.

For more information, see [Managing your domains](/docs/apps?topic=apps-update-domain).

## You have unsaved changes
{: #ts_unsaved_changes}
{: troubleshoot}

When you click items on the app details page, you might not be able to perform any actions. You also might be prompted to save changes before you can continue.

When you try to check your app or services on the app details page, the following error message is displayed:
{: tsSymptoms}

`You have unsaved changes. Are you sure you want to leave this page?`

When you scroll your mouse over the **INSTANCES** or **MEMORY QUOTA** fields on the runtime pane, the values change. This behavior is by design. However, you're prompted to save the memory or instance settings before you go to another page.
{: tsCauses}

Close the message window, and click **RESET** in your runtime pane.
{: tsResolve}

## Can't access {{site.data.keyword.cloud_notm}} services because of authorization errors
{: #ts_vcap}
{: troubleshoot}

Authorization errors might occur when your app accesses an {{site.data.keyword.cloud_notm}} service, if the service credentials are hardcoded in your app.

After you configure your app to communicate with an {{site.data.keyword.cloud_notm}} service, you deploy the app to {{site.data.keyword.cloud_notm}}. However, you can't use the app to access the {{site.data.keyword.cloud_notm}} service and receive an authorization error.
{: tsSymptoms}

The hardcoded credentials in the app might not be correct. Every time that the service is re-created, the credentials to access it change.
{: tsCauses}

Instead of hardcoding the credentials in your app, use connection parameters from the VCAP_SERVICES environment variable. The methods to use connection parameters from the VCAP_SERVICES environment variable vary depending on program languages. For example, for Node.js apps, you can use the following command:
{: tsResolve}

```text
process.env.VCAP_SERVICES
```

## 502 Bad Gateway errors are received
{: #ts_502_error}
{: troubleshoot}

If you receive `502 Bad Gateway` errors when you interact with apps on {{site.data.keyword.cloud_notm}}, check the {{site.data.keyword.cloud_notm}} status page, and then take appropriate actions.

You receive error messages that start with 502 Bad Gateway. For example, you might see `502 Bad Gateway: Registered endpoint failed to handle the request.`
{: tsSymptoms}

A Bad Gateway error usually happens when you go to a website that uses a proxy server to store and relay the data from the main server that hosts the site. The main server and the proxy server might not connect properly. Then, you see the HTTP status code 502 in your browser window. This status code indicates that the site's main server didn't receive the HTTP implementation that it expected from the proxy server.
{: tsCauses}

Other less common causes of a Bad Gateway error are internet service provider (ISP) dropouts, bad firewall configurations, and browser cache errors.

If you suspect that an {{site.data.keyword.cloud_notm}} service is down, first check the [{{site.data.keyword.cloud_notm}} status](https://cloud.ibm.com/status){: external} page. A workaround might be to [use the service in another {{site.data.keyword.cloud_notm}} region](/docs/overview?topic=overview-locations). If the service status is normal, try the following steps to solve the problem:
{: tsResolve}

   * Retry the action:
       * Reload the page by pressing F5 on your keyboard, or by clicking **Refresh**. If this step doesn't    work, clear your browser's cache and cookies, and then reload again.
       * Use a different browser.
       * Restart your router, your modem, and your computer. Rebooting these devices can clear up various  errors that lead to the error 502.
   * Wait and try again later. Temporary problems might occur with your internet service provider or the { {site.data.keyword.cloud_notm}} services. You can wait until the temporary problems are solved.
   * If the problem still exists, contact {{site.data.keyword.cloud_notm}} support. See [Contacting {{site.data.keyword.cloud_notm}} Support](/docs/get-support?topic=get-support-using-avatar){: external} for  more information.

## Android apps can't receive {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

Android apps in certain regions where Google isn't accessible can't receive notifications that you send out through the IBM {{site.data.keyword.mobilepushshort}} service. In this case, a workaround is to use third-party services.

You bind a {{site.data.keyword.mobilepushshort}} service for your {{site.data.keyword.cloud_notm}} app and send a message to the registered devices. However, apps that are developed on Android can't receive your notifications in certain regions.
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} service uses the Google Cloud Messaging (GCM) service to dispatch notifications to mobile apps that are developed on Android. To enable the Android apps to receive notifications, Google Cloud Messaging (GCM) service must be accessible by the mobile apps. In regions where the Android apps can't reach the GCM service, the Android apps can't receive {{site.data.keyword.mobilepushshort}}.
{: tsCauses}

As a workaround, use third-party services that don't rely on the GCM service; for example, [jpush](https://www.jiguang.cn/en/){: external}.
{: tsResolve}

## Double-byte characters aren't displayed properly when apps are pushed to {{site.data.keyword.cloud_notm}}
{: #ts_doublebytes}
{: troubleshoot}

Double-byte characters might not be displayed properly if Unicode support isn't configured properly for the servlet or JSP files.

When an app is pushed to the {{site.data.keyword.cloud_notm}}, the double-byte characters that are specified within the app aren't displayed properly.
{: tsSymptoms}

The problem might occur if Unicode support isn't configured properly for the servlet or JSP files.
{: tsCauses}

You can use the following code in your servlet or JSP file:
{: tsResolve}

* In the servlet source file
   ```java
   response.setContentType("text/html; charset=UTF-8");
   ```
   {: codeblock}
  
* In the JSP
   ```jsp
   <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
   ```
   {: codeblock}

## Node.js apps can't be deployed
{: #ts_nodejs_deploy}
{: troubleshoot}

You might experience problems when you update a Node.js app or deploy a Node.js app to {{site.data.keyword.cloud_notm}}.

When you update a Node.js app or deploy your Node.js app to {{site.data.keyword.cloud_notm}}, you might see one of the following error messages:
{: tsSymptoms}

`An app was not successfully detected by any available buildpack.`

`Instance (index 0) failed to start accepting connections.`

`Cannot get instances since staging failed.`

Possible causes are as follows:
{: tsCauses}

   * The start command isn't specified.
   * Files that are required to deploy a Node.js app are either missing from the app or in a folder other than the root directory.

Use one of the following methods, depending on the cause of the problem:
{: tsResolve}

* Specify the start command by one of the following methods:

   * Use the Cloud Foundry command-line interface. For example:

      ```text
      ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
      ```
      {: codeblock}

   * Use the [package.json](https://www.npmjs.com/package/jsonfile){: external} file. For example:

      ```json
      {
      ...
      "scripts": {
      "start": "node app.js"
      }
      }
      ```
      {: codeblock}

   * Use the `manifest.yml` file. For example:

      ```json
      applications:
      name: MyUniqueNodejs01
      ...
      command: node app.js
      ...
      ```
      {: codeblock}

* Ensure that a `package.json` file exists in your Node.js app so that the Node.js buildpack can recognize the app. Ensure that this file is in the root directory of your app. The following example shows a simple `package.json` file:
   ```json
    {
         "name": "MyUniqueNodejs01",
         "version": "0.0.1",
         "description": "A sample package.json file",
         "dependencies": {
                 "express": "3.4.x",
                 "jade": "1.1.x"
         },
         "engines": {
                 "node": "0.10.x"
         },
         "scripts": {
                   "start": "node app.js"
         }
    }
   ```
   {: codeblock}

* In the JSP
   ```jsp
   <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
   ```
   {: codeblock}

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

## Building an app fails with Docker error
{: #build_error}
{: troubleshoot}

When you try to build an app with the `ibmcloud dev build` command, it fails with a Docker username/password error. 
{: tsSymptoms}

Incorrect Docker Hub credentials are being used to authenticate. 
{: tsCauses}

Log out of Docker Hub in the Docker client.
{: tsResolve}
