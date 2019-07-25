# How to use guaranteed-performance Server Load Balancer instances? {#concept_umd_czv_tdb .concept}

Alibaba Cloud plans to charge specification fee on guaranteed-performance Server Load Balancer instances from April 1th, 2018, and continue to sell shared-performance Server Load Balancer instances.

## 1. What are guaranteed-performance instances? {#section_lht_gym_vdb .section}

A guaranteed-performance instance provides guaranteed performance metrics \(performance SLA\) and is opposite to a shared-performance instance. For a shared-performance instance, the performance metrics are not guaranteed and the resources are shared by all instances.

All instances are shared-performance instances before Alibaba launches guaranteed-performance instances. You can view the instance type on the console.

Hover your mouse pointer to the green icon of the target instance to view the performance metrics, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15444272613277_en-US.png)

The following are three key performance metrics for guaranteed-performance instances:

-   Max Connection

    The maximum number of connections to a SLB instance. When the maximum number of connections reaches the limits of the capacity, the new connection will be dropped.

-   Connection Per Second \(CPS\)

    The rate at which a new connection is established per second. When the CPS reaches the limits of the capacity, the new connection will be dropped.

-   Query Per Second \(QPS\)

    The number of HTTP/HTTPS requests that can be processed per second. This metrics is only available for Layer-7 Server Load Balancer. When the QPS reaches the limits of the specification, the new connection will be dropped.


Alibaba Cloud Server Load Balancer provides the following capacities for guaranteed-performance instances:

|Type|Specification|Max Connection|Connection Per Second \(CPS\)|Query Per Second \(QPS\)|
|:---|:------------|:-------------|:----------------------------|:-----------------------|
|Specification 1|Small I \(slb.s1.small\)|5,000|3,000|1,000|
|Specification 2|Standard I \(slb.s2.small\)|50,000|5,000|5,000|
|Specification 3|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|
|Specification 4|Higher I \(slb.s3.small\)|200,000|20,000|20,000|
|Specification 5|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|
|Specification 6|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|

If you want to use a larger specification, contact your customer manager.

## 2. How are guaranteed-performance instances billed? {#section_eth_yzm_vdb .section}

Guaranteed-performance instances are billed as follows:

Total fee \(per instance\) = instance fee + traffic fee + specification fee

**Note:** You can select a shared-performance intranet SLB instance or a guaranteed-performance intranet SLB instance. Specification fee is charged on intranet guaranteed-performance instances in the same way as Internet guaranteed-performance instances. But intranet guaranteed-performance instances are free from traffic fee and instance fee.

The specification fee of a performance-guarantee instance is charged by usage. No matter what kind of specification you choose, the instance specification fee will be charged according to the specification you actually use.

For example, if you purchase the slb.s3.large specification \(1,000,000; CPS 500,000; QPS 50,000\) and the actual usage of your instance in an hour is as follow:

|Max Connection|CPS|QPS|
|:-------------|:--|:--|
|90,000|4,000|11,000|

-   From the perspective of Max Connection, the actual metrics 90,000 occurs between the limit 50,000 defined in the Standard I \(slb.s2.small\) specification and the limit 100,000 defined in the Standard II \(slb.s2.medium\) specification. Therefore, the specification of the Max Connection metrics in this hour is Standard II \(slb.s2.medium\).
-   From the perspective of CPS, the actual metrics 4,000 occurs between the limit 3,000 defined in the Small I \(slb.s1.small\) specification and the limit 5,000 defined in the Standard I \(slb.s2.small\) specification. Therefore, the specification of the CPS metrics in this hour is Standard I \(slb.s2.small\).
-   From the perspective of QPS, the actual metrics 11,000 occurs between the limit 10,000 defined in the Standard II \(slb.s2.medium\) specification and the limit 20,000 defined in the Higher I \(slb.s3.small\) specification. Therefore, the specification of the QPS metrics in this hour is Higher I \(slb.s3.small\).

    Comparing these three metrics, the specification of the QPS metrics is highest, therefore, the specification fee of the instance in this hour is charged at the price of the Higher I \(slb.s3.small\) specification.


The following figure is an example showing how the specification fee is billed for an SLB instance in the first three hours:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4113/15444272612301_en-US.png)

The billing of the guaranteed-performance instances is flexible. The capacity you select when purchasing an instance is the performance limitation of the instance. For example, if slb.s3.medium is selected, the new connections are dropped when the HTTP requests in one second reach 30,000.

## 3. What is the price of each specification? {#section_n5z_s1n_vdb .section}

The following table lists the price of each specification. In addition to the specification fee, you are also charged for instance fee and traffic fee. For more information, see [Pay-As-You-Go](../reseller.en-US/Pricing/Pay-As-You-Go.md#).

|Region|Specification|Max Connection|CPS|QPS|Specification fee \(USD/hour\)|
|:-----|:------------|:-------------|:--|:--|:-----------------------------|
| China \(Hangzhou\)

 China \(Zhangjiakou\)

 China \(Hohhot\)

 China \(Qingdao\)

 China \(Beijing\)

 China \(Shanghai\)

 China \(Shenzhen\)

 |Specification 1: Small I \(slb.s1.small\)|5,000|3,000|1,000|Free|
|Specification 2: Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.05|
|Specification 3: Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.10|
|Specification 4: Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.20|
|Specification 5: Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.31|
|Specification 6: Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.51|
| Singapore

 Malaysia \(Kuala Lumpur\)

 Indonesia \(Jakarta\)

 India \(Mumbai\)

 US \(Silicon Valley\)

 US \(Virginia\)

 China \(Hong Kong\)

 |Specification 1: Small I \(slb.s1.small\)|5,000|3,000|1,000|Free|
|Specification 2: Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.06|
|Specification 3: Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.12|
|Specification 4: Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.24|
|Specification 5: Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.37|
|Specification 6: Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.61|

## 4. How to select a guaranteed-performance instance? {#section_ifx_kcn_vdb .section}

Because the specification fee is billed based on the actual usage, we recommend that you select the largest specification \(slb.s3.large\). This guarantees the business flexibility \(flexibility\) and will not cause extra costs. If your traffic does not reach the largest specification, you can select a more reasonable specification, such as slb.s3.medium.

## 5. Can I modify the specification after the instance is created? {#section_dmb_q2n_vdb .section}

Yes. You can change the specification at any time and the change takes effect immediately.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15444272613284_en-US.png)

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15444272613287_en-US.png)

**Note:** 

-   Once a shared-performance instance is changed to a guaranteed-performance instance, it cannot be changed back.
-   Some instances may exist in older clusters due to historical stock. If you change a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds. Therefore, we recommend that changing the capacity in period of low traffic volume or performing load balancing among instances through [GSLB](https://promotion.aliyun.com/ntms/act/globalslb.html?spm=5176.71615.741495.1.307291894icRpB&wh_ttid=pc) first.
-   The IP of the SLB instance will not be changed after you changing the instance type or the capacity.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4163/15444272613288_en-US.png)

## 6. When will the guaranteed-performance instances be charged? {#section_gvt_kfn_vdb .section}

Alibaba Cloud plans to charge specification fee on guaranteed-performance Server Load Balancer instances from April 1st, 2018, and continue to sell shared-performance Server Load Balancer instances.

The charging of specification fee will take effect in batches as follows:

-   The first batch:

    Effective time: From April 1 to April 10

    Regions: Singapore, Malaysia \(Kuala Lumpur\), Indonesia \(Jakarta\), India \(Mumbai\), US \(Silicon Valley\), US \(Virginia\)

-   The second batch:

    Effective time: From April 11 to April 20

    Effective regions: China \(Hangzhou\), China \(Zhangjiakou\), China \(Hohhot\), China \(Hong Kong\)

-   The third batch:

    Effective time: From April 21 to April 30

    Effective regions: China \(Qingdao\), China \(Beijing\), China \(Shanghai\), China \(Shenzhen\)


## 7. After Alibaba Cloud starts to charge specification fee on guaranteed-performance instances, will extra fees be charged on shared-performance instances? {#section_hxl_pfn_vdb .section}

No.

The billing of the original shared-performance instances is the same if you do not change it to a performance-guaranteed instance. However, if you change the shared-performance instance to the guaranteed-performance one, the specification fee will be charged.

## 8. Why sometimes guaranteed-performance instances cannot reach the performance limit as defined in the specification? {#section_ehc_vfn_vdb .section}

It applies the cask theory.

Guaranteed-performance instances do not guarantee that the three metrics can reach the specification limits at the same time. The limitation is triggered as long as a metric first reaches the limitation defined in the specification.

For example, you have purchased a guaranteed-performance instance of the Higher I \(slb.s3.small\) specification. When the QPS of the instance reaches 20,000 but the number of maximum connections does not reach 200,000, the new connections are still dropped because the QPS has reached the limitation.

## 9. Can I still buy shared-performance instances? {#section_flq_wfn_vdb .section}

Yes.

However, shared-performance instances will be phased out in the future. Please pay attention to the official announcement.

## 10. Will intranet SLB instances be charged for specification fee? {#section_nfy_xfn_vdb .section}

If the intranet SLB instance is a shared-performance instance, no specification fee is charged. If the intranet SLB instance is a guaranteed-performance instance, corresponding specification fee is charged, and no other fees are charged. The specification fees are collected as the same as the Internet guaranteed-performance instances, but intranet guaranteed-performance instances are free from instance fee and traffic fee.

