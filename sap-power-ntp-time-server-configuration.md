---

copyright:
  years: 2020
lastupdated: "2020-09-03"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, network connectivity, NTP, time server

subcollection: sap-netweaver-power

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Configuring the NTP client      
{: #ntp_time_server}

A newly provisioned AIX virtual server might not show the correct time when you run the `date` command. The initial time setting on the server often differs by 10 - 15 minutes from the correct time. This time difference can cause problems when you install and run your SAP system on the server, or when you connect the SAP system to your on-premises landscape.
{: shortdesc}

You can keep the time current by configuring an NTP daemon that receives the correct time from an NTP time server. To set up NTP on AIX, see
[How to configure NTP in your Environment and common issues](https://www.ibm.com/support/pages/how-configure-ntp-your-enviornment-and-common-issues){: external}.

To enable the AIX virtual server to synchronize with the NTP server, add the network IP address of your company’s NTP server or a public NTP server to the NTP configuration file `/etc/ntpd.conf`.

Be sure to configure NTP to use the SLEWING option `-x` as recommended in the following SAP Notes:

* [1972803 - SAP on AIX: Recommendations](https://launchpad.support.sap.com/#/notes/1972803){: external}
* [2456565 - Set NTP with SLEWING option in AIX](https://launchpad.support.sap.com/#/notes/2456565){: external}
  
After you complete the configuration, check that the NTP daemon runs with the `-x` argument as follows:

```
root@ibmdemnw01:/home/root> ps -ef | grep -i xntpd
    root 32309530        1   0 00:13:24      -  0:00 /usr/sbin/xntpd -x
```


