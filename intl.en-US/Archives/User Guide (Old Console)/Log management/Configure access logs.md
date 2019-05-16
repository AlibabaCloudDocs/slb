# Configure access logs {#concept_bl3_24n_vdb .concept}

By analyzing the access logs of an SLB instance with Alibaba Cloud Log Service, you can understand the behavior and geographical distribution of client users, troubleshoot problems and so on.

## What are access logs {#section_h3l_1ls_vdb .section}

SLB access logs collect detailed information of all requests sent to SLB, including the request time, client IP address, latency, request URL, server response, and so on. As the entry of Internet access, SLB receives massive client requests. You can use access logs to analyze user behavior and geographical distribution, troubleshoot issues.

After enabling SLB access logging, you can store access logs in the Logstore for analysis. You can also disable access logging at any time.

There is no extra charge for SLB access logs. But corresponding fees are collected when using Log Service. If you store logs in OSS, you can save storage costs.

**Note:** Only Layer-7 SLB supports configuring access logs and this function is available in all regions now.

## Benefits of SLB access logs {#section_jzd_pls_vdb .section}

The following are benefits of SLB access logs:

-   Simple log processing

    Free developers and maintenance staff from tedious and time-consuming log processing so that they can concentrate on business development and technical research.

-   Cost-effective

    Performance and cost problems must be taken into consideration when processing access logs, because the amount of SLB access logs is very large. Integrated with Log Service, the access log processing is faster and cost-effective than self-build open-source solutions. Log Service can analyze one hundred million logs in one second.

-   Real-time

    Scenarios such as DevOps, monitoring, and alerting require real-time log data. Traditional data storage and analysis tools cannot meet this requirement. For example, it takes long time to ETL data to Hive at which a lot of work is spent on data integration. Powered by its powerful computing capability, Log Service can process and analyze access logs in seconds.

-   Flexible

    You can enable or disable SLB access logging according to the instance capacity. Additionally, you can set the storage period \(1 to 365 days\) as needed and the Logstore's capacity is scalable to meet increasing business service demands.


## Configure access logs {#section_ntc_tls_vdb .section}

Before configuring access logs, make sure:

1.  A Layer-7 listener is added.
2.  Log Service is activated.

To configure access logs, complete these steps.

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  In the left-side navigation pane, click **Logs** \> **Access Log**.
3.  Click **Authorize**, and then click **Confirm Authorization Policy** to authorize SLB to write logs to Log Service.

    **Note:** If you are a RAM user, you must be authorized to use the SLB access logging. For more information, see [Authorize a RAM user to use access logging](reseller.en-US/Archives/User Guide (Old Console)/Log management/Authorize a RAM user to configure access logs.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082912474_en-US.png)

4.  On the Access Log page, find the target SLB instance and click **Configure**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082912475_en-US.png)

5.  Select a Log Service project and Logstore, and then click **Confirm**.

    If there is no available Logstore, click **Create**. Make sure that the name of the project is unique.

    **Note:** Make sure the Log Service project and the SLB instance are in the same region.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082912476_en-US.png)

6.  Configure data import.
    1.  Click the **Data Import Wizard** link to configure data import. Or click **Confirm** and configure data import on the Log Service console later. In this tutorial, the Data Import Wizard link is selected.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082912479_en-US.png)

    2.  Click **Next**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082912480_en-US.png)

    3.  Log Service has pre-configured indexing field for SLB. Click **Next**.

        **Note:** After enabling indexing search, you will be charged for indexing traffic.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082912482_en-US.png)

    4.  Click **Confirm** to complete data import.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082912483_en-US.png)


## Search and analyze access logs {#section_od1_l4s_vdb .section}

After configuring SLB access logging, you can search and view logs using the following fields.

|Field|Description|
|:----|:----------|
|body\_bytes\_sent|The size of HTTP body \(in byte\) sent to the client.|
|client\_ip|The client IP.|
|host|The host header in the request.|
|http\_user\_agent|The received http\_user\_agent header in the request.|
|request\_length|The request length including startline, HTTP header and HTTP body.|
|request\_method|The request method.|
|request\_time|The time interval from the first request received by the SLB to the response sent by the SLB.|
|request\_uri|The received request URI.|
|slbid|The SLB instance ID.|
|status|The response status code sent by the SLB.|
|upstream\_addr|The IP address and port number of the backend server.|
|upstream\_response\_time|The time from when SLB is ready to send requests to the backend server to when SLB sends response to the client.|
|upstream\_status|Response status code sent from backend servers.|

## Search access logs {#section_hd5_r4s_vdb .section}

To search access logs, complete these steps:

1.  Go to the log search page. You can navigate to the search page from the SLB console or the Log Service Console:
    -   From the SLB console:

        On the Access Log page, click **View Logs**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082922484_en-US.png)

    -   From the Log Service console:

        On the Logstores page, click **Search** of the target Logstore.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082922492_en-US.png)

2.  Click the corresponding index field to view detailed information.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082922493_en-US.png)

3.  Enter an SQL statement to query.

    For example, enter the following SQL statement to query Top 20 clients.

    ```
    * | select ip_to_province(client_ip) as client_ip_province, count(*) as pv group by
          client_ip_province order by pv desc limit 50
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082922494_en-US.png)


## Analyze access logs {#section_cvs_xps_vdb .section}

You can analyze access logs through the dashboard, which provides various graphic information.

To analyze access logs, complete these steps:

1.  On the Log Service console, click the project name of the target project.
2.  In the left-side navigation pane, click **Search/Analytics - Query** \> **Dashboard**, and then click **View**.

    You can view information such as top clients, top hosts, status code and so on.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082922495_en-US.png)


## Disable access logging {#section_vgd_kqs_vdb .section}

To disable access logging, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  In the left-side navigation pane, click **Logs** \> **Access Log**.
3.  Find the target instance, and then click **Delete**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15580082922497_en-US.png)


