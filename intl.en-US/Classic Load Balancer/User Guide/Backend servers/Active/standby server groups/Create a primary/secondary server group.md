# Create a primary/secondary server group

This topic describes how to create a primary/secondary server group and then add Elastic Compute Service \(ECS\) instances to the primary/secondary server group. A primary/secondary server group contains a primary server and a secondary server that can fail over to prevent service interruption. By default, the primary server handles all requests that are distributed by the SLB instance. When the primary server fails, requests are redirected to the secondary server.

Before you create a primary/secondary server group, make sure that the following requirements are met:

-   A Server Load Balancer \(SLB\) instance is created. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).
-   ECS instances are created and applications are deployed on the ECS instances to process requests.

**Note:** Only TCP and UDP listeners support primary/secondary server groups.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  On the Instances page, select the region of the SLB instance that you want to manage.

3.  Find the SLB instance and click its instance ID.

4.  Click the Primary/Secondary Server Groups tab.

5.  On the Primary/Secondary Server Groups tab, click **Create Primary/Secondary Server Group**.

6.  On the Create Primary/Secondary Server Group page, configure the primary/secondary server group.

    1.  In the **Primary/Secondary Server Group Name** field, enter a name for the primary/secondary server group.

    2.  Click **Add**. In the My Servers panel, select the ECS instances that you want to add.

        You can add only two ECS instances to a primary/secondary server group.

    3.  Click **Next**.

    4.  On the **Configure Ports and Weights** wizard page, specify the backend ports that you want to open on the ECS instances to receive requests. If you want to open more than one port on an ECS instance, click **Add Port** in the **Actions** column.

        You can open the same port on different backend servers that are connected to the same SLB instance.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8545109951/p7370.png)

    5.  Click **Add**.

7.  On the **Create Primary/Secondary Server Group** page, select an ECS instance in the **Type** column as the primary server.

8.  Click **Create**.


**Related topics**  


[CreateMasterSlaveServerGroup](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Active/standby server groups/CreateMasterSlaveServerGroup.md)

