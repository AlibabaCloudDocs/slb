# Backend server overview {#concept_wwc_l4n_vdb .concept}

Before using the load balancing service, you must add one or more ECS instances as the backend servers to an SLB instance to process the distributed client requests.

SLB service virtualizes the added ECS instances in the same region into an application pool featured with high performance and high availability. You can also manage backend servers through a VServer group. Different listeners can be associated with different server groups so that different listeners of an SLB instance can forward requests to the backend servers with different ports.

**Note:** After a VServer group is configured for a listener, the listener will forward requests to the ECS instances in the associated VServer group instead of the ECS instances in the default server group.

You can increase or decrease the number of the backend ECS instances at any time and specify the ECS instances that receive requests. However, we recommend that you enable the health check function, and there must be at least one normal ECS to maintain service stability.

When adding ECS instances to an SLB instance, note the following:

-   SLB does not support cross-region deployment. Make sure that the ECS instances and the SLB instance are in the same region.
-   SLB does not limit the operating system used in the ECS instances as long as the applications deployed in the ECS instances are the same, and the data is consistent. However, we recommend that you use the same operating system for better management and maintenance.
-   Up to 50 listeners can be added to an SLB instance. Each listener corresponds to an application deployed on backend ECS instances. The listening port of an SLB instance corresponds to the application port opened on the ECS instance.
-   You can specify a weight for each ECS instance in the backend server pool. An ECS instance with a higher weight will receive a larger number of connection requests.
-   If you have enabled the session persistence function, the requests distributed to the backend ECS instances may be imbalanced. If so, we recommend that you disable the session persistence function to check if the problem persists.

    When the traffic is not distributed evenly, troubleshoot as follows:

    1.  Collect the access logs of the web service within a period of time.
    2.  Check if the number of logs of multiple ECS instances are different according to SLB configurations. If session persistence is enabled, you need to strip the access logs for the same IP address. If weights are configured for SLB, you need to calculate whether the percentage of access logs matches the weight ratio.\)
-   When an ECS instance is undergoing live migration, the persistent connections of the SLB may be interrupted and can be restored by reconnecting them. Be prepared for the reconnection.

## Default server group {#section_fzb_g5n_n2b .section}

A default server group contains ECS instances that receive requests. If a listener is not associated with a VServer group or an active/standby server group, requests are forwarded to ECS instances in the default server group by default.

See [Manage a default server group](intl.en-US/Backend servers/Manage a default server group.md#) to create a default server group.

## Active/standby server group {#section_z1g_nbt_vdb .section}

An active/standby server group only contains two ECS instances. One acts as the active server and the other acts as the standby server. No health check is performed on the standby server. When the active server is declared as unhealthy, the system forwards traffic to the standby server. When the active server is declared as healthy and restores service, the traffic is forwarded to the active server again.

See [Manage an active/standby server group](intl.en-US/Backend servers/Manage an active__standby server group.md#) to create an active/standby server group.

**Note:** Only Layer-4 listeners \(TCP and UDP protocols\) support configuring active/standby server groups.

## VServer group {#section_xqs_h2v_vdb .section}

When you need to distribute different requests to different backend servers, or you want to configure domain name or URL based forwarding rules, you can use VServer groups.

See [Manage a VServer group](intl.en-US/Backend servers/Manage a VServer group.md#) to create a VServer group.

