---

copyright:
  years: 2020
lastupdated: "2020-08-09"

keywords: SAP NetWeaver, SAP landscape, SAP Business Suite, SAP Business Warehouse, SAP BW

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:faq: .faq}
{:note: .note}

# Planning your system landscape
{: #planning-your-system-landscape}

An SAP *landscape* is a group of two or more SAP *systems* that usually include development, quality and test, and production. One SAP system consists of one or more *SAP instances*, which are a group of processes that are started and stopped at the same time. For more information about SAP landscapes, see
 * [SAP on Power Systems Best Practices Guide](https://www-03.ibm.com/support/techdocs/atsmastr.nsf/WebIndex/WP102618){: external} (click the link in the middle of the page)
 * [IBM Power Systems Virtualization Operation Management for SAP Applications](http://www.redbooks.ibm.com/abstracts/redp5579.html?Open){: external}
{: shortdesc}

There are several possible landscape configurations for a large number of SAP solutions in the market. These solutions include SAP NetWeaver-based products, such as [SAP Business Suite](https://open.sap.com/courses/suitehana1){: external}, SAP Business Warehouse, and all specific SAP add-ons, which the {{site.data.keyword.IBM}} {{site.data.keyword.powerSysShort}}s support. More solutions to keep in mind are any non-SAP NetWeaver-based SAP solutions and any third-party software that might integrate with SAP. Contact [SAP Support](https://support.sap.com/en/index.html){: external} if you’re planning to deploy non-SAP NetWeaver-based or third-party software in your IaaS landscape.

You want to be as detailed as possible when you determine the size of your server based on the applications you plan to run, potential growth, and performance. Additionally, keep in mind your storage and memory requirements for your applications. SAP systems in a landscape have specific requirements for connectivity, either among each other or to external systems. For more information, see [Items to consider when planning your SAP landscape](/docs/sap-netweaver-power?topic=sap-netweaver-power-considerations#considerations).

If you plan to migrate an on-premises SAP installation into the {{site.data.keyword.powerSys_notm}}s environment, make sure that you don't carry over existing performance issues. Run an up-to-date sizing report, and review a recent SAP Early Watch report of your SAP system. For more information, see [SAP EarlyWatch Alert](https://support.sap.com/en/offerings-programs/support-services/earlywatch-alert.html){: external} and [SAP Note 207223 - SAP EarlyWatch Alert Processed at SAP](https://launchpad.support.sap.com/#/notes/207223){: external}.

Table 1 contains the steps within the planning process. Use it to help build your target SAP landscape.

| Step | Details |
| --- | --- |
| 1 | [Items to consider when planning your SAP landscape](/docs/sap-netweaver-power?topic=sap-netweaver-power-considerations) |
| 2 | [Get SAP and {{site.data.keyword.cloud_notm}} credentials and create accounts](/docs/sap-netweaver-power?topic=sap-netweaver-power-get_sap_ibm_credentials#get_sap_ibm_credentials) |
| 3 | [Review any relevant SAP and {{site.data.keyword.cloud_notm}} documentation](/docs/sap-netweaver-power?topic=sap-netweaver-power-review_doc) |
| 4 | [Determine your SAP NetWeaver applications](/docs/sap-netweaver-power?topic=sap-netweaver-power-3-determining-your-sap-netweaver-applications) |
| 5 | [Determine your database management system](/docs/sap-netweaver-power?topic=sap-netweaver-power-determining-your-database-management-system)
| 6 | [Bring your SAP product license](/docs/sap-netweaver-power?topic=sap-netweaver-power-bring-your-own-sap-product-license)
| 7 | [Size the server](/docs/sap-netweaver-power?topic=sap-netweaver-power-size_the_server#size_the_server) |
| 8 | [Configure high availability](/docs/sap-netweaver-power?topic=sap-netweaver-power-ha_config) |
| 9 | [Determine your configuration](/docs/sap-netweaver-power?topic=sap-netweaver-power-determine_configuration#determine_configuration) |
{: caption="Table 1. Planning process overview" caption-side="top"}

## Next Steps
{: #planning-landscape-next-steps}

Select the appropriate step in Table 1 to begin planning your SAP landscape.
