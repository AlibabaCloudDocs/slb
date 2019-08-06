# Create a master-slave server group {#task_stv_n4n_vdb .task}

If you have traditional active/standby requirements, where one backend server is used as the master server and the other is used as the slave server, create a master-slave server group. When the master server works normally, requests are distributed to it; when the master server is down, the requests will be distributed to the slave server to avoid service interruption.

-   You have [created an SLB instance](reseller.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#).
-   You have created ECS instances and deploy applications to process distributed requests. 

After a master-slave server group is configured for a listener, the listener will forward requests to the ECS instances in the server group instead of the ECS instances in the backend server pool.

**Note:** Only Layer-4 listeners \(TCP and UDP protocols\) support configuring master-slave server groups.

1.   Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb). 
2.   On the Instances page, select a region. 
3.  Click the ID of an SLB instance. 
4.  In the left-side navigation pane, click **Server** \> **Master-Slave Server Groups**. 
5.   On the Master-Slave Server Group page, click **Master-Slave Server Group**. 
6.   In the Master-Slave Server Group dialog box, complete these steps: 
    1.   Enter a group name in the **Group Name** field. 
    2.   Select the network type for the ECS instance you want to add. 
    3.   In the **Available Servers**, select the ECS instances to add. 
    4.   In the **Selected Servers** list, enter the port number and weight for each added ECS instance, and then select one ECS instance as the slave server. Click **Confirm**. 

