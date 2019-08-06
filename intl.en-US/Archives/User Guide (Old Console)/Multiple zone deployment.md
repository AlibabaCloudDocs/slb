# Multiple zone deployment {#concept_i55_h4n_vdb .concept}

When creating SLB instances, you can create SLB instances in the region with multiple zones to improve the availability.

## What is multiple zone? {#section_blw_bxt_vdb .section}

A cloud product zone refers to a set of independent infrastructures. Different zones have independent infrastructures \(such as network, power supply and air-conditioning\), thus an infrastructure fault in one zone does not affect other zones.

To provide more reliable services, SLB has deployed multiple zones in most regions to achieve disaster recovery across data centers. When the data center in the master zone is faulty and unavailable, SLB is able to switch to the data center in the slave zone to restore its service capabilities within 30 seconds.

Note the following about SLB master-slave zones:

-   SLB supports attaching ECS instances in different zones as long as the ECS instances and the SLB instance are in the same region. SLB can distribute traffic to the ECS instances in different zones.
-   Normally, the SLB instance in the slave zone is in the standby state. You cannot manually switch the active/standby state of an SLB instance. SLB will switch to the slave zone only when the data center of the master zone is unavailable such as outage. SLB will not switch to the slave zone if an SLB instance is faulty.
-   SLB and ECS are deployed in different clusters. When an SLB instance is unavailable, the ECS instance is still available. Therefore, after SLB switches to the slave zone, the SLB instance in the slave zone still can distribute traffic to the added ECS instances.  However, if all clusters in a zone is unavailable or the optical cable is broken, then all the services in the zone including SLB and ECS cannot work anymore.

For more information, see [SLB high availability](../../../../intl.en-US/Best Practices/High availability best practice.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4155/2835_en-US.png)

## Master-slave zone list {#section_ml2_ykb_wdb .section}

The following table lists the master-slave in zones. You can call the DescribeZones API to obtain available master-slave zones in a region.

|Regions|Zone type|Zone|Zone|
|:------|:--------|:---|:---|
|China \(Hangzhou\)|Multi-zone|**Master zone**|**Slave zone**|
|Zone B|Zone D|
|Zone D|Zone E|
|Zone E|Zone F|
|Zone F|Zone E|
|China \(Shanghai\)|Multi-zone|**Master zone**|**Slave zone**|
|Zone A|Zone B|
|Zone B|Zone A or Zone D|
|Zone C|Zone B|
|Zone D|Zone B|
|China \(Shenzhen\)|Multi-zone|**Master zone**|**Slave zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|Zone C|Zone B|
|China \(Qingdao\)|Multi-zone|**Master zone**|**Slave zone**|
|Zone B|Zone C|
|Zone C|Zone B|
|China \(Beijing\)|Multi-zone|**Master zone**|**Slave zone**|
|Zone A|Zone B or Zone D|
|Zone B|Zone A or Zone C|
|Zone C|Zone B|
|Zone D|Zone A|
|China \(Zhangjiakou\)|Single zone|Zone A|Zone A|
|China \(Hohhot\)|Single zone|Zone A|Zone A|
|Germany  \(Frankfurt\)|Single zone|Zone A|Zone A|
|UAE \(Dubai\)|Single zone|Zone A|Zone A|
|Singapore|Multi-zone|**Master zone**|**Slave zone**|
|Zone A|Zone B|
|Zone B|Zone A|
|Australia \(Sydney\)|Single zone|Zone A|Zone A|
|Malaysia \(Kuala Lumpur\)|Single zone|Zone A|Zone A|
|Japan \(Tokyo\)|Single zone|Zone A|Zone A|
|China \(Hong Kong\)|Multi-zone|**Master zone**|**Slave zone**|
|Zone B|Zone C|
|Zone C|Zone B|
|US \(Virginia\)|Single zone|Zone A|Zone A|
|US \(Virginia\)|Multi-zone|**Master zone**|**Slave zone**|
|Zone A|Zone B|
|Zone B|Zone A|

