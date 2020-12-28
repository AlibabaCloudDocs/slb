# Why are requests unbalanced among ECS instances?

This topic describes the reasons why requests are unevenly distributed among ECS instances and how to troubleshoot this problem.

## Causes

Requests may be unevenly distributed among ECS instances due to the following reasons:

-   The ECS instances request only a small number of connections.
-   The ECS instances deliver different performance.

    **Note:** The memory usage of ECS instances is not an accurate indicator for determining whether requests are evenly distributed.

-   The session persistence feature is enabled.

    If session persistence is enabled, it causes request imbalance when a small number of clients access the SLB instance. This is especially common when a small number of clients are used to test the SLB instance. For example, session persistence based on source IP addresses is enabled for a TCP listener, and a client is used to conduct stress test on the load balancing service.

-   The ECS instance fails the health check.

    Backend servers in abnormal health status can also lead to request imbalance, especially during a stress test. Imbalance occurs if a backend ECS instance fails the health check or if the health status of a backend ECS instance changes frequently.

-   TCP Keepalive is enabled.

    When TCP Keepalive is enabled only for some backend ECS instances, connections accumulate on these ECS instance. This causes requests to be unevenly distributed.


## Troubleshooting methods and solutions

-   Check whether the weights of backend ECS instances are the same.
-   Check whether the ECS instances have failed health checks or if the health status is unstable in a specific period of time. Check whether the health check is correctly configured with the status code.
-   Check whether both the WLC scheduling algorithm and session persistence are enabled. If so, change the scheduling algorithm to WRR.

