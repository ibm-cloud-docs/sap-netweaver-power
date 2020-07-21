---

copyright:
  years: 2020
lastupdated: "2020-07-17"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Configuring your system for SAP NetWeaver workloads
{: #config-workload}

Use the following steps to configure your system to support SAP NetWeaver workloads.
{: shortdesc}

## Configuring SUSE Linux Enterprise Server for SAP NetWeaver
{: #config-suse}

After you deploy {{site.data.keyword.IBM}} {{site.data.keyword.powerSysShort}}, the following needs to be done within the operating system.

1. Configure root user access. You can log in to the system as a root user by using a configured SSH key. Logging in as a root user with a password through SSH is deactivated. You can log in as a root user by using the default password `root` in a virtual console window. After you log in, change the default password for the root user.
1. Start and enable the multipath deamon, for example, by running `systemctl start multipathd` and `systemctl enable multipathd`.
1. Set jumbo frames for network adapters. _Jumbo frames_ is another way of saying network maximum transmission units (MTU) of 9000-byte payload frames. All the network components in {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}}s support jumbo frames. In cases where certain network components don't support jumbo frames (for example, in communication to the external world), setting MTU=9000 can cause network issues. Therefore, set MTU=9000 only on adapters that are used internally.

  You must set jumbo frames on private networks that are used for communication between multiple instances in SAP three-tier systems.

  ```
  # cd /etc/sysconfig/network
  # vi ifcfg-ethX <--- name of ethernet device used for communication between SAP instances
  BROADCAST=''
  ETHTOOL_OPTIONS=''
  BOOTPROTO='static'
  IPADDR='xx.xx.xx.xx/xx'
  NAME='Virtual Ethernet card 0' NETWORK=''
  REMOTE_IPADDR=''
  STARTMODE='auto'
  USERCONTROL='no'
  MTU='9000'
  ```
  {: pre}

  To activate the changes, restart your network (`ifdown ethX; ifup ethX`) or set MTU for current configuration (with `ip link set dev <ethX> mtu 9000`).
1. Verify hostname resolution. Check that the DNS server is correctly entered in `/etc/resolv.conf` and that instance hostname resolution is possible (in the simplest case, through an entry in `/etc/hosts`).
1. Synchronize time. Ensure that the {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}}s that belong to the same SAP system have their time synchronized. For example, connect you partition to the time server with `ntpdate -u <ntpserver>`.
1. Tune SUSE Linux&reg; Enterprise Server for the SAP NetWeaver workload. On {{site.data.keyword.powerSys_notm}}s, the same image of SUSE Linux Enterprise Server is used for SAP NetWeaver and SAP HANA. Run the following command to tune the operating system for the SAP NetWeaver workload: `saptune solution apply NETWEAVER`. Enable the tuning daemon by running `systemctl enable tuned`.
1. Prepare file systems on additional storage volumes. If you attached additional storage volumes to your {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}}, you must create file systems by using Linux Logical Volume Manager.
1. Register your SAP virtual server by SUSE. Register your {{site.data.keyword.IBM_notm}} {{site.data.keyword.powerSys_notm}} by SUSE (for example, by running `SUSEConnect -r <suse_registration_key> -e <suse_registration_email>`).

## Configuring AIX for SAP NetWeaver
{: #config-aix}

After successful deployment of an {{site.data.keyword.IBM}} {{site.data.keyword.powerSys_notm}} with AIX, make sure you follow the configuration steps in [SAP Note 323816 - AIX: User limit settings](https://launchpad.support.sap.com/#/notes/323816) and [SAP Note 1972803 - SAP on AIX: Recommendations](https://launchpad.support.sap.com/#/notes/1972803).

## Next Steps
{: #config-workload-next-steps}

[Configuring system access for SAP NetWeaver installation](/docs/sap-netweaver-power?topic=sap-netweaver-power-config_system_access)

[Ordering storage](/docs/sap-netweaver-power?topic=sap-netweaver-power-order_storage)

[Downloading and installing SAP software and applications](/docs/sap-netweaver-power?topic=sap-netweaver-power-install_sap)

[Creating an SAP license key](/docs/sap-netweaver-power?topic=sap-netweaver-power-create-key)

[Monitoring your system with SAP tools](/docs/sap-netweaver-power?topic=sap-netweaver-power-monitoring)