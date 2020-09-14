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

# Storage and the AIX Logical Volume Manager   
{: #storage_aix_lvm}

Follow these recommendations on creating storage and the AIX Logical Volume Manager (LVM) for the database and application layer.
{: shortdesc}

## Storage and volume affinity  
{: #storage_volume_affinity}

When you create storage by using the {{site.data.keyword.cloud}} console, specify volume affinity to prevent issues with new volume discovery on existing virtual server instances.

Keep the following points in mind:

* You can't mix Tier 1 and Tier 3 storage.
* After you provision storage with volume affinity, you can't go back and change it. Carefully plan your storage layer and make sure that your configuration is correct. 
* After you provision new volume, you can toggle bootable and sharing switches. Sharing is especially useful for an Oracle RAC implementation.

For more information about volume affinity, see [Ordering storage](/docs/sap-netweaver-power?topic=sap-netweaver-power-order_storage).

## Logical volumes and mount points  
{: #storage_aix_lvm_mount_points}

Be sure to follow the recommendations of third-party software vendors about the configuration of logical volumes and mount points for the filesystems. 

For more information, see the following links:

[Installation of SAP Systems Based on the Application Server ABAP of SAP NetWeaver with IBM DB2](https://help.sap.com/doc/4f95f7ac741a1014956dd879c2537334/CURRENT_VERSION/en-US/db6_inst_71x_unix_abap.pdf){: external}

[SAP Note 2172935 - Installation - SAP Systems based on SAP NetWeaver : Oracle Database](https://launchpad.support.sap.com/#/notes/2172935){: external}

[Directory and Filesystem Structure for MaxDB](https://maxdb.sap.com/doc/7_6/44/118d969c471a75e10000000a1553f6/content.htm){: external}

### More recommendations

* Create separate volume groups for database and applications. For example, for an Oracle installation, create the `oraclevg`. For SAP products, create the `appsvg` or `sapvg`, depending on the products that you choose to install.
* Allocate sufficient storage to each of the volume groups and follow a standard naming convention when you create logical volumes. Add your preferred SID to the logical volume name.

## Creating separate storage for an installation repository 
{: #storage_aix_swpm}

SAP Software Provisioning Manager requires additional files that will be used for the installation of SAP products such as exported images, SAP kernel files, and database clients.
The disk space requirements depend on the SAP product and database that you plan to install.

Calculate the sum of SAP packages on the [SAP Marketplace](https://support.sap.com/en/my-support/software-downloads.html){: external} that are required for your installation. Before you install SAP products by using Software Provisioning Manager, provide the required storage. 
Create a dedicated volume group and logical volume and mount it on `/swrepo/SAP`. 



