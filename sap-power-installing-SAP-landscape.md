---

copyright:
  years: 2020
lastupdated: "2020-08-31"

keywords: SAP NetWeaver, downloading SAP software, installing SAP software, SAP Download Manager, SAP Certified

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Downloading and installing SAP software and applications
{: #install_sap}

## Downloading your software
{: #download-software}

Log in to the [SAP Support Portal](https://support.sap.com/en/index.html){: external} and click **Download Software** to download the required digital versatile discs (DVDs) to a local share drive that is visible to the private {{site.data.keyword.cloud}} network.
{: shortdesc}

You might want to install additional tools for easier handling of SAP software on AIX. For more information, see [AIX Toolbox for Linux Applications](/docs/sap-netweaver-power?topic=sap-netweaver-power-aix_toolbox).
{: tip}

## Before you begin
{: #before-downloading}
You can either download each DVD or use the [SAP Download Manager](https://support.sap.com/en/my-support/software-downloads.html){: external} by using the [SAP Download Basket](https://blogs.sap.com/2018/02/16/get-prepared-for-the-new-software-download-basket/){: external}. If you are using the SAP Download Manager, download it to an on-premises machine and transfer it to your SAP NetWeaver server. For more information about the SAP Download Manager, see [SAP Note 2559006](https://launchpad.support.sap.com/#/notes/2559006){: external}. SAP Notes require an SAP S-user ID.

## Installing
After you download the installation media, follow the standard SAP installation procedure that is documented in the [SAP installation guide](https://help.sap.com/viewer/nwguidefinder){: external} for your SAP version and components and the corresponding [SAP Notes](https://support.sap.com/en/my-support/knowledge-base.html){: external}. SAP Notes require an SAP S-user ID.

If you use the public IP address for SAP installation, be sure to set up SSH tunneling between your on-premises machine and the {{site.data.keyword.powerSysShort}}. For more information, see [SSH tunneling](/docs/sap-netweaver-power?topic=sap-netweaver-power-ssh_tunneling).

## Next Steps
{: #downloading-next-steps}

[Creating an SAP license key](/docs/sap-netweaver-power?topic=sap-netweaver-power-create-key)

[Monitoring your system with SAP tools](/docs/sap-netweaver-power?topic=sap-netweaver-power-monitoring)