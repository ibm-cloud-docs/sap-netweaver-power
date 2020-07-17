---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: SAP NetWeaver, downloading SAP software, installing SAP software, SAP Download Manager, SAP Certified

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Creating an SAP license key
{: #create-key}

SAP has changed the mechanism for licensing when an {{site.data.keyword.IBM}} {{site.data.keyword.powerSysShort}} is running on the {{site.data.keyword.cloud}}. In the {{site.data.keyword.cloud_notm}}, the product license is not dependent on the underlying hardware that's running the server. The license is associated with the virtual server. The SAP license key, `saplikey` or `SLICENSE`, displays a "hardware key". The hardware key is no longer based on the hardware ID, but on the partition UUID of the logical partition (LPAR). The partition UUID is persisted by the platform across reboots, reconfigurations, OS reinstalls, and partition migrations, making it independent of the hardware that is running the virtual servers.
{: shortdesc}

Use the following steps to create your SAP license key.

1. Run the `saplikey -get` command on the server that you're using as the SAP message server. As an alternative to the `saplikey` command and if your SAP system is already installed, you can use the `SLICENSE` transaction to retrieve the `HARDWARE KEY`.
1. Use the `HARDWARE KEY` output value to generate a valid SAP software license from [SAP Support](https://support.sap.com/en/index.html){: external}. Select **Request Keys** and enter you SAP S-user ID.
1. Use the SAP system data to create a valid license key.
1. Use the SAP transaction `SLICENSE` or the `saplikey` command to install the license on your SAP system.

  When you request an SAP software license, be sure to use the `HARDWARE KEY` that was generated with an SAP kernel that has the minimum level required for running on {[site.data.keyword.cloud_notm]}. The minimum patch level of the kernel is found in [SAP Note 2879336](https://launchpad.support.sap.com/#/notes/2879336){: external}. Otherwise, your SAP software license will become invalid as soon as your virtual server is moved to different hardware in the {{site.data.keyword.cloud}}.

For downloading and installation steps, see [Downloading and installing SAP software and applications](/docs/sap-netweaver-power?topic=sap-netweaver-power-install_sap).

## Next Steps
{: #create-key-next-steps}

[Monitoring your system with SAP tools](/docs/sap-netweaver-power?topic=sap-netweaver-power-monitoring)
