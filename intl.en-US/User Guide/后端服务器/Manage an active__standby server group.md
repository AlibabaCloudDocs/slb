# Manage an active/standby server group {#concept_ewt_whp_42b .concept}

If you have traditional active/standby requirement, where one backend server is used as the active server and the other as the standby server, create an active/standby server group. When the active server works normally, requests are distributed to it; when the active server is down, the requests will be distributed to the standby server to avoid service interruption.

An active/standby server group only contains two ECS instances. One acts as the active server and the other acts as the standby server. No health check is performed on the standby server. When the active server is declared as unhealthy, the system forwards traffic to the standby server. When the active server is declared as healthy and restores service, the traffic is forwarded to the active server again.

**Note:** Only Layer-4 listeners \(TCP and UDP protocols\) support configuring active/standby server groups.

## Create an active/standby server group {#section_jqy_c3p_42b .section}

Before creating an active/standby server group, make sure the following conditions are met:

-   You have [created an SLB instance](reseller.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#).
-   You have created ECS instances and deploy applications to process distributed requests.

To add ECS instances, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/).
2.  On the Server Load Balancer page, select a region.
3.  Click the ID of the target SLB instance.
4.  Click the Active/Standby Server Groups tab.
5.  On the Active/Standby Server Groups page, click **Create Active/Standby Server Group**.
6.  On the Create Active/Standby Server Group page, complete these steps:
    1.  In the **Name** text box, enter the name of the active/standby server group.
    2.  Click **Add** to select the server to add in the Available Servers list.

        You can add up to two ECS instances to an active/standby server group.

    3.  Click **Add to Selected Server List** and click **OK**.
    4.  In the **Servers Added** tab, complete the following configuration and click **OK**.

        -   **Port**: The backend port opened on the ECS instance to receive requests.

            The back-end ports in a Server Load Balancer instance can be the same.

        -   **Server**: Select a server to act as the active server.
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15671/15560200757370_en-US.png)


## Delete an active/standby server group {#section_upw_1np_42b .section}

To delete an active/standby server group, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/).
2.  On the Server Load Balancer page, select a region.
3.  Click the ID of the target SLB instance.
4.  Click the Active/Standby Server Groups tab.
5.  Click **Delete** next to the target active/standby server group.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15671/15560200757475_en-US.png)

6.  In the displayed dialog box, click **OK**.

