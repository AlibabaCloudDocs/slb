# Create an IPv6 instance {#task_uz2_kjz_c2b .task}

This topic describes how to create an IPv6 SLB instance. After an IPv6 instance is created, the system allocates a public IPv6 address to the instance to forward requests from IPv6 clients.

IPv6 is the next-generation IP protocol designed by IETF \(Internet Engineering Task Force\) to replace the current version of IP protocol \(IPv4\). By extending the length of IPv4 address from 32 bits to 128 bits, it expands the address space by 79,228,162,514,264,337,593,543,950,336 times. After IPv6 is used, each grain of sand on the world can be allocated with an IP address.

**Note:** 

-   Currently, only Zone E and Zone F in the China \(Hangzhou\) region, Zone F and Zone G in the China \(Beijing\) region, and Zone E \(primary zone\) and Zone D \(secondary zone\) in the China \(Shanghai\) region support creating IPv6 instances and the instances must be guaranteed-performance instances.
-   The Internet IPv6 network environment is still in the early stage of construction, and some links may be inaccessible. If such problem occurs, submit a ticket for technical support. Besides, SLA is not provided in the open beta test stage.
-   IPv6 has a longer IP header than IPv4. Therefore, when you use a UDP listener on an IPv6 SLB instance, you must ensure that the MTU of the NIC communicating with SLB on the backend server \(ECS instance\) is not greater than 1480 \(some applications need to synchronize their configuration files based on this MTU value\). Otherwise the packets may be discarded because they are too large.

    If you use a TCP/HTTP/HTTPS listener, no additional configurations are required because the TCP protocol supports MSS auto-negotiation.

-   HTTP listeners can use the `X-Forwarded-For` header field to obtain source client IPv6 addresses.

SLB IPv6 instances have the following features:

-   Smooth migration and no impact on your service

    You can directly bind ECS instances that use IPv4 addresses to an IPv6 SLB instance and smoothly migrate the service to IPv6 without modifying the original system.

    IPv6 has no impact on the original IPv4 service. If the traffic volume increases, you only need to increase backend ECS instances.

-   IPv6 access control ensures more secure and reliable service deployment

    SLB supports IPv6 access control. You can configure access control lists according to your business needs.

    -   A blacklist can effectively block the access of malicious addresses to the SLB service.
    -   If a whitelist is configured, only addresses in the whitelist can access the SLB service.

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**.
3.  On the Server Load Balancer page, click **Create SLB Instance** in the upper-left corner.
4.  Configure the SLB instance. For the IP version, select **IPv6**. Other configurations are the same as configurations of common instances. For more information, see [SLB configurations](reseller.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#table_ivr_hjn_vdb).

    **Note:** Currently, only Zone E and Zone F in the China \(Hangzhou\) region, Zone F and Zone G in the China \(Beijing\) region, and Zone E \(primary zone\) and Zone D \(secondary zone\) in the China \(Shanghai\) region support creating IPv6 instances and the instances must be guaranteed-performance instances.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15645/15560900697308_en-US.png)

5.  Go back to the **Server Load Balancer** page to view the created IPv6 instance.

After the IPv6 instance is created, the system allocates an IPv6 address to it.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15645/15560900697309_en-US.png)

