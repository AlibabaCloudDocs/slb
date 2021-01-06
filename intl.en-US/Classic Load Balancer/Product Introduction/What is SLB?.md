# What is SLB?

This topic provides an overview of Server Load Balancer \(SLB\). SLB distributes inbound network traffic across multiple Elastic Compute Service \(ECS\) instances that act as backend servers based on forwarding rules. You can use SLB to improve the responsiveness and availability of your applications.

## Overview

After you add ECS instances that are deployed in the same region to an SLB instance, SLB uses virtual IP addresses \(VIPs\) to virtualize these ECS instances into backend servers in a high-performance server pool that ensures high availability. Client requests are distributed to the ECS instances based on forwarding rules.

SLB checks the health status of the ECS instances and automatically removes unhealthy ones from the server pool to eliminate single points of failure \(SPOFs\). This enhances the resilience of your applications. You can also use SLB to defend your applications against distributed denial of service \(DDoS\) attacks.

## Components

SLB consists of three components:

-   SLB instances

    An SLB instance is a running SLB service entity that receives traffic and distributes traffic to backend servers. To get started with SLB, you must create an SLB instance and add at least one listener and two ECS instances to the SLB instance.

-   Listeners

    A listener checks client requests and forwards them to backend servers. It also performs health checks on backend servers.

-   Backend servers

    ECS instances are used as backend servers to receive distributed requests. You can separately add ECS instances to the server pool, or use vServer groups or primary/secondary server groups to add and manage ECS instances in batches.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1013359951/p936.png)


## Benefits

-   High availability

    SLB is designed with full redundancy that avoids SPOFs and supports zone-disaster recovery.

    SLB can be scaled based on application loads and can provide continuous service during traffic fluctuations.

-   High scalability

    You can increase or decrease the number of backend servers to adjust the load balancing capability of your applications.

-   Cost-effectiveness

    SLB can save 60% of load balancing costs compared with using traditional hardware solutions.

-   Security

    You can use SLB with Apsara Stack Security to defend your applications against up to 5 Gbit/s DDoS attacks.

-   High concurrency

    An SLB cluster supports hundreds of millions of concurrent connections and a single SLB instance supports tens of millions of concurrent connections.


