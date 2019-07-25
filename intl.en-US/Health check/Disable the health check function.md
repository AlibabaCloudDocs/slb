# Disable the health check function {#task_it1_1qn_vdb .task}

If you disable the health check function, requests may be distributed to unhealthy ECS instances, resulting in disruption to your services. Therefore, we recommend that you enable the health check function.

**Note:** You can only disable the health check function for HTTP and HTTPS listeners. The health check function for UDP and TCP listeners cannot be disabled.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select the region of the target SLB instance. On the Server Load Balancer page, find the target SLB instance and click the instance ID.
3.  On the Listeners tab, find the target listener and click **Configure** in the **Actions** column.
4.  On the Configure Listener page, click **Next** until the **Health Check** tab is displayed.
5.  Turn off **Enable Health Check**, click **Next**, click **Submit**, and then click **OK**.

