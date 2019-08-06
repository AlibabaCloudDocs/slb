# Manage a default server group {#concept_ewt_whp_42b .concept}

Before you use the Server Load Balancer \(SLB\) service, you must add at least one default server to the default server group to receive client requests forwarded by SLB.

## Add default servers {#section_jqy_c3p_42b .section}

Before you add ECS instances to the default server group, make sure the following conditions are met:

-   An SLB instance is created. For more information, see [Create an SLB instance](reseller.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#).
-   ECS instances are created and applications are deployed on the ECS instances to process distributed requests.

To add backend servers, follow these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the Default Server Group tab.
5.  Click **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15669/15647270307365_en-US.png)

6.  On the Available Servers page, select the ECS instances to add to the default server group.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15669/15647270307367_en-US.png)

7.  Click **Next: Set Weight and Port**.
8.  On the Available Servers page, set the weights and ports of added ECS instances, and click **OK**.

    Weight: An ECS instance with a higher weight receivers more requests.

    You can modify server weights in batches:

    -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156472703011116_en-US.png): Duplicate to below. If you modify the weight of the current server, the weights of all servers blow are also changed.
    -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156472703011119_en-US.png): Duplicate to above. If you modify the weight of the current server, the weights of all servers above are also changed.
    -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156472703011120_en-US.png): Duplicate to all. If you modify the weight of the current server, the weights of all servers in the default server group are also changed.
    -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156472703111121_en-US.png): Clear all. If you clear the weight of the current server, the weights of all servers in the default server group are also cleared.
    **Note:** If the weight is set to 0, the server no longer receives new requests.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15669/156472703111124_en-US.png)

9.  Click **OK**.

## Edit the weight of a backend server {#section_iwj_tjp_42b .section}

To edit the weight of a backend server, follow these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the Default Server Group tab.
5.  Rest the pointer over the weight value of the target backend server, and then click the displayed pencil icon.

    ![](images/7470_en-US.png)

6.  Modify the weight and then click **OK**.

    An ECS instance with a higher weight receives more requests.

    **Note:** If the weight is set to 0, no requests are sent to the ECS instance.


## Remove a backend server {#section_mdw_fkp_42b .section}

To remove a backend server, follow these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the Default Server Group tab.
5.  Find the target backend server and click **Remove** in the **Actions** column.

