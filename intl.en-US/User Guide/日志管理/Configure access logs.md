# Configure access logs {#concept_bl3_24n_vdb .concept}

This topic describes how to configure access logs. By using Alibaba Cloud Log Service, you can analyze the access logs of a Server Load Balancer \(SLB\) instance to understand the behavior and geographical distribution of client users and troubleshoot problems.

## What are access logs? {#section_h3l_1ls_vdb .section}

The access logs collect detailed information of all requests sent to an SLB instance, including the request time, client IP address, latency, request URL, and server response. As the entry of Internet access, SLB receives massive client requests. You can use access logs to analyze user behavior and geographical distribution, and conduct troubleshooting.

After you enable the SLB access log feature, you can store the access logs in the Logstore of Log Service to collect and analyze the access logs. You can also disable the access log feature at any time.

SLB access logs can be used free of charge. You only need to pay for fees related to the use of Log Service.

**Note:** 

-   Only Layer-7 SLB supports configuring access logs and this function is available in all regions.
-   Make sure that the HTTP header value does not contain `||`, otherwise, the exported logs may be misplaced.

## Benefits {#section_jzd_pls_vdb .section}

The following are benefits of SLB access logs:

-   Easy to use

    Free developers and maintenance staff from tedious and time-consuming log processing so that they can concentrate on business development and technical research.

-   Cost-effective

    Access logs are typically massive. Processing access logs takes a lot of time and consumes a lot of resources. With Log Service, the access log processing is faster and cost-effective than self-build open-source solutions. Log Service can analyze one hundred million logs in one second.

-   Real-time

    Scenarios such as DevOps, monitoring, and alerting require real-time log data. Traditional data storage and analysis tools cannot meet this requirement. For example, it takes long time to ETL data to Hive where a lot of time is spent on data integration. Powered by its powerful big data computing capability, Log Service can process and analyze access logs in seconds.

-   Flexible

    You can enable or disable the SLB access log feature according to the instance specification. Additionally, you can set the storage period \(1 to 365 days\) as needed and the Logstore's capacity is scalable to meet increasing service demands.


## Configure access logs {#section_ntc_tls_vdb .section}

Before configuring access logs, make sure:

-   A Layer-7 listener is added.
-   Log Service is activated.

To configure access logs, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  In the left-side navigation pane, choose **Logs** \> **Access Logs**.
3.  Select a region.
4.  Click **Authorize**, and then click **Confirm Authorization Policy** to authorize SLB to write logs to Log Service.

    If you are using a RAM account, the primary account must perform authorization. For more information, see [Authorize a RAM user to use access logging](reseller.en-US/Archives/User Guide (Old Console)/Log management/Authorize a RAM user to configure access logs.md#).

    **Note:** This operation is required only at the first time.

5.  On the Access Logs page, find the target SLB instance and click **Configure Logging**.
6.  Select the LogProject and LogStore of Log Service and then click **OK**.

    If there is no available LogStore, click **Log Service console** to create log projects.

    **Note:** Make sure that the name of the LogProject is globally unique and the region of the LogProject is the same as that of the SLB instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/15560980027478_en-US.png)


## Search and analyze access logs {#section_od1_l4s_vdb .section}

After configuring SLB access logs, you can search and view logs using the following indexing fields.

|Field|Description|
|:----|:----------|
|body\_bytes\_sent|The size of HTTP body \(in byte\) sent to the client.|
|client\_ip|The client IP address.|
|host|The host header in the request.|
|http\_user\_agent|The received http\_user\_agent header in the request.|
|request\_length|The length of the request including startline, HTTP header and HTTP body.|
|request\_method|The request method.|
|request\_time|The interval between the time SLB receives the first request and the time SLB returns a response.|
|request\_uri|The URL of the received request.|
|Slbid|The ID of the SLB instance.|
|status|The status of the SLB response.|
|Upstream\_addr|The IP address and port number of the backend server.|
|upstream\_response\_time|The interval between the time SLB sends a request to the backend server and the time SLB sends a response to the client.|
|upstream\_status|The response status code of the backend server received by SLB.|

## Search access logs {#section_hd5_r4s_vdb .section}

To search access logs, complete these steps:

1.  Go to the log search page. You can navigate to the search page from the SLB console or the Log Service Console:
    -   From the SLB console:

        On the Access Logs page, click **View Logs**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/15560980027479_en-US.png)

    -   From the Log Service Console:

        On the Logstores page, click **Search** of the target Logstore.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/155609800212838_en-US.png)

2.  Click the target log field to view detailed information.
3.  Enter an SQL statement to query access logs.

    For example, enter the following SQL statement to query the Top20 clients, which is used for analyzing the request resource to assist business decision-making.

    ```
    * | select ip_to_province(client_ip) as client_ip_province, count(*) as pv group by
          client_ip_province order by pv desc limit 50
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4150/15560980022494_en-US.png)


## Analyze access logs {#section_cvs_xps_vdb .section}

You can analyze access logs through the dashboard, which provides rich graphic information.

To analyze access logs, complete these steps:

1.  In the Log Service console, click the project link of the SLB instance.
2.  In the left-side navigation pane, click **Search/Analytics - Query** \> **Dashboard**, and then click the name of the access log.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/155609800312867_en-US.png)


## Disable access logging {#section_vgd_kqs_vdb .section}

To disable access logging, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  In the left-side navigation pane, choose **Logs** \> **Access Logs**.
3.  Select a region.
4.  On the Access Logs page, find the target instance and click **Delete** to disable access logging.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15681/15560980037480_en-US.png)

5.  In the displayed dialog box, click **OK**.

