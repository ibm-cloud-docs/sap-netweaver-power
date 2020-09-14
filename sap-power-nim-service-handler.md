---

copyright:
  years: 2020
lastupdated: "2020-08-31"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, network connectivity, NIM service handler, AIX, 

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

# Using the NIM service handler on your new AIX virtual server instance       
{: #nim_service_handler}

If you plan to run a NIM Service Handler (NIMSH) on your AIX virtual server to connect to a NIM server, make sure that you avoid the following port conflict.
{: shortdesc}

The NIM client daemon (NIMSH) uses reserved ports 3901 and 3902 (see [Using the NIM service handler for client communication](https://www.ibm.com/support/knowledgecenter/en/ssw_aix_72/install/adv_config_nimsh.html){: external}). If you install an SAP Central Services Instance with instance number 01 or 02 on the same virtual server, a conflict is generated. By default, the SAP Central Services Instance installation configures port number 39XX for SAP Message Server internal communication, where XX is the two-digit SAP instance number.

An SAP installation places the port number into the SAP profile file `DEFAULT.PFL`. For example, the following entry in `DEFAULT.PFL` is for an SAP Central Services instance number 01:

```
rdisp/msserv_internal = 3901
```
To avoid port conflicts, do one of the following actions:

* Use instance number 00 for your SAP Central Services instance or another instance number that is not 01 or 02. 
* Change the value of the `rdisp/msserv_internal` profile parameter to a port value that does not conflict with the reserved ports of NIMSH or any other program on your server.

You can check the status of the NIM components on the AIX server as follows:

```
# lssrc -a |grep -i nim 

 nimsh            nimclient                     inoperative 

 nimhttp                                        inoperative 
```



