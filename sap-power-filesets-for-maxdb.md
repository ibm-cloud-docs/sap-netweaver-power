---

copyright:
  years: 2020
lastupdated: "2020-08-12"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, provisioning, AIX, Db2, requirements

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:important: .important}

# SAP MaxDB  
{: #requirements_for_sap_maxdb}

Before you install SAP MaxDB, make sure that the required AIX filesets are installed.
{: shortdesc}

Run the following command:

```
lslpp -l | egrep -w 'bos.mp64|bos.rte.libc*|xlC.aix61.rte|xlC.sup.aix50.rte'
```
* bos.mp64 – Base Operating System 64-bit
* bos.rte.libc – libc Library
* xlC.aix61.rte	– IBM XL C++ Runtime for AIX 6.1
* xlC.sup.aix50.rte	– XL C/C++ Runtime for AIX 5.2
* bos.mp64 – Base Operating System 64-bit
* bos.rte.libc – libc Library

For more information about the required AIX filesets, see [SAP Note 720261 - System prerequisite AIX - liveCache/MaxDB 7.4-7.9](https://launchpad.support.sap.com/#/notes/720261){: external}.

I/O usage is intensive during the Software Provisioning Manager installation phase. If there isn't enough paging space to complete the Software Provisioning Manager MaxDB tasks, the stability of the system can be impacted. Before you install third-party tools, make sure that sufficient paging space is provisioned according to the third-party software manufacturer's space recommendations.
{: important}