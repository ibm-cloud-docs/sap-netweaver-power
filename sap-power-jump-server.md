---

copyright:
  years: 2020
lastupdated: "2020-08-12"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, network connectivity, jump server

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

# Getting started with the jump server  
{: #jump_server}

If you are using {{site.data.keyword.dl_full}} and a jump server in your configuration, you can use the jump server as a software installation repository. The jump server has private and public IP addresses for accessing [SAP Software Center](https://launchpad.support.sap.com/#/softwarecenter){: external} or third-party vendor websites to download fixes or updates that can be stored on the jump server. 
{: shortdesc}

If you are using the Windows platform, you can install useful tools like WinSCP to transfer the software from the jump server to your AIX or Linux&reg; {{site.data.keyword.powerSysShort}}. The following table lists tools for jump servers on Windows:

| Tool          | Purpose                               | Link                           |
|---------------|---------------------------------------|--------------------------------|
| WinSCP        | Upload and download third-party files | [WinSCP Download and Install](https://winscp.net/eng/docs/guide_install){: external}    |
| PuTTY         | SSH client                            | [Download PuTTY: latest release](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html){: external} |
| VNC Viewer    | Virtual session connections           | [Download VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/windows/){: external}           |
| WinRAR        | File decompression and compression    | [WinRAR Demo Edition](https://www.rarlab.com/download.htm){: external}            |
| Java 8        | Prerequisite for SAP GUI for Windows  | [Java SE Runtime Environment 8 Downloads](https://www.oracle.com/java/technologies/javase-jre8-downloads.html){: external}                |
| SAP GUI       | SAP GUI for Windows                   | [SAP GUI 7.6 Core Download](https://launchpad.support.sap.com/#/softwarecenter/template/products/_APP=00200682500000001943&_EVENT=DISPHIER&HEADER=N&FUNCTIONBAR=Y&EVENT=TREE&TMPL=INTRO_SWDC_IU_FC&V=INST&REFERER=CATALOG-INSTALLATIONS&ROUTENAME=products/By%20Category%20-%20SAP%20Frontend%20Components){: external}      |
| Google Chrome | Internet browser                      | [Download Chrome](https://www.google.com/chrome/?brand=CHBD&gclid=EAIaIQobChMImqvg5Zb36gIVKoBQBh0QTwsyEAAYASABEgIR_vD_BwE&gclsrc=aw.ds){: external}         |
{: caption="Table 1. Tools for jump servers on Windows" caption-side="top"}

If you are using Windows as a jump server, you can use Windows PowerShell which includes a built-in SSH server.

For jump servers on Linux, the list of tools is nearly identical. For file uploads and downloads, you can use FileZilla, native SFTP, or SCP functionality.

Download SAP's SAPCAR utility, so when you download SAP Installation Media that is often bundled into `.SAR` files, you can extract the files immediately on the target AIX or Linux {{site.data.keyword.powerSys_notm}}:

1. Go to the [SAP Software Center](https://launchpad.support.sap.com/#/softwarecenter){: external}.
2. In **Downloads**, search for SAPCAR.
3. Select **SAPCAR 7.21**.
4. For the operating system, select **AIX 64BIT** or **LINUX ON POWER LE 64BIT**. 
5. Click the latest entry in the list and download to your jump server.
6. Transfer SAPCAR to your AIX or Linux {{site.data.keyword.powerSys_notm}}.


