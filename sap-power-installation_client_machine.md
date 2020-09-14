---

copyright:
  years: 2020
lastupdated: "2020-08-13"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, best practices, Software Provisioning Manager, installation, client machine

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

# Installing by using a client machine
{: #installing_client_machine}

Follow these steps to install the system by using a client machine.
{:shortdesc}

1. Set up SSH tunneling on the client machine. For more information, see [SSH tunneling](/sap-netweaver-power?topic=sap-netweaver-power-ssh_tunneling).
1. Set a variable on the server for `TMPDIR` on the AIX server:
    ```
    export TMPDIR=/swrepo/SAP/SWPM/tmp
    ```
    Otherwise, Software Provisioning Manager uses the system-wide `/tmp` directory for `sapinstdir` logging and quickly runs out of space.  

1. Unpack the Software Provisioning Manager SAR file on the server.
1. Unpack the installation into the respective folders.
1. Run the Prerequisites Check to make sure that all requirements are met for the installation.
    1. Go to the `/swrepo/SAP/prereqcheck` directory.
    2. Run the Software Provisioning Manager `sapinst` executable as follows: 
        ```
        /swrepo/SAP/SWPM/sapinst SAPINST_REMOTE_ACCESS_USER=swpmuser SAPINST_HTTPS_PORT=443
        ```
1. Open a browser on your client machine and go to this URL:
    ```
    https://<Public IP address of your AIX server>:443/sapinst/docs/index.html
    ```
1. In login box, enter the swpmuser and the password that you defined.
1. Open the Prerequisites Checker. For example, for Db2: On the Welcome page, select **SAP NetWeaver 7.5 > IBM Db2 for Linux, UNIX, and Windows > Preparations > Prerequisites Check**.
1. On the Prerequisite Checker Options page, select the first three options.
2. Click **Next** to proceed through the wizard until the Prerequisites Checker Results are displayed. 

If you see a swap size MEDIUM result, check that you have sufficient swap space on your system.
{:note}

After you complete the prerequisites check, you can proceed with the SAP NetWeaver installation for the Application Server, Central Services, and the Database Installation.


