---

copyright:
  years: 2020
lastupdated: "2020-08-09"

keywords: SAP NetWeaver, {{site.data.keyword.cloud_notm}}, network connectivity, jump server, routes, AIX, Linux

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

# Adding routes on your instance for the jump server   
{: #adding_routes}

After you configure {{site.data.keyword.dl_full}} and your jump server is provisioned with a private and public IP address, update the network route on your virtual server instance so it can connect to your jump server. The following example shows how to connect a jump server on Windows to the AIX virtual server instance. 
{: shortdesc}

## AIX instance 
{: #aix_instance}

1. Go to the [Resource list](https://cloud.ibm.com/resources){: external} to find your jump server.
2. In the devices list, click your jump server to display the Devices Overview.
3. In the Network Details, note the private interface information. Click the information icon ("**i**") next to the private IP address to display the Gateway and Subnet Mask information. This information is required when you add the route to your AIX virtual server instance.
4. Log on to your AIX virtual server instance and add the route.

    For example, given the following information:

    **Private IP address:** 10.123.111.78

    **Subnet:** 255.255.255.192

    **Default Gateway:** 10.123.111.1
        
    You can run the following command:

    `route add -net 10.123.111.0 255.255.255.192 10.123.111.1`
  
    Note that the route is added temporarily; it disappears when you reboot.
    
    To add the route permanently across reboots, run the following command:

    ```
    chdev -l inet0  -a route=net,-hopcount,0,-netmask,255.255.255.192,-if,en0,,,,-static,10.123.111.0,10.123.111.1
    ```

1. Run `netstat -rn` and check that the entry appears in the list. Ping the jump server network, log on to the jump server, and use Windows Powershell to connect to the AIX instance from the jump server.

## Linux

To update the persistent route in Linux, add details to the `/etc/sysconfig/network/ifroute-XX` file, where `XX` is the network adapter.

In the file, add details in the following format: 

```
[Destination Address]  [Default Gateway]  [Subnet Mask]  [Network Adapter]
```

For example: 

```
cat  /etc/sysconfig/network/ifroute-eth0

10.123.456.0  10.123.456.1 255.255.255.192 eth0
```



