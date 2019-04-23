# Delete an SLB instance {#task_bh5_dll_vdb .task}

Delete the SLB instance when you no longer need the load balancing service to avoid additional charges. Deleting the Server Load Balancer instance does not delete or affect backend ECS instances.

**Note:** 

-   If you have resolved a domain name to the SLB endpoint, resolve it to another IP address first to avoid service interruption.
-   Only Pay-As-You-Go SLB instances can be released. Subscription SLB instances are automatically released if they are not renewed timely.
-   The backend ECS instances are still running after the SLB instance is released. You can release the backend ECS instances if you do not need them anymore.

1.   Log on to the [SLB console](https://partners-intl.console.aliyun.com/#/slb). 
2.   On the Instances page, select the region where the instance is located. 
3.  Locate the target instance, click **Release** at the bottom of the list or click **More** \> **Release** in the actions column. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15703/15560018517522_en-US.png)

4.   In the Release dialog box, select **Release Now** or **Release on Schedule**. 

    If you select **Release on Schedule**, set a release time.

5.  Click **Next**. 
6.  Click **OK** to release the SLB instance. 

