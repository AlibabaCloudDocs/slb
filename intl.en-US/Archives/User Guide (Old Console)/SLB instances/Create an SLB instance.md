# Create an SLB instance {#task_ctx_xsm_vdb .task}

Before creating an SLB instance, make sure that you have properly prepared the environment. For more information, see [Plan and prepare](../../../../intl.en-US/Quick Start (New Console)/Plan and prepare.md#).

1.   Log on to the [SLB console](https://slbnew.console.aliyun.com/#/list/cn-hangzhou). 
2.   On the Instances page, click **Create Server Load Balance**. 
3.   Configure the SLB instance according to the following information. 

    |Configuration|Description|
    |:------------|:----------|
    |**Region**| Select the region where the SLB instance is located.

 **Note:** Make sure that the region of the SLB instance is the same as that of backend ECS instances.

 |
    |**Zone type**|Display the zone type of the selected region. The zone of a cloud product refers to a set of independent infrastructure and is usually represented by Internet data centers \(IDCs\). Different zones have independent infrastructure \(network, power supply, air-conditioning and so on\). Therefore, an infrastructure fault in one zone will not affect other zones. A zone belongs to a specific region, however, a single region may have one or more zones. SLB has deployed multi-zone in most regions.    -   Single zone: The SLB instance is deployed only in one zone.
    -   Multi-zone: The SLB instance is deployed in two zones. By default, the instance in the primary zone is used to distribute traffic. If the primary zone is faulty, the instance in the backup zone will automatically take over the load balancing service.
|
    |**Primary zone**|Select the primary zone for the SLB instance. The primary zone carries traffic in normal conditions.|
    |**Backup zone**|Select the backup zone for the SLB instance. The backup zone only takes over traffic when the primary zone is unavailable.|
    |**Instance spec**| Select a performance capacity for the instance.

 The performance metrics varies based on different capacities. For more information, see [Guaranteed-performance instances](../../../../intl.en-US/Best Practices/How to use a guaranteed-performance Server Load Balancer instance?.md#).

 |
    |**Instance Type**|Select the instance type based on your business needs. A public or a private IP address is allocated to the SLB instance based on the instance type.    -   Internet: Internet SLB instances distribute requests from Internet clients to backend ECS instances according to your listening rules.
    -   Intranet: Intranet SLB instances only distribute requests from clients that have access to the private network of the SLB instance.
|
    |**Network type**|If the selected instance type is Intranet, you have to select a network type for the instance:    -   Classic network: The IP of the instance is allocated and managed by Alibaba Cloud in a unified manner.
    -   VPC: The IP of the instance is allocated from your specified VSwitch CIDR block.
|
    |**Bandwidth**|Display the billing method.|
    |**Quantity**|Select the number of instances to create.|

4.  Click **Buy Now** and complete the payment. 

