---

copyright:
   years: 2021
lastupdated: "2021-12-16"

keywords: apps, tutorial, deploy to ibm cloud, cluster deployment, devops toolchain, delivery pipeline, reference architecture, terraform, schematics, satellite, quick start

subcollection: apps

content-type: tutorial
services: schematics, terraform, openshift, containers
account-plan: paid
deployable: quickstart
completion-time: 1.5h

---

{:shortdesc: .shortdesc}
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:term: .term}
{:external: target="_blank" .external}
{:step: data-tutorial-type='step'}

# Creating an {{site.data.keyword.satellitelong_notm}} environment on AWS by using scripts
{: #tutorial-trysat}
{: toc-content-type="tutorial"}
{: toc-completion-time="1.5h"}

This tutorial and set of scripts provide a mostly automated way to set up an {{site.data.keyword.satellitelong_notm}} location and Red Hat OpenShift cluster on Amazon Web Services (AWS). This is not a production-ready solution, but it provides a useful tool for proof-of-concepts, learning, and experimenting.
{: shortdesc}

{{site.data.keyword.satellitelong}} is a managed distributed cloud solution that allows you to run parts of {{site.data.keyword.cloud}} with managed services in your data center or other public clouds. To learn more about {{site.data.keyword.satelliteshort}}, see the [{{site.data.keyword.satellitelong_notm}} product page](https://www.ibm.com/cloud/satellite){: external}.

The scripts expect a Unix-like environment and work on MacOS or Linux&trade;. The scripts are likely to work on Windows&trade; Subsystem for Linux (WSL), but this scenario is not tested.

This solution is not an officially supported IBM product; any support is on an unofficial, best-effort basis only. For more information, see the [MIT license](https://github.com/ibm-garage/try-sat-aws/blob/master/LICENSE.txt){: external}. This solution is not fully evaluated from a security, robustness, or any other nonfunctional perspective. The cluster that is created is public. Therefore, do not put anything sensitive on this cluster or location. If you plan to keep the location or cluster long term, you are responsible for reviewing the security of the infrastructure. Be sure to destroy the location or cluster when you no longer need it to minimize the possibility of attacks. You are responsible for costs that you incur on {{site.data.keyword.cloud_notm}} or AWS.
{: important}

## Before you begin
{: #trysat-prereqs}

* To complete this tutorial, use a [Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account](/docs/account?topic=account-upgrading-account) where you are the owner or have [full Administrator access](/docs/account?topic=account-assign-access-resources). If you already have an {{site.data.keyword.cloud_notm}} account and need to upgrade it, see [Upgrading your account](/docs/account?topic=account-upgrading-account). Your {{site.data.keyword.satelliteshort}} location is managed from this account.
* [Install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started) if you want to interact with elements of the toolchain or infrastructure after they are created.
* Install [GNU Make](https://www.gnu.org/software/make/){: external}. If you have a Linux system, it is likely that you already have this tool. If you have MacOS, ensure that [Homebrew](https://brew.sh/){: external} is installed, and then install GNU Make by using the `brew install make` command. You must run `make` by using `gmake`, not `make`). If you have WSL, you probably have GNU Make already.
* You must have a GitHub account.
* Clone this [try-sat-aws Git repository](https://github.com/ibm-garage/try-sat-aws){: external} somewhere locally. Then, inside the repository directory, run `make install` (or `gmake install` on MacOS) to ensure that the necessary {{site.data.keyword.cloud_notm}} CLI plug-ins are installed.
* You must have an AWS account. This is where the virtual machines for your {{site.data.keyword.satelliteshort}} location are created and where they run.
* Optional. Install [direnv](https://direnv.net/){: external}. This makes it easier to use `.envrc`.
* Optional. Install the [AWS CLI](https://aws.amazon.com/cli/){: external}. If you install and configure this CLI, you can use the `set-env` script to simplify the process of configuration later.
* Optional. Be familiar with [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-about-schematics).

## Create the AWS location
{: #trysat-create-location}
{: step}

1. Create the {{site.data.keyword.satelliteshort}} location on AWS. A prebuilt 'template' is available in the {{site.data.keyword.cloud_notm}} console that creates the necessary resources on AWS, including virtual machines, together with creating the location in {{site.data.keyword.cloud_notm}} and attaching those virtual machines to {{site.data.keyword.cloud_notm}} to form the location.

   For information about creating the {{site.data.keyword.satelliteshort}} location on AWS, see [Automating your AWS location setup with a Schematics template](/docs/satellite?topic=satellite-aws). You can keep most of the settings at the default values, but pay attention specifically to the following settings when you create the location:
      * Ensure that you set the AWS region for where you want the resources to be created.
      * You might want to change the name of the {{site.data.keyword.satelliteshort}} location to something more    easy-to-remember, for example `try-sat-1`.
      * You might want to change the resource group for the {{site.data.keyword.satelliteshort}} location to suit your {{site.data.keyword.cloud_notm}} account.
   
1. Track the creation of your AWS location by using the [{{site.data.keyword.bpshort}} workspace](https://{DomainName}/schematics/workspaces){: external}.
   1. From the {{site.data.keyword.satelliteshort}} console, select **Manage in Schematics**.
   1. From the {{site.data.keyword.bpshort}} console, click the name of your workspace.
   1. Select **Jobs** from the navigation pane, and then find the current job row, and click **View log** to review the log details.
   1. Wait for the {{site.data.keyword.bpshort}} job to finish and the workspace to enter an `Active` state.
   1. Ensure that your AWS location is in the 'Normal' state before you proceed.

For more information about {{site.data.keyword.bpshort}} locations, see [Locations and service endpoints](/docs/schematics?topic=schematics-locations).

### Resources created by the template
{: #trysat-resources}

The following resources are created by the template in your AWS cloud account.

- 1 virtual private cloud (VPC).
- 1 subnet for each of the 3 zones in the region.
- 1 security group to meet the host networking requirements for {{site.data.keyword.satelliteshort}}.
- 6 EC2 instances spread evenly across zones, or the number of hosts that you specified.

The following resources are created by the template in your {{site.data.keyword.cloud_notm}} account.

- 1 {{site.data.keyword.satelliteshort}} location.
- 3 {{site.data.keyword.satelliteshort}} hosts that represent the EC2 instances in AWS, attached to the location and assigned to the {{site.data.keyword.satelliteshort}} location control plane.
- 3 {{site.data.keyword.satelliteshort}} hosts that represent the EC2 instances in AWS, attached to the location, unassigned, and available to use for services like an {{site.data.keyword.openshiftshort}} cluster. If you added more than 6 hosts, the number of hosts equals the number that you specified minus the three that are assigned to the control plane.

Check out the actual [Terraform code](https://github.com/terraform-ibm-modules/terraform-ibm-satellite/releases/tag/v1.0.2){: external} that was used to create the resources.

### Security considerations
{: #trysat-security-considerations}

The AWS resources are created with relatively open security groups, and the EC2 instances are assigned public IP addresses. This might not be suitable for scenarios other than a quick proof-of-concept or a demo. Changing the security group and removing IP addresses affect the {{site.data.keyword.satelliteshort}} and Red Hat OpenShift operations and might make the cluster inoperable. Be aware of the following considerations:

- The AWS EC2 hosts that are in the {{site.data.keyword.satelliteshort}} location have public IP addresses and are accessible from the public network.
- TCP Ports 80 and 443 of the cluster nodes and control plane nodes are open for connections from any IP address. Port 443 is used for Red Hat&reg; OpenShift&reg; console access over HTTPS.
- Port range 30000-32767 is open for TCP/UDP connection from any IP address for {{site.data.keyword.satelliteshort}} internal connection and management.
- SSH access to the hosts is not available from outside, and the SSH access with root user ID is locked. However,  other user accounts might be enabled for connections from within the VPC.

## Create the Red Hat OpenShift cluster, attach the workers, and fix the DNS
{: #trysat-create-cluster}
{: step}

1. Inside your clone of the repository, copy the file `.envrc-template` to `.envrc.`
1. Complete each of the templated environment variables. Follow the instructions that are included within the file.
1. If you are not using `direnv`, type `source .envrc` to load `.envrc` into your terminal's environment.
1. Run `make all` (or `gmake all` on MacOS). This command creates the Red Hat OpenShift cluster, attaches the worker node VMs, and configures networking so that the cluster is publicly accessible.
1. Scroll past any messages, even if they are error messages.

The entire process takes approximately one hour. If the process takes significantly longer, or if you see any repeated persistent errors, [submit an issue on this repository](https://github.com/ibm-garage/try-sat-aws){: external}.

## Next steps
{: #trysat-next-steps}

For more information about how to access your cluster, see [Accessing OpenShift clusters](/docs/openshift?topic=openshift-access_cluster#access_cluster_sat). The process in this tutorial publicly exposed your cluster, so you do not need to complete the steps in [Accessing clusters through the public cloud service endpoint](/docs/openshift?topic=openshift-access_cluster#access_public_se).

At this point, you can do any of the following actions:

- Log in to the Red Hat OpenShift web console by using the {{site.data.keyword.cloud_notm}} console. In the console, select **OpenShift** > **Clusters** > select your cluster > **OpenShift Web Console**.
- Connect to Red Hat OpenShift on the command line by:
    - [Logging in to {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login) by using the {{site.data.keyword.cloud_notm}} CLI. You can do this by running `make login_ibmcloud` (inside this repository).
    - [Getting the cluster configuration](/docs/openshift?topic=openshift-kubernetes-service-cli#cs_cluster_config) by using the {{site.data.keyword.cloud_notm}} CLI. You can do this by running `make get_cluster_config` (inside this repository).
    - Logging in to Red Hat OpenShift by running `make login_cluster` (inside this repository).

## Cleanup
{: #trysat-cleanup}

There is no fully documented or automated cleanup process yet. However, you can try these options:

- Destroy the resources that are in the {{site.data.keyword.bpshort}} workspace that is associated with your location. Destroying the resources deletes the location and the AWS EC2 virtual machines. Be sure to double-check this in the AWS console. For more information, see [Deleting a workspace](/docs/schematics?topic=schematics-workspace-setup&interface=ui#del-workspace).
- You might want to remove the cluster from your {{site.data.keyword.cloud_notm}} console. For more information, see [Removing clusters](/docs/openshift?topic=openshift-remove).
