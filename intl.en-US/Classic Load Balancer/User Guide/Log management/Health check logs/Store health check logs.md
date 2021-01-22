# Store health check logs

You can view health check logs generated in the last three days on the Health Check Logs page. To view health check logs earlier than three days, you must download the complete health check logs and store them in an Object Storage Service \(OSS\) bucket.

You can view the health check logs of backend servers by using the log management feature of Server Load Balancer \(SLB\). SLB retains health check logs only for the last three days. To store health check logs for longer, you can store them in an OSS bucket.

You can enable and disable the log storage feature at any time. After log storage is enabled, SLB creates a folder named AliyunSLBHealthCheckLogs in the selected bucket to store health check logs. Health check logs of SLB instances are generated on an hourly basis. The system automatically creates a subfolder whose name corresponds to the date of the stored health check log files. For example, a subfolder may be named 20170707.

The log files generated each hour are named after the time at which they are generated. For example, a health check log file generated from 00:00 to 01:00 is named 01.txt, and a health check log file generated from 01:00 to 02:00 is named 02.txt.

**Note:** Health check logs are generated only when the health status of a backend server is abnormal. Health check logs are generated on an hourly basis. If no exceptions are detected on the backend server within an hour, no health check logs are generated for that hour.

## Step 1: Create a bucket

1.  On the [OSS product page](https://www.aliyun.com/product/oss/?spm=5176.doc31884.2.2.P4koVw), click **Activate OSS**.

2.  Log on to the [OSS console](https://oss.console.aliyun.com/overview).

3.  Click **Create Bucket**.

4.  In the Create Bucket panel, configure parameters and click **OK**.

    **Note:** Make sure that the bucket and the SLB instance are in the same region.


## Step 2: Authorize SLB to access OSS

After you create a bucket, you must authorize the `SLBLogDefaultRole` role to access OSS resources.

**Note:** Authorization is required only when you configure log storage for the first time.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).

2.  In the left-side navigation pane, choose **Logs** \> **Health Check Logs**.

3.  On the Health Check Logs page, click the **Log Storage** tab.

4.  Click **1. Activate OSS**.

5.  After OSS is activated, click **Activate Now** in the 2. Authorize the required RAM role section.

6.  On the Cloud Resource Access Authorization page, read the authorization description and click **Confirm Authorization Policy**.

7.  Log on to the [Resource Access Management \(RAM\) console](https://ram.console.aliyun.com/overview).

8.  In the left-side navigation pane, click **RAM roles**, find the SLBLogDefaultRole role, and then click **Add Permissions** in the Actions column.

9.  In the Add Permissions panel, set Select Policy to **System Policy**, select the **AliyunOSSFullAccess** policy from the list, and then click **OK**.

10. Click **Complete**.


## Step 3: Configure log storage

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **Logs** \> **Health Check Logs**.

3.  On the Health Check Logs page, click the **Log Storage** tab.

4.  Click **Configure Log Storage** corresponding to a region.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9810122851/p7333.png)

5.  In the Configure Log Storage panel, select the bucket that you created and set Log Type to Health Check Log.

6.  Click **OK**.

7.  Turn on the switch in the **Status** column to enable log storage.


