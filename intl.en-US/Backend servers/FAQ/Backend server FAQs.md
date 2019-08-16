# Backend server FAQs {#concept_dt4_dh5_vdb .concept}

-   [Can I adjust the number of backend ECS instances while my SLB instance is running?](reseller.en-US/FAQ/Backend server FAQs.md#section_bt3_knx_wdb)
-   [Can I use different operating systems for different backend ECS instances?](reseller.en-US/FAQ/Backend server FAQs.md#section_ct3_knx_wdb)
-   [Can I add ECS instances from different regions to the same SLB instance?](reseller.en-US/FAQ/Backend server FAQs.md#section_dt3_knx_wdb)
-   [Why do my records show frequent access to my backend ECS instances from IP addresses that start with 100?](reseller.en-US/FAQ/Backend server FAQs.md#section_gt3_knx_wdb)
-   [Why are responses returned by SLB compressed even though my ECS instance is not configured for compression?](reseller.en-US/FAQ/Backend server FAQs.md#section_ot3_knx_wdb)
-   [Is chunked transfer encoding supported if my backend ECS instances use HTTP1.0?](reseller.en-US/FAQ/Backend server FAQs.md#section_pt3_knx_wdb)
-   [Why do my backend ECS instances frequently receive requests where the value of the UA string is KeepAliveClient?](reseller.en-US/FAQ/Backend server FAQs.md#section_c43_sqx_wdb)

## Can I adjust the number of backend ECS instances while my SLB instance is running? {#section_bt3_knx_wdb .section}

Yes.

You can increase or decrease the number of backend ECS instances in an SLB instance at any time and switch between different ECS instances. Before you perform these operations, make sure that health check is enabled and that there is at least one normally running backend ECS instance to avoid service interruption.

## Can I use different operating systems for different backend ECS instances? {#section_ct3_knx_wdb .section}

Yes.

There is no limitation on the operating system used on backend ECS instances as long as applications deployed on the ECS instances are the same and the data is consistent. To facilitate daily management and maintenance, we recommend that you use the same operating system for backend ECS instances.

## Can I add ECS instances from different regions to the same SLB instance? {#section_dt3_knx_wdb .section}

No.

Server Load Balancer does not support cross-region deployment. The ECS instances to be added must belong to the same region as the SLB instance.

## Why do my records show frequent access to my backend ECS instances from IP addresses that start with 100? {#section_gt3_knx_wdb .section}

In addition to forwarding external requests to backend ECS instances by using the intranet IP address of the system server, the SLB system also accesses the ECS instances to perform health checks and monitor service availability.

The IP address range of the SLB system is 100.64.0.0/10（100.64.0.0/10 is reserved by Alibaba Cloud, and will not be used by any user, there is no security risk \), so there are many IP addresses beginning with 100 accessing ECS instances.

To guarantee the service availability, you have to configure appropriate access rules for these IP address ranges.

## Why are responses returned by SLB compressed even though my ECS instance is not configured for compression? {#section_ot3_knx_wdb .section}

The possible reason is that the client web browser supports compression. You can disable Gzip function when creating listeners in the console or use TCP listeners instead.

## Is chunked transfer encoding supported if my backend ECS instances use HTTP1.0? {#section_pt3_knx_wdb .section}

Yes.

## Why do my backend ECS instances frequently receive requests where the value of the UA string is KeepAliveClient? {#section_c43_sqx_wdb .section}

Issue

Backend ECS instances frequently receive GET requests, but there are no visitor IP addresses. Instead, source IP addresses of these requests are intranet IP addresses of Alibaba Cloud, and the value of the User-Agent string is KeepAliveClient.

Cause

TCP listeners are being used, which use the HTTP protocol for health checks. Specifically, when health checks that use HTTP protocol are performed in TCP listeners, GET requests are used by default.

Solution

We recommend that you use the same protocol for both listeners and health checks.

