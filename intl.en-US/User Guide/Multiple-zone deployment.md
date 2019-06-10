# Multiple-zone deployment {#concept_i55_h4n_vdb .concept}

You can create SLB instances in a region with multiple zones to improve the service availability.

## What is multiple-zone deployment? {#section_blw_bxt_vdb .section}

A cloud product zone is a set of independent infrastructures. Different zones have independent infrastructures \(such as network, power supply, and air-conditioning\). Therefore, infrastructure faults in one zone does not affect other zones.

To provide more reliable services, SLB has deployed multiple zones in most regions to achieve disaster recovery across data centers. When the data center in the primary zone is faulty and unavailable, SLB is able to switch to the data center in the secondary zone to restore its service within 30 seconds.

Note the following about SLB primary/secondary zones:

-   SLB supports ECS instances in different zones as long as the ECS instances and the SLB instance belong to the same region. SLB can distribute traffic to the ECS instances in different zones.
-   Normally, the SLB instance in the secondary zone is in the standby state. You cannot manually switch to the secondary zone. SLB switches to the secondary zone only when the primary zone is unavailable due to reasons such as data center power outage and exit cable failures. SLB does not switch to the secondary zone when an SLB instance in the primary zone is faulty.
-   SLB and ECS are deployed in different clusters. When an SLB instance in Zone A is unavailable, the ECS instances in Zone A are not necessarily unavailable. Therefore, after SLB switches to the secondary zone due to SLB cluster faults, the SLB instance in the secondary zone still can distribute traffic to the ECS instances in different zones. However, if power outrage or optical cable failures occur to all clusters in a zone, all services \(including but not limited to SLB instances and ECS instances\) in the zone cannot work anymore.

For more information, see [SLB high availability](../intl.en-US/Product Introduction/High availability of SLB.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4155/15601528492835_en-US.png)

## Primary/secondary zone list {#section_ml2_ykb_wdb .section}

The following table lists the primary/secondary zones in different regions. You can call the DescribeZones API to query available primary/secondary zones in a region.

|Region|Zone type|Zones|
|:-----|:--------|:----|
|China \(Hangzhou\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone B|Zone DZone G

|
|Zone D|Zone E|
|Zone E|Zone DZone F

|
|Zone F|Zone E|
|Zone G|Zone BZone H

|
|Zone H|Zone G|
|China \(Shanghai\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone AZone C

Zone D

|
|Zone C|Zone B|
|Zone D|Zone BZone E

|
|Zone E|Zone DZone F

|
|Zone F|Zone E|
|China \(Shenzhen\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone AZone C

|
|Zone C|Zone BZone D

|
|Zone D|Zone CZone E

|
|Zone E|Zone D|
|China \(Qingdao\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone B|Zone C|
|Zone C|Zone B|
|China \(Beijing\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone BZone D

Zone E

|
|Zone B|Zone C|
|Zone C|Zone E|
|Zone D|Zone A|
|Zone E|Zone CZone F

|
|Zone F|Zone EZone G

|
|Zone G|Zone F|
|China \(Zhangjiakou\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|China \(Hohhot\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|Germany \(Frankfurt\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|UK \(London\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|UAE \(Dubai\)|Single-zone|Zone A|
|Singapore|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|Zone C|Zone B|
|Australia \(Sydney\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|Malaysia \(Kuala Lumpur\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|Indonesia \(Jakarta\)|Single-zone|Zone A|
|India \(Mumbai\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|Japan \(Tokyo\)|Single-zone|Zone A|
|Hong Kong|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone B|Zone C|
|Zone C|Zone B|
|US \(Virginia\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|US \(Silicon Valley\)|Multi-zone|**Primary zone**|**Secondary zone**|
|Zone A|Zone B|
|Zone B|Zone A|

