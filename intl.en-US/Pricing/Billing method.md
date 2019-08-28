# Billing method {#concept_dph_vfs_wdb .concept}

The fees for a Server Load Balancer \(SLB\) instance are calculated using the Pay-As-You-Go billing method and are calculated based on your actual traffic usage. You can release a Pay-As-You-Go instance at any time.

To purchase a Pay-As-You-Go SLB instance, go to [the purchase page](https://common-buy-intl.alibabacloud.com/?spm=5176.11783163.content.slbList_setting_buyslb.6fe8679bLl5zeT&commodityCode=slb_intl#/buy).

## Billing items {#section_g0i_yr1_3ce .section}

The following table details the items that are billed. Billing items vary by network type and instance type, as shown in the following table.

**Note:** “-” means that the corresponding item is not billed, and “✔” means that the corresponding item is billed.

|Network type|Instance type|Instance fee|Traffic fee|Specification fee|
|:-----------|:------------|:-----------|:----------|:----------------|
|Internet|Shared-performance instances|✔|✔|-|
|Guaranteed-performance instances|✔|✔|✔|
|Intranet|Shared-performance instances|-|-|-|
|Guaranteed-performance instances|-|-|✔|

## Instance fee {#section_053_v2x_jw7 .section}

SLB instances that communicate through the Internet are charged for public IP address reservations. SLB instances that communicate through the intranet do not incur such charges. Instance fees for SLB instances that use the Internet are calculated as follows:

-   Instance fee = unit price × instance reservation time

    The reservation time is the period from the time at which the instance is created to the time at which the instance is released.

-   Instance fees are billed on an hourly basis. If your period of usage is less than one hour, the bill is rounded up to one hour.


If the price on the purchase page of the console is different from the price listed in the following table, take the price on the purchase page as the standard.

|Region|Instance fee \(USD/hour\)|
|:-----|:------------------------|
|China \(Hangzhou\), China \(Beijing\), China \(Shenzhen\), China \(Shanghai\), China \(Zhangjiakou\)|0.003|
|China \(Qingdao\)|0.003|
|China \(Hong Kong\)|0.009|
|US \(Virginia\), US \(Silicon Valley\)|0.005|
|Singapore|0.006|
|Japan \(Tokyo\)|0.009|
|Germany \(Frankfurt\)|0.006|
|UAE \(Dubai\)|0.009|
|Australia \(Sydney\)|0.006|

## Traffic fee {#section_r4x_jlm_83f .section}

SLB instances that communicate through the Internet incur traffic fees based on your usage. However, SLB instances that communicate through the intranet can be used free of charge. Traffic fees for SLB instances that use the Internet are calculated as follows:

-   Internet traffic fee = unit traffic price × time

    Internet traffic is the outbound \(downstream\) traffic. Inbound \(upstream\) traffic is not charged.

-   Traffic fees are billed on an hourly basis. If your period of usage is less than one hour, the bill is rounded up to one hour.

    If the price on the purchase page of the console is different from the price listed in the following table, take the price on the purchase page as the standard.

    |Region|Traffic fee \(USD/Gbit/s\)|
    |:-----|:-------------------------|
    |China \(Hangzhou\), China \(Beijing\), China \(Shenzhen\), China \(Shanghai\), China \(Zhangjiakou\)|0.125|
    |China \(Qingdao\)|0.113|
    |China \(Hong Kong\)|0.156|
    |US \(Virginia\), US \(Silicon Valley\)|0.078|
    |Singapore|0.117|
    |Japan \(Tokyo\)|0.120|
    |Germany \(Frankfurt\)|0.070|
    |UAE \(Dubai\)|0.447|
    |Australia \(Sydney\)|0.096|


## Specification fee {#section_r13_y1h_j2b .section}

The following are three key performance metrics for guaranteed-performance instances. The limits of these metrics are different for instances of different specifications. For more information, see [Guaranteed-performance instance FAQs](../reseller.en-US/FAQ/Guaranteed-performance instance FAQ.md#).

-   Max Connection

    The maximum number of connections to an SLB instance. When the number of connections reaches the limit of the specification, new connections will be dropped.

-   Connection Per Second \(CPS\)

    The rate at which new connections are established per second. When the CPS reaches the limit of the specification, new connections will be dropped.

-   Query Per Second \(QPS\)

    The number of HTTP/HTTPS requests that can be processed per second. This metric is available only for Layer-7 SLB listeners. When the QPS reaches the limit of the specification, new connections will be dropped.


The specification fee of a guaranteed-performance instance is charged based on your actual usage. If the actual performance of the instance is between two specifications, the specification fee is calculated according to the higher specification.

For example, you choose the specification of slb.s3.large \(Max Connection: 1,000,000; CPS: 500,000; QPS: 50,000\), and the actual usage of the instance in an hour is as follows:

|Max Connection|CPS|QPS|
|:-------------|:--|:--|
|90,000|4,000|11,000|

-   With respect to Max Connection, the actual metric value of 90,000 lies between the limit of 50,000 defined in Standard I \(slb.s2.small\) and the limit of 100,000 defined in Standard II \(slb.s2.medium\). Therefore, the specification of the Max Connection metric for this hour is Standard II \(slb.s2.medium\).

-   With respect to CPS, the actual metric value of 4,000 occurs between the limit of 3,000 defined in the Small I \(slb.s1.small\) specification and the limit of 5,000 defined in the Standard I \(slb.s2.small\) specification. Therefore, the specification of the CPS metric for this hour is Standard I \(slb.s2.small\).

-   With respect to QPS, the actual metric value of 11,000 occurs between the limit of 10,000 defined in Standard II \(slb.s2.medium\) and the limit of 20,000 defined in Higher I \(slb.s3.small\). Therefore, the specification of the QPS metric for this hour is Higher I \(slb.s3.small\).

    Out of the three metrics, QPS has the highest instance specification. Therefore, the specification fee of the instance in this hour is charged according to the price of the Higher I \(slb.s3.small\) specification.


The following figure provides a demonstration of how the specification fee is billed for an SLB instance:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13418/15669622523113_en-US.png)

The billing is more flexible for guaranteed-performance instances. The specification you select when purchasing an instance is the higher performance limit of the instance. For example, if you select slb.s3.medium, new requests will be dropped when requests reach 30,000 in one second.

The prices detailed in the following table are for reference purposes only. The price you see on the console will more accurately reflect your usage.

|Region|Specification|Max Connection|CPS|QPS|Specification fee \(USD/hour\)|
|:-----|:------------|:-------------|:--|:--|:-----------------------------|
| China \(Hangzhou\)

 China \(Zhangjiakou\)

 China \(Hohhot\)

 China \(Qingdao\)

 China \(Beijing\)

 China \(Shanghai\)

 China \(Shenzhen\)

 |Small I \(slb.s1.small\)|5,000|3,000|1,000|Free of charge|
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

 |Small I \(slb.s1.small\)|5,000|3,000|1,000|Free of charge|
|Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.06|
|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.12|
|Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.24|
|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.37|
|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.61|

