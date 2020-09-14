---

copyright:
  years: 2020
lastupdated: "2020-08-10"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, provisioning, storage, AIX, paging space

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Extending or adding paging space     
{: #extending_paging_space}

Prechecks can include a paging space check, which analyzes your system and determines whether your server has sufficient paging space for the database or application installation. 
{: shortdesc}

Some databases require at least 32 GB. Instead of increasing the size of the current paging space `hd6`, create a second paging volume when you define additional storage for the database or application volume groups.

After you create volume groups for applications and databases, you can create the new paging space to reside on the volumes within the volume groups.

The `lsps -s` command shows the total amount of paging space on your system, for example:

```
root@ibmdemnw01:/swrepo/AIX> lsps -s
Total Paging Space   Percent Used
      25760MB	             0%
```
 
The `lsps -a` command shows	the distribution of the paging space defined on your system, for example:

```
root@ibmdemnw01:/swrepo/AIX> lsps -a
Page Space  Physical Volume   Volume Group   Size %Used 	Active	Auto	Type Ch
hd6         hdisk4            rootvg	       160MB   20   yes     yes     lv
paginglv	  hdisk2            fr02swreposvg 25600MB	  0   yes     yes     lv
root@ibmdemnw01:/swrepo/AIX> I
``` 
This example shows that a paging space was defined in the volume group `fr02swreposvg` on `hdisk2` called `paginglv` in addition to the standard paging space `hd6` in the `rootvg`. 

If your new AIX server instance doesn't have sufficient paging space when you begin the implementation phase of your database or application, it can lead to multiple errors, for example, PGSPACE_KILL where the VMM starts to prune system processes. Be sure to follow third-party software recommendations for their products. 
