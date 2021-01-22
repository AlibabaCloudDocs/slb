# Create an SLB instance

This topic describes how to create an Internet SLB instance. After an Internet SLB instance is created, a public IP address is allocated to the instance and then you can resolve domain names to this address.

You can add multiple listeners and backend servers to an SLB instance.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **Instances** \> **Instances**.

3.  On the Instances page, click **Create Instance**.

4.  On the Server Load Balancer page, configure the parameters of an SLB instance.

    For this example, configure the following parameters:

    -   **Billing Method**: Select a billing method. For this example, select **Pay-As-You-Go**.
    -   **Region**: SLB does not support cross-region deployment. Therefore, you must select the same region as the backend ECS instances. For this example, select **China \(Qingdao\)**.
    -   **Zone Type**: Multiple zones have been deployed in most regions for zone-disaster recovery. If the primary zone fails or becomes unavailable, the SLB instance will fail over to the secondary zone in about 30 seconds. When the primary zone recovers, the SLB instance will automatically switch back to the primary zone.

        For this example, select **China North 1 Zone C** as the primary zone, and **China North 1 Zone B** as the secondary zone.

    -   **Instance Name**: Enter a name for the instance or use the instance name that is automatically created by the system.
    -   **Instance Spec**: Select **Small Ⅰ \(slb. s1.small\)**. An SLB instance of this specification supports a maximum of 5000 concurrent connections, 3000 connections per second \(CPS\), and 1000 queries per second \(QPS\).
    -   **Instance Type**: Select **Internet**.
    -   **IP Version**: Select **IPv4**.
    -   **Backend Server Type**: Select **Local region**. It indicates that backend servers in the current region can be attached to the SLB instance.
    -   **Internet Charge Type**: Select **By traffic**.
5.  Click **Buy Now**.

6.  On the Confirm Order page, select **I have read and agreed to Server Load Balancer \(SLB\) Agreement of Service**, and then click **Activate Now**.

    You can resolve domain names to the public IP address of the SLB instance. For more information, see [Resolve a domain name](/intl.en-US/Classic Load Balancer/Quick Start (New Console)/Resolve a domain name.md).


