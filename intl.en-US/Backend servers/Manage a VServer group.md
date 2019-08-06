# Manage a VServer group {#concept_ewt_whp_42b .concept}

A virtual server group \(VServer group\) is a group of ECS instances. If you associate a VServer group with a listener, the listener distributes requests to the associated VServer group instead of other backend servers.

For Layer-7 listeners, the following algorithm is used to determine whether requests are forwarded to default backend server groups, or VServer groups, and whether forwarding rules are applied:

-   If the requests match a forwarding rule, the requests are distributed to the VServer group associated with the rule.
-   If no forwarding rule is matched and a VServer group is configured on the listener, the requests are distributed to the VServer group associated with the listener.
-   If no VServer group is configured on the listener, the requests are forwarded to ECS instances in the default server group.

## Create a VServer group {#section_jqy_c3p_42b .section}

Before you create a VServer group, make sure the following conditions are met:

-   A Server Load Balancer \(SLB\) instance is created. For more information, see [Create an SLB instance](reseller.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#).
-   ECS instances are created and applications are deployed on the ECS instances to process distributed requests.

Note the following when you create a VServer group:

-   The ECS instances added to a VServer group and the SLB instance must belong to the same region.
-   One ECS instance can be added to multiple VServer groups.
-   One VServer group can be associated with multiple listeners of an SLB instance.
-   A VServer group consists of ECS instances and application ports.

To add ECS instances, follow these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the VServer Groups tab.
5.  On the VServer Groups page, click **Create VServer Group**.
6.  On the Create VServer Group page, complete these steps:
    1.  In the **VServer Group Name** field, enter a name for the VServer group to be created.
    2.  Click **Add** and on the Available Servers page, select the servers to add.
    3.  Click **Next: Set weight and Port**.
    4.  Enter the port and weight of each ECS instance, and click **OK**.

        -   **Port**: The backend port opened on the ECS instance to receive requests.

            The backend ports in an SLB instance can be the same.

        -   **Weight**: An ECS instance with a higher weight receivers more requests.

            **Note:** If the weight is set to 0, no requests are sent to the ECS instance.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/15650963277368_en-US.png)

        You can modify the ports and weights of added servers in batches.

        -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156509632811116_en-US.png): Duplicate to below. If you modify the port or weight of the current server, the ports or weights of all servers blow are also changed.
        -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156509632811119_en-US.png): Duplicate to above. If you modify the port or weight of the current server, the ports or weights of all servers above are also changed.
        -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156509632811120_en-US.png): Duplicate to all. If you modify the port or weight of the current server, the ports or weights of all servers in the VServer group are also changed.
        -   Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/156509632811121_en-US.png): Clear all. If you clear the port or weight of the current server, the ports or weights of all servers in the VServer group are also cleared.

## Edit a VServer group {#section_iwj_tjp_42b .section}

To modify the ECS instance configuration in a VServer group, follow these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, select the region of the target instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the VServer Groups tab.
5.  Find the target VServer group, and then click **Edit** in the **Actions** column.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/15650963287473_en-US.png)

6.  Modify the ports and weights of ECS instances or click **Delete** to remove ECS instances from the VServer group, and then click **OK**.

## Delete a VServer group {#section_upw_1np_42b .section}

To delete a VServer group, follow these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, select the region of the target instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the VServer Groups tab.
5.  Find the target VServer group, and then click **Delete** in the **Actions** column.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15670/15650963287474_en-US.png)

6.  In the displayed dialog box, click **OK**.

