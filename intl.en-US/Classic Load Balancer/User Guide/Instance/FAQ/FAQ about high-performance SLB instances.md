# FAQ about high-performance SLB instances

High-performance Server Load Balancer \(SLB\) instances provide guaranteed performance. Beginning April 1, 2018, Alibaba Cloud starts to charge high-performance SLB instances based on specifications.

This topic provides answers to some frequently asked questions about high-performance SLB instances.

-   [What is a high-performance SLB instance?](#section_lht_gym_vdb)
-   [How are high-performance SLB instances billed?](#section_eth_yzm_vdb)
-   [What is the pricing of each specification?](#section_n5z_s1n_vdb)
-   [What is the optimal specification for a high-performance SLB instance?](#section_ifx_kcn_vdb)
-   [Can I change the specification of a high-performance SLB instance?](#p7)
-   [When does Alibaba Cloud begin to charge a specification fee on high-performance SLB instances?](#section_gvt_kfn_vdb)
-   [Are extra fees charged for shared-resource SLB instances in addition to the specification fee?](#section_hxl_pfn_vdb)
-   [Why is a high-performance SLB instance unable to reach the performance limit defined in the specification?](#section_ehc_vfn_vdb)
-   [Are shared-resource SLB instances still available for purchase?](#section_flq_wfn_vdb)
-   [Is a specification fee charged for internal-facing SLB instances?](#section_nfy_xfn_vdb)
-   [What do I do if I need more high-performance SLB instances?](#section_wvo_8kk_3m9)

## What is a high-performance SLB instance?

A high-performance SLB instance provides guaranteed performance. Shared-resource SLB instances share resources with each other, which means that performance cannot be guaranteed.

Before Alibaba Cloud released high-performance SLB instances, all instances were shared-resource instances. You can view the instance type in the SLB console.

The following table describes the differences between shared-resource SLB instances and high-performance SLB instances.

|Feature|Shared-resource SLB instance|High-performance SLB instance|
|-------|----------------------------|-----------------------------|
|Resource allocation|Shared resources|Exclusive resources|
|Service uptime guaranteed by terms of service level agreement|Not supported|99.95%|
|IPv6|×|√|
|Support for Server Name Indication \(SNI\) certificates|×|√|
|Blacklists and whitelists|×|√|
|Mounting elastic network interface \(ENI\)|×|√|
|Assigning secondary IP addresses to ENIs that are bound to ECS instances|×|√|
|HTTP-to-HTTPS redirection|×|√|
|Consistent hashing|×|√|
|TLS security policies|×|√|
|HTTP2|×|√|
|Websocket\(S\)|×|√|

You can move the pointer over the question mark that corresponds to the specification of a high-performance SLB instance to view the performance metrics, as shown in the following figure.

![Performance metrics for high-performance SLB instances](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2723498951/p7175.png)

The following section lists three key metrics for high-performance SLB instances:

-   Max Connection

    The maximum number of concurrent connections that an SLB instance supports. When the number of concurrent connections reaches the specified limit, new connection requests are dropped.

-   Connections Per Second \(CPS\)

    The number of new connections that are established per second. When the CPS value reaches the specified limit, new connection requests are dropped.

-   Queries Per Second \(QPS\)

    The number of HTTP or HTTPS queries \(requests\) that can be processed per second. This metric is specific to Layer 7 listeners. When the QPS value reaches the specified limit, new connection requests are dropped.


The following table lists the specifications of high-performance SLB instances provided by Alibaba Cloud.

|Type|Specification|Max Connection|CPS|QPS|Purchase method|
|:---|:------------|:-------------|:--|:--|---------------|
|Type 1|Small I \(slb.s1.small\)|5,000|3,000|1,000|Available for purchase from the official website of Alibaba Cloud.|
|Type 2|Standard I \(slb.s2.small\)|50,000|5,000|5,000|Available for purchase from the official website of Alibaba Cloud.|
|Type 3|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|Available for purchase from the official website of Alibaba Cloud.|
|Type 4|Higher I \(slb.s3.small\)|200,000|20,000|20,000|Available for purchase from the official website of Alibaba Cloud.|
|Type 5|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|Available for purchase from the official website of Alibaba Cloud.|
|Type 6|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|Available for purchase from the official website of Alibaba Cloud.|
|Type 7|Super II \(slb.s3.xlarge\)|2,000,000|200,000|100,000|Contact your account manager.|
|Type 8|Super III \(slb.s3.xxlarge\)|5,000,000|500,000|100,000|Contact your account manager.|

## How are high-performance SLB instances billed?

High-performance SLB instances are billed based on the following formula:

Total fee \(per instance\) = Instance fee + Data transfer fee or bandwidth fee + Specification fee

**Note:** The specification fee for internal-facing high-performance SLB instances is charged in the same way as Internet-facing high-performance SLB instances. However, no data transfer, bandwidth fee, or instance fee is charged for internal-facing high-performance SLB instances.

The specification fee of a high-performance SLB instance is charged based on the actual usage no matter which specification you choose.

Assume that you purchase an SLB instance of the Super I \(slb.s3.large\) specification \(Max Connection: 1,000,000; CPS: 500,000; QPS: 50,000\). The following table provides the metric values of your SLB instance within an hour.

|Max Connection|CPS|QPS|
|:-------------|:--|:--|
|90000|4000|11000|

-   The actual Max Connection value of 90,000 is between the limit of 50,000 defined in Standard I \(slb.s2.small\) and the limit of 100,000 defined in Standard II \(slb.s2.medium\). Therefore, the specification of the Max Connection metric for this hour is Standard II \(slb.s2.medium\).
-   The actual CPS value of 4,000 is between the limit of 3,000 defined in Small I \(slb.s1.small\) and the limit of 5,000 defined in Standard I \(slb.s2.small\). Therefore, the specification of the CPS metric for this hour is Standard I \(slb.s2.small\).
-   The actual QPS value of 11,000 lies between the limit of 10,000 defined in Standard II \(slb.s2.medium\) and the limit of 20,000 defined in Higher I \(slb.s3.small\). Therefore, the specification of the CPS metric for this hour is Higher I \(slb.s3.small\).

    The QPS metric uses the highest specification \(slb.s3.small\) among three metrics. Therefore, the instance is charged based on the Higher I \(slb.s3.small\) specification for this hour.


The hourly specification fee is charged based on the preceding method. The following figure shows an example.

![Method to calculate the hourly specification fee-2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2723498951/p2301.png)

Billing is more flexible for pay-as-you-go high-performance SLB instances. The specification that you select when you purchase an SLB instance represents the upper performance limit of the instance. For example, if you select Higher II \(slb.s3.medium\), the instance performance cannot be higher than Higher II \(slb.s3.medium\).

## What is the pricing of each specification?

The following table lists the pricing of each specification. In addition to the specification fee, you are also charged an instance fee and a data transfer fee. For more information, see [Pay-as-you-go](/intl.en-US/Classic Load Balancer/CLB Pricing/Pay-as-you-go.md).

|Region|Specification|Max Connection|CPS|QPS|Specification fee \(USD/hour\)|Bandwidth|
|:-----|:------------|:-------------|:--|:--|:-----------------------------|---------|
|Mainland China|Specification 1: Small I \(slb.s1.small\)|5000|3000|1000|Free of charge for a limited period|Bandwidth is charged independent of the specifications.-   Instances charged by data transfer: For more information about the instance bandwidth, see [Peak bandwidth limits](/intl.en-US/Classic Load Balancer/User Guide/Limits/Peak bandwidth limits.md).
-   Instances charged by bandwidth: The bandwidth is specified when you purchase an instance. |
|Specification 2: Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.05|
|Specification 3: Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.10|
|Specification 4: Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.20|
|Specification 5: Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.31|
|Specification 6: Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.51|
|China \(Hong Kong\) and regions outside China|Specification 1: Small I \(slb.s1.small\)|5,000|3,000|1,000|Free of charge for a limited period|Bandwidth is charged independent of the specifications.-   Instances charged by data transfer: For more information about the instance bandwidth, see [Peak bandwidth limits](/intl.en-US/Classic Load Balancer/User Guide/Limits/Peak bandwidth limits.md).
-   Instances charged by bandwidth: The bandwidth is specified when you purchase an instance. |
|Specification 2: Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.06|
|Specification 3: Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.12|
|Specification 4: Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.24|
|Specification 5: Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.37|
|Specification 6: Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.61|

## What is the optimal specification for a high-performance SLB instance?

The specification fee is charged based on your actual usage. We recommend that you select the highest specification \(slb.s3.large\) to ensure service flexibility at no extra cost. However, if the capacity of Super I \(slb.s3.large\), which is the highest-performance SLB instance type, significantly exceeds your business demand, you can select a more appropriate type, such as Higher II \(slb.s3.medium\).

## Can I change the specification of a high-performance SLB instance?

Yes, you can change the specification of a high-performance SLB instance in the console. For more information, see [包年包月实例变配]().

**Note:**

-   After a shared-resource SLB instance is changed to a high-performance SLB instance, the high-performance SLB instance cannot be changed back.
-   Some previously created SLB instances are deployed in clusters of earlier versions. If you change these instances to high-performance SLB instances, a service interruption may occur for 10 to 30 seconds due to instance migration. Other changes to configuration do not interrupt your services. We recommend that you make the change during off-peak hours.
-   The IP addresses of the instances are not affected when you change the instance configurations.

![Warnings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3723498951/p7345.png)

## When does Alibaba Cloud begin to charge a specification fee on high-performance SLB instances?

Beginning April 1, 2018, a specification fee is charged on high-performance SLB instances. You can still purchase shared-resource SLB instances.

The specification fee is charged based on the regions of high-performance SLB instances in batches.

-   The first batch:

    Start time: from April 1, 2018 to April 10, 2018

    Regions: Singapore \(Singapore\), Malaysia \(Kuala Lumpur\), Indonesia \(Jakarta\), India \(Mumbai\), US \(Silicon Valley\), and US \(Virginia\)

-   The second batch:

    Start time: from April 11, 2018 to April 20, 2018

    Regions: China \(Hangzhou\), China \(Zhangjiakou\), China \(Hohhot\), and China \(Hong Kong\)

-   The third batch:

    Start time: from April 21, 2018 to April 30, 2018

    Regions: China \(Qingdao\), China \(Beijing\), China \(Shanghai\), and China \(Shenzhen\)


## Are extra fees charged for shared-resource SLB instances in addition to the specification fee?

No.

No extra fee is charged. You can change a shared-resource SLB instance to a high-performance SLB instance by changing the specification. When you change a shared-resource SLB instance to a high-performance SLB instance, a specification fee is charged.

## Why is a high-performance SLB instance unable to reach the performance limit defined in the specification?

This issue can be explained by the cask theory.

High-performance SLB instances do not guarantee that the three metrics can reach the specification limits at the same time. The instance performance is limited as long as one of the metrics defined in the specification is reached.

Assume that you have purchased a high-performance SLB instance of the Higher I \(slb.s3.small\) specification. When the QPS of the instance reaches 20,000 but the number of maximum connections does not reach 200,000, new connection requests are dropped because the QPS limit is reached.

## Are shared-resource SLB instances still available for purchase?

No.

## Is a specification fee charged for internal-facing SLB instances?

If the internal-facing SLB instance is a shared-resource SLB instance, no specification fee is charged. If the internal-facing SLB instance is a high-performance SLB instance, a specification fee is charged.

The specification fee for internal-facing SLB instances is charged in the same way as Internet-facing SLB instances. No instance fee or data transfer fee is charged for internal-facing SLB instances.

## What do I do if I need more high-performance SLB instances?

If you need more high-performance SLB instances but the number of the instances has reached the quota, you can apply for the slb\_privilege\_allow\_more\_guaranteed\_performance\_instances privilege for a quota increase. This privilege allows you to apply for more high-performance SLB instances, but you cannot apply for more shared-resource SLB instances. For more information, see [Manage quotas](/intl.en-US/Classic Load Balancer/User Guide/Limits/Manage quotas.md).

