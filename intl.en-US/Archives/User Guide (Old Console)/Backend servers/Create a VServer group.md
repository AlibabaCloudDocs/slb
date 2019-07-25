# Create a VServer group {#task_xm3_p4n_vdb .task}

A virtual server group \(VServer group\) is a group of ECS instances. VServer groups allow you to manage and customize backend servers in the listener dimension. It allows listeners in a Server Load Balancer instance to use different backend servers. Then, different requests can be distributed to different backend servers.

-   You have [created an SLB instance](intl.en-US/User Guide/SLB instances/Create an SLB instance.md#).
-   You have created an ECS instance for receiving the forwarded requests.

If you use a VServer group when configuring a listener, the listener distributes requests to the associated VServer group. The listener no longer distribute the requests to ECS instances in the backend server pool.

For a Layer-7 listener, if you add backend servers in the server pool, configure a VServer group, and adding a forwarding rule at the same time, the requests are distributed in the following order:

-   If the client requests match the configured domain name forwarding rule, the requests are distributed to the VServer group associated with the rule.
-   If not, the requests are distributed to the VServer group associated with the listener.
-   If no VServer group is configured for the listener, the requests are distributed to the ECS instances in the backend server pool.

When using the VServer group, note the following limitations:

-   Only backend servers in the same region as listeners can be added to a VServer group.
-   One ECS instance can be added to multiple VServer groups.
-   One VServer group can be associated with multiple listeners.
-   The VServer group consists of multiple ECS instances with different port numbers.

1.  Log on to the [SLB console](https://slbnew.console.aliyun.com/?spm=5176.2020520102.1002.d10slb.Nu53OX#/list/cn-hangzhou). 
2.  On the Instances page, select a region. 
3.  Click the ID of an SLB instance. 
4.  In the left-side navigation pane, click **Server** \> **VServer Group**. 
5.  On the VServer Group page, click **Create VServer Groups**. 
6.  In the Create VServer Group dialog box, complete these steps: 
    1.  Enter a group name in the **Group Name** field.
    2.  Select the network type for the ECS instance you want to add.
7.  In the **Available Servers**, select the ECS instances to add. The selected instances are displayed in the **Selected Servers** list.
8.  In the **Selected Servers** list, enter the port number and weight for each added ECS instance, and then click **Confirm**. The created VServer group is displayed on the VServer Group page. You can delete or add ECS instances for the VServer group \(click **Edit**\). You can also associate this VServer Group with the instance's listeners or forwarding rules.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4124/2676_en-US.png)


