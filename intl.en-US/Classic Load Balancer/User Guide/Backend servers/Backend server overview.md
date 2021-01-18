# Backend server overview

Before the Server Load Balancer \(SLB\) service can be used, you must add ECS instances as backend servers to an SLB instance to process client requests.

## Backend server introduction

You can set virtual IP addresses for SLB instances. This way, the added ECS instances in the same region can be virtualized into an application service pool that provides high performance and availability. You can manage backend servers by using VServer groups. Each listener of an SLB instance can be associated with a specific VServer group so that different listeners can forward requests to their associated backend servers that use different ports.

**Note:** If you associate a VServer group with a listener, the listener will distribute requests to backend servers in the associated VServer group instead of those in the default server group.

## Restriction description

You can increase or decrease the number of backend ECS instances at any time and switch ECS instances to receive client requests. However, we recommend that you enable the health check feature and make sure that at least one ECS instance is running properly to maintain service stability.

When you add ECS instances to an SLB instance, take note of the following items:

-   SLB does not support cross-region deployment. Make sure that the added ECS instances and the corresponding SLB instance belong to the same region.
-   You can use different operating systems for the backend ECS instances of an SLB instance. However, the applications deployed in the ECS instances must be the same and have consistent data. We recommend that you use the same operating system to facilitate management and maintenance.
-   Up to 50 listeners can be added to a single SLB instance. Each listener corresponds to an application deployed on backend ECS instances. Listening ports of an SLB instance correspond to application service ports opened on backend ECS instances.
-   You can specify a weight for each ECS instance in the application service pool. An ECS instance with a higher weight receives more requests.
-   If session persistence is enabled, requests may not be evenly distributed to backend ECS instances. To solve this problem, we recommend that you disable session persistence and check whether the problem persists.

    If requests are not distributed evenly, troubleshoot as follows:

    1.  Collect statistics on the access logs of the web service on backend ECS instances for a period of time.
    2.  Check whether the numbers of access logs of backend ECS instances match SLB configurations. For example, if session persistence is enabled, you must differentiate the access logs for the same IP address. If different weights are configured for backend ECS instances, you must check whether the percentage of access logs is normal based on the percentage of weights.
-   When an ECS instance is undergoing hot migration, persistent connections to SLB may be interrupted. You can solve this problem by reestablishing the connections.

## Default server groups

A default server group contains ECS instances that are used to receive client requests. If a listener is not associated with a VServer group or a primary/secondary server group, the listener will forward requests to ECS instances in the default server group.

For more information about how to create a default server group, see [Add ECS instances to the default server group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Default server groups/Add ECS instances to the default server group.md).

## Primary/secondary server groups

A primary/secondary server group only contains two ECS instances. One ECS instance acts as the primary server and the other acts as the secondary server. Health checks are not performed on the secondary server. If the primary server is declared unhealthy, traffic is redirected to the secondary server. If the primary server is declared healthy, services will be restored and traffic will be forwarded to the primary server again.

For more information about how to create a primary/secondary server group, see [Add ECS instances to a primary/secondary server group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Active/standby server groups/Add ECS instances to a primary/secondary server group.md).

**Note:** Only TCP and UDP listeners support configuring primary/secondary server groups.

## VServer groups

If you want to distribute different requests to different backend servers or configure domain name- or URL-based forwarding rules, you can use VServer groups.

For more information about how to create a VServer group, see [Add ECS instances to a VServer group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/VServer groups/Add ECS instances to a VServer group.md).

