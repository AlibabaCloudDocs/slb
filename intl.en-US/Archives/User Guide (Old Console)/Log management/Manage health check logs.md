# Manage health check logs {#concept_dvm_dnn_vdb .concept}

You can view the health logs within three days on Health Check Log page.  If you want to get the health check logs three days before or longer, you can store the health check logs to OSS. Therefore, you can download complete health check logs.

## Store health check logs {#section_xvc_fd4_vdb .section}

You can view the health check logs of the backend servers by using the health check log function. Currently, logs in three days are provided. If you want to view more logs, store the health check logs to OSS.

You can enable and disable the storage function at any time.  After the storage function is enabled, SLB will create a folder named AliyunSLBHealthCheckLogs in the selected bucket to store the health check logs. The health logs are generated hourly and the system will create a subfolder named after the date to store the log files generated in that day, for example 20170707.

The log files in a day are named after the time when they are generated. For example, the log file that is generated between 00:00-01:00, the file name will be 01.txt and the log file that is generated between 01:00-02:00, the file name will be 02.txt.

**Note:** The health check logs are generated only when the backend server is abnormal. If no failures occur for all the backend servers in an hour, no health check logs are generated in that hour.

To store health check logs, complete these steps:

1.  [Crate a bucket.](#section_tx2_td4_vdb)
2.  [Authorize SLB to access OSS](#section_y4n_3f4_vdb)
3.  [Configure log storage](#section_bhz_4g4_vdb)

## Step 1 Create a bucket {#section_tx2_td4_vdb .section}

1.  Open the [OSS product page](https://www.aliyun.com/product/oss/?spm=5176.doc31884.2.2.P4koVw) and click **Buy Now** to activate the OSS service.
2.  Log on to the OSS console.
3.  Click **Create Bucket**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/2444_en-US.png)

4.  In the Create Bucket dialog box, configure the bucket and click **OK**.

    **Note:** Make sure that the region of the bucket and the SLB instance are the same.


## Step 2 Authorize SLB to access OSS {#section_y4n_3f4_vdb .section}

After creating a bucket, you have to authorize the log role \(`SLBLogDefaultRole`\) to access OSS resources.

**Note:** The authorization is required only for first configuration.

1.  On the SLB console, click **Logs** \> **Health Check Log**.
2.  Click **1. Activate OSS.** if OSS has not been activated yet.
3.  On the Health Check Log page, click **Add Role Now** in the 2. Add the RAM role to your account. section.
4.  Read the authorization description, and then click **Confirm Authorization Policy**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/2448_en-US.png)

5.  Log on to the RAM console.
6.  In the left-side navigation pane, click **Roles** and find the role named SLBLogDefaultRole, and then click **Authorize**.
7.  In the Edit Role Authorization Policy dialog box, find the **AliyunOSSFullAccess** policy, and then click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/2449_en-US.png)

    After the authorization, click **SLBLogDefaultRole**, and then click **Role Authorization Policies** to view the attached policy.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/2450_en-US.png)


## Step 3 Configure log storage {#section_bhz_4g4_vdb .section}

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  In the left-side navigation pane, click **Logs** \> **Health Check Log**.
3.  On the Health Check Log page, click **Storage**.
4.  Click **Logstores Configuration** link of the target region.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/2452_en-US.png)

5.  In the Logstores Configuration dialog box, select a bucket to store health check logs, and then click **Confirm**.
6.  Click the status switch to enable log storing.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/2454_en-US.png)


## View health check logs {#section_ocw_5h4_vdb .section}

To view the health check logs in three days, complete these steps:

1.  Log on to the [SLB console](https://slbnew.console.aliyun.com/#/list/cn-hangzhou).
2.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
3.  In the left-side navigation pane, click **Logs** \> **Health Check Log**.
4.  On the Health Check Log page, click the **View Log** tab.

    **Note:** Health check logs are generated only when the health status of the backend servers is abnormal. If no failures occur for all the backend servers in an hour, no health check logs are generated in that hour.

    -   The `SLB_instance_IP:port to Added_ECS_instance_IP:port abnormal; cause:XXX` log message indicates that the backend server is abnormal. Troubleshoot according to the detailed error message.
    -   The `SLB_instance_IP:port to Added_ECS_instance_IP:port normal` log message indicates that the backend server becomes normal again.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/2458_en-US.png)


## Download health check logs {#section_iqd_k34_vdb .section}

You can download the completed health check logs stored in OSS.

1.  Log on to the OSS console.
2.  On the Overview page, click the target bucket and then click **Files**.
3.  On the Files page, click AliyunSLBHealthCheckLogs/.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/2459_en-US.png)

4.  Click the folder of the heath logs to download.
5.  Click **Edit** of the target folder. Then, click **Copy File URL** in the displayed page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4149/2460_en-US.png)

6.  Enter the copied URL in the web browser to download the logs.

