# Associate an EIP with an SLB instance

You can associate an Elastic IP Address \(EIP\) with a Server Load Balancer \(SLB\) instance of the VPC network. After you associate an EIP with an SLB instance, the SLB instance can forward requests from the Internet.

An EIP is a public IP address that can be purchased and owned independently. You can associate an EIP with an ECS instance of a VPC network, a private network SLB instance of a VPC network, or a NAT gateway. For more information, see [What is an EIP?](/intl.en-US/.md).

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).

2.  In the left-side navigation pane, choose **Instances** \> **Instances**.

3.  Select a region and find the SLB instance with which you want to associate an EIP.

    **Note:** The SLB instance to be associated with an EIP must meet the following requirements:

    -   The network type of the SLB instance must be VPC.
    -   The SLB instance and the EIP must belong to the same region.
    -   Only one EIP can be associated with an SLB instance.
4.  Choose ![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2877921161/p230094.png), and then click **Bind EIP** in the corresponding **Actions** column.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5623498951/p7389.png)

5.  In the panel that appears, select an EIP from **Available EIPs**.

    **Note:** If you associate a private network SLB instance with an EIP, the VPC network traffic that passes through the SLB instance may be disrupted for a short period of time. We recommend that you associate the SLB instance during off-peak hours or switch the workloads to other instances first.

6.  Click **OK**.


