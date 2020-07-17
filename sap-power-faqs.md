---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, {{site.data.keyword.Db2_on_Cloud_short}}, FAQs, VLAN, application server, SAP Certified, high availability, highly available

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# FAQs
{: #faqs}

## Which version of Db2 can I use to run SAP NetWeaver on {{site.data.keyword.powerSys_notm}}s?
{: faq}

Check [SAP Note 2855850](https://launchpad.support.sap.com/#/notes/2855850){: external} regularly and also reference [SAP Product Availability Matrix](https://support.sap.com/en/release-upgrade-maintenance.html#section_1969201630){: external}.

## Can I split my distributed SAP environment between different data centers?
{: faq}

For a distributed SAP installation, it's best to have all nodes in the same data center and VLAN segment. Deviations from this can yield latency and timeouts, which would render your SAP system unresponsive.

## Can I download the SAP distribution software directly from {{site.data.keyword.cloud_notm}}?
{: faq}

Currently, we don't have a direct link for SAP software downloads. You download the distribution DVDs just like you do today for an on-premises deployment. Access to SAPs Software Center is provided by using the network option that you selected; see [Network for management of an SAP system](/docs/sap-netweaver-power?topic=sap-netweaver-power-considerations#management-network).

## What are the operating system requirements for Db2, AIX and SAP NetWeaver?
{: faq}

For operating system requirements, see the following links:

[1780629 - AIX: Minimal OS Requirements for SAP Kernel](https://launchpad.support.sap.com/#/notes/1780629){: external}

[2267287 - Using SAP systems with AIX 7.2](https://launchpad.support.sap.com/#/notes/2267287){: external}

## For Oracle installs, I have to activate aioservers but it's missing in AIX 7x. Where is this setting?
{: faq}

The smit fast path is missing because the AIO server setting is automatically updated when the kernel extension notices that the aio sync operation is requested. You can view the main pages for `ioo` and the correct settings and command examples. For the required settings, see [Checking Asynchronous Input Output Processes AIX 64-Bit](https://docs.oracle.com/en/database/oracle/oracle-database/12.2/axdbi/checking-asynchronous-input-output-processes.html#GUID-2F121FA1-0A7F-48BB-95F2-1661D8046BDC){: external}.


## With an Oracle install, how do I activate the iocp device when it's "Defined"?
{: faq}

Use the smit menu with fast path command `smitty iocp => Change/Show Characteristics of I/O Completion Ports => STATE to be configured at system restart` and select **available**. This ensures that the device is available even after a system restart.

If you use the `mkdev -l iocp0` command on the command line, the devíce will be available only when the system is rebooted, and the device will show as **Defined** again. To ensure that this device is activated after a system restart, add the `-P` flag so the ODM is updated: `mkdev -l iocp0 -P`
{: note}

## When I run the Oracle installer precheck, failed items are listed. What should I do?
{: faq}

Part of the RUNINSTALLER function is to ensure that you complete the necessary pre-checks before you install the product. A common error is that you don't have enough free space in `/tmp`. If so, increase the amount of free space; Oracle 122 requires 5 GB of free space. Another common error is that you don't have 12 GB of paging space available. Defining enough paging space is not limited to extending the Paging Logical Volume hd6 in the volume group. You can also create a new paging space on a different volume by using smit mklv. When you see the LV type, specify paging. Normally when this occurs, a new paging space that is called paging00 is created on the hard disk you selected. When you finish and have more than 12 GB paging defined, go back to the Oracle INSTALLER and select rerun checks. No errors should be returned and you can proceed with the installation.

## Is there a Central SAP Note for installing NetWeaver on Oracle?
{: faq}

The following Central SAP Note provides hardware and storage requirements for Oracle and details the required file systems and mount points.

[2172935 - Installation - SAP Systems based on SAP NetWeaver: Oracle Database](https://launchpad.support.sap.com/#/notes/2172935){: external}

## Is there a Central SAP Note for using MaxDB for NetWeaver installations?
{: faq}

The following Central SAP Note for MaxDB outlines the installation and provides other useful information for MaxDB users:

[2365014 - Installation of SAP Systems Based on SAP NetWeaver: SAP MaxDB](https://launchpad.support.sap.com/#/notes/2365014){: external}


