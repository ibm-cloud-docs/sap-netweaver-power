---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Configuring system access for SAP NetWeaver installation
{: #config_system_access}

Depending on your chosen network option, use the following information to configure access for your SAP NetWeaver installation.
{: shortdesc}

## IBM Power Systems Virtual Servers that host an SAP workload accessible through a virtual server on IBM Cloud
{: #host_sap_workload_vs}

1. [Create a virtual server](https://cloud.ibm.com/gen1/infrastructure/provision/vs?cm_sp=Cloud-Product-_-OnPageNav-IBMCloudPlatform_IBMVirtualMachines-_-VSI_Prod_Midpage) in {{site.data.keyword.cloud}} console.
  * Specify a private VLAN that is connected to the {{site.data.keyword.dlc_short}} connection.
  * When you configure [security groups](/docs/security-groups?topic=security-groups-getting-started), ensure that ports required for communication with the SAP workload are open.
 For more information about creating virtual servers (devices) in {{site.data.keyword.cloud}}, see [Getting started with virtual servers](/docs/virtual-servers?topic=virtual-servers-getting-started-tutorial).
2. Specify routing between servers in {{site.data.keyword.cloud}} and {{site.data.keyword.powerSysShort}}s:
  * On the server in {{site.data.keyword.cloud}}, add a route to the gateway of the private subnet connected to the {{site.data.keyword.IBM}} {{site.data.keyword.powerSysShort}}s.
  * On {{site.data.keyword.powerSys_notm}}s, add a route to the gateway of the private subnet connected to the server in {{site.data.keyword.cloud}}.

## IBM Power Systems Virtual Servers that host an SAP workload connected to on-premises networks

* Specify routing between servers in the on-premises network and {{site.data.keyword.powerSys_notm}}s:
  * On servers in the on-premises network, add a route to the gateway of the private subnet connected to the {{site.data.keyword.powerSys_notm}}s.
  * On {{site.data.keyword.powerSys_notm}}s, add a route to the gateway of the on-premises networks.

## Next Steps
{: #config_system_access_next_steps}

[Ordering storage](/docs/sap-netweaver-power?topic=sap-netweaver-power-order_storage)

[Downloading and installing SAP software and applications](/docs/sap-netweaver-power?topic=sap-netweaver-power-install_sap)

[Creating an SAP license key](/docs/sap-netweaver-power?topic=sap-netweaver-power-create-key)

[Monitoring your system with SAP tools](/docs/sap-netweaver-power?topic=sap-netweaver-power-monitoring)
