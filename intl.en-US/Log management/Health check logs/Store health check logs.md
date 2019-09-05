# Store health check logs {#task_1597687 .task}

You can view the health logs of Server Load Balancer \(SLB\) in the past three days on the Health Check Logs page. If you want to get health check logs generated three days or longer before, you can store the health check logs to Object Storage Service \(OSS\) where you can also download the health check logs.

You can view the health check logs of backend servers by using the health check log function of SLB. Currently, logs in the past three days are provided. If you want to view more logs, store the health check logs to OSS.

You can enable and disable the storage function at any time. After the storage function is enabled, SLB creates a folder named AliyunSLBHealthCheckLogs in the selected OSS bucket to store health check logs of SLB. Health check logs are generated on an hourly basis and the system automatically creates a subfolder named after the date to store the log files generated in that day, for example, 20170707.

The log files generated in each hour of a day are named after the time when they are generated. For example, the name of a log file generated between 00:00-01:00 is 01.txt and the name of a log file generated between 01:00-02:00 is 02.txt.

**Note:** Health check logs are generated only when the health status of a backend server is abnormal. If no failures occur to backend servers in an hour, no health check logs are generated in that hour.

To store health check logs, follow these steps:

1.  [Create a bucket](#section_tx2_td4_vdb)
2.  [Authorize SLB to access OSS](#section_y4n_3f4_vdb)
3.  [Configure log storage](#section_bhz_4g4_vdb)

## Step 1 Create a bucket {#section_adr_o9s_8l1 .section}

1.  Open the [OSS product page](https://www.alibabacloud.com/product/oss?spm=a2c5t.11065253.1996646101.searchclickresult.2003677d1D1ihj) and click **Buy Now** to activate the OSS service.
2.  Log on to the OSS console.
3.  Click **Create Bucket**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/15676493872444_en-US.png)

4.  In the Create Bucket dialog box, configure the bucket and click **OK**. 

    **Note:** Make sure that the bucket and the SLB instance belong to the same region.


## Step 2 Authorize SLB to access OSS {#section_uts_s6t_3xo .section}

After creating a bucket, you must authorize the role `SLBLogDefaultRole` to access OSS resources.

**Note:** The authorization is required only for the first time.

1.  In the left-side navigation pane of the SLB console, choose **Logs** \> **Health Check Logs**.
2.  On the Health Check Logs page, click the **Log Storage** tab.
3.  Click **1. Activate OSS.** if OSS has not been activated yet.
4.  After you activate the OSS service, return to the Health Check Logs page, click **Activate Now** in the 2. Authorize the required RAM role. section.
5.  Read the authorization description, and then click **Confirm Authorization Policy**.
6.  Log on to the RAM console.
7.  In the left-side navigation pane, click **Roles**, find the role named SLBLogDefaultRole, and then click **Authorize**.
8.  In the Edit Role Authorization Policy dialog box, find the **AliyunOSSFullAccess** policy, click the policy, and then click **OK**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/15676493872449_en-US.png)

    After the authorization, click the name of the role **SLBLogDefaultRole**, and then click the **Role Authorization Policies** tab to view the attached policy.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/15676493872450_en-US.png)


## Step 3 Configure log storage {#section_3n9_zom_zjw .section}

1.  Log on to the [Server Load Balancer console](https://partners-intl.console.aliyun.com/#/slb). 
2.  In the left-side navigation pane, choose **Logs** \> **Health Check Logs**.
3.  On the Health Check Logs page, click the **Log Storage** tab.
4.  Find the target region and click **Configure Log Storage**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15683/15676493877333_en-US.png)

5.  In the Configure Log Storage dialog box, select a bucket to store health check logs, and then click **OK**.
6.  Turn on the status switch to enable log storage.

