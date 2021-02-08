# Pay-as-you-go

SLB instances support the pay-as-you-go method and are billed based on actual traffic. You can release pay-as-you-go instances at any time.

## Pay-by-traffic

To purchase a pay-by-traffic SLB instance, go to the [buy page](https://common-buy-intl.alibabacloud.com/?spm=5176.11783163.content.slbList_setting_buyslb.6fe8679bLl5zeT&commodityCode=slb_intl#/buy).

## Billing items

The total fees of an instance is the sum of all billing items. The following table lists billing items, which vary with network and performance types.

**Note:** "-" indicates that the fee is not charged and "✔" indicates that the fee is charged.

|Network type|Performance type|Instance fee|Traffic fee|Specification fee|
|:-----------|:---------------|:-----------|:----------|:----------------|
|Internet instance|Shared-performance instance|✔|✔|-|
|Guaranteed-performance instance|✔|✔|✔|
|Internal instance|Shared-performance instance|-|-|-|
|Guaranteed-performance instance|-|-|✔|

## Pay-by-bandwidth

Pay-by-bandwidth instances are billed in the following ways:

**Note:**

-   The billing items vary with network and performance types. For more information, see [t4098.md\#section\_v1h\_35t\_tdb](). For example, only instance fees and bandwidth fees are charged for shared-performance Internet instances.
-   The peak inbound bandwidth of a pay-by-bandwidth instance is the same as the peak outbound bandwidth.
-   For pay-by-bandwidth instances, fees are independent of instance status and traffic usage. Instances are charged after they are created and until they are released.

-   Instance fee = Unit price × Instance retention period

    The retention period lasts from the time when the instance is created to the time when the instance is released.

-   Bandwidth fee = Daily peak bandwidth × Unit bandwidth price × Duration

    Bandwidth fees are billed on an hourly basis and settled on an daily basis. If you use an instance for less than one hour, the duration is calculated as one hour. If the instance runs for less than one day, it is calculated by multiplying the actual hours by the unit price of the maximum bandwidth for the day.

    The bandwidth fee is based on the bandwidth selected when an instance is created. However, if you change the bandwidth within a billing cycle, the bandwidth fee is based on the maximum bandwidth within that billing cycle.

-   Specification fee: The specification fee of a guaranteed-performance instance is charged based on your actual usage.

    **Note:** Whitelist-allowed specifications refer to specifications higher than slb.s3.large \(exclusive\) and are not included.


The prices listed in the following table are for reference only. For more information, see the Server Load Balancer console.

|Region|Instance fee \(USD/hour\)|Instance fee \(USD/day\)|1-5 Mbit/s bandwidth fee \(USD/hour\)|1-5 Mbit/s bandwidth fee \(USD/day\)|Over 5 Mbit/s bandwidth fee \(USD/hour\)|Over 5 Mbit/s bandwidth fee \(USD/day\)|
|------|-------------------------|------------------------|-------------------------------------|------------------------------------|----------------------------------------|---------------------------------------|
|China \(Hangzhou\), China \(Shanghai\), China \(Beijing\), China \(Zhangjiakou\), China \(Hohhot\), China \(Shenzhen\), China \(Chengdu\), and China \(Heyuan\)|0.003|0.072|0.006|0.144|0.02|0.48|
|China \(Qingdao\)|0.003|0.072|0.005|0.12|0.016|0.384|
|China \(Hong Kong\)|0.009|0.216|0.006|0.144|0.02|0.48|
|Singapore, Indonesia \(Jakarta\), India \(Mumbai\), Malaysia \(Kuala Lumpur\), Germany \(Frankfurt\), UK \(London\), and Australia \(Sydney\)|0.04|0.96|0.035|0.84|0.12|2.88|
|Japan \(Tokyo\)|0.009|0.216|0.007|0.168|0.023|0.552|
|UAE \(Dubai\)|0.009|0.216|0.048|11.52|0.118|2.832|
|US \(Silicon Valley\) and US \(Virginia\)|0.005|0.12|0.006|0.144|0.02|0.48|

## Instance fees

Instance fees are charged for Internet instances, which use public IP addresses.

**Note:** Internal instances are exempt from instance fees.

Instance fees for Internet instances are calculated in the following way:

-   Instance fee = Unit price × Instance retention period

    The retention period lasts from the time when the instance is created to the time when the instance is released.

-   Instance fees are billed on an hourly basis and settled in real time. If you use an instance for less than one hour within a billing cycle, the retention period is calculated as one hour.


The prices listed in the following table are for reference only. For more information, see the Server Load Balancer console.

|Region|Instance fee \(USD/hour\)|
|:-----|:------------------------|
|China \(Hangzhou\), China \(Beijing\), China \(Qingdao\), China \(Shenzhen\), China \(Shanghai\), China \(Zhangjiakou\), China \(Hohhot\), China \(Heyuan\), and China \(Chengdu\)|0.003|
|China \(Hong Kong\), Japan \(Tokyo\), UAE \(Dubai\)|0.009|
|US \(Silicon Valley\) and US \(Virginia\)|0.005|
|Singapore, Malaysia \(Kuala Lumpur\), Indonesia \(Jakarta\), India \(Mumbai\), UK \(London\), Germany \(Frankfurt\), and Australia \(Sydney\)|0.006|

## Traffic fees

Traffic fees are charged for Internet instances based on actual traffic.

**Note:** Internal instances are exempt from traffic fees.

Traffic fees for Internet instances are calculated in the following way:

-   Traffic fee = Unit traffic price × Duration

    Only outbound traffic \(downstream traffic\) is charged, but not inbound traffic \(upstream traffic\).

-   Traffic fees are billed on an hourly basis and settled in real time. If you use an instance for less than one hour within a billing cycle, the duration is calculated as one hour.

    The prices listed in the following table are for reference only. For more information, see the Server Load Balancer console.

    |Region|Traffic fee \(USD/GB\)|
    |:-----|:---------------------|
    |China \(Hangzhou\), China \(Beijing\), China \(Shenzhen\), China \(Shanghai\), China \(Zhangjiakou\), China \(Hohhot\), China \(Chengdu\), and China \(Heyuan\)|0.125|
    |China \(Qingdao\)|0.113|
    |China \(Hong Kong\)|0.156|
    |US \(Silicon Valley\) and US \(Virginia\)|0.078|
    |Malaysia \(Kuala Lumpur\)|0.112|
    |Singapore, Indonesia \(Jakarta\), and India \(Mumbai\)|0.117|
    |Japan \(Tokyo\)|0.087|
    |Germany \(Frankfurt\)|0.070|
    |UAE \(Dubai\)|0.447|
    |Australia \(Sydney\)|0.096|


## Specification fee

The following are three key performance metrics for guaranteed-performance instances. The limits of these metrics vary according to specification. For more information, see [Guaranteed-performance instance FAQ](/intl.en-US/User Guide/Instance/FAQ/Guaranteed-performance instance FAQ.md).

-   Max Connection

    The maximum number of connections to an SLB instance. When the number of connections reaches the limit of the specification, new connections are dropped.

-   Connection Per Second \(CPS\)

    The number of new connections that are established per second. When the CPS reaches the limit of the specification, new connections are dropped.

-   Queries Per Second \(QPS\)

    The number of HTTP/HTTPS requests that can be processed per second. This metric is available only for layer-7 SLB listeners. When the QPS reaches the limit of the specification, new connections are dropped.


The specification fee of a guaranteed-performance instance is charged based on your actual usage. If the actual performance of the instance is between two specifications, the specification fee is calculated according to the higher specification.

For example, you choose the specification of slb.s3.large \(Max Connection: 1,000,000; CPS: 100,000; QPS: 50,000\), and the actual usage of the instance in an hour is as follows:

|Max Connection|CPS|QPS|
|:-------------|:--|:--|
|90,000|4,000|11,000|

-   With respect to Max Connection, the actual metric value of 90,000 lies between the limit of 50,000 defined in Standard I \(slb.s2.small\) and the limit of 100,000 defined in Standard II \(slb.s2.medium\). Therefore, the billable specification of the Max Connection metric for this hour is Standard II \(slb.s2.medium\).

-   With respect to CPS, the actual metric value of 4,000 falls between the limit of 3,000 defined in the Small I \(slb.s1.small\) specification and the limit of 5,000 defined in the Standard I \(slb.s2.small\) specification. Therefore, the billable specification of the CPS metric for this hour is Standard I \(slb.s2.small\).

-   With respect to QPS, the actual metric value of 11,000 falls between the limit of 10,000 defined in Standard II \(slb.s2.medium\) and the limit of 20,000 defined in Higher I \(slb.s3.small\). Therefore, the billable specification of the QPS metric for this hour is Higher I \(slb.s3.small\).

    Out of the three metrics, the billable specification of the QPS metric is the highest. Therefore, the specification fee of the instance in this hour is charged according to the price of the Higher I \(slb.s3.small\) specification.


The following figure is an example showing how the specification fee is billed for an SLB instance:

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0542995851/p3113.png)

The billing is more flexible for guaranteed-performance instances. The specification you select when purchasing an instance is the higher performance limit of the instance. For example, if you select Higher II \(slb.s3.medium\), new requests are dropped when requests reach 30,000 in one second.

The prices detailed in the following table are for reference purposes only. The price you see in the console more accurately reflect your usage.

|Region|Specification|Max Connection|CPS|QPS|Specification fee \(USD/hour\)|
|:-----|:------------|:-------------|:--|:--|:-----------------------------|
|China \(Hangzhou\)

 China \(Zhangjiakou\)

 China \(Hohhot\)

 China \(Qingdao\)

 China \(Beijing\)

 China \(Shanghai\)

 China \(Shenzhen\)

|Specification 1: Small I \(slb.s1.small\)|5000|3000|1000|Free of charge for a limited period|
|Specification 2: Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.05|
|Specification 3: Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.10|
|Specification 4: Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.20|
|Specification 5: Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.31|
|Specification 6: Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.51|
|Singapore

 Malaysia \(Kuala Lumpur\)

 Indonesia \(Jakarta\)

 India \(Mumbai\)

 US \(Silicon Valley\)

 US \(Virginia\)

 China \(Hong Kong\)

|Specification 1: Small I \(slb.s1.small\)|5,000|3,000|1,000|Free of charge for a limited period|
|Specification 2: Standard I \(slb.s2.small\)|50,000|5,000|5,000|0.06|
|Specification 3: Standard II \(slb.s2.medium\)|100,000|10,000|10,000|0.12|
|Specification 4: Higher I \(slb.s3.small\)|200,000|20,000|20,000|0.24|
|Specification 5: Higher II \(slb.s3.medium\)|500,000|50,000|30,000|0.37|
|Specification 6: Super I \(slb.s3.large\)|1,000,000|100,000|50,000|0.61|

