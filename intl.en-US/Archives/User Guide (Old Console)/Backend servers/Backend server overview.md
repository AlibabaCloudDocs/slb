# Backend server overview {#concept_wwc_l4n_vdb .concept}

Before using the load balancing service, you must add one or more ECS instances as the backend servers to an SLB instance to process the distributed client requests.

You can increase or decrease the number of the backend ECS instances at any time. However, we recommend that you enable the health check function, and there must be at least one normal ECS to maintain service stability.

SLB service virtualizes the added ECS instances in the same region into an application pool featured with high performance and high availability. By default, the backend servers are maintained in the instance, that is, all the listeners under the SLB instance can only forward the traffic to the same port of the same server.

You can also add ECS instances in the way of server groups. Different listeners can be associated with different server groups so that different listeners of an SLB instance can forward requests to the backend servers with different ports.

**Note:** After a server group is configured for a listener, the listener will forward requests to the ECS instances in the selected server group instead of the ECS instances in the backend server pool.

## Master-slave server group {#section_z1g_nbt_vdb .section}

If you have the traditional master-backup requirements, where one backend server is used as the master server and the other is used as the slave server. When the master server works normally, requests are distributed to it; when the master server is down, the requests will be distributed to the slave server. To avoid service interruption, you can create a master-slave server group.

No health check is performed on the slave server. When the master server fails, the traffic is directly distributed to the slave sever. When the health check of the master server succeeds, the traffic will be automatically distributed to it.

The master-slave server group is available only for Layer-4 listeners. For more information, see [Create master-slave server groups](intl.en-US/User Guide/Backend servers/Create a master-slave server group.md#).

## VServer groups {#section_xqs_h2v_vdb .section}

When you need to distribute different requests to different backend servers, or you want to configure domain name or URL based forwarding rules, you can use VServer groups. For more information, see [Create VServer groups](intl.en-US/User Guide/Backend servers/Create a VServer group.md#).

## Notes {#section_shm_k2v_vdb .section}

When adding ECS instances to an SLB instance, note the following:

-   SLB does not support cross-region deployment. Make sure that the region for the ECS instances and the SLB instance is the same.
-   SLB does not limit the operating system used in the ECS instances as long as the applications deployed in the ECS instances are the same, and the data is consistent. However, we recommend that you use the same operating system for better management and maintenance.
-   Up to 50 listeners can be added to an SLB instance. Each listener corresponds to an application deployed on the ECS. The front-end port of the listener is the application port opened on the ECS instance.
-   You can specify a weight for each ECS instance. An ECS instance with the higher weight receives more requests. Set the weight based on service capacity and status of the backend ECS instance.

    **Note:** If you have enabled the session persistence function, the requests distributed to the backend ECS may be imbalanced. If so, we recommend that you disable the session persistence function to check if the problem persists.

    When the traffic is not distributed as configured among the backend servers, troubleshoot as follows:

    1.  Collect the access logs of the web service within a period of time.
    2.  Check if the number of logs of multiple ECS instances are different. \(If session persistence is enabled, you need to strip the access logs for the same IP address from the log. If the weight is configured for SLB, you need to calculate whether the percentage of access traffic recorded in the logs matches the weight ratio.\)
-   When an ECS instance is undergoing live migration, the persistent connections of the SLB may be interrupted and can be restored by reconnecting them. Be prepared for the reconnection.

