# Delete an SLB instance {#task_bh5_dll_vdb .task}

This topic describes how to delete a Server Load Balancer \(SLB\) instance. To avoid additional charges, you can delete an SLB instance when you no longer need the load balancing service. Deleting the SLB instance does not delete or affect backend ECS instances.

**Note:** 

-   If you have resolved a domain name to the SLB endpoint, resolve it to another IP address first to avoid service interruptions.
-   Only Pay-As-You-Go SLB instances can be released. Subscription SLB instances are automatically released if they are not renewed in a timely manner.
-   The backend ECS instances are still running after the SLB instance is released. You can release the backend ECS instances if you do not need them anymore.

1.  Log on to the [SLB console](https://partners-intl.console.aliyun.com/#/slb).
2.  On the Instances page, select the region to which the target SLB instance belongs.
3.  Find the target SLB instance, click **Release** at the bottom of the list or choose **More** \> **Release** in the **Actions** column. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15703/15668727507522_en-US.png)

4.  In the Release dialog box, select **Release Now** or **Release on Schedule**. 

    If you select **Release on Schedule**, set a release time.

5.  Click **Next**.
6.  Click **OK** to release the SLB instance.

