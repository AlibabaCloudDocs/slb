# Create a VServer group {#task_1597080 .task}

A virtual server group \(VServer group\) is a group of ECS instances. If you associate a VServer group with a listener, the listener distributes requests to the associated VServer group instead of other backend servers.

Before you create a VServer group, make sure the following conditions are met:

-   A Server Load Balancer \(SLB\) instance is created. For more information, see [Create an SLB instance](reseller.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#).
-   ECS instances are created and applications are deployed on the ECS instances to process distributed requests.

Note the following before you create a VServer group:

-   The ECS instances added to a VServer group and the SLB instance must belong to the same region.
-   One ECS instance can be added to multiple VServer groups.
-   One VServer group can be associated with multiple listeners of an SLB instance.
-   A VServer group consists of ECS instances and application ports.

1.  Log on to the [Server Load Balancer console](https://partners-intl.console.aliyun.com/#/slb). 
2.  On the Server Load Balancer page, select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the VServer Groups tab.
5.  On the VServer Groups tab, click **Create VServer Group**.
6.  On the Create VServer Group page, configure the VServer group. 
    1.  Enter a name for the VServer group to be created in the **VServer Group Name** field.
    2.  Click **Add** and on the Available Servers page, select the servers to add.
    3.  Click **Next: Set weight and Port**.
    4.  Enter the port and weight of each ECS instance, and click **OK**. Set the port and weight according to the following information:

        -   **Port**: The backend port opened on the ECS instance to receive requests.

            The backend ports in an SLB instance can be the same.

        -   **Weight**: An ECS instance with a higher weight receives more requests.

            **Note:** If the weight is set to 0, no request is sent to the ECS instance.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/15659460247368_en-US.png)

        You can modify the ports and weights of added servers in batches.

        -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156594602411116_en-US.png): Duplicate to below. If you modify the port or weight of the current server, the ports or weights of all servers blow are also changed.
        -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156594602511119_en-US.png): Duplicate to above. If you modify the port or weight of the current server, the ports or weights of all servers above are also changed.
        -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156594602511120_en-US.png): Duplicate to all. If you modify the port or weight of the current server, the ports or weights of all servers in the VServer group are also changed.
        -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156594602511121_en-US.png): Clear all. If you clear the port or weight of the current server, the ports or weights of all servers in the VServer group are also cleared.

**More information**  


[AddVServerGroupBackendServers](../reseller.en-US/Developer Guide/VServer groups/AddVServerGroupBackendServers.md#)

