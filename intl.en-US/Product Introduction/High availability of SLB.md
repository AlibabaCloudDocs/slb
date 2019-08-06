# High availability of SLB {#concept_ppk_txt_vdb .concept}

This topic describes the high-availability architecture of Server Load Balancer \(SLB\) in terms of different system designs and product configurations to meet different business needs. You can also use SLB together with Alibaba Cloud DNS to achieve cross-region disaster recovery.

## High availability of the SLB system {#section_nk4_zxt_vdb .section}

Deployed in clusters, SLB can synchronize sessions to protect the ECS instances from single points of failure \(SPOFs\). This improves redundancy and guarantees the service stability. Layer-4 SLB uses the open source software Linux Virtual Server \(LVS\) and Keepalived to achieve load balancing. Layer-7 SLB uses Tengine to achieve load balancing. Tengine, a Web server project based on Nginx, adds advanced features dedicated for high-traffic websites.

Requests from the Internet reach the LVS cluster through ECMP routing. Each LVS in the LVS cluster synchronizes the session to other LVS machines in the cluster through multicast packets, thereby implementing session synchronization among machines in the LVS cluster. At the same time, the LVS cluster performs health checks on the Tengine cluster and removes abnormal machines from the Tengine cluster to ensure the availability of Layer-7 SLB.

Best practice:

Session synchronization protects persistent connections from being affected by server failure in the cluster. However, for short connections or when the session synchronization rule is not triggered by the connection \(the three-way handshake is not completed\), server failure in the cluster may still affect user requests. To prevent session interruptions caused by machine failure in the cluster, you can add a retry mechanism to the service logic to reduce the impact on user access.

## High availability of a single SLB instance {#section_g3m_pvv_wdb .section}

To provide more reliable services, multiple zones for SLB are deployed in most regions. If a primary zone becomes unavailable, SLB rapidly switches to a secondary zone to restore its service capabilities within 30 seconds. When the primary zone becomes available, SLB automatically switches back to the primary zone.

**Note:** The primary zone and secondary zone form zone-level disaster tolerance. An SLB instance switches to the secondary zone only when Alibaba Cloud detects that the current zone is unavailable due to power outage or optical cable failures rather than the failure of an instance.

Best practice:

1.  We recommend that you create an SLB instance in a region with multiple zones for disaster tolerance.
2.  You can deploy ECS instances in the primary zone and secondary zone respectively as needed. You can set the zone where most ECS instances are located to the primary zone to minimize access latency.

    However, we recommend that you do not deploy all ECS instances in one zone. You also need to deploy a small number of ECS instances in the secondary zone, so that the secondary zone can still process requests in extreme conditions \(the primary zone is unavailable\).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4169/15640682963122_en-US.png)


## High availability of multiple SLB instances {#section_vvj_kwv_wdb .section}

If your availability requirements are extremely high, the availability guaranteeing mechanism of a single SLB may fail to meet your demands. For example, when the SLB instance is unavailable due to network attacks or configuration errors, zone switching is not triggered because no zone-level failure occurs. To solve that problem, you can create multiple SLB instances and schedule requests by using Alibaba Cloud DNS, or achieve cross-region disaster recovery through global SLB.

Best practice:

You can deploy SLB instances and ECS instances in multiple zones of a region or in multiple regions and schedule access requests by using Alibaba Cloud DNS.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4169/15640682963121_en-US.png)

## High availability of backend ECS instances {#section_cnp_dzt_vdb .section}

SLB checks the service availability of backend ECS instances by performing health checks. Health checks improve the overall availability of frontend services and help reduce the impact of service availability when backend servers are abnormal.

When SLB discovers that an instance is unhealthy, it distributes requests to other healthy ECS instances, and only resumes distributing requests to the instance when it has restored to a healthy status. For more information, see [Health check overview](../../../../reseller.en-US/Health check/Health check overview.md#) .

Best practice:

You need to enable and correctly configure the health check function. For more information, see [Configure health checks](../../../../reseller.en-US/Health check/Configure health checks.md#) .

