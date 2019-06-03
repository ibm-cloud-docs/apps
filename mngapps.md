---

copyright:
  years: 2015, 2018
lastupdated: "2019-06-03"

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Checking the status of your app
{: #manageapps}

Your resource list in the {{site.data.keyword.cloud}} console provides summary information for the applications that you created. The summary information includes the name, icon, URL, runtime, running status, and service instances that are bound to the app.
{:shortdesc}

## Understanding the status of your app
{: #status}

From your resource list, you can view the status of each app. In the state column for each app, you can see whether the instances of app are running.

<dl>
<dt>
<strong>
Stopped or Unknown (gray)
</strong>
</dt>
<dd>
Your app is stopped or the status is unknown. The gray icon indicates that the app is stopped or the status is unknown.
</dd>
<dt>
<strong>
Running (green)
</strong>
</dt>
<dd>
Your app is running. The green icon indicates that the app is started and all instances are running.
</dd>
<dt>
<strong>
_Number_  running (yellow)
</strong>
</dt>
<dd>
The app is started, but not all instances are running. The yellow icon indicates that fewer than 100% of the instances are running. The number of instances that are running and the number of instances that failed are displayed.
</dd>
<dt>
<strong>
Not running (red)
</strong>
</dt>
<dd>
Your app isn’t running. The red icon indicates that the app is started, but no instance is running.
</dd>
</dl>

## Viewing your app details
{: #viewingapps}

You can view more information about an app by clicking the name of it in your resource list. Then, you can see the app's Overview page.

On the Apps Overview page, after an app is deployed, you can start, stop, restart, or in the case of web apps, modify the number of instances and the amount of memory that is used by the app. For web apps, {{site.data.keyword.cloud_notm}} doesn’t automatically scale your app based on its load, so you must manage it yourself.

If an update is made, apps can be redeployed. The mechanism for updating the app is the same mechanism that is used to deploy it originally. {{site.data.keyword.cloud_notm}} stops all running instances and replaces them with new instances automatically.
