# Create an IPv6 instance

This topic describes how to create an IPv6 Server Load Balancer \(SLB\) instance. After you create an IPv6 SLB instance, the system allocates a public IPv6 address to the instance to forward requests from IPv6 clients.

IPv6 is short for Internet Protocol Version 6. IPv6 is the new generation of IP protocol designed by Internet Engineering Task Force \(IETF\) to replace the current version of IP protocol \(IPv4\). By extending the length of IPv4 address from 32 bits to 128 bits, IPv6 expands the address space by 79,228,162,514,264,337,593,543,950,336 times. After IPv6 is used, each instance can be allocated with an IP address.

**Note:**

-   Currently, IPv6 instances are supported in the following zones, and the instances must be guaranteed-performance instances.
    -   China \(Hangzhou\): Zone E and Zone F
    -   China \(Beijing\): Zone F and Zone G
    -   China \(Shanghai\): Zone D and Zone E
    -   China \(Shenzhen\): Zone D and Zone E
    -   China \(Zhangjiakou\): Zone A and Zone B
    -   China \(Hong Kong\): Zone B and Zone C
-   Guaranteed-performance IPv6 instances are supported in the following zones: China East 1 Finance Zone H and Zone I, China East 2 Finance Zone F and Zone G, and China South 1 Finance Zone E.
-   The IPv6 network environment is currently being developed. If you cannot access the lines, you can submit a ticket for technical support. SLA is not guaranteed in the public preview period.
-   IPv6 addresses have longer IP headers than IPv4 addresses. When you create a UDP listener for an IPv6 SLB instance, make sure that the maximum transmission unit \(MTU\) size of the network interface controller \(NIC\) on each backend server \(ECS instance in most cases\) that communicates with the SLB instance is less than or equal to 1,200 bytes. Otherwise, oversized packets may be discarded. The configuration files of some applications need to be modified based on the MTU size.

    If you use a TCP, HTTP, or HTTPS listener, you do not need to perform additional configuration steps because TCP supports automatic maximum segment size \(MSS\) adjustment.

-   HTTP listeners can use the `X-Forwarded-For` header field to obtain source IPv6 addresses of clients.

Features of IPv6 instances:

-   Smooth migration without negative impacts on your business.

    The IPv6 SLB instances can be connected to IPv4 ECS instances. In this way, you can enable your IPv4 business to support IPv6 without changing the system.

    Adding an IPv6 entry has no impact on the original IPv4 business. If the traffic volume increases, you can increase the number of ECS instances.

-   More secure and reliable business deployment

    Alibaba Cloud SLB supports IPv6 access control. You can configure access control lists according to your business needs.

    -   You can configure a blacklist for SLB to block network traffic from malicious IP addresses.
    -   You can also configure a whitelist for SLB to allow network traffic from only authorized IP addresses.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).

2.  In the left-side navigation pane, choose **Instances** \> **Instances**.

3.  On the Instances page, click **Create Instance** in the upper-left corner.

4.  Create an SLB instance. Specify **IPv6** as the IP version.

    For other parameters, use standard instance settings. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).

    **Note:** Currently, IPv6 instances are supported in the following zones, and the instances must be guaranteed-performance instances.

    -   China \(Hangzhou\): Zone E and Zone F
    -   China \(Beijing\): Zone F and Zone G
    -   China \(Shanghai\): Zone D and Zone E
    -   China \(Shenzhen\): Zone D and Zone E
    -   China \(Zhangjiakou\): Zone A and Zone B
    -   China \(Hong Kong\): Zone B and Zone C
    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4623498951/p7308.png)

5.  Go back to the Instances page to view the created IPv6 instance.


After the IPv6 instance is created, the system allocates an IPv6 address to it.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4623498951/p7309.png)

**Related topics**  


[CreateLoadBalancer](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/CreateLoadBalancer.md)

