---

copyright:
  years: 2020
lastupdated: "2020-08-12"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, LVM, logical volume, mount points, volume affinity

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

# Installing the system  
{: #installation_overview}

Before you install the system by using Software Provisioning Manager (SWPM), follow these preliminary steps:
{: shortdesc}

1. Create a user in the `smitty user` menu called `swpmuser` so you can avoid running the installation as the `root` user. If you didn't create a separate `rootgrp`, keep the primary group as `system`. Also include this user in the system and root groups so it is basically an administrative user. You will use this user when you start the Software Provisioning Manager tool as a Remote Access Tool user.

1. Create the following directory structure under your software repository mount point `/swrepo/SAP` for Software Provisioning Manager and other required software as recommended here: [Creating separate storage for a repository for Software Provisioning Manager and other required software](/docs/sap-netweaver-power?topic=sap-netweaver-power-storage_aix_lvm#storage_aix_swpm).

| Directory             | Purpose                                                      |
|-------------------------|--------------------------------------------------------------|
| `/swrepo/SAP/SWPM/`       | Location to unpack the Software Provisioning Manager SAR file                         |
| `/swrepo/SAP/SWPM/tmp`    | Temporary storage and cache for Software Provisioning Manager installation            |
| `/swrepo/SAP/kernel`      | Location for the SAP kernel files                            |
| `/swrepo/SAP/export`      | Location for the export files needed                         |
| `/swrepo/SAP/DB`         | Location for the database product and client software        |
| `/swrepo/SAP/others`      | Location for miscellaneous software such as saphostagent |
| `/swrepo/SAP/prereqcheck` | Location for the prerequisite check output                        |
{: caption="Table 1. Software repository directory structure" caption-side="top"}

