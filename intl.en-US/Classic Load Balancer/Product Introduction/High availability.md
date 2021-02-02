# High availability

This topic describes the high-availability architecture of CLB. You can use CLB in concert with DNS to implement geo-disaster recovery. CLB is designed to offer a multi-zone service availability of 99.99% and a single-zone service availability of 99.90%.

## High availability of the CLB architecture

CLB instances are deployed in clusters to synchronize sessions and protect backend servers from SPOFs, improving redundancy and ensuring service stability. Layer-4 CLB uses the open-source Linux Virtual Server \(LVS\) and Keepalived software to balance loads, whereas Layer-7 CLB uses Tengine. Tengine, a web server project launched by Taobao, is based on NGINX and adds advanced features dedicated for high-traffic websites.

Requests from the Internet reach an LVS cluster along Equal-Cost Multi Path \(ECMP\) routes. In the LVS cluster, each machine uses multicast packets to synchronize sessions with the other machines. At the same time, the LVS cluster performs health checks on the Tengine cluster and removes unhealthy machines from the Tengine cluster to ensure the availability of Layer-7 CLB.

Best practice:

You can use session synchronization to prevent persistent connections from being affected by server failures within a cluster. However, for short-lived connections or if the session synchronization rule is not triggered by the connection \(the three-way handshake is not completed\), server failures in the cluster may still affect user requests. To prevent session interruptions caused by server failures within the cluster, you can add a retry mechanism to the service logic to reduce the impact on user access.

## The high-availability solution with one CLB instance

To provide more stable and reliable load balancing services, you can deploy CLB instances across multiple zones in most regions to achieve cross-data-center disaster recovery. Specifically, you can deploy a CLB instance in two zones within the same region whereby one zone acts as the primary zone and the other acts as the secondary zone. If the primary zone suffers an outage, a failover is triggered to redirect requests to the servers in the secondary zone within approximately 30 seconds. After the primary zone is restored, traffic will be automatically switched back to the servers in the primary zone.

**Note:** Zone-disaster recovery is implemented between the primary and secondary zones. CLB implements failovers only when the whole CLB cluster within the primary zone is unavailable or fails, for example, due to power outage or optical cable failures. A failover will not be triggered when a single backend server fails.

Best practice:

1.  We recommend that you create CLB instances in regions that support primary/secondary deployment for zone-disaster recovery.
2.  You can choose the primary zone for your CLB instance based on the distribution of ECS instances. That is, select the zone where most of the ECS instances are located as the primary zone for minimized latency.

    However, we recommend that you do not deploy all ECS instances in the primary zone. When you develop a failover solution, you must deploy several ECS instances in the secondary zone to ensure that requests can still be distributed to backend servers in the secondary zone for processing when the primary zone experiences a downtime.

    ![The high-availability solution with one SLB instance](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7642522161/p3122.png)


## The high-availability solution with multiple CLB instances

In the context of one CLB instance, traffic distribution for your applications can still be compromised by network attacks or invalid CLB configurations, because the failover between the primary zone and the secondary zone is not triggered. As a result, the load-balancing performance is impacted. To avoid this situation, you can create multiple CLB instances to form a global load-balancing solution and achieve cross-region backup and disaster recovery. Also, you can use the instances with DNS to schedule requests so as to ensure service continuity.

Best practice:

You can deploy CLB instances and ECS instances in multiple zones within the same region or across different regions, and then use DNS to schedule requests.

![The high-availability solution with multiple SLB instances](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7642522161/p3121.png)

## The high-availability solution with backend ECS instances

With health check enabled, CLB verifies the availability of backend ECS instances \(or backend servers\), and thus improves the availability of frontend services by minimizing downtime that is caused by health issues of ECS instances.

After you enable the health check feature, when an ECS instance is detected unhealthy, CLB distributes new requests to other healthy ECS instances. CLB will only send requests to this backend ECS instance when it is restored and considered healthy. For more information, see [Health check overview](/intl.en-US/Classic Load Balancer/User Guide/Health check/Health check overview.md).

Best practice:

Make sure health check is enabled and properly configured. For more information, see [Configure health check](/intl.en-US/Classic Load Balancer/User Guide/Health check/Configure health checks.md).

