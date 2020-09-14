---

copyright:
  years: 2020
lastupdated: "2020-08-11"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, provisioning, AIX, Linux, VNC

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# AIX Toolbox for Linux Applications 
{: #aix_toolbox}

When you download SAP packages from the [SAP Marketplace](https://support.sap.com/en/my-support/software-downloads.html){: external}, sometimes the files are packed into multispanning archives. Tools are required to decompress the files and rebuild the packages.
{: shortdesc}

For more information, see [SAP Note 886535 - Downloading multispanning archives (RAR archive)](https://launchpad.support.sap.com/#/notes/886535){: external} and [SAP Note 960755 - Unpacking ZIP archives in Unix](https://launchpad.support.sap.com/#/notes/960755){: external}. 

The required tools, unrar and unzip, can be downloaded from the [AIX Toolbox For Linux Applications](https://www.ibm.com/support/pages/aix-toolbox-linux-applications-downloads-alpha#U){: external}. Download the tools and use RPM to install them on your AIX system. You might need to install additional filesets as a prerequisite. These files might already be in the limited AIX repository that is supplied when the AIX server is provisioned.

Additional installation files can be found on the `/usr/sys/inst.images` mountpoint.

The `vnc` package is another useful tool in the AIX Toolbox for Linux Applications. After you install the `vnc` package into your AIX server, you will be able to start a VNC server on your AIX server. Then you can use a VNC viewer such as TightVNC on the jump server or another desktop to connect to your AIX server to start an SAP installation by using Software Provisioning Manager (formerly known as SAPINST) with the web front end. For more information, see [Software Provisioning Manager](https://support.sap.com/en/tools/software-logistics-tools/software-provisioning-manager.html){: external} and [Installing by using a jump server](/docs/sap-netweaver-power?topic=sap-netweaver-power-installing_jump_server).
