---

copyright:
  years: 2020
lastupdated: "2020-08-12"

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

# Installing by using a jump server
{: #installing_jump_server}

Follow these steps to install the system by using the jump server and tools that are installed on your AIX virtual server. 
{:shortdesc}

## On the AIX server
{: #on_aix_server}

1. Set a password. The VNC executable can be started multiple times and open multiple channels. Set a password to prevent other people from working on your channel.
    1. Go to the `/home/root/.vnc` directory.
    2. Run the `vncpasswd` command.
    3. Set the password for your connection. 
1. In the `root` directory, run the `vncserver` command to start a vncserver session.

## On your laptop or jump server
{: #on_laptop_or_jump_server}

### Opening a terminal
{: #open_terminal}

1. Connect the VNC Viewer software to the AIX server. In the VNC Viewer window, enter the address that was displayed when you started the vncserver on AIX. To use a hostname, make sure to update the `/etc/hosts` file so that the hostname resolves to IP. 

    Your new server must be resolvable in the Windows or operating system of your laptop (for direct connections) and in your jump server. If an encryption warning is displayed, click **Continue**. When prompted, enter your password and click **OK**.
    {:important} 

1. Open a terminal. Enter `xterm` or `aixterm` on the command line.

### Setting variables
{: #set_variables}

When you run SAPINST, set variables to ensure that there are enough resources to start the executable and that it exports the correct details about you and your system.

1. Echo the `$DISPLAY` variable. The output should show the same details as the connection.
2. Run the `xhost +` command to disable access control.
3. Run the `xauth` command to list the currently assigned keys that are needed to connect.

    Make a copy of the entries. If you need to switch to an SAP ACCOUNT for any reason, you can add the keys, access the session, and export the $DISPLAY again.
    {:tip}

1. Set the following variables for the installation session that are needed for SAPINST:

    ```
    export SAPINST_REMOTE_ACCESS_USER=<Your User ID here, root or swpmuser>
    export SAPINST_USE_HOSTNAME=<Hostname or Virtual Address>
    export LIBPATH=/sapmnt/<SID>/exe
    export CPIC_MAX_CONV=500
    export JAVA_HOME=/usr/java8_64
    export PATH=$JAVA_HOME/bin:$PATH
    export TMP=/swrepo/SAP/SWPM/tmp
    export TEMP=/swrepo/SAP/SWPM/tmp
    export TMPDIR=/swrepo/SAP/SWPM/tmp
    umask 022
    ulimit -n 32000
    ulimit -d unlimited
    ulimit -s unlimited
    ulimit -f unlimited
    ulimit -m unlimited
    ```
    * The `$LIBPATH` variable should point to your `/sapmnt/<SID>/exe` directory, which should already be on your system.
    * `JAVA_HOME` should point to the `/usr/javaX_64` version installed on your server.
    * The exports for the `TEMP;`, `TEMPDIR`, and `TMP` directories ensure that SAPINST doesn't use the `/tmp` directory on AIX for the installation.
    * Make sure that the temp exports are set to a dedicated filesystem where you have unpacked SAPINST.
    * The `umask` and `ulimit` settings are recommended.

### Testing SAPINST and installing
{: #test_sapinst}

1. In the SAPINST directory, run the following command:
    ```
    ./sapinst SAPINST_SLP_MODE=true
    ```
1. When prompted to confirm, enter `y`.
1. In your browser, go to the following URL:

    https://<AIX server IP address>:4237/sapinst/docs/index.html

2. When prompted, log in with the Software Provisioning Manager user or root user.
3. Select your preferred product and proceed to install.

### Port forwarding
{: #port_forwarding}
If you're using a Windows operating system and the VNC port isn't working or it's closed, you need to tunnel to make the port for VNC 5901 usable. If you're using a recent version of Windows PowerShell, an SSH server is included so you can use SSH commands on the command line. For more information, see [SSH tunneling](/docs/sap-netweaver-power?topic=sap-netweaver-power-ssh_tunneling).

### Common problems and solutions
{: #common_issues}  
Here are some common issues that occur with Software Provisioning Manager:
* Capacity of the `/tmp` directory during the pre-flight checks. The recommendation is at least 5 GB.
* Make sure that there's at least 32 GB of paging space. This can be adjusted after the AIX server is installed with the required database and applications. The recommendation is to run the required workload and tune the I/O resources.
* Extend `hd4` or “`/`” to 150 MB. Otherwise, you'll get a WARNING during the prerequisite tests for Db2 and Oracle.
* Check `/etc/security/login.cfg` during installation. For more information, see [login.cfg file updates](/docs/sap-netweaver-power?topic=sap-netweaver-power-updating_login_cfg).
* `Required EXPORT750 (Folder EXP1) missing` – If you want to install the system in another language, download the EXP1 compressed file and associated LANG .zip files. Download them to the jump server or `swrepos` filesystem and specify them when the Software Provisioning Manager installer requests them.
* R3load TestConnect fails – To resolve this issue, refer to the following SAP Notes: 

    [SAP Note 1875902 - R3load -testconnect fails during using SWPM in step testDatabaseConnection](https://launchpad.support.sap.com/#/notes/1875902)

    [SAP Note 2805859 - A1EEGEN 000 (DBS) DbSlErrorMsg rc = 28 "no connection info in DBCON found"](https://launchpad.support.sap.com/#/notes/2805859)







