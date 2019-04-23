# Manage a default server group {#concept_ewt_whp_42b .concept}

Before using the SLB service, you must add at least one default server to receive client requests forwarded by SLB.

## Add default servers {#section_jqy_c3p_42b .section}

Before adding ECS instances to the default server group, make sure the following conditions are met:

-   You have [created an SLB instance](reseller.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#).
-   You have created ECS instances and deployed applications to process distributed requests.

To add ECS instances, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, select a region.
3.  Click the ID of the target instance.
4.  Click the Default Server Group tab.
5.  Click **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15669/15560190927365_en-US.png)

6.  On the Available Servers page, find the target ECS instance and click **Add**, or click multiple target ECS instances and click **Add to Selected Server List** at the bottom of the page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15669/15560190927367_en-US.png)

7.  Click **OK**.
8.  In the Available Servers dialog box, specify the weights of ECS instances and click **OK**.

    Weight: An ECS instance with a higher weight receivers more requests.

    **Note:** If the weight is set to 0, no requests will be sent to the ECS instance.

    You can modify the ports and weights of added servers in batches.

    -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/155601909211116_en-US.png): Duplicate to below. If you modify the weight of the current server, the weights of all servers blow are also changed.
    -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/155601909211119_en-US.png): Duplicate to above. If you modify the weight of the current server, the weights of all servers above are also changed.
    -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/155601909211120_en-US.png): Duplicate to all. If you modify the weight of the current server, the weights of all servers in the default server group are also changed.
    -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/155601909311121_en-US.png): Clear all. If you clear the weight of the current server, the weights of all servers in the default server group are also cleared.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15669/155601909311124_en-US.png)

9.  Click **OK**.

## Edit the weight of a backend server {#section_iwj_tjp_42b .section}

To edit the weight of a backend server, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, select a region.
3.  Click the ID of the target SLB instance.
4.  Click the Default Server Group tab.
5.  Hover the mouse to the weight area of the target backend server, and then click the displayed pencil icon.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15669/15560190937471_en-US.png)

6.  Modify the weight and then click **OK**.

    An ECS instance with a higher weight will receive a larger number of connection requests.

    **Note:** If the weight is set to 0, no requests will be sent to the ECS instance.


## Remove a backend server {#section_mdw_fkp_42b .section}

To remove a backend server, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, select a region.
3.  Click the ID of the target SLB instance.
4.  Click the Default Server Group tab.
5.  Click **Remove** in the **Actions** column to remove the backend server.

