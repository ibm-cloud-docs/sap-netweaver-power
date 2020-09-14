---

copyright:
  years: 2020
lastupdated: "2020-09-10"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, provisioning, storage, AIX, tmp

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Extending `/tmp`      
{: #extending_tmp}

SAP installations as well as Db2 and Oracle database software installations use PREINSTALLER checks to make sure that your system is database-ready. One of the checks is the amount of free space in `/tmp`. For example, at least 5 GB of available space is expected for Oracle installations. For Db2, the free space check expects 512 MB.
{: shortdesc}

To extend `/tmp`:

1. Check the space available in the `rootvg`. Run the following command:
    ```
    lsvg rootvg | grep "FREE PPs"
    ```
    If more storage is required, you should have sufficient space to extend `/tmp` because you already added an extra disk.

1. Run the following command:
    ```
    chfs -a size=5G /tmp
    ``` 
    The size of the logical volume on which `/tmp` resides (typically `hd3`) and the file system capacity is increased to 5 GB. 

You can run the same command with `+5G /tmp` to append the size of the file system and add 5 GB to the existing size.

You can enter a higher value to extend the file system further, for example, if you need more capacity, or if there are issues with free space in either “`/`” or `/tmp` during the PREINSTALLER check.

## Next Step
{: #extending-tmp-next-steps}

[Extending or adding paging space](/docs/sap-netweaver-power?topic=sap-netweaver-power-extending_paging_space)



