---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, deployment, BYOL, database, {{site.data.keyword.powerSys_notm}}

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}

# Setting up your Power Systems Virtual Server instances
{: #set-up-power-infrastructure}

The guidance for setting up your SAP NetWeaver certified {{site.data.keyword.IBM}} {{site.data.keyword.powerSysShort}} colocated and connected with {{site.data.keyword.cloud}}, including data volume and operating system (OS), is in the following section.
{:shortdesc}

## Before you begin
{: #before-you-begin-provisioning}

Be sure to do the following before ordering your {{site.data.keyword.powerSys_notm}}:

 * Set up your [resource groups](/docs/resources?topic=resources-rgs) if you are setting up multiple servers for various purposes.
 * [Invite users](/docs/iam?topic=iam-getstarted) and determine what resources and resource groups they can access.
 * Select a version of the {{site.data.keyword.IBM_notm}} provided AIX stock images. The operating system version levels of the stock images are subject to change. You cannot use an existing AIX license for logical partitions (LPARs) in a {{site.data.keyword.powerSys_notm}} instance. For Linux&reg; images, you must use your own license. For more information, see [SAP Note 2855850](https://launchpad.support.sap.com/#/notes/2855850){: external}.


## Create your {{site.data.keyword.powerSys_notm}} service
{: order-server}

The {{site.data.keyword.cloud}} console requires a unique log-in ID, which is an {{site.data.keyword.IBM_notm}}id. Use the following steps to create your {{site.data.keyword.powerSys_notm}} service. Additional information can be found under [Creating a {{site.data.keyword.powerSys_notm}}](/docs/power-iaas?topic=power-iaas-creating-power-virtual-server).

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){: external} with your unique credentials.
1. Click **Create resource** > **Compute** > **Infrastructure** > **{{site.data.keyword.powerSys_notm}}**.
1. Select your **region** and **pricing plan**.
1. Enter a unique **Service name** and select your **Resource group**. You can also enter a **Tag** for your service.
1. Click **Create**. You are redirected to the Resource list for your account where you can see when your service was provisioned.

### Configure your Power Systems Virtual Server service
{: #configure-server}

Do the following steps to configure your {{site.data.keyword.powerSys_notm}} service.

1. Add an SSH key to securely connect to your {{site.data.keyword.powerSys_notm}}. For more information, see [Adding an SSH key](/docs/ssh-keys?topic=ssh-keys-adding-an-ssh-key).
1.	Configure the private network subnets that will be used for the SAP workload. For more information, see [Configuring and adding a private network subnet](/docs/power-iaas?topic=power-iaas-configuring-subnet).
1. Open a support ticket to connect your private networks to {{site.data.keyword.dl_full}} on classic connection. Provide information about the private network (network name, CIDR, colocation name) in the ticket.
1.	If required, create more management systems (for example, OS update server, time server, jump server).
1.	If required, configure {{site.data.keyword.dl_full}} to {{site.data.keyword.cloud}} classic or to on-premises networks.

## Create a new {{site.data.keyword.powerSys_notm}} instance
{: #configure-dedicated-server}

Use the following steps to create your new instance.

1. Highlight your provisioned service from the Resources list and click **New Instance**.
1. Enter a **Name**, which is a permanent or temporary name for your servers and enter the **Number of instances** to be provisioned. Be aware that additional options appear if you enter more than one instance. See [Creating a {{site.data.keyword.powerSys_notm}}](/docs/power-iaas?topic=power-iaas-creating-power-virtual-server) for option details.
1. Specify the **VM-pinning rule**. You can choose to soft pin or hard pin a virtual machine to the host where it is running. When you soft pin a virtual machine for high availability, PowerVC automatically migrates the virtual machine back to the original host when the host is back to its operating state. If the virtual machine has a licensing restriction with the host, the hard pin option restricts the movement of the virtual machine during maintenance. The hard pin option is not required for SAP NetWeaver workloads because the SAP license is bound to the virtual instance by a unique ID and not to the physical server. The default pinning policy is None. The recommended choice for {{site.data.keyword.powerSys_notm}}s hosting SAP workloads is soft pin.
1. Select your **SSH key**.
1. Under Profile, select  **Dedicated processor** or **Shared processor** and select your **Machine type**. Machine type determines the number of available cores and memory. For more information about each machine type, see [S922](https://www.ibm.com/support/knowledgecenter/en/POWER9/p9hdx/9009_22a_landing.htm){: external}, and [E980](https://www.ibm.com/us-en/marketplace/power-system-e980){: external}.
1. Use the slide to select the number of cores and GBs of memory. The **Total due per month** increases dynamically based on the number of cores and amount of memory you select.
1. Select AIX or “SLES for SAP (NetWeaver) – Client supplied subscription” as the **Operating system**, and a version of the {{site.data.keyword.IBM_notm}}-provided AIX or {{site.data.keyword.IBM_notm}} Power Linux stock image. {{site.data.keyword.IBM_notm}}i and operating system custom images are not supported at this time.

   * With AIX 7.1, only images at version 7100-05-05 or higher are supported for SAP.
   * With AIX 7.2, only images at version 7200-04-01 or higher are supported for SAP.
   * With SLES for SAP (NetWeaver) – Client supplied subscription, all the listed images are supported,

1. Under Profile, select Dedicated processor or Shared processor and select your Machine type. Machine type determines the number of available cores and memory. For more information about each machine type, see S922 and E980.
1. Use the slide to select the number of cores and GBs of memory. The Total due per month increases dynamically based on the number of cores and amount of memory you select.
1. You can either create **new storage volumes** or attach existing storage volumes that are already defined in your {{site.data.keyword.cloud_notm}} account. If you create a new volume, specify a unique name for the volume so you can identify it in the list of all volumes.
8. Select **Private networks** for communication between SAP instances. For more information, see [Configuring a private network](/docs/power-iaas?topic=power-iaas-configuring-subnet). Optionally, you can configure an additional public network, for example, to get OS updates over the internet.
1. Click **I have read and agree to the agreements listed below** and click **Create**.
1. The new instance becomes visible in the list of Virtual server instances with a status of **Creating** within minutes. When the Status is Active, can log in to the server (for example, by using SSH).

  After an AIX server becomes active, a console session is required for the initial setting of the root user password. Without completing this step, SSH login as 'root' appears disabled.
  {: important}

## Next Steps
{: #setting-up-infrastructure-next-steps}

You are now ready to begin Managing your {{site.data.keyword.powerSys_notm}}. See [Managing your SAP NetWeaver environment](/docs/sap-netweaver-power?topic=sap-netweaver-power-manage_environment) for your next steps.
