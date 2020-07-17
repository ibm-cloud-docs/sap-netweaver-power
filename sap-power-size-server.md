---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: SAP NetWeaver, SAP Application Performance Standard, SAPS, SAP Quick Sizer

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# Sizing the server
{: #size_the_server}

After you decide which SAP solutions you plan to use, your next step is to determine the number of {{site.data.keyword.IBM}} {{site.data.keyword.powerSysShort}}s that you need to support your SAP landscape, and ensure that the servers are correctly sized.
{: shortdesc}

## Understanding the SAP sizing methodology
{: #size_method}

The SAP sizing methodology for SAP NetWeaver-centric applications is based on SAP benchmarks, such as information from SAP and actual customer experiences. The base SAP workload unit is an SAP Application Performance Standard (SAPS). The SAPS is a definition of throughput that is coined by SAP capacity planning and performance testing personnel. For example, 100 SAPS are defined as 2,000 fully business processed order-line items per hour in the standard SAP Sales and Distribution (SAP SD) application benchmark. This is equivalent to 2,400 SAP transactions per hour with the SAP Enterprise Resource Planning (SAP ERP) solution. The capability of processors is measured during the standard (SAP SD) benchmark test that is certified by SAP. For more information about the benchmark methodology, see [SAP Standard Application Benchmarks](https://www.sap.com/about/benchmark.html){: external}

## Using the SAP Quick Sizer
{: #quicksizer}

The [SAP Quick Sizer](https://www.sap.com/about/benchmark/sizing.quick-sizer.html#quick-sizer=){: external} is a web-based tool that is provided by SAP for all partners and customers. Sizing information is input directly into the tool, where it sizes SAP NetWeaver-based applications and non-SAP NetWeaver-based applications. Be sure to select the **Classic version** of the tool. SAP Quick Sizer requires an SAP S-user ID.

It calculates the workload (in SAPS) and adjusts it to allow for suitable processor use. So, if a workload of 4,800 SAP SD benchmark transactions per hour was required, the tool calculates this as 200 SAPS. If a target processor load of 33% is allowed, adjust this to find a processor capable of 600 SAPS at 100% (=200 at 33%).

While the sizing method might be considered conservative, consider the fact that the SAPS numbers for your servers were calculated based on highly tuned SAP systems running only specific SAP SD workloads. Depending on the type of SAP application, any custom configuration or custom coding in your system, your results might vary. Also, requirements for your project, such as proof-of-concept (PoC) or regarding performance and response time, might be different.

## Choosing a Power Systems Virtual Server
{: #choose_server}

After you determine your SAP applications and the SAPS numbers have been calculated through the SAP Quick Sizer, or based on your current landscape, you are ready to choose a server. Currently, E922 and E980 are the supported {{site.data.keyword.powerSys_notm}}s. For more information about the supported servers, see [SAP Note 2855850](https://launchpad.support.sap.com/#/notes/2855850){: external}.

## Mapping CPUs derived from SAPS to CPUs in a {{site.data.keyword.powerSys_notm}} environment
{: #mapping-cpus}

The SAPS result from the sizing and the choice of the server results in the number of CPUs that are required to support your workload.

When you create a {{site.data.keyword.powerSys_notm}} by using the {{site.data.keyword.cloud}} console, you select the number of CPUs of your server. For more information, see [Creating a {{site.data.keyword.powerSys_notm}}](/docs/power-iaas?topic=power-iaas-creating-power-virtual-server). For information about the pricing difference between CPU types, see [Pricing for Power Systems Virtual Servers on IBM Cloud](/docs/power-iaas?topic=power-iaas-pricing-virtual-server). For a description of the technical differences between dedicated, shared capped, and shared uncapped CPUs, see [this FAQ](/docs/power-iaas?topic=power-iaas-power-iaas-faqs#processor).

For **shared** processors, you choose the number of CPUs that the new server is entitled to use. This number should correspond to the number of CPUs that were the result of your sizing. The entitled CPUs should be sufficient for normal production operation and to cover workload during peak time. Don't count on additional CPUs that you might get out of the shared processor pool for uncapped processors.

For **dedicated** processors, the number of dedicated CPUs should correspond to the number of CPUs that were the result of your sizing.

For more information about shared and dedicated processors, see [Assigning the appropriate processor entitled capacity](https://www.ibm.com/support/pages/assigning-appropriate-processor-entitled-capacity).

## Migrating an existing SAP system
{: #migrating}

If you are planning to migrate an existing SAP system from any source to your {{site.data.keyword.cloud_notm}} environment, you can determine the SAPS numbers from the SAPS numbers of your current environment. Use the information on your current workload (the CPUs and RAM used) and get the SAPS equivalents for your CPU from the [SAP SD benchmark results](https://www.sap.com/about/benchmark.html){: external}.

## Next Steps
{: #size-server-next-steps}

 [Configure high availability](/docs/sap-netweaver-power?topic=sap-netweaver-power-ha_config)
 
 [Determining your configuration](/docs/sap-netweaver-power?topic=sap-netweaver-power-determine_configuration)
