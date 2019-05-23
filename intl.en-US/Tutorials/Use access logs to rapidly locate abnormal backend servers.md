# Use access logs to rapidly locate abnormal backend servers {#concept_knk_w3s_gfb .concept}

When client access delay occurs, you can view the dashboard in Log Service to analyze the response time of the SLB instance to rapidly locate an abnormal backend server.

This tutorial introduces how to use access logs to rapidly locate an abnormal backend server. For more information, see [Configure access logs](../intl.en-US/User Guide/Log management/Configure access logs.md#).

## Configure access logs {#section_fhr_xjs_gfb .section}

Before you configure access logs, make sure that:

-   A Layer-7 listener is added.
-   Log Service is activated.

To configure access logs, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, choose **Logs** \> **Access Logs**.
3.  Select a region.
4.  Click **Authorize**, and then click **Confirm Authorization Policy** to authorize SLB to write logs to Log Service.

    If you are a RAM user, you must obtain permissions from the corresponding account. For more information, see [Authorize a RAM user to use access logs](../intl.en-US/User Guide/Log management/Authorize a RAM user to use access logs.md#).

    **Note:** This step is required only at the first time.

5.  On the Access Logs page, find the target SLB instance and click **Configure Logging**.
6.  Select the LogProject and LogStore and then click **OK**.

    If there is no available LogStore, click **Log Service console** to create log projects.

    **Note:** Make sure that the name of the LogProject is globally unique and the region of the LogProject is the same as that of the SLB instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/15586041397478_en-US.png)


## Search access logs {#section_vgk_gks_gfb .section}

To search access logs, complete these steps:

1.  Go to the log search page. You can navigate to the search page from the SLB console or the Log Service Console:
    -   From the SLB console:

        On the Access Logs page, click **View Logs**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/15586041397479_en-US.png)

    -   From the Log Service Console:

        On the Logstores page, click **Search** of the target Logstore.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/155860413912838_en-US.png)

2.  Click the target log field to view detailed information.
3.  Enter an SQL statement to query access logs.

    For example, enter the following SQL statement to query the Top20 clients, which is used for analyzing the request source to assist business decision-making.

    ```
    * | select ip_to_province(client_ip) as client_ip_province, count(*) as pv group by
          client_ip_province order by pv desc limit 50
    ```

    ![](../DNslb1866251/../DNSLB11827830/images/2494_en-US.png)


## Locate the abnormal backend server {#section_bnz_gks_gfb .section}

You can locate the abnormal backend server by checking the dashboard of Log Service.

1.  On the Log Service console, click the project link of the SLB instance.
2.  In the left-side navigation pane, click **Search/Analytics - Query** \> **Dashboard**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/155860413912867_en-US.png)

3.  Click the link of the SLB access log.
4.  In the dashboard, view the value in the **top upstream response time** tab. You can select to display the **Average upstream response time \(s\)** in descending order to check if the response time of any backend server surpasses 1 second.

    If so, run the ssh command to log on to the backend server. Check if the CPU has kept running at high levels and handle the high loads.

    ![](images/12870_en-US.png)


