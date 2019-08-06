# Create an IPv6 instance {#task_uz2_kjz_c2b .task}

This topic describes how to create an IPv6 Server Load Balancer \(SLB\) instance. After an IPv6 SLB instance is created, the system allocates a public IPv6 address to the instance to forward requests from IPv6 clients.

IPv6 is the abbreviation of Internet Protocol Version 6. IPv6 is the next-generation IP protocol designed by IETF \(Internet Engineering Task Force\) to replace the current version of IP protocol \(IPv4\). By extending the length of IPv4 address from 32 bits to 128 bits, it expands the address space by 79,228,162,514,264,337,593,543,950,336 times. After IPv6 is used, each grain of sand on the world can be allocated with an IP address.

**Note:** 

-   Currently, IPv6 instances are supported in the following zones, but the instances must be guaranteed-performance instances.
    -   Zones E and F in the China \(Hangzhou\) region
    -   Zones F and G in the China \(Beijing\) region
    -   Zones D and E in the China \(Shanghai\) region
    -   Zones D and E in the China \(Shenzhen\) region
-   The Internet IPv6 network environment is still in the early stage of construction, and some links may be inaccessible. If such problem occurs, submit a ticket for technical support. SLA is not provided in the open beta test stage.
-   IPv6 has a longer IP header than IPv4. Therefore, when you use a UDP listener in an IPv6 SLB instance, you must ensure that the MTU of the NIC communicating with SLB on the backend server \(ECS instance\) is not greater than 1480 \(some applications need to synchronize their configuration files based on this MTU value\). Otherwise, the packets may be discarded because they are too large.

    If you use a TCP, HTTP, or HTTPS listener, no additional configurations are required because the TCP protocol supports MSS auto-negotiation.

-   HTTP listeners can use the `X-Forwarded-For` header field to obtain source IPv6 addresses of clients.

IPv6 instances have the following features:

-   Smooth migration and no impact on your service

    You can directly associate ECS instances that use IPv4 addresses with an IPv6 SLB instance and smoothly migrate the service to IPv6 without modifying the original system.

    IPv6 has no impact on the original IPv4 service. If the traffic volume increases, you only need to increase backend ECS instances.

-   IPv6 access control ensures more secure and reliable service deployment

    SLB supports IPv6 access control. You can configure access control lists according to your business needs.

    -   A blacklist can effectively block the access of malicious addresses to the SLB service.
    -   If a whitelist is configured, only addresses in the whitelist can access the SLB service.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**.
3.  On the Server Load Balancer page, click **Create SLB Instance** in the upper-left corner.
4.  Configure the SLB instance. For the IP version, select **IPv6**. Other configurations are the same as configurations of common instances. For more information, see [SLB configurations](intl.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#table_ivr_hjn_vdb).

    **Note:** Currently, IPv6 instances are supported in the following zones, but the instances must be guaranteed-performance instances.

    -   Zones E and F in the China \(Hangzhou\) region
    -   Zones F and G in the China \(Beijing\) region
    -   Zones D and E in the China \(Shanghai\) region
    -   Zones D and E in the China \(Shenzhen\) region
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15645/15645483217308_en-US.png)

5.  Go back to the **Server Load Balancer** page to view the created IPv6 instance.

After the IPv6 instance is created, the system allocates an IPv6 address to it.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15645/15645483227309_en-US.png)

