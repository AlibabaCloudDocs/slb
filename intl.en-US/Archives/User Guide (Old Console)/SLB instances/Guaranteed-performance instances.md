# Guaranteed-performance instances {#concept_umd_czv_tdb .concept}

Alibaba Cloud launched the guaranteed-performance instances in May 2017, and charged the capacity fee on guaranteed-performance instances on April 1, 2018.

[1. What are guaranteed-performance instances?](#section_lht_gym_vdb)

[2. How are guaranteed-performance instances billed?](#section_eth_yzm_vdb)

[3. What is the price of each capacity?](#section_n5z_s1n_vdb)

[4. How to select a guaranteed-performance instance?](#section_ifx_kcn_vdb)

[5. Can I modify the capacity after the instance is created?](#section_dmb_q2n_vdb)

[6. When will the guaranteed-performance instances be charged?](#section_gvt_kfn_vdb)

[7. After Alibaba Cloud starts to charge capacity fee on guaranteed-performance instances, will extra fees be charged on shared-performance instances?](#section_hxl_pfn_vdb)

[8. Why sometimes guaranteed-performance instances cannot reach the performance limit as defined in the capacity?](#section_ehc_vfn_vdb)

[9. Can I still buy shared-performance instances?](#section_flq_wfn_vdb)

[10. Will intranet SLB instances be charged for capacity fee?](#section_nfy_xfn_vdb)

## 1. What are guaranteed-performance instances? {#section_lht_gym_vdb .section}

A guaranteed-performance instance provides guaranteed performance metrics \(performance SLA\). It is opposite to a shared-performance instance. For a shared-performance instance, the performance metrics are not guaranteed and the resources are shared by all instances.

All instances are shared-performance instances before Alibaba launches guaranteed-performance instances. You can view the instance type on the console.

Hover your mouse pointer to the green icon of the target instance to view the performance metrics, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4113/15647275302294_en-US.png)

The following are three key performance metrics for guaranteed-performance instances:

-   Max Connection

    The maximum number of connections to a SLB instance. When the maximum number of connections reaches the limits of the capacity, the new connection will be dropped.

-   Connection Per Second \(CPS\)

    The rate at which a new connection is established per second. When the CPS reaches the limits of the capacity, the new connection will be dropped.

-   Query Per Second \(QPS\)

    The number of HTTP/HTTPS requests that can be processed per second. When the QPS reaches the limits of the capacity, the new connection will be dropped.


Alibaba Cloud Server Load Balancer provides the following capacities for guaranteed-performance instances:

|Type|Type|Max Connection|CPS|QPS|
|:---|:---|:-------------|:--|:--|
|Capacity 1|Small I \(slb.s1.small\)|5,000|3,000|1,000|
|Capacity 2|Standard I \(slb.s2.small\)|50,000|5,000|5,000|
|Capacity 3|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|
|Capacity 4|Higher I \(slb.s3.small\)|200,000|20,000|20,000|
|Capacity 5|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|
|Capacity 6|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|

If you want to use a larger capacity, contact your customer manager.

## 2. How are guaranteed-performance instances billed? {#section_eth_yzm_vdb .section}

Guaranteed-performance instances are billed as follows:

Total fee \(per instance\) = instance fee + traffic fee + capacity fee

**Note:** For intranet SLB instances, you can also choose to use guaranteed-performance instances. If guaranteed-performance instances are selected, capacity fee is collected and billed as the Internet SLB instance, but no traffic fee and instance fee are collected.

The performance guarantee instance specification fee is charged by usage, no matter what kind of specification you choose, the instance specification fee will be charged according to the specifications you actually use.

For example, if you purchase the slb.s3.large capacity \(1,000,000; CPS 500,000; QPS 50,000\) and the actual usage of your instance in an hour is as follow:

|Max Connection|CPS|QPS|
|:-------------|:--|:--|
|90,000|4,000|11,000|

-   From the perspective of Max Connection, the actual metrics 90,000 occurs between the limit 50,000 defined in the Standard I \(slb.s2.small\) capacity and the limit 100,000 defined in the Standard II \(slb.s2.medium\) capacity. Therefore, the capacity of the Max Connection metrics in this hour is Standard II \(slb.s2.medium\).
-   From the perspective of CPS, the actual metrics 4,000 occurs between the limit 3,000 defined in the Small I \(slb.s1.small\) capacity and the limit 5,000 defined in the Standard I \(slb.s2.small\) capacity. Therefore, the capacity of the CPS metrics in this hour is Standard I \(slb.s2.small\).
-   From the perspective of QPS, the actual metrics 11,000 occurs between the limit 10,000 defined in the Standard II \(slb.s2.medium\) capacity and the limit 20,000 defined in the Higher I \(slb.s3.small\) capacity. Therefore, the capacity of the QPS metrics in this hour is Higher I \(slb.s3.small\)

    Comparing these three metrics, the capacity of the QPS metrics is highest, therefore, the capacity fee of the instance in this hour is charged at the price of the Higher I \(slb.s3.small\) capacity.


The following figure is an example showing how the capacity fee is billed for an SLB instance in the first three hours:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4113/15647275302301_en-US.png)

The billing of the guaranteed-performance instances is flexible. The capacity you select when purchasing an instance is the performance limitation of the instance. For example, if slb.s3.medium is selected, the new connections are dropped when the HTTP requests in one second reach 30,000.

## 3. What is the price of each capacity? {#section_n5z_s1n_vdb .section}

The following table lists the capacity price of each capacity. In addition to the capacity fee, you are also charged for instance fee and traffic fee. For more information, see [Billing method](../../../../reseller.en-US/Pricing/Billing method.md#).

|Region|Type|Max Connection|CPS|QPS|Capacity fee \(USD/Hour\)|
|:-----|:---|:-------------|:--|:--|:------------------------|
| China \(Hangzhou\)

 China \(Zhangjiakou\)

 China \(Hohhot\)

 China \(Qingdao\)

 China \(Beijing\)

 China \(Shanghai\)

 China \(Shenzhen\)

 |Small I \(slb.s1.small\)|5,000|3,000|1,000|Free|
|Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.05|
|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.10|
|Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.20|
|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.31|
|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.51|
| Singapore

 Malaysia \(Kuala Lumpur\)

 Indonesia \(Jakarta\)

 India \(Mumbai\)

 US \(Silicon Valley\)

 US \(Virginia\)

 China \(Hong Kong\)

 |Small I \(slb.s1.small\)|5,000|3,000|1,000|Free|
|Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.06|
|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.12|
|Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.24|
|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.37|
|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.61|

Capacity fees of guaranteed-performance instances in the international regions enjoy an 83% discount.

## 4. How to select a guaranteed-performance instance? {#section_ifx_kcn_vdb .section}

Because the capacity fee is billed based on the actual usage, we recommend that you select the largest capacity \(slb.s3.large\). This guarantees the business flexibility \(flexibility\) and will not cause extra costs. If your traffic does not reach the largest capacity, you can select a more reasonable capacity, such as slb.s3.medium.

## 5. Can I modify the capacity after the instance is created? {#section_dmb_q2n_vdb .section}

Yes. You can change the capacity at any time and the change takes effect immediately.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4113/15647275302324_en-US.png)

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4113/15647275312325_en-US.png)

**Note:** 

-   After you change a shared-performance instance to a guaranteed-performance instance, you cannot change it back.
-   Some SLB servers are deployed in old clusters. If you change a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds. We recommend that you change the specification when the business is not busy.
-   The IP of the SLB instance will not be changed after you changing the instance type or the capacity.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4113/15647275312326_en-US.png)

## 6. When will the guaranteed-performance instances be charged? {#section_gvt_kfn_vdb .section}

Alibaba Cloud launched the guaranteed-performance instances in May 2017, and charged the capacity fee on guaranteed-performance instances on April 1, 2018.

The capacity fee takes effect in batches as follows:

-   The first batch:

    Time: From April 1st to April 10th

    Regions: Singapore, Malaysia \(Kuala Lumpur\), Indonesia \(Jakarta\), India \(Mumbai\), US \(Silicon Valley\), US \(Virginia\)

-   The second batch:

    Time: From April 11th to April 20th

    Regions: China \(Hangzhou\), China \(Zhangjiakou\), China \(Hohhot\), China \(Hong Kong\)

-   The third batch:

    Time: From April 21th to April 30th

    Regions: China \(Qingdao\), China \(Beijing\), China \(Shanghai\), China \(Shenzhen\)


## 7. After Alibaba Cloud starts to charge capacity fee on guaranteed-performance instances, will extra fees be charged on shared-performance instances? {#section_hxl_pfn_vdb .section}

No.

The billing of the original shared-performance instances is the same if you do not change it to a performance-guaranteed instance. You can change a shared-performance instance to a guaranteed-performance instance. After changing to the guaranteed-performance instance, capacity fees are collected.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4113/15647275312327_en-US.png)

## 8. Why sometimes guaranteed-performance instances cannot reach the performance limit as defined in the capacity? {#section_ehc_vfn_vdb .section}

The cask theory.

Guaranteed-performance instances do not guarantee that the three metrics can reach the capacity limits at the same time. The limitation is triggered as long as a metric first reaches the limitation defined in the capacity.

For example, you have purchased a guaranteed-performance instance of the Higher I \(slb.s3.small\) capacity. When the QPS of the instance reaches 20,000 but the number of maximum connections does not reach 200,000, the new connections are still dropped because the QPS has reached the limitation.

## 9. Can I still buy shared-performance instances? {#section_flq_wfn_vdb .section}

Yes.

However, shared-performance instances will be phased out in the future. Please pay attention to the official announcement.

## 10. Will intranet SLB instances be charged for capacity fee? {#section_nfy_xfn_vdb .section}

If the intranet SLB instance is a shared-performance instance, no capacity fee is charged. If the intranet SLB instance is a guaranteed-performance instance, corresponding capacity fee is charged, and no other fees are charged.

