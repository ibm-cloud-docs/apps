---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# {{site.data.keyword.cloud_notm}} Developer Console Walkthrough
{: #intro}

<!--I can't see how a customer needs to be walked through the experience without performing a specific task.-->


The {{site.data.keyword.cloud}} Developer Experience enables a cloud native application developer to create an app from a variety of starter kits, create and connect key {{site.data.keyword.Bluemix_notm}}-optimized services, and then quickly download working code or set up for continuous delivery. The Developer Experience provides a set of developer consoles across {{site.data.keyword.Bluemix_notm}} that allow you to create, view, configure, and manage your app as well as deploy it to a devops pipeline or download it for local development.

To see a list of developer consoles, click [here](devex_elements.html#developer_consoles).
{: tip}

By creating an app thorough an {{site.data.keyword.cloud_notm}} developer console, all of the required parts of your app are maintained under your account on the {{site.data.keyword.cloud_notm}} server.  Thus you can move back and forth between the developer console GUI and [{{site.data.keyword.dev_cli_notm}}](/docs/cli/idt/index.html) should you choose to do so.

{{site.data.keyword.cloud_notm}} developer consoles give you a seamless path to building a production-ready starter app for the use case you select.  Let's look at the steps you might take in your journey.

Ready to jump in?  Visit the [{{site.data.keyword.cloud_notm}} Web App developer console](https://{DomainName}/developer/appservice) to get started.
{: tip}

##Overview screen
{: #overview_screen}

The Overview screen gives you content that is tailored to the topic or channel focus of the developer console in which you are working. From the overview screen you can see documentation, access learning resources, browse services, see featured starter kits, or link to a larger collection of starter kits. Click `Starter Kits` in the navigation to step into the Starter Kits view.

![Developer console Overview screen](images/overview_screen.png "Overview screen") <br> *Developer console Overview screen*

##Starter Kits view
{: #starter_kits_view}

The Starter Kits view shows the collection of starter kits specific to a use case area.  You can click various links on a starter kit card to see demonstrations and more information.  Select a starter kit to move to the Create New App view.

In some cases, selecting a starter kit takes you to more details about the starter kit.  If that is the case, simply click the `Create` button to move to the Create New App view.{: tip}

![Developer console Starter Kits view](images/starter_kits_view.png "Starter Kits view") <br> *Developer console Starter Kits view*

##Create New App view
{: #create_new_project_view}

From the Create New App view you name your app, provide deployment and routing information, and select a language.  Notice on the right you can also see the services that will automatically provision when you create your app along with pricing plans and terms for each.  Click `Create` to move to the App Details view.  If you aren't already logged in to {{site.data.keyword.cloud_notm}}, you need to do so at this point.

![Developer console Create New App view](images/create_new_project_view.png "Create New App view") <br> *Developer console Create New App view*

## App Details view
{: #project_details_view}

The App Details view displays list of services that are configured for your app. For each item in the list, you see the service name, links to other information, and an *actions* button with three vertically aligned dots. The *actions* button options are to remove service from app, open dashboard for service, and delete service. Please note that removing a service instance only removes the association to this app and doesn't delete the service instance.  Also, notice that service credentials are consolidated on this view so you don't have to visit each individual service instance views to get them.

![Developer console App Details view](images/project_details_view.png "App Details view") <br> *Developer console App Details view*

The App Details view also allows you to add new or existing services to your app that weren't part of the original starter kit. Click the `Add Resource` link in the service list box to do this.  The available services depend on the type of app and the services that are available in a region, so not all services are available to associate with all apps.

![Developer console Add Resource dialog](images/add_resource_dialog.png "Add Resource dialog") <br> *Developer console Add Resource dialog*

On the App Details view you have access to your code in two ways:

*  [Recommended] Click the `Deploy to Cloud` button to push your code to a repo and deploy your app to {{site.data.keyword.cloud_notm}}.  For more information about the {{site.data.keyword.cloud_notm}} DevOps toolchain, click [here](/docs/services/ContinuousDelivery/toolchains_about.html#toolchains_about).
*  For a quick look at your app code, select `Download Code` to produce and download the code for your app.

##App List view
{: #project_list_view}

You can see a list of all the apps you have created from the Apps List view.  You can rename or delete your apps from here. Click an app name row to return to the App Details view.

![Developer console App List view](images/project_list_view.png "App List view") <br> *Developer console App List view*
