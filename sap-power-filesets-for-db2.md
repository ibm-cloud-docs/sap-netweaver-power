---

copyright:
  years: 2020
lastupdated: "2020-08-11"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, provisioning, AIX, Db2, requirements

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Db2  
{: #requirements_for_db2}

Before you install IBM Db2, make sure that the system requirements are met.
{: shortdesc}

For the software requirements for Db2 and SAP, see [Installation of SAP Systems Based on the Application Server ABAP and DB2](https://help.sap.com/doc/4f95f7ac741a1014956dd879c2537334/CURRENT_VERSION/en-US/db6_inst_71x_unix_abap.pdf){: external}.

For dependencies and download details for Db2, see [System requirements for IBM Db2 for Linux, UNIX, and Windows](https://www.ibm.com/support/pages/node/612045){: external}.

The following additional filesets must be installed for Db2 installations:

* bos.adt.* – Base Application Development 
* bos.perf.* – Performance and diagnostics tools 
* perfagent.tools – Performance monitoring tools

You can run the following command to check whether the filesets are available:

```
lslpp -l |egrep -w 'bos.adt.base|bos.perf.libperfstat|bos.adt.lib| bos.adt.libm|bos.perf.perfstat|bos.perf.proctools'
```


