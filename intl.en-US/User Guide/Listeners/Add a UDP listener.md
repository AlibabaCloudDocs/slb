# Add a UDP listener {#concept_dy4_2pn_42b .concept}

The UDP protocol is applicable to scenarios with preference for real-time content over reliability, such as video chats and real-time financial quotations. You can add a UDP listener to forward requests from the UDP protocol.

## Limits {#section_rln_3pn_42b .section}

Before you add a UDP listener, note the following limits:

-   Currently, ports 250, 4789, and 4790 are reserved.
-   Currently, fragmented packets are not supported.
-   UDP listeners of an SLB instance of the classic network do not support viewing source IP addresses.
-   The following operations require five minutes to take effect if they are performed in a UDP listener:
    -   Remove backend ECS instances.
    -   Set the weight of a backend ECS instance to 0 after the ECS instance is declared as unhealthy.
-   Because IPv6 has a longer IP header than IPv4, when you use a UDP listener on an IPv6 SLB instance, you must ensure that the MTU of the NIC on the backend server \(ECS instance\) communicating with the SLB instance is not greater than 1480 \(some applications need to synchronizing its configuration files based on this MTU value\). Otherwise, packets may be discarded because they are too large.

    If you use a TCP, HTTP, or HTTPS listener, no additional configurations are required because the TCP protocol supports MSS auto-negotiation.


## Prerequisites {#section_tx3_vqn_42b .section}

At least one Server Load Balancer \(SLB\) instance is created. For more information, see [Create an SLB instance](intl.en-US/User Guide/Server Load Balancer instance/Create an SLB instance.md#).

## Step 1 Open the listener configuration wizard {#section_wx3_5qn_42b .section}

To open the listener configuration wizard, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**.
3.  Select the region of the target instance.
4.  Select one of the following methods to open the listener configuration wizard:
    -   On the Server Load Balancer page, find the target instance and then click **Configure Listener**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155900848510004_en-US.png)

    -   On the Server Load Balancer page, click the ID of the target SLB instance. On the Listeners tab page, click **Add Listener**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16161/15590084857399_en-US.png)


## Step 2 Configure the UDP listener {#section_ly4_2pn_42b .section}

To configure the UDP listener, follow these steps:

1.  On the Protocol and Listener page, configure the UDP listener according to the following information.

    |Configuration|Description|
    |:------------|:----------|
    |**Select Listener Protocol**|Select the protocol type of the listener. In this topic, select **UDP**.

 |
    |**Listening Port**|The listening port used to receive requests and forward the requests to backend servers. The port number is in the range of 1 to 65535.

 **Note:** UDP and TCP listening port numbers can be repeated only in the SLB instances that belong to the Australia \(Sydney\), UAE \(Dubai\), or UK \(London\) regions. In other cases, the listening port number must be unique.

 |
    |**Advanced configurations**|
    |**Scheduling Algorithm**|SLB supports four scheduling algorithms: round robin, weighted round robin \(WRR\), weighted least connections \(WLC\), and consistent hash.     -   **Weighted Round-Robin \(WRR\)**: Backend servers with higher weights receive more requests than those with smaller weights.
    -   **Round-Robin \(RR\)**: Requests are evenly and sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: A backend server with a higher weight will receive more requests. When the weight values of two backend servers are the same, the backend server with a smaller number of connections is more likely to be polled.
    -   **Consistent Hash \(CH\)**:

        -   **Source IP**: The consistent hash based on source IP addresses. Requests from the same source IP address are scheduled to the same backend server.
        -   **Tuple**: The consistent hash based on four factors: source IP address + destination IP address + source port + destination port. The same streams are scheduled to the same backend server.
        -   **QUIC ID**: The consistent hash based on the QUIC Connection ID. The same QUIC Connection IDs are scheduled to the same backend server.

**Note:** The QUIC protocol is rapidly evolving. The algorithm is based on [draft-ietf-quic-transport-10](https://datatracker.ietf.org/doc/draft-ietf-quic-transport/10/) and does not guarantee the compatibility of all QUIC versions. We recommend that you do enough tests before using it for the production environment.

**Note:** 

Currently, the Consistent Hash \(CH\) algorithm is only supported in the following regions:

        -   Japan \(Tokyo\)
        -   Australia \(Sydney\)
        -   Malaysia \(Kuala Lumpur\)
        -   Indonesia \(Jakarta\)
        -   Germany \(Frankfurt\)
        -   US \(Silicon Valley\)
        -   US \(Virginia\)
        -   UAE \(Dubai\)
        -   China \(Hohhot\)
 |
    |**Enable Access Control**|Select whether to enable the access control function.|
    |**Access Control Method**| Select an access control method after enabling the access control function:

     -   **Whitelist**: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling a whitelist poses some business risks. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP addresses in the corresponding access control list, no requests are forwarded.

    -   **Blacklist**: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

 |
    |**Access Control List**|Select an access control list as the whitelist or the blacklist. **Note:** An IPv6 instance can only be associated with IPv6 access control lists and an IPv4 instance can only be associated with IPv4 access control lists. For more information, see [Configure an access control list](intl.en-US/Archives/User Guide (Old Console)/Access control/Configure an access control list.md#).

 |
    |**Enable Peak Bandwidth Limit**| Select whether to configure the listener bandwidth.

 If the SLB instance is billed by bandwidth, you can set different peak bandwidth values for different listeners to limit the traffic passing through the listeners. The sum of the peak bandwidth values of all listeners under an SLB instance cannot exceed the bandwidth value of that SLB instance.

 By default, all listeners share the bandwidth of the SLB instance.

 **Note:** SLB instances billed by traffic have no bandwidth peak limit by default.

 |
    |**Get Client Source IP Address**|The backend server of a Layer-4 listener can directly obtain the real IP address of a client. **Note:** UDP listeners of an SLB instance of the classic network do not support viewing source IP addresses.

 |
    |**Automatically Enable Listener After Creation**|Choose whether to start the listener after the listener is configured. This function is enabled by default.|

2.  Click **Next**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16161/15590084867426_en-US.png)


## Step 3 Add backend servers {#section_ylm_3qn_42b .section}

You need to add backend servers to process requests. You can use the default server group configured for the instance, or configure a VServer group or an active/standby server group for the listener. For more information, see [Backend server overview](intl.en-US/User Guide/Backend servers/Backend server overview.md#).

In this topic, select **Default Server Group**.

1.  Select **Default Server Group** and then click **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155900848610030_en-US.png)

2.  Select the ECS instances to add and then click **Add to Selected Server List**. Click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15590084867499_en-US.png)

3.  Configure the ports and weights of the added backend servers.
    -   Port

        The port opened on a backend server \(ECS instance\) to receive requests. The port number is in the range of 1 to 65535. Ports of backend servers can be the same in an SLB instance.

    -   Weight

        The weight of a backend server \(ECS instance\). An ECS instance with a higher weight will receive more requests.

        **Note:** If the weight is set to 0, no requests will be sent to the ECS instance.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15590084867504_en-US.png)

4.  Click **Next**.

## Step 4 Configure health checks {#section_ay4_jqn_42b .section}

SLB checks the service availability of backend servers \(ECS instances\) by performing health checks. The health check function improves the overall availability of your services and avoids the impact of backend server failures. Click **Modify** to change health check configurations. For more information, see [Configure health checks](intl.en-US/User Guide/Health check/Configure health checks.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155900848610032_en-US.png)

## Step 5 Submit the configurations {#section_ey5_lqn_42b .section}

To confirm the listener configurations, complete these steps:

1.  On the Submit page, check listener configurations. You can click **Modify** to change the configurations.
2.  Click **Submit**.
3.  On the Submit page, click **OK** after the configurations are successful.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155900848610033_en-US.png)


After the configurations are successful, you can view the created listener on the **Listeners** page.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155900848610034_en-US.png)

## Related operations {#section_pz4_2pn_42b .section}

-   [Configure health checks](intl.en-US/User Guide/Health check/Configure health checks.md#)
-   [Manage a default server group](intl.en-US/User Guide/Backend servers/Manage a default server group.md#)
-   [Manage a VServer group](intl.en-US/User Guide/Backend servers/Manage a VServer group.md#)
-   [Manage an active/standby server group](intl.en-US/User Guide/Backend servers/Manage an active__standby server group.md#)
-   [Configure access control](intl.en-US/User Guide/Access control/Configure access control.md#)

