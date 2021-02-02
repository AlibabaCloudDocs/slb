# What is CLB?

This topic provides an overview of Classic Load Balancer \(CLB\). CLB distributes inbound network traffic across multiple Elastic Compute Service \(ECS\) instances that act as backend servers based on forwarding rules. You can use CLB to improve the responsiveness and availability of your applications.

## Overview

After you add ECS instances that are deployed in the same region to a CLB instance, CLB uses virtual IP addresses \(VIPs\) to virtualize these ECS instances into backend servers in a high-performance server pool that ensures high availability. Client requests are distributed to the ECS instances based on forwarding rules.

CLB checks the health status of the ECS instances and automatically removes unhealthy ones from the server pool to eliminate single points of failure \(SPOFs\). This enhances the resilience of your applications. You can also use CLB to defend your applications against distributed denial of service \(DDoS\) attacks.

## Components

CLB consists of three components:

-   CLB instances

    A CLB instance is a running CLB service entity that receives traffic and distributes traffic to backend servers. To get started with CLB, you must create a CLB instance and add at least one listener and two ECS instances to the CLB instance.

-   Listeners

    A listener checks client requests and forwards them to backend servers. It also performs health checks on backend servers.

-   Backend servers

    ECS instances are used as backend servers to receive distributed requests. You can separately add ECS instances to the server pool, or use vServer groups or primary/secondary server groups to add and manage ECS instances in batches.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1496322161/p936.png)


## Benefits

-   High availability

    CLB is designed with full redundancy that avoids SPOFs and supports zone-disaster recovery.

    CLB can be scaled based on application loads and can provide continuous service during traffic fluctuations.

-   High scalability

    You can increase or decrease the number of backend servers to adjust the load balancing capability of your applications.

-   Cost-effectiveness

    CLB can save 60% of load balancing costs compared with using traditional hardware solutions.

-   Security

    You can use CLB with Apsara Stack Security to defend your applications against up to 5 Gbit/s DDoS attacks.

-   High concurrency

    A CLB cluster supports hundreds of millions of concurrent connections and a single CLB instance supports tens of millions of concurrent connections.


