---

copyright:
  years: 2020
lastupdated: "2020-08-11"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, provisioning, AIX, Oracle, filesets

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Oracle Database products  
{: #filesets_for_oracle}

Before you install Oracle Database products, make sure that the required filesets are installed.
{: shortdesc}

## Oracle 12 on AIX IBM Power Systems
{: #oracle_12_filesets}

Oracle 12 is supported on AIX 7.1 and 7.2. For a list of required operating system filesets and APARs, see the [system requirements](https://docs.oracle.com/en/database/oracle/oracle-database/12.2/axdbi/operating-system-requirements-for-ibm-aix-on-power-systems-64-bit.html#GUID-265A2566-3693-4285-A514-5AB81DF91A85){: external}.

Run the following command to check whether the filesets are available:

```
lslpp -l |egrep -w 'bos.adt.base|bos.perf.libperfstat|bos.adt.lib| bos.adt.libm|bos.perf.perfstat|bos.perf.proctools|xlC.aix61.rte|xlC.rte'
```

## Oracle 19 on AIX IBM Power Systems
{: #oracle_19_filesets}

Oracle 19 is supported on AIX 7.1 and 7.2.

For a list of operating system filesets and APARs, see the [system requirements](https://docs.oracle.com/en/database/oracle/oracle-database/19/axdbi/operating-system-requirements-for-ibm-aix-on-power-systems-64-bit.html#GUID-265A2566-3693-4285-A514-5AB81DF91A85){: external}.

