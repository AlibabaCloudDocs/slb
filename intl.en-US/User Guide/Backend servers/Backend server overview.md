---
keyword: [SLB, load balancing, backend servers, traffic forwarding]
---

# Backend server overview

Before you use the Server Load Balancer \(SLB\) service, you must add Elastic Compute Service \(ECS\) instances as backend servers to an SLB instance to process client requests.

## Backend server overview

You can set virtual IP addresses for an SLB instance. This way, the added ECS instances in the same region can be virtualized into an application service pool that provides high performance and availability. You can manage backend servers by using vServer groups. A listener of an SLB instance can be associated with a specific vServer group so that different listeners can forward requests to their associated backend servers that use different ports.

**Note:** If you associate a vServer group with a listener, the listener distributes requests to backend servers in the associated vServer group instead of those in the default server group.

## Limits

You can increase or decrease the number of backend ECS instances at any time and switch ECS instances to receive client requests. When you perform the operations, make sure that the health check feature is enabled and at least one ECS instance is running as expected to maintain service stability.

When you add backend ECS instances, take note of the following items:

-   SLB does not support cross-region deployment. Make sure that the added ECS instances and the corresponding SLB instance belong to the same region.
-   You can add ECS instances of different operating systems to an SLB instance. However, the applications deployed on the ECS instances must be the same and have consistent data. We recommend that you use ECS instances of the same operating system to facilitate management and maintenance.
-   Up to 50 listeners can be added to a single SLB instance. Each listener corresponds to an application deployed on backend ECS instances. Listening ports of an SLB instance correspond to application service ports that are opened on backend ECS instances.
-   You can specify a weight for each ECS instance in the application service pool. An ECS instance with a higher weight receives more requests.
-   If session persistence is enabled, requests may not be evenly distributed to backend ECS instances. To solve this problem, we recommend that you disable session persistence and check whether the problem persists.

    If requests are not evenly distributed, troubleshoot the issue in the following way:

    1.  Collect statistics on the access logs of the web service on backend ECS instances for a specified period.
    2.  Check whether the numbers of access logs of backend ECS instances match SLB configurations. If session persistence is enabled, you must differentiate the access logs for the same IP address. If different weights are configured for backend ECS instances, you must check whether the percentage of access logs is normal based on the percentage of weights.
-   When an ECS instance is undergoing hot migration, persistent connections to SLB may be interrupted. You can solve this problem by reestablishing the connections.

## Default server groups

A default server group contains ECS instances that are used to receive requests. If a listener is not associated with a vServer group or a primary/secondary server group, the listener forwards requests to ECS instances in the default server group.

Before you use the SLB service, you must add at least one default backend server to receive client requests forwarded by SLB. For more information, see [Add ECS instances to the default server group](/intl.en-US/User Guide/Backend servers/Default server groups/Add ECS instances to the default server group.md).

## vServer groups

You can use a vServer group if you want to distribute different requests to different backend servers or configure forwarding rules based on domain names and URLs. For more information, see [Create a vServer group](/intl.en-US/User Guide/Backend servers/VServer groups/Create a vServer group.md).

## Primary/secondary server groups

A primary/secondary server group contains only two ECS instances. One ECS instance acts as the primary server and the other acts as the secondary server. Health checks are not performed on the secondary server. If the primary server is detected unhealthy, traffic is redirected to the secondary server. After the primary server recovers and is considered healthy, traffic is switched back to the primary server. For more information, see [Create a primary/secondary server group](/intl.en-US/User Guide/Backend servers/Active/standby server groups/Create a primary/secondary server group.md).

**Note:** You can add primary/secondary server groups only for TCP and UDP listeners.

**Related topics**  


[Add ECS instances to the default server group](/intl.en-US/User Guide/Backend servers/Default server groups/Add ECS instances to the default server group.md)

[Create a vServer group](/intl.en-US/User Guide/Backend servers/VServer groups/Create a vServer group.md)

[Create a primary/secondary server group](/intl.en-US/User Guide/Backend servers/Active/standby server groups/Create a primary/secondary server group.md)

