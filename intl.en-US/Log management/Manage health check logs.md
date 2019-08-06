# Manage health check logs {#concept_dvm_dnn_vdb .concept}

You can view the health logs of Server Load Balancer \(SLB\) within three days on the Health Check Logs page. If you want to get health check logs generated three days or longer before, you can store the health check logs to OSS and download complete health check logs.

## Store health check logs {#section_xvc_fd4_vdb .section}

You can view the health check logs of backend servers by using the health check log function of SLB. Currently, logs in the past three days are provided. If you want to view more logs, store the health check logs to OSS buckets.

You can enable and disable the storage function at any time. After the storage function is enabled, SLB will create a folder named AliyunSLBHealthCheckLogs in the selected bucket to store health check logs of SLB. Health check logs are generated on an hourly basis and the system will create a subfolder named after the date to store the log files generated in that day, for example, 20170707.

The log files generated in each hour of a day are named after the time when they are generated. For example, the file name of a log file generated between 00:00-01:00 is 01.txt and the file name of a log file generated between 01:00-02:00 is 02.txt.

**Note:** Health check logs are generated only when backend servers are abnormal. If no failures occur to backend servers in an hour, no health check logs are generated in that hour.

To store health check logs, follow these steps:

1.  [Create a bucket](#section_tx2_td4_vdb)
2.  [Authorize SLB to access OSS](#section_y4n_3f4_vdb)
3.  [Configure log storage](#section_bhz_4g4_vdb)

## Step 1 Create a bucket {#section_tx2_td4_vdb .section}

1.  Open the [OSS product page](https://www.alibabacloud.com/product/oss?spm=a3c0i.7911826.1160486.dproductb1.19d214b3ZMTOMm) and click **Buy Now** to activate the OSS service.
2.  Log on to the OSS console.
3.  Click **Create Bucket**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/15640561302444_en-US.png)

4.  In the Create Bucket dialog box, configure the bucket and click **OK**.

    **Note:** Make sure that the bucket and the SLB instance belong to the same region.


## Step 2 Authorize SLB to access OSS {#section_y4n_3f4_vdb .section}

After creating a bucket, you must authorize the role \(`SLBLogDefaultRole`\) to access OSS resources.

**Note:** The authorization is required only for the first time.

1.  In the left-side navigation pane of the SLB console, click **Logs** \> **Health Check Logs**.
2.  Click **1. Activate OSS.** if OSS has not been activated yet.
3.  On the Health Check Logs page, click **Authorize Now** in the 2. Authorize the required RAM role. section.
4.  Read the authorization description, and then click **Confirm Authorization Policy**.
5.  Log on to the RAM console.
6.  In the left-side navigation pane, click **Roles**, find the role named SLBLogDefaultRole, and then click **Authorize**.
7.  In the Edit Role Authorization Policy dialog box, find the **AliyunOSSFullAccess** policy, click the policy, and then click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/15640561312449_en-US.png)

    After the authorization, click the role name of **SLBLogDefaultRole**, and then click the **Role Authorization Policies** tab to view the attached policy.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/15640561312450_en-US.png)


## Step 3 Configure log storage {#section_bhz_4g4_vdb .section}

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  In the left-side navigation pane, click **Logs** \> **Health Check Logs**.
3.  On the Health Check Logs page, click the **Log Storage** tab.
4.  Find the target region and click **Configure Log Storage**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15683/15640561317333_en-US.png)

5.  In the Configure Log Storage dialog box, select a bucket to store health check logs, and then click **OK**.
6.  Turn on the status switch to enable log storage.

## View health check logs {#section_ocw_5h4_vdb .section}

To view the health check logs generated in the past three days, follow these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  In the left-side navigation pane, click **Logs** \> **Health Check Logs**.
3.  On the Health Check Logs page, click the **Logs** tab.

    **Note:** Health check logs are generated only when the health status of a backend server is abnormal. Health check logs are generated every one hour. If no failure occurs to backend servers in an hour, no health check logs are generated in that hour.

    -   The `SLB_instance_IP:port to Added_ECS_instance_IP:port abnormal; cause:XXX` log message indicates that the backend server is abnormal. Troubleshoot according to the detailed error message.
    -   The `SLB_instance_IP:port to Added_ECS_instance_IP:port normal` log message indicates that the backend server becomes normal again.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15683/15640561317334_en-US.png)


## Download health check logs {#section_iqd_k34_vdb .section}

You can download the completed health check logs stored in OSS buckets.

1.  Log on to the OSS console.
2.  On the Overview page, click the target bucket and then click **Files**.
3.  On the Files page, click AliyunSLBHealthCheckLogs/.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/15640561312459_en-US.png)

4.  Click the folder of the heath logs to download.
5.  Click **Edit** of the target folder. Then, click **Copy File URL** in the displayed page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/15640561312460_en-US.png)

6.  Enter the copied URL in the web browser to download the logs.

