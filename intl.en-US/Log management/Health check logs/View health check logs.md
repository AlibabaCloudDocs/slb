# View health check logs {#task_1597697 .task}

You can view the health check logs of Server Load Balancer \(SLB\) instances generated in the past three days through the SLB console.

1.  Log on to the [Server Load Balancer console](https://partners-intl.console.aliyun.com/#/slb). 
2.  In the left-side navigation pane, choose **Logs** \> **Health Check Logs**.
3.  On the Health Check Logs page, click the **Logs** tab. 

    **Note:** Health check logs are generated only when the health status of a backend server is abnormal. Health check logs are generated every one hour. If no failure occurs to backend servers in an hour, no health check logs are generated in that hour.

    -   The `SLB_instance_IP:port to Added_ECS_instance_IP:port abnormal; cause:XXX` log message indicates that the backend server is abnormal. Troubleshoot according to the detailed error message.
    -   The `SLB_instance_IP:port to Added_ECS_instance_IP:port normal` log message indicates that the backend server becomes normal again.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15683/15676504037334_en-US.png)


