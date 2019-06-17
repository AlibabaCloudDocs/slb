# Why is the traffic among my ECS instances unevenly distributed? {#concept_ppc_kh5_vdb .concept}

## Causes {#section_jdz_lby_wdb .section}

Traffic may be unevenly distributed due to the following reasons:

-   Only a small number of requests are being received by ECS instances.
-   The target ECS instances have different network capacities.

    **Note:** The memory usage of ECS instances does not indicate whether requests are evenly distributed.

-   Session persistence is enabled.

    If session persistence is enabled, it will cause traffic imbalance when few clients are accessing the Server Load Balancer \(SLB\) instance. This is especially common when a small number of clients are used to test the SLB instance. For example, session persistence \(based on source IP addresses\) is enabled for a TCP listener and a client is used to test the load balancing service.

-   The ECS instance status is abnormal.

    Backend servers with abnormal heath status can also lead to an imbalance especially during a stress test. If the health check for a backend ECS instance fails or the health status of a backend ECS instance changes frequently, this will cause an imbalance.

-   TCP Keepalive is enabled.

    When some backend ECS instances enable TCP Keepalive and others do not, the connections will accumulate on the ECS instances with TCP Keepalive enabled. This scenario will cause an imbalance.


## Troubleshooting {#section_dkk_qby_wdb .section}

-   Check whether the weights of backend ECS instances are the same.
-   Check whether health checks of backend ECS instances fail or whether the health status is unstable in a specified period. Check whether the health check is correctly configured with the status code.
-   Check whether both the WLC scheduling algorithm and session persistence are enabled. If so, change the scheduling algorithm to WRR.

