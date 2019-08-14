# Guaranteed-performance instance FAQ {#concept_umd_czv_tdb .concept}

Guaranteed-performance Server Load Balancer \(SLB\) instances are instances whose performance is guaranteed in terms of specific indicators, such as the maximum number of connections, Connection Per Second \(CPS\), and Query Per Second \(QPS\). Note that Alibaba Cloud now charges specification fees for guaranteed-performance instances.

The following are frequently asked questions about guaranteed-performance instances:

-   [What is a guaranteed-performance instance?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#section_lht_gym_vdb)
-   [How are guaranteed-performance instances billed?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#section_eth_yzm_vdb)
-   [What is the price of each specification?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#section_n5z_s1n_vdb)
-   [What is the optimal specification for a guaranteed-performance instance?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#section_ifx_kcn_vdb)
-   [Can I change the specification of my SLB instance after it is created?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#p7)
-   [When did Alibaba Cloud begin to charge specification fees on guaranteed-performance instances?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#section_gvt_kfn_vdb)
-   [Is an extra fee included for shared-performance instances after Alibaba Cloud starts charging for the specification fee?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#section_hxl_pfn_vdb)
-   [Why sometimes guaranteed-performance instances cannot reach the performance limit defined in the specification?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#section_ehc_vfn_vdb)
-   [Are shared-performance instances still available for purchase?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#section_flq_wfn_vdb)
-   [Is a specification fee charged for intranet SLB instances?](reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#section_nfy_xfn_vdb)

## What is a guaranteed-performance instance? {#section_lht_gym_vdb .section}

A guaranteed-performance instance provides guaranteed performance metrics \(performance SLA\) and is opposite to a shared-performance instance. For a shared-performance instance, performance metrics are not guaranteed and resources are shared by all instances.

All instances were shared-performance instances before Alibaba Cloud launched guaranteed-performance instances. You can view the instance type in the SLB console.

You can rest the pointer over the question mark icon of the target guaranteed-performance instance to view the performance metrics, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15642/15658021617175_en-US.png)

The following are three key performance metrics for guaranteed-performance instances:

-   Max Connection

    The maximum number of connections to an SLB instance. When the number of connections reaches the limit of the specification, new connection requests will be dropped.

-   Connection Per Second \(CPS\)

    The rate at which new connections are established per second. When the CPS reaches the limit of the specification, new connection requests will be dropped.

-   Query Per Second \(QPS\)

    The number of HTTP/HTTPS requests that can be processed per second. This metric is available only for Layer-7 SLB listeners. When the QPS reaches the limit of the specification, new connection requests will be dropped.


Alibaba Cloud SLB provides the following specifications for guaranteed-performance instances:

|Type|Specification|Max Connection|CPS|QPS|
|:---|:------------|:-------------|:--|:--|
|Specification 1|Small I \(slb.s1.small\)|5,000|3,000|1,000|
|Specification 2|Standard I \(slb.s2.small\)|50,000|5,000|5,000|
|Specification 3|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|
|Specification 4|Higher I \(slb.s3.small\)|200,000|20,000|20,000|
|Specification 5|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|
|Specification 6|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|

If you want to use a larger specification, contact your customer manager.

## How are guaranteed-performance instances billed? {#section_eth_yzm_vdb .section}

Guaranteed-performance instances are billed as follows:

Total fee \(per instance\) = instance fee + traffic fee + specification fee

**Note:** The specification fee is charged on intranet guaranteed-performance instances in the same way as Internet guaranteed-performance instances. But no traffic fee or instance fee is charged for intranet guaranteed-performance instances.

The specification fee of a guaranteed-performance instance is charged based on actual usage. No matter what specification you choose, the specification fee will be charged according to the specification you actually use.

For example, if you purchase the Super I specification \(Max Connection: 1,000,000; CPS: 100,000; QPS: 50,000\) and the actual usage of your instance in an hour is as follows:

|Max Connection|CPS|QPS|
|:-------------|:--|:--|
|90,000|4,000|11,000|

-   With respect to Max Connection, the actual metric value of 90,000 lies between the limit of 50,000 defined in Standard I \(slb.s2.small\) and the limit of 100,000 defined in Standard II \(slb.s2.medium\). Therefore, the specification of the Max Connection metric for this hour is Standard II \(slb.s2.medium\).
-   With respect to CPS, the actual metric value of 4,000 occurs between the limit of 3,000 defined in the Small I \(slb.s1.small\) specification and the limit of 5,000 defined in the Standard I \(slb.s2.small\) specification. Therefore, the specification of the CPS metric for this hour is Standard I \(slb.s2.small\).
-   With respect to QPS, the actual metric value of 11,000 occurs between the limit of 10,000 defined in Standard II \(slb.s2.medium\) and the limit of 20,000 defined in Higher I \(slb.s3.small\). Therefore, the specification of the QPS metric for this hour is Higher I \(slb.s3.small\).

    Out of the three metrics, QPS has the highest instance specification. Therefore, the specification fee of the instance in this hour is charged according to the price of the Higher I \(slb.s3.small\) specification.


The following figure is an example showing how the specification fee is billed for an SLB instance:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4113/15658021612301_en-US.png)

The billing is more flexible for guaranteed-performance instances. The specification you select when purchasing an instance is the higher performance limit of the instance. For example, if you select Higher II \(slb.s3.medium\), new requests will be dropped when requests reach 30,000 in one second.

## What is the price of each specification? {#section_n5z_s1n_vdb .section}

The following table lists the price of each specification. In addition to the specification fee, you are also charged for instance fee and traffic fee. For more information, see [Billing method](../reseller.en-US/Pricing/Billing method.md#).

|Region|Specification|Max Connection|CPS|QPS|Specification fee \(USD/hour\)|
|:-----|:------------|:-------------|:--|:--|:-----------------------------|
| China \(Hangzhou\)

 China \(Zhangjiakou\)

 China \(Hohhot\)

 China \(Qingdao\)

 China \(Beijing\)

 China \(Shanghai\)

 China \(Shenzhen\)

 |Specification 1: Small I \(slb.s1.small\)|5,000|3,000|1,000|Free of charge|
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

 |Specification 1: Small I \(slb.s1.small\)|5,000|3,000|1,000|Free of charge|
|Specification 2: Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.06|
|Specification 3: Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.12|
|Specification 4: Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.24|
|Specification 5: Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.37|
|Specification 6: Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.61|

## What is the optimal specification for a guaranteed-performance instance? {#section_ifx_kcn_vdb .section}

Because the specification fee is billed based on actual usage, we recommend that you select the largest specification \(slb.s3.large\). This guarantees your service flexibility and will not cause extra costs. If your traffic does not reach the largest specification, you can select a more reasonable specification, such as slb.s3.medium.

## Can I change the specification of my SLB instance after it is created? {#p7 .section}

Yes. You can change the specification in the console at any time and the change takes effect immediately.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15642/15658021617343_en-US.png)

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15642/15658021617344_en-US.png)

**Note:** 

-   After a shared-performance instance is changed to a guaranteed-performance instance, it cannot be changed back.
-   Some previously created SLB instances are deployed in old clusters. If you change a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds. Therefore, for such scenarios, we recommend that you make the change when the traffic is low.
-   IP addresses of SLB instances will not be affected after you change the instance type or the specification.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15642/15658021617345_en-US.png)

## When did Alibaba Cloud begin to charge specification fees on guaranteed-performance instances? {#section_gvt_kfn_vdb .section}

Alibaba Cloud began to charge specification fee on guaranteed-performance instances from April 1, 2018, and continues to sell shared-performance instances.

The charging of specification fee takes effect in batches as follows:

-   The first batch:

    Start time: From April 1, 2018 to April 10, 2018

    Effective regions: Singapore, Malaysia \(Kuala Lumpur\), Indonesia \(Jakarta\), India \(Mumbai\), US \(Silicon Valley\), US \(Virginia\)

-   The second batch:

    Start time: From April 11, 2018 to April 20, 2018

    Effective regions: China \(Hangzhou\), China \(Zhangjiakou\), China \(Hohhot\), China \(Hong Kong\)

-   The third batch:

    Start time: From April 21, 2018 to April 30, 2018

    Effective regions: China \(Qingdao\), China \(Beijing\), China \(Shanghai\), China \(Shenzhen\)


## Is an extra fee included for shared-performance instances after Alibaba Cloud starts charging for the specification fee? {#section_hxl_pfn_vdb .section}

No.

Extra fees are not charged for shared-performance instances unless you change them to guaranteed-performance instances.

## Why sometimes guaranteed-performance instances cannot reach the performance limit defined in the specification? {#section_ehc_vfn_vdb .section}

It applies the cask theory.

Guaranteed-performance instances do not guarantee that the three metrics can reach the specification limits at the same time. The limitation is triggered as long as a metric reaches the limit defined in the specification.

When the QPS of the instance reaches 20,000 but the number of maximum connections does not reach 200,000, new connections are still dropped because the QPS has reached the limit.

## Are shared-performance instances still available for purchase? {#section_flq_wfn_vdb .section}

Yes.

Shared-performance instances are still available now, but they will be phased out in the future. Please pay attention to official announcements or emails.

## Is a specification fee charged for intranet SLB instances? {#section_nfy_xfn_vdb .section}

If the intranet SLB instance is a shared-performance instance, no specification fee is charged. If the intranet SLB instance is a guaranteed-performance instance, a specification fee is charged. The calculation method of the specification fee for intranet instances is the same as that for Internet instances. No instance fee or traffic fee is charged for intranet instances.

