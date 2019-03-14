---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-14"

keywords: apps, custom domain, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creating and using a custom domain
{: #updatingapps}

Domains provide the URL route that is allocated to your organization in {{site.data.keyword.cloud}}. To use a custom domain, you must register the custom domain on a public DNS server, configure the custom domain in {{site.data.keyword.cloud_notm}}. Then, map the custom domain to the {{site.data.keyword.cloud_notm}} system domain on the public DNS server. After your custom domain is mapped to the system domain, requests for your custom domain are routed to your application in {{site.data.keyword.cloud_notm}}.
{:shortdesc}

You can create and use a custom domain by using either the {{site.data.keyword.cloud_notm}} console or the command-line interface.

## Using the {{site.data.keyword.cloud_notm}} console

Complete the following steps to create a custom domain for your org by using the console:

1. Go to **Manage > Account**, and select **Cloud Foundry orgs**.
2. Click the name of the org for which you're creating a custom domain.
3. Click the **Domains** tab.
4. Click **Add a domain**, and enter your domain name and select the region.
5. Confirm your updates. Click **Add**.

As an example, you can use `*.mycompany.com` to associate the route `www.mybluemix.com` to your app. You can also use `example.mycompany.com` to associate the route `www.example.mybluemix.com` to your app.
{: tip}

Add the route with the custom domain to an application.

1. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) > **resource list**, then click the row for the application that you want to add the route to. The Overview page is displayed.
2. Click the **Routes** menu, select **Edit Routes**.
3. Click **Add route**, and specify the route that you want to use for the application.
4. Confirm your updates by clicking **Save**.

## Using the {{site.data.keyword.cloud_notm}} command-line interface

1. Create a custom domain for your organization by typing the following command:
   ```
   ibmcloud app domain-create <your org name> mydomain
   ```

2. Add the route with the custom domain to an application. For Cloud Foundry apps, type the following command:
   ```
   ibmcloud app route-map myapp mydomain -n host_name
   ```

   For container groups, type the following command:
   ```
   cf ic route map -n host_name -d mydomain mycontainergroup
   ```

After you configure the custom domain in {{site.data.keyword.cloud_notm}}, map the custom domain to the {{site.data.keyword.cloud_notm}} system domain on your registered DNS server:

1. Set up a 'CNAME' record for the custom domain name on your DNS server. Steps for setting up the CNAME record vary depending on your DNS provider. For example, if you use GoDaddy, you follow the [Domains Help ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} guidance from GoDaddy.
2. Map the custom domain name to the secure endpoint for the {{site.data.keyword.cloud_notm}} region where your application is running. Use the following region endpoints to provide the URL route that is allocated to your organization in {{site.data.keyword.cloud_notm}}.

  * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
  * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

In a browser or command-line interface, enter the following URL to access the `myapp` application:
```
http://host_name.mydomain

```

To remove an orphaned route, run the following command:
```
ibmcloud app route-delete domain -n hostname -f
```
{: tip}

In that example, `domain` is the name of your domain, and `hostname` is the host name of the route for your application. For more information about the `ibmcloud app route-delete` command, enter the command `ibmcloud app route-delete -h`.
