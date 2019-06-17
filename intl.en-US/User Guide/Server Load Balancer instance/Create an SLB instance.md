# Create an SLB instance {#task_ctx_xsm_vdb .task}

This topic describes how to create a Server Load Balancer \(SLB\) instance.

The required instance type, instance region, network type, and listener protocol are known. The environment is prepared. For more information, see [Plan and prepare](../../../../intl.en-US/Quick Start (New Console)/Plan and prepare.md#).

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**, and click **Create SLB Instance** in the upper-left corner.
3.  Configure the SLB instance according to the following information. 

    |Configuration|Description|
    |:------------|:----------|
    |**Region**| Select the region to which the SLB instance belongs.

 **Note:** Make sure that the region of the SLB instance is the same as that of backend ECS instances.

 |
    |**Zone Type**|The zone type of the selected region is displayed. The zone of a cloud product refers to a set of independent infrastructure and is usually represented by data centers. Different zones have independent infrastructure \(network, power supply, air-conditioning and so on\). Therefore, an infrastructure fault in one zone does not affect other zones. A zone belongs to a specific region. A single region may have one or more zones. SLB has deployed multiple zones in most regions.     -   Single zone: The SLB instance is deployed only in one zone.
    -   Multi-zone: The SLB instance is deployed in two zones. By default, the primary zone is used. If the primary zone is faulty, the secondary zone automatically takes over the load balancing service.
 |
    |**Primary Zone**|Select the primary zone for the SLB instance. The primary zone carries traffic in normal conditions.|
    |**Backup Zone**|Select the secondary zone for the SLB instance. The secondary zone only takes over traffic when the primary zone is unavailable.|
    |**Instance name**|Enter a name for the SLB instance to be created. The name must be 1 to 80 characters in length and can contain letters, numbers, Chinese characters, hyphens \(-\), slashes \(/\), periods \(.\), and underscores \(\_\).

 |
    |**Resource Group**|The resource group to which the SLB instance to be created belongs.|
    |**Instance Spec**| Select a performance specification for the instance.

 The performance metrics vary by specification. For more information, see [Guaranteed-performance instances](../../../../intl.en-US/FAQ/FAQ/How to use guaranteed-performance Server Load Balancer instances?.md#).

 |
    |**Instance Type**|Select the instance type based on your business needs. A public or a private IP address is allocated to the SLB instance based on the instance type. For more information, see [SLB instance overview](intl.en-US/User Guide/Server Load Balancer instance/SLB instance overview.md#).     -   Internet: An Internet SLB instance only provides a public IP address and you can access the SLB service from the Internet.
    -   Intranet: An intranet SLB instance only provides a private IP address and you can access the SLB service only from the intranet.
 |
    |**IP version**|Select the IP version of the SLB instance, which can be IPv4 or IPv6. **Note:** ​Currently, IPv6 instances are supported only in the following regions. However, the instances must be guaranteed-performance instances.

    -   Zone E and Zone F in the China \(Hangzhou\) region
    -   Zone F and Zone G in the China \(Beijing\) region
    -   Zone D and Zone E in the China \(Shanghai\) region
    -   Zone D and Zone E in the China \(Shenzhen\) region
 |
    |**Quantity**|Select the number of SLB instances to create.|

4.  Click **Buy Now** and complete the payment.

