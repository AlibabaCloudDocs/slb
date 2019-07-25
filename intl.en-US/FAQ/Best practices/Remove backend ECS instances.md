# Remove backend ECS instances {#concept_mhh_xj5_vdb .concept}

Directly removing backend ECS instances from a Server Load Balancer instance may cause service interruption. We recommend setting the weight of an ECS instance to zero first, and then remove it when no traffic is distributed to it.

## Remove backend ECS instances {#section_ed4_qbw_wdb .section}

Directly removing backend ECS instances from a Server Load Balancer instance may cause service interruption. We recommend that you follow these steps to remove ECS instances:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Choose a region and then click the ID of the target Server Load Balancer instance.
3.  In the Details left-side navigation pane, click **Server** \> **Backend Server**.

    If the ECS instance is added to a server group, click the VServer group or active/standby server group accordingly.

4.  Hover the mouse pointer to the weight of the target ECS instance and then set the value to 0.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4166/15421821563124_en-US.png)

5.  When no traffic is distributed to the ECS instance, click **Remove** to remove it from the backend server pool.

## Troubleshoot {#section_ukg_5cw_wdb .section}

If there are ongoing service requests sent to the ECS instance after removing it from the backend server pool, check the following:

-   Whether the ECS instance is added to backend server pools of other Server Load Balancer instances.

    You can use the ECS instance ID and the Intranet IP to filter Server Load Balancer instances that the ECS instance is added to.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4166/15421821563126_en-US.png)

-   Log on to the ECS instance, run the `netstat` command to check whether the ECS instance is deployed with Internet services.
    -   Windows: Run `netstat -ano` to view all open ports on the instance.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4166/15421821563130_en-US.png)

    -   Linux: Run this command to view all open ports on the instance or use other parameters of the `netstat` command.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4166/15421821563131_en-US.png)


