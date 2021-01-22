# Backend server FAQ

The following questions about backend ECS instances are frequently asked:

-   [Can I adjust the number of backend ECS instances while my SLB instance is running?](#section_bt3_knx_wdb)
-   [Can I use different operating systems for different backend ECS instances?](#section_ct3_knx_wdb)
-   [Can I attach ECS instances from different regions to the same SLB instance?](#section_dt3_knx_wdb)
-   [Why do my records show frequent access to my backend ECS instances from IP addresses that start with 100?](#section_gt3_knx_wdb)
-   [Why are responses from SLB compressed even though my ECS instances are not configured for compression?](#section_ot3_knx_wdb)
-   [Is chunked transfer encoding supported if my backend ECS instances use HTTP/1.0?](#section_pt3_knx_wdb)
-   [Why do my backend ECS instances frequently receive requests whose UA string value is KeepAliveClient?](#section_c43_sqx_wdb)

## Can I adjust the number of backend ECS instances while my SLB instance is running?

Yes.

You can increase or decrease the number of backend ECS instances for an SLB instance at any time and switch between ECS instances. Before you perform these operations, make sure that health check is enabled and at least one backend ECS instance is running. This ensures service stability.

## Can I use different operating systems for different backend ECS instances?

Yes.

You can use different operating systems for the backend ECS instances of an SLB instance. However, the applications deployed on the ECS instances must be the same and have the same data. To facilitate maintenance, we recommend that you use the same operating system for backend ECS instances.

## Can I attach ECS instances from different regions to the same SLB instance?

Yes.

SLB supports cross-region deployment. You can add the IP addresses of ECS instances in different regions to the SLB whitelist to use the instances as backend servers. This feature is available for public preview. Submit a ticket or contact your business manager to use this feature.

## Why do my records show frequent access to my backend ECS instances from IP addresses that start with 100?

SLB forwards external requests to backend ECS instances by using the internal IP address of the system server. SLB also accesses the ECS instances to perform health checks and monitor service availability.

The IP address range of the SLB system is 100.64.0.0/10 \(100.64.0.0/10 is reserved by Alibaba Cloud. It is not used by any user and therefore causes no security risks\). Therefore, many IP addresses that start with 100 are accessing the ECS instances.

To ensure service availability, you must configure appropriate access rules for these IP addresses.

## Why are responses from SLB compressed even though my ECS instances are not configured for compression?

A possible cause is that the client web browser supports compression. You can disable the Gzip feature when you create listeners in the console, or use TCP listeners.

## Is chunked transfer encoding supported if my backend ECS instances use HTTP/1.0?

Yes.

## Why do my backend ECS instances frequently receive requests whose UA string value is KeepAliveClient?

Problem description:

Backend ECS instances frequently receive GET requests, but no users are sending access requests to the ECS instances. Source IP addresses of these requests are internal IP addresses of Alibaba Cloud, and the value of the User-Agent string is KeepAliveClient.

Cause:

TCP listeners are used, but the HTTP protocol is used to perform health checks. When health checks that use the HTTP protocol are performed in TCP listeners, GET requests are used by default.

Solution:

We recommend that you use the same protocol for both listeners and health checks.

