---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: power systems, infrastructure as a service, multiple virtual servers, hybrid cloud environment, Linux, aix

subcollection: sap-netweaver-power

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}

# What is a Power Systems Virtual Server?
{: #about-virtual-server}

{{site.data.keyword.powerSys_notm}}s, also known as logical partitions (LPAR), run on IBM Power Systems hardware with the PowerVM hypervisor.
{:shortdesc}

{{site.data.keyword.powerSys_notm}}s are a form of infrastructure as a service (IaaS). With the {{site.data.keyword.powerSys_notm}} service, you can quickly create and deploy one or more virtual servers that are running either the AIX or Linux&reg; operating systems. After you provision the virtual server, it is your responsibility to make sure that your operating system is secure.

Current AIX and Linux clients can use the {{site.data.keyword.powerSys_notm}} service for a number of workload scenarios, including disaster recovery, development environments, and partial IT infrastructure moves. {{site.data.keyword.powerSys_notm}} clients can stay competitive with the scaling of their infrastructure and remain flexible with their workload management and capacity both on- and off-premise. And since the infrastructure layer is identical, system administrators who run on-premises AIX or Linux systems today can use their same tools, workflows, and enhancements in the cloud.

## Key features
{: #key-features}

The following are some of the key features for the {{site.data.keyword.powerSys_notm}} service.

### Straightforward billing
{: #straightforward-billing}

The {{site.data.keyword.powerSys_notm}} service uses a monthly billing rate that includes the licenses for the AIX operating systems. The monthly billing rate is pro-rated by the hour based on the resources that are deployed to the {{site.data.keyword.powerSys_notm}} instance for the month. When you create the {{site.data.keyword.powerSys_notm}} instance, you can see the total cost for your configuration based on the options that you specify. You can quickly identify the configuration options that provide you with the best value for your business needs. For more information, see [Pricing](/docs/power-iaas?topic=power-iaas-pricing-virtual-server#pricing-virtual-server).

{{site.data.keyword.IBM_notm}} PowerLinux clients can use their own licenses for the operating systems images that are provided by {{site.data.keyword.IBM_notm}} [bring your own license (BYOL)]. With BYOL, clients can reuse their licenses in the {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}} environment without any additional costs.

### Hybrid cloud environment
{: #hybrid-cloud}

You can use the {{site.data.keyword.powerSys_notm}} service to run any AIX or Linux workloads off-premise from your existing Power Systems hardware infrastructure. By running your workloads in {{site.data.keyword.powerSys_notm}}s, you can enjoy all of the advantages the cloud has to offer such as self-service, fast delivery, elasticity, and connectivity to other {{site.data.keyword.cloud}} services. Although your AIX and Linux workloads are running in {{site.data.keyword.powerSys_notm}}s, you still keep the same scalable, resilient, production-ready features that Power Systems hardware is known to provide.

### Infrastructure customization
{: #infra-customization}

You can configure and customize the following options when you create a {{site.data.keyword.powerSys_notm}}:

* Number of virtual server instances
* Number of cores
* Amount of memory
* Data volume size and type
* Network interfaces

## Hardware specifications
{: #hardware-specifications}

The following IBM Power Systems can host an SAP workload on {{site.data.keyword.powerSys_notm}}: IBM Power System S922 (9009-22A) and IBM Power System E980 (9080-M9S). For more information about these systems and how they're used inside the {{site.data.keyword.powerSys_notm}} service, see their data sheets and the hardware overview table.

If you'd like to compare your current environment's performance to what's available through the {{site.data.keyword.powerSys_notm}} service, see the [IBM Power Systems performance report](https://www.ibm.com/downloads/cas/K90RQOW8){: external}. For a more condensed comparison, see the [IBM Power Systems CPW performance data comparison](https://www.itechsol.com/wp-content/uploads/2018/07/IBM-Power-Systems-CPW-Performance-Data-Comparison-P7-vs-P8-vs-P9-rev3-July-2018.pdf){: external}.
{: tip}

**Data sheets**

* [IBM Power System S922 (9009-22A)](https://www.ibm.com/downloads/cas/KQ4BOJ3N){: external}
* [IBM Power System E980 (9080-M9S)](https://www.ibm.com/downloads/cas/VX0AM0EP){: external}

| Compute  | Storage   | Network   |
|--------- | --------- | --------- |
|<ul><li>Power e980 (9080-M9S)</li><li>Power s922 (9009-22A)</li></ul> | <ul><li>Storwize V7000F(2076-AF6) dual controller</li><li>Storwize V7000 (2076-624) dual controller </li><li>IBM SAN64B-6 (Brocade)</li></ul> | <ul><li>Cisco Nexus9000 93180YC-EX (10G)</li><li>Cisco Nexus9000 C9348GC-FXP (1G)</li><li>Avocent ACS8048</li></ul> |
{: class="simple-tab-table"}
{: tab-group="hardware"}
{: caption="Table 1. Hardware overview" caption-side="top"}
{: #hw-spec-1}
{: tab-title="Washington, D.C. (WDC04), Dallas (DAL13), Frankfurt and London (FRA04/FRA05/LON06)"}
