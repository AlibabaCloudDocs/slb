# Disable the health check feature

This topic describes how to disable the health check feature for a Server Load Balancer \(SLB\) instance. If you disable the health check feature, requests may be distributed to unhealthy backend Elastic Compute Service \(ECS\) instances. This causes service disruptions. We recommend that you enable the health check feature.

**Note:** You can disable the health check feature for only HTTP and HTTPS listeners. Health checks that are configured for UDP and TCP listeners cannot be disabled.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).

2.  On the Instances page, find the SLB instance that you want to manage and click its instance ID.

3.  On the Listener tab, find the listener for which you want to disable the health check feature and click **Modify Listener** in the **Actions** column.

4.  On the Configure Listener page, click **Next** to proceed to the **Health Check** wizard page.

5.  Turn off the Enable Health Check switch and click **Next**.

6.  Click **Submit** and click **OK**.


