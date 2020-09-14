---

copyright:
  years: 2020
lastupdated: "2020-08-10"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, provisioning, storage, AIX

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Adding storage for the rootvg during AIX server provisioning      
{: #adding_storage}

Configure additional space in the `rootvg` for third-party vendor prerequisite checks.
{: shortdesc}

After provisioning the AIX server, the `rootvg` has approximately 8 GB of free space. To prevent issues with prerequisite checks when you install database software, add another disk with a partition size of 30 GB.

1. During virtual server instance (VSI) provisioning, create a new storage volume that is 30 GB in size.
2. After the AIX server is provisioned, run the `lspv` command for an overview of `hdisks`. The output shows one disk that belongs to the rootvg and another disk that does not have a physical volume identifier and a volume group assigned:
    ```
    # lspv
    hdisk0          none                                None
    hdisk1          00f6db0af58e9775                    rootvg          active
    ```
1. To extend the `rootvg` volume group, run the following command:

    ```
    extendvg rootvg <new hdisk>
    ```

## Next Steps
{: #storage-next-steps}

[Extending /tmp](/docs/sap-netweaver-power?topic=sap-netweaver-power-extending_tmp)

[Extending or adding paging space](/docs/sap-netweaver-power?topic=sap-netweaver-power-extending_paging_space)





