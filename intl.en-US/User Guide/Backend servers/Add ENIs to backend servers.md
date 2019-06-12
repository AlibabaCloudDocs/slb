# Add ENIs to backend servers {#task_dvk_hbv_4fb .task}

An Elastic Network Interface \(ENI\) is a virtual network interface that can be associated with an ECS instance in a VPC. By using ENIs, you can build high-availability clusters, implement failover at a lower cost, and achieve refined network management. You can add ENIs to the backend servers of a guaranteed-performance Server Load Balancer \(SLB\) instance.

A guaranteed-performance SLB instance supports adding VServer groups containing ECS instances that are associated with multiple ENIs.

For more information, see [Attach an ENI](../../../../intl.en-US/Network/Elastic Network Interfaces/Attach an ENI.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156032313714314_en-US.png)

**Note:** Only guaranteed-performance SLB instances support adding ENIs.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).
2.  In the left-side navigation pane, choose **Server Load Balancer**. On the Server Load Balancer page, click the ID of the target SLB instance.
3.  Select the backend server group type and click **Add**. Default server groups, VServer groups, and active/standby server groups all support adding ENIs.
4.  On the Available Servers page, select backend servers. You can add ENIs to the backend server group. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156032313814315_en-US.png)

5.  Click **Add to Selected Server List**.
6.  Click **OK**. 

    Go back to the Server Load Balancer page. The backend server group associated with ENIs is shown as follows:

    where,

    -   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156032313814372_en-US.png): Represents an ECS instance.
    -   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156032313814373_en-US.png): Represents an ENI.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/156032313814320_en-US.png)


