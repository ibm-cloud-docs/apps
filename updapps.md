---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-21"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creating and using a custom domain
{: #updatingapps}

You can use the command line or {{site.data.keyword.Bluemix}} Continuous Delivery to update the applications in {{site.data.keyword.Bluemix_notm}}. In many cases, even for the buildpacks such as Node.js, you must also supply a -c parameter to specify which command is used to start your application.
{:shortdesc}

Domains provide the URL route that is allocated to your organization in {{site.data.keyword.Bluemix_notm}}. To use a custom domain, you must register the custom domain on a public DNS server, configure the custom domain in {{site.data.keyword.Bluemix_notm}}, and then map the custom domain to the {{site.data.keyword.Bluemix_notm}} system domain on the public DNS server. After your custom domain is mapped to the system domain, requests for your custom domain are routed to your application in {{site.data.keyword.Bluemix_notm}}.

You can create and use a custom domain by using either the {{site.data.keyword.Bluemix_notm}} console or the command-line interface.

## Using the {{site.data.keyword.Bluemix_notm}} console

Complete the following steps to create a custom domain for your org by using the console:

1. Go to **Manage** > **Account** > **Cloud Foundry Orgs**.
2. Click the name of the org for which you're creating a custom domain.
3. Click the **Domains** tab.
4. Click **Add a domain**, and enter your domain name and select the region.
5. Confirm your updates. Click **Add**. 

As an example, you can use `*.mycompany.com` to associate the route `www.mybluemix.com` to your app. You can also use `example.mycompany.com` to associate the route `www.example.mybluemix.com` to your app.
{: tip}

Add the route with the custom domain to an application.

1. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) > **Dashboard**, then click the row for the application that you want to add the route to. The **Overview** page is displayed.
2. From the **Routes** menu, select **Edit Routes**.
3. Click **Add route**, and specify the route that you want to use for the application.
4. Confirm your updates by clicking **Save**.

## Using the {{site.data.keyword.Bluemix_notm}} command-line interface

1. Create a custom domain for your organization by typing the following command:

   ```
   bluemix app domain-create <your org name> mydomain
   ```

2. Add the route with the custom domain to an application. For CF apps, type the following command:

   ```
   bluemix app route-map myapp mydomain -n host_name

   ```

   For container groups, type the following command:

   ```
   cf ic route map -n host_name -d mydomain mycontainergroup

   ```

After you configure the custom domain in {{site.data.keyword.Bluemix_notm}}, map the custom domain to the {{site.data.keyword.Bluemix_notm}} system domain on your registered DNS server:

1. Set up a 'CNAME' record for the custom domain name on your DNS server. Steps for setting up the CNAME record vary depending on your DNS provider. For example, if you use GoDaddy, you follow the [Domains Help ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} guidance from GoDaddy.
2. Map the custom domain name to the secure endpoint for the {{site.data.keyword.Bluemix_notm}} region where your application is running. Use the following region endpoints to provide the URL route that is allocated to your organization in {{site.data.keyword.Bluemix_notm}}:

  * US-SOUTH: `secure.us-south.bluemix.net`
  * US-EAST: `secure.us-east.bluemix.net`
  * EU-DE: `secure.eu-de.bluemix.net`
  * EU-GB: `secure.eu-gb.bluemix.net`
  * AU-SYD: `secure.au-syd.bluemix.net`

In a browser or command-line interface, enter the following URL to access the myapp application:

```
http://host_name.mydomain

```

To remove an orphaned route, run the following command:

```
bluemix app route-delete domain -n hostname -f

```
{: tip}

`domain` is the name of your domain, and `hostname` is the host name of the route for your application. For more information about the **bluemix app route-delete** command, type `bluemix app route-delete -h`.

