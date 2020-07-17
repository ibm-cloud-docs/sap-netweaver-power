---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, SAP-certified {{site.data.keyword.powerSys_notm}}, {{site.data.keyword.powerSysShort}}, {{site.data.keyword.powerSys_notm}}

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Getting started with SAP NetWeaver on IBM Power Systems Virtual Servers
{: #getting-started}

{{site.data.keyword.IBM}} and SAP continue a collaboration since the early 1970s in multiple areas, including hardware, software, cloud, services, and finance. They are now collaborating to run SAP NetWeaver-based applications on {{site.data.keyword.IBM}} {{site.data.keyword.powerSysShort}} colocated and connected with {{site.data.keyword.cloud}}.
{: shortdesc}

This content provides you with recommendations for the provisioning and installation of the infrastructure to support SAP NetWeaver-based SAP products and subscription on {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}}s. It does not replace any SAP NetWeaver implementation-related documentation. Its purpose is to help you with infrastructure planning and provisioning so you can begin your SAP installation. The SAP installation (including database installation) does not vary from installations for on-premises environments. Recommendations and guidelines are provided to help you operate your SAP system in the {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}} environment.

## Before you begin
{: #before-you-begin-getting-started}

Table 1 contains information that will help you with your implementation.

| Task | Details |
| ----- | ----- |
| Read {{site.data.keyword.cloud}} and SAP content that is related to your implementation | * [What is {{site.data.keyword.cloud}}](https://www.ibm.com/cloud) |
| | * [Get started with {{site.data.keyword.cloud}}](https://www.ibm.com/cloud/get-started) |
| | * [SAP workloads on {{site.data.keyword.cloud}}](https://www.ibm.com/cloud/sap/certified-infrastructure)|
| You might also find the following SAP documentation useful: | * [How to create an SAP S-user ID](https://www.youtube.com/watch?v=4wICiRTP8u0/) Only super administrators or S-users with the required authorization are allowed to create S-user IDs. |
| | * [SAP NetWeaver Help](https://help.sap.com/viewer/product/SAP_NETWEAVER/ALL/en-US) |
| | * [SAP Notes through SAP Support](https://support.sap.com/en/index.html) |
| Sign up for {{site.data.keyword.cloud}} | [Signing up for {{site.data.keyword.cloud}}](/docs/account/adminpublic.html#signing-up-for-ibm-cloud) |
| Access the {{site.data.keyword.cloud}} console | [{{site.data.keyword.cloud}} console](https://cloud.ibm.com) is your graphical gateway to all your infrastructure components-compute, networking, and storage. You need an [IBMid and password](/docs/account?topic=account-signup) to access the console. |
| Invite users to your account and manage their access | IBM Identity and Access Management (IAM) service is used to set up your users and grant them access to based on their roles. See [Getting started with IAM tutorial](/docs/iam?topic=iam-getstarted) and [Best practices for assigning access](/docs/iam?topic=iam-account_setup) set up your users and grant them system access. |
| Create resource groups | A **resource** is anything that you can create from the catalog that is managed by and contained within a **resource** group. See [Creating and managing resource groups](/docs/resources?topic=resources-rgs) and [Best practices for organizing resources in a resource group](/docs/resources?topic=resources-bp_resourcegroups).
{: caption="Table 1. Before you begin steps" caption-side="top"}

## Terminology
{: #terminology}

Before you create a virtual server, you must understand the terminology that is associated with a {{site.data.keyword.powerSys_notm}}.

### {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}} colocated and connected with {{site.data.keyword.cloud_notm}} versus classic infrastructure
{: #cloud-vs-classic}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}}s are located in the same data centers as the Intel-based {{site.data.keyword.cloud_notm}} servers, which are referred to as {{site.data.keyword.cloud}} classic infrastructure. In the data centers, the {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}}s are separated from the rest of the {{site.data.keyword.cloud_notm}} servers in separate rooms (colocated) with separate networks and separate Fibre Channel attached storage. There are predefined connections to the {{site.data.keyword.cloud_notm}} so that {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}}s are accessible through the internet. The internal networks are fenced and might be connected to the outside (classic infrastructure or on-premises environments) through {{site.data.keyword.dlc_full}}. In the following content, if {{site.data.keyword.cloud_notm}} is referenced in the context of {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}}s, then it is always meant as {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}}s colocated and connected with {{site.data.keyword.cloud_notm}}.

### Resource versus resource group
{: resource-versus-group}

A **resource**, for the context of {{site.data.keyword.powerSys_notm}} is not a user, it's anything that you can create from the catalog. For example, a {{site.data.keyword.powerSys_notm}}. A **resource group** contains multiple resources, for example, a set of servers used strictly for development activities. For more information, see [What is a resource?](/docs/resources?topic=resources-resource).

### Service versus instance
{: #service-versus-instance}

There is difference between a {{site.data.keyword.powerSys_notm}} **service** and a {{site.data.keyword.powerSys_notm}} **instance**. Think of the {{site.data.keyword.powerSys_notm}} **service** as a container for all {{site.data.keyword.powerSys_notm}} **instances** at a specific geographic location. The {{site.data.keyword.powerSys_notm}} **service** is available from the **Resource list** in the {{site.data.keyword.cloud}} UI. The service can contain multiple {{site.data.keyword.powerSys_notm}} **instances**.

For example, you can have two {{site.data.keyword.powerSys_notm}} **services**, one in Dallas and another in Washington DC. Each service can contain multiple {{site.data.keyword.powerSys_notm}} **instances**. For more information, see [Getting started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.powerSys_notm}}](/docs/power-iaas?topic=power-iaas-getting-started).

All instances of an SAP system must run in the same service. Multiple systems can be distributed through different services, in which case IT operations must ensure that latency is acceptable for their scenarios.
{: note}

### Dedicated versus shared processor
{: #dedicated-shared}

For descriptions of dedicated and shared processors, [click here](/docs/power-iaas?topic=power-iaas-power-iaas-faqs#processor). Depending on the SAP workload, supported processor options are restricted. For more information, see [SAP Note 2855850](https://launchpad.support.sap.com/#/notes/2855850){: external}.

## Implementing SAP NetWeaver on {{site.data.keyword.powerSys_notm}}

Table 2 contains steps to help you get your {{site.data.keyword.powerSys_notm}} infrastructure quickly built.

| Task | Details |
| ----- | ----- |
| Plan your landscape | Use the information in [Planning your system landscape](/docs/sap-netweaver-power?topic=sap-netweaver-power-planning-your-system-landscape) to architect, size, and provision your IBM Power Systems Virtual Server environment to support your SAP NetWeaver workload. |
| Provision your system | Use the steps and information in [Setting up your Power Systems Virtual Server instances](/docs/sap-netweaver-power?topic=sap-netweaver-power-set-up-power-infrastructure) to set up your IBM Power Systems Virtual Server infrastructure. |
| Install SAP NetWeaver | You install the SAP NetWeaver software on your IBM Power Systems Virtual Server infrastructure as if the servers were on-premises. For more information about installing SAP NetWeaver, see [Downloading and installing SAP software and applications](/docs/sap-netweaver-power?topic=sap-netweaver-power-install_sap) for more information. |
{: caption="Table 2. Steps to get up and running quickly" caption-side="top"}