# View health check logs

You can view health check logs generated in the last three days in the SLB console.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **Logs** \> **Health Check Logs**.

3.  On the Health Check Logs page, click the **Logs** tab.

    **Note:** Health check logs are generated only when the health status of a backend server is abnormal. Health check logs are generated on an hourly basis. If no exception is detected on the backend server within an hour, no health check logs are generated for that hour.

    -   If the entry `SLB_instance_IP:port to Added_ECS_instance_IP:port abnormal; cause:XXX` is displayed in the health check log, the health status of the backend server is abnormal. Troubleshoot based on the detailed error message.
    -   If the entry `SLB_instance_IP:port to Added_ECS_instance_IP:port normal` is displayed in the health check log, the health status of the backend server becomes normal again.

