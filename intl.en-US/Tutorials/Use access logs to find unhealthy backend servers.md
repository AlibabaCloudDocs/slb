# Use access logs to find unhealthy backend servers

When the response is delayed, you can view the response time of the SLB instance in the dashboard provided by Log Service. Then you can find unhealthy backend servers.

This topic describes how to use access logs to rapidly find unhealthy backend servers. For more information, see [Configure access logging]().

## Step 1: Configure SLB access logs

Before you configure LB access logs, make sure that:

1.  A Layer-7 listener is added.
2.  Log Service is activated.

Perform the following operations:

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, choose **Logs** \> **Access Logs**.
3.  Select the region for the SLB instance.
4.  Click **Authorize**, and then click **Confirm Authorization Policy** to allow SLB to write logs to Log Service.

    If you log on to the console as a RAM user, you must first use your Alibaba Cloud account to authorize the RAM user. For more information, see [Authorize a RAM user to use access logs](/intl.en-US/Classic Load Balancer/User Guide/Log management/Access logs/Authorize a RAM user to use access logs.md).

    **Note:** If you have authorized SLB, skip this step.

5.  On the Access Logs page, find the SLB instance and click **Configure Logging** in the Actions column.
6.  Configure Project and Logstore and then click **OK**.

    **Note:** Make sure that the name of the Project is globally unique and the region of the Project is the same as that of the SLB instance.


## Step 2: View access logs

Perform the following operations:

1.  Go to the log search page. You can go to the search page from the SLB or Log Service console.
    -   From the SLB console

        On the Access Logs page, click **View Logs**.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3291019951/p7479.png)

    -   From the Log Service console

        On the Logstores page, click **Search** of the Logstore.

2.  Click the log field to view detailed information.
3.  Enter an SQL statement to query specific access logs.

    For example, you can enter the following SQL statement to query the Top20 clients, which is used to analyze the request source and assist business decision-making.

    ```
    * | select ip_to_province(client_ip) as client_ip_province, count(*) as pv group by
          client_ip_province order by pv desc limit 50
    ```

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3291019951/p2494.png)


## Step 3: Find unhealthy backend servers

You can find unhealthy backend servers by checking the dashboard of Log Service.

1.  Log on to the [Log Service](https://sls.console.aliyun.com) console and click the project link of the SLB instance.
2.  In the left-side navigation pane, click ![Dashboard](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9636821161/p229906.png).
3.  Click the link of the SLB access logs.
4.  In the dashboard, view the value in the **top upstream response time** tab. You can choose to display the **Average upstream response time \(s\)** in descending order to check if the response time of a backend server is more than one second.

    If the response time is within one second, run the ssh command to log on to the backend server. Check if the CPU utilization is high and handle the issue if yes.

