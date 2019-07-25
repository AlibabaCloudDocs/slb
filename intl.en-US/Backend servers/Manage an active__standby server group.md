# Manage an active/standby server group {#concept_ewt_whp_42b .concept}

If you need active/standby failover configurations, where one backend server is used as the active server and the other as the standby server, you can create an active/standby server group. When the active server works normally, requests are distributed to the active server. If the active server is down, requests are distributed to the standby server to avoid service interruptions.

An active/standby server group only contains two ECS instances. One acts as the active server and the other acts as the standby server. No health check is performed on the standby server. When the active server is declared as unhealthy, the system forwards traffic to the standby server. When the active server is declared as healthy and restores service, the traffic is forwarded to the active server again.

**Note:** Only Layer-4 listeners \(TCP and UDP protocols\) support active/standby server groups.

## Create an active/standby server group {#section_jqy_c3p_42b .section}

Before you create an active/standby server group, make sure the following conditions are met:

-   A Server Load Balancer \(SLB\) instance is created. For more information, see [Create an SLB instance](intl.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#).
-   ECS instances are created and applications are deployed on the ECS instances to process distributed requests.

To create an active/standby server group, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/).
2.  On the Server Load Balancer page, select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the Active/Standby Server Groups tab.
5.  On the Active/Standby Server Groups tab, click **Create Active/Standby Server Group**.
6.  On the Create Active/Standby Server Group page, complete these steps:
    1.  In the **Name** filed, enter a name for the active/standby server group to be created.
    2.  Click **Add** and on the Available Servers page, select the servers to add.

        You can add up to two ECS instances to an active/standby server group.

    3.  Click **Next: Set Weight and Port**.
    4.  In the **Servers Added** section, set the port, select an active server, and click **OK**.

        -   **Port**: The backend port opened on the ECS instance to receive requests.

            The backend ports in an SLB instance can be the same.

        -   **Server**: Select a server to act as the active server.
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15671/15640486867370_en-US.png)


## Delete an active/standby server group {#section_upw_1np_42b .section}

To delete an active/standby server group, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/).
2.  On the Server Load Balancer page, select the region of the target SLB instance.
3.  Click the ID of the target SLB instance.
4.  Click the Active/Standby Server Groups tab.
5.  Find the target active/standby server group and click **Delete** in the **Actions** column.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15671/15640486877475_en-US.png)

6.  In the displayed dialog box, click **OK**.

