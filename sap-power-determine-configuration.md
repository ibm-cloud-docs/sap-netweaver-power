---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, RDBMS, SAP Application Performance Standards, SAPS, SAP Certified, database

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}

# Determining your configuration
{: #determine_configuration}

It's important to design your SAP stack configuration, deployment, and database, for example, SAP HANA. With an SAP NetWeaver system, you have two deployment options:
  * Central system, which is a single-host installation (two-tier)
  * Distributed system, which is a multi-host installation (three-tier)

The options influence your server choice. You might want to distribute your workload to different servers or keep the workload on one server for simplicity. For more information, see [Setting up your {{site.data.keyword.powerSys_notm}}](/docs/sap-netweaver-power?topic=sap-netweaver-power-set-up-power-infrastructure).
{:shortdesc}

## Network configuration
{: #network-config}

Ensure that you have a working network Direct Link connection between the {{site.data.keyword.IBM}} {{site.data.keyword.powerSysShort}} data centers and {{site.data.keyword.cloud}} or your on-premises networks. This connection is required for management and for access to your SAP applications. For more information, see [Ordering Direct Link Connect on classic](/docs/power-iaas?topic=power-iaas-ordering-direct-link-connect).

## Storage configuration
{: #storage_config}

Keep the following points in the mind when you create new storage volumes:
  * Tier 1 and Tier 3 storage cannot be mixed.
  * After you provision your storage with Affinity, you can't change it. Carefully plan your storage layer and make sure that your configuration is correct. Affinity is highly advised to prevent issues with new volume discovery on existing virtual server instances.
  * After your new volumes are provisioned, you can toggle bootable and sharing switches.
{: important}

For {{site.data.keyword.powerSys_notm}}s for SAP HANA sample storage configurations, see [SAP HANA Determining your configuration](/docs/sap-hana-power?topic=sap-hana-power-determine_configuration). For SAP's storage requirements, especially file system sizes, see [SAP HANA Storage Requirements](https://www.sap.com/documents/2015/03/74cdb554-5a7c-0010-82c7-eda71af511fa.html?infl=9e705342-b66e-49d2-9023-c7aa7ef6f6af){: external}.

### Sample storage configuration for Linux
{: #sample-Linux}

Table 1 is a sample storage configuration for a {{site.data.keyword.powerSys_notm}} for SAP NetWeaver on Linux.

The storage can't be combined within one {{site.data.keyword.powerSys_notm}}; it must be either Tier 1 or Tier 3. When you provision the Linux server, you automatically get the standard LVM configuration for the root volume group. These file systems are included in table 1. Disk sizes depend on whether the installation is Greenfield, or whether the server is a copy of an on-premises AIX server that you decided to use as a sizing reference.

The naming convention for the LVM entries is optional, but it's advised to include the SID of your SAP NetWeaver system especially if you plan to install one or more instances.

| Storage | Volume group | Logical volume | Mountpoint |
| --- | --- | --- | --- |
| OS disk | Default configuration | Default configuration | Default configuration |
| Application disk | `app<sid>vg` | `lvusrsap` | `/usr/sap` |
| | | `lvusrsap<SID>` | `/usr/sap/<SID` |
| | | `lvusrsapmnt` | `/sapmnt/<SID>` |
| | | `lvusrsaptrans` | '/usr/sap/trans' |
| | | `lvsapDAH` | `/usr/sap/DAH` |
{: caption="Table 1. Sample storage layout for Linux" caption-side="top"}

### Sample storage configuration for Oracle
{: #sample-oracle}

Table 2 is a sample configuration for an AIX {{site.data.keyword.powerSys_notm}} for an SAP NetWeaver application server using Oracle as the example.

The storage cannot be combined within the same {{site.data.keyword.powerSys_notm}}, and can be either Tier 1 or Tier 3. It's recommended to provision three additional disks to enable separation between the OS, database, and application layer. Disk size depends on if the installation is Greenfield or if the server is a copy of an "on-premises" AIX server you have decided to use as a sizing reference.

The naming convention for the LVM entries is optional, but it's advised to include the SID of your SAP NetWeaver system, especially if you plan to install one or more instances.

| Storage | Volume group | Logical volume | Mount point |
| --- | --- | --- | --- |
| OS disk | Default configuration | Default configuration | Default configuration |
| Application disk | `app<sid>vg` | `lvusrsap` | `/usr/sap` |
| | | `lvusrsap<SID>` | `/usr/sap/<SID>` |
| | | `lvusrsapmnt` | `/sapmnt/<SID>` |
| | | `lvusrsaptrans` | '/usr/sap/trans' |
| | | `lvsapDAH` | `/usr/sap/DAH` |
| Database storage | `db<sid>vg` | `lv<SID>arch` | `/oracle/<SID>/oraarch` |
| | | `lv<SID>reorg` | `/oracle/<SID>/sapreorg` |
| | | `lv<SID>origlogA` | `/oracle/<SID>/origlogA` |
| | | `lv<SID>origlogB` | `/oracle/<SID>/origlogA` |
| | | `lv<SID>ora` | `/oracle/<SID>` |
| | | `lv<SID>sapdata1` | `/oracle/<SID>/sapdata1` |
| | | `lv<SID>sapdata2` | `/oracle/<SID>/sapdata2` |
| | | `lvorastage` | `/oracle/stage` |
| | | `lv<SID>sapdata3` | `/oracle/<SID>/sapdata3` |
| | | `lv<SID>sapdata4` | `/oracle/<SID>/sapdata4` |
| | | `lv<SID>oraclient` | `/oracle/client` |
{: caption="Table 2. Sample storage layout for Oracle" caption-side="top"}

For more information, see [SAP Note 2172935](https://launchpad.support.sap.com/#/notes/2172935){: external}.

### Sample storage configuration for {{site.data.keyword.Db2_on_Cloud_short}}
{: #sample-db2}

Table 3 is a sample storage configuration for an AIX {{site.data.keyword.powerSys_notm}} for a {{site.data.keyword.Db2_on_Cloud_short}} server.

The storage cannot be combined within the same {{site.data.keyword.powerSys_notm}}, and can be either Tier 1 or Tier 3. It's recommended to provision three more disks to enable separation between the OS, database, and application layer. Disk size depends on whether the installation is Greenfield or the server is a copy of an "on-premises" AIX server that you have decided to use as a sizing reference.

The naming convention for the LVM entries is optional, but it's advised to include the SID of your SAP NetWeaver system especially if you plan to install one or more instances.

| Storage | Volume group | Logical volume | Mountpoint |
| --- | --- | --- | --- |
| OS disk | Default configuration | Default configuration | Default configuration |
| Application disk | `app<sid>vg` | `lvusrsap` | `/usr/sap` |
| | | `lvusrsap<SID>` | `/usr/sap/<SID>` |
| | | `lvusrsapmnt` | `/sapmnt/<SID>` |
| | | `lvusrsaptrans` | '/usr/sap/trans' |
| | | `lvsapDAH` | `/usr/sap/DAH` |
| Db2 database storage I | `<sid>db2vg` | `loglv<SID>` | NA |
| | | `lv<SID>db2` | `/db2/<SID>` |
| | | `lvhome<SID>` | `/db2/db2<SID>` |
| | | `lv<SID>db2dump` | `/db2/<SID>/db2dump` |
| | | `lv<SID>logdir` | `/db2/<SID>/log_dir` |
| | | `lv<SID>log_archive` | `/db2/<SID>/log_archive` |
| | | `lv<SID>saptmp` | `/db2/<SID>/saptemp1` |
| | | `lv<SID>db2sw` | `/db2/db2/<DBSID>/db2_sw` |
| Db2 database storage II | `<sid>db2datvg` | `lv<SID>sapdata1` | `/db2/<SID>/sapdata1` |
| | | ``lv<SID>sapdata2` | `/db2/<SID>/sapdata2` |
| | | ``lv<SID>sapdata3` | `/db2/<SID>/sapdata3` |
| | | ``lv<SID>sapdata4` | `/db2/<SID>/sapdata4` |
{: caption="Table 2. Sample storage layout for Db2 on Cloud" caption-side="top"}

For more information, see [Required File Systems for IBM Db2 for Linux, UNIX, and Windows](https://help.sap.com/viewer/4fbd902c7c76410bb82c6311dd4dc94b/CURRENT_VERSION/en-US/713eb64f45c6448c8dbe8a51b85680ee.html){: external} and [SAP Note 1707361](https://launchpad.support.sap.com/#/notes/1707361){: external}.

## Next Steps
{: #determine-configuration-next-steps}

You are now ready to begin provisioning your {{site.data.keyword.powerSys_notm}}. See [Setting up your Power Systems Virtual Server instances](/docs/sap-netweaver-power?topic=sap-netweaver-power-set-up-power-infrastructure) for your next steps.
