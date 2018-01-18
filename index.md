---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# Creating apps in {{site.data.keyword.Bluemix_notm}}
{: #create}

In {{site.data.keyword.Bluemix}}, you can build enterprise-level mobile and web applications and take advantage of cloud extensions hosted by {{site.data.keyword.Bluemix_notm}}. You can use the {{site.data.keyword.Bluemix}} console and command line tools to build, run and deploy your apps. Follow this end-to-end development scenario to get started.

## Step 1: Sign up for an {{site.data.keyword.Bluemix_notm}} account
{: #sign-up}

Go to [bluemix.net](bluemix.net). Enter your email, name, company, region, phone number, and you're done. You don't need a credit card to sign up for a free account. Feel free to look around.

## Step 2: Look through the catalog
{: #catalog}

The {{site.data.keyword.Bluemix_notm}} catalog lists the infrastructure and platform resources it offers. You can start building your app by selecting a virtual machine, container, or Cloudant, a Cloud Foundry app. If you need platform resources, {{site.data.keyword.Bluemix_notm}} also offers boilerplates, which provide runtimes and other services to help you start building.

## Step 3: Create a resource
{: #resource}

1. In your [dashboard](https://console.bluemix.net/dashboard/apps/), click **Create resource**.

2. From the catalog, select an app from the Platform section. Then, choose your runtime. For example, you can choose an IBM runtime environment, such as Liberty for Java, which are supported by IBM buildpacks. You can also choose Community runtimes, such as Tomcat, which rely on open source and third-party buildpacks.

  * [Getting started with Containers](../containers/container_index.html)
  * [Getting started with Openwhisk](../openwhisk/index.html)
  * [Creating Cloud Foundry apps](../cfapps/index.html#creating_cloud_foundry_apps)

3. Enter your app name, hostname and choose your pricing plan.

4. Select your development style. You can edit your app in your preferred text editor and use the {{site.data.keyword.Bluemix_notm}} command line to deploy it to {{site.data.keyword.Bluemix_notm}}. You can also use {{site.data.keyword.Bluemix_notm}} DevOps Services to deploy your application from a browser or use Eclipse Tools for {{site.data.keyword.Bluemix_notm}} to work on applications in the Eclipse integrated development environment.

## Step 4: Start adding code
{: #code}

Each app comes with a getting started section that helps you get all the software and content you need to start working.

In your dashboard, click your app, and then click **Getting Started**, which can help you get the software you'll need to develop your app, point you to the source code, and help you deploy your app for the first time.

## Next steps
{: #next}

After your app is developed, use our [best practices](best-practice.html) and [cloud readiness](cloud-ready.html) guides to make sure your app is ready for {{site.data.keyword.Bluemix_notm}}. Then, [deploy](../starters/install_cli.html) your app.
