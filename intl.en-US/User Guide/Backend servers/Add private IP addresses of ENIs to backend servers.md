# Add private IP addresses of ENIs to backend servers {#task_dvk_hbv_4fb .task}

An Elastic Network Interface \(ENI\) is a virtual network interface that can be attached to an ECS instance in a VPC. When you add backend servers to a guaranteed-performance Server Load Balancer \(SLB\) instance, you can choose to add the primary and secondary private IP addresses of ENIs if the ENIs are associated with ECS instances.

The ECS instances are associated with ENIs.

For more information about how to associate an ENI with an ECS instance, see [Attach an ENI](../../../../intl.en-US/Network/Elastic Network Interfaces/Attach an ENI.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156076423814314_en-US.png)

**Note:** Only guaranteed-performance SLB instances support adding the primary and secondary private IP addresses of ENIs to backend servers.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).
2.  In the left-side navigation pane, click **Server Load Balancer**. On the Server Load Balancer page, click the ID of the target SLB instance.
3.  Select the backend server group type by clicking the corresponding tab. Default server groups, VServer groups, and active/standby server groups all support adding the primary and secondary private IP addresses of ENIs. In this topic, click the **Default Server Group** tab and then click **Add**.
4.  On the Available Servers page, turn on **Advanced Mode** and click ![](images/48762_en-US.png) to select ENIs and its secondary private IP addresses. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156076423814315_en-US.png)

5.  Click **Next: Set Weight and Port** to set the weights and port numbers of the added backend servers.
6.  Click **OK** and you can see the added ENIs and its private IP addresses on the **Default Server Group** tab. 

    If the default server group is added for a listener, you can see the backend servers added with ENIs and secondary private IP addresses on the Server Load Balancer page as follows:

    where,

    -   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156076423814372_en-US.png): Represents an ECS instance.
    -   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156076423814373_en-US.png): Represents an ENI and its secondary private IP address.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156076423914320_en-US.png)


