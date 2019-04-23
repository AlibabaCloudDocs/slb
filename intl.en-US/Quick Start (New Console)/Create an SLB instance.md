# Create an SLB instance {#task_bh5_dll_vdb .task}

This topic describes how to create an Internet Server Load Balancer \(SLB\) instance. After an Internet SLB instance is created, a public IP address is allocated to the instance and you can resolve a domain name to this address.

You can add multiple listeners and backend servers to an SLB instance.

1.  Log on to the [SLB](https://partners-intl.console.aliyun.com/#/slb) console. 
2.  On the Server Load Balancer page, click **Create SLB Instance**. 
3.  Configure the instance. For more information, see [Create an SLB instance](../../../../reseller.en-US/User Guide/Server Load Balancer instance/Create an SLB instance.md#). In this example, configure the SLB instance as follows:
    -   **Region**: SLB does not support cross-region deployment. The region of the SLB instance must be the same as that of ECS instances. In this example, select **China \(Hangzhou\)**.
    -   **Zone Type**: Multiple zones are deployed in most regions for disaster tolerance. SLB can switch to the backup zone to provide the load balancing service when the primary zone is unavailable, and will automatically switch back to the primary zone when the primary zone is recovered.

        In this example, select **China East 1 Zone B** as the primary zone, and **China East 1 Zone D** as the backup zone.

    -   **Instance name**: \(Optional\) Enter the instance name. In this example, enter **SLB1**.
    -   **Instance Type**: Select **Internet**.
    -   **Instance Spec**: Select **Small Ⅰ \(slb.s1.small\)**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15700/15560012037476_en-US.png)

4.  Click **Buy Now** and complete the payment. 
5.  Go back to the SLB console. 
6.  To edit the instance name, select the **China \(Hangzhou\)** region on the Server Load Balancer page. Rest the pointer near the name of the created instance and then click the pencil icon. Enter a name and click **OK**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15700/15560012037482_en-US.png)

7.  Optional. You can resolve a domain name to the public IP address of the SLB instance. For more information, see [Resolve a domain name](reseller.en-US/Quick Start (New Console)/Resolve a domain name.md#). 

