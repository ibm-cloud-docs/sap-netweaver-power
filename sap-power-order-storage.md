---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: SAP NetWeaver, {{site.data.keyword.blockstorageshort}}, {{site.data.keyword.filestorage_full_notm}}, {{site.data.keyword.cloud_notm}}, {{site.data.keyword.powerSys_notm}}

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering storage
{: #order_storage}

A 20 GB boot disk is automatically created when you provision a new {{site.data.keyword.IBM}} {{site.data.keyword.powerSysShort}} with AIX. The size of the Linux&reg; root volume is 100 GB. If you need more space for the root volume group, create a new storage volume and attach it to the virtual server instance. Next, rescan for the new devices and extend the root volume group with the new disk in the operating system.
{: shortdesc}

Use the following steps to add a storage volume.

1. Click **New volume**.
2. Enter the **Name**, **Type**, and **Size** of the storage volume. You can also select whether to make it **Shareable** and set an **Affinity policy**.

  Specify a unique name for the volume so you can identify it in the list of all volumes.
  {: tip} 

1. Select **Affinity** for the **Affinity policy** and specify the boot disk as the **Affinity volume**. Specifying an affinity policy ensures that the new storage will be available in the list to attach to your virtual server instance. By identifying the boot disk as the affinity volume, your volumes are on the same backbone storage.

   Mixing storage tiers is not supported. If you have a virtual server instance that uses Tier 1, you cannot define Tier 3 disks.
   {: important}

2. Agree to the **Service Agreement** and **Terms and Conditions**, then click **Create Storage Volume**.
3. Go to the Storage Volume overview to see your new volume listed.
4. Attach the new volume to your virtual server instance by selecting your instance in the list of Attached Volumes, then click **Manage Existing**. Select the volume that you created and click **Finish**.  

  **Linux:** If you attached new volumes to your Linux OS, you must run a SCSI scan or restart the operating system (OS).<br>
  
  **AIX:** Run the `cfgmgr` command. Server restart isn't necessary. To get the disk overview, run `lsdev -Cc disk`.

1. Extend your existing file systems or create a new one with Logical Volume Manager (LVM). For more information, see the following links:
    * [Adding storage for the rootvg during AIX server provisioning](/docs/sap-netweaver-power?topic=sap-netweaver-power-adding_storage)
    * [Extending /tmp](/docs/sap-netweaver-power?topic=sap-netweaver-power-extending_tmp)
    * [Extending or adding paging space](/docs/sap-netweaver-power?topic=sap-netweaver-power-extending_paging_space)
    * [Storage and the AIX Logical Volume Manager](/docs/sap-netweaver-power?topic=sap-netweaver-power-storage_aix_lvm)

If you'd like to attach or detach a volume, click **Manage existing volumes** and select the volume. You can also change the boot status of a volume by clicking the **Bootable** toggle.

## Next Steps
{: #order-storage-next-steps}

[Downloading and installing SAP software and applications](/docs/sap-netweaver-power?topic=sap-netweaver-power-install_sap)

[Creating an SAP license key](/docs/sap-netweaver-power?topic=sap-netweaver-power-create-key)

[Monitoring your system with SAP tools](/docs/sap-netweaver-power?topic=sap-netweaver-power-monitoring)
