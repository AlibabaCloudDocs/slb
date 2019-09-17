# What is Server Load Balancer? {#concept_whs_lp4_tdb .concept}

Server Load Balancer \(SLB\) is a traffic distribution and control service that distributes inbound traffic among multiple ECS instances according to configured forwarding rules. SLB expands service capabilities of applications and enhances their availability.

## Overview {#section_dy5_4qx_k2b .section}

By setting a virtual service address, SLB virtualizes added ECS instances into an application service pool that has high performance and high availability, and distributes client requests to ECS instances in the server pool based on forwarding rules.

SLB also checks the health status of added backend servers, and automatically isolates abnormal ECS instances to eliminate Single Point of Failures \(SPOFs\), improving the overall service capability of your application. Additionally, working with Alibaba Anti-DDoS, SLB can defend DDoS attacks.

## Components {#section_ppv_hq4_tdb .section}

SLB consists of the following components:

-   SLB instances

    An SLB instance is a running load balancing service that distributes incoming traffic to backend servers. To use the SLB service, you must create an SLB instance, and then configure the instance with at least one listener and two backend servers.

-   Listeners

    A listener checks client requests and forwards the requests to backend servers according to the configured rules. It also performs health checks on backend servers.

-   Backend servers

    Backend servers are the ECS instances added to an SLB instance to process the distributed requests. You can add ECS instances to the default server group, a VServer group, or an active/standby server group for better management.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4091/1568714082936_en-US.png)


## Benefits {#section_ws5_vq4_tdb .section}

-   High availability

    SLB is designed to work in full-redundancy mode and avoids SPOFs. It supports local and cross-region disaster tolerance. When SLB is used together with DNS, the service availability is up to 99.95%.

    You can scale your service based on application loads, without interrupting service continuity.

-   Scalable

    You can increase or decrease the number of backend servers to adapt to the service needs of your applications.

-   Cost effectiveness

    Compared with traditional load balancing hardware, SLB reduces the cost by 60%.

-   Secure

    Combined with Alibaba Cloud Security, SLB can defend against up to 5 Gbit/s DDoS attacks, such as HTTP flood and SYN flood attacks.


