# Backend servers support adding ENI {#task_dvk_hbv_4fb .task}

An Elastic Network Interface \(ENI\) is a virtual network interface that can be attached to an ECS instance in a VPC. By using ENIs, you can build high-availability clusters, implement failover at a lower cost, and achieve refined network management. The backend servers of a guaranteed-performance SLB instance support attaching ENI.

A guaranteed-performance SLB instance supports adding VServer groups containing ECS instances bound with multiple ENIs.

For more information, see [Attach an ENI to an instance](../../../../intl.en-US//Attach an ENI to an instance.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155860429814314_en-US.png)

**Note:** Only guaranteed-performance SLB instances support adding ENIs.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou). 
2.  In the left-side navigation pane, click **Server Load Balancer**. On the Server Load Balancer page, click the ID of the target SLB instance. 
3.  Select the backend server group type and click **Add**. Both the default server group, VServer groups, and active/standby server groups support adding ENI. 
4.  On the Available Servers page, select backend servers. You can add ENI to the backend servers. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155860429814315_en-US.png)

5.  Click **Add to Selected Server List**. 
6.  Click **OK**. 

    Go back to the Server Load Balancer page. The backend server group attached with ENI is shown as follows:

    Where:

    -   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155860429814372_en-US.png): Represents an ECS instance.
    -   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155860429814373_en-US.png): Represents an ENI.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155860429914320_en-US.png)


