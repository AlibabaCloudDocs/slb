# Add a TCP listener {#concept_xvg_qmn_vdb .concept}

This topic describes how to add a TCP listener. TCP listeners apply to scenarios where high transmission reliability and data accuracy are required, but some flexibility regarding network latency is permitted. You can add a TCP listener to forward requests from the TCP protocol.

## Prerequisites {#section_brc_4p5_vdb .section}

At least one Server Load Balancer \(SLB\) instance is created. For more information, see [Create an SLB instance](intl.en-US/User Guide/Server Load Balancer instance/Create an SLB instance.md#).

## Step 1 Open the listener configuration wizard {#section_p32_zln_42b .section}

To open the listener configuration wizard, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**.
3.  Select the region of the target instance.
4.  Select one of the following methods to open the listener configuration wizard:
    -   On the Server Load Balancer page, find the target instance and then click **Configure Listener**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155805995410004_en-US.png)

    -   On the Server Load Balancer page, click the ID of the target SLB instance. On the Listeners tab page, click **Add Listener**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16161/15580599547399_en-US.png)


## Step 2 Configure a TCP listener {#section_mhj_lmn_42b .section}

To configure a TCP listener, complete these steps:

1.  On the Protocol and Listener page, configure the TCP listener according to the following information.

    |Configuration|Description|
    |:------------|:----------|
    |**Select Listener Protocol**|Select the protocol type of the listener. In this topic, select **TCP**.

 |
    |**Listening Port**|The listening port used to receive requests and forward the requests to backend servers. The port number is in the range of 1 to 65535.

 **Note:** The listening ports must be unique in an SLB instance.

 |
    |**Advanced configurations**|
    |**Scheduling Algorithm**|SLB supports four scheduling algorithms: weighted round robin, round-robin, weighted least connections, and consistent hash.     -   **Weighted Round-Robin \(WRR\)**: Backend servers with higher weights receive more requests than those with smaller weights.
    -   **Round-Robin \(RR\)**: Requests are evenly and sequentially distributed to the backend servers.
    -   **Weighted Least Connections \(WLC\)**: A server with a higher weight will receive a larger percentage of live connections at any one time. When the weight value is the same, a backend server with a smaller number of connections is more frequently \(and probably\) accessed.
    -   **Consistent Hash \(CH \)**:

        -   **Source IP**: The consistent hash based on the source IP address. The same source IP addresses are scheduled to the same backend server.
        -   **Tuple**: The consistent hash based on the quaternion \(source IP address + destination IP address + source port + destination port\). The same streams are scheduled to the same backend server.
**Note:** 

The consistent hash \(CH\) algorithm is only supported in the following regions currently:

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
    |**Enable Session Persistence**|Select whether to enable session persistence. If session persistence is enabled, all session requests from the same client are sent to the same backend server.

 For TCP listeners, session persistence is based on IP addresses. Requests from the same IP address are forwarded to the same backend server.

 |
    |**Enable Access Control**|Select whether to enable the access control function.|
    |**Access Control Method**| Select an access control method after enabling the access control function:

     -   **Whitelist**: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling a whitelist poses some business risks. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP entry in the corresponding access control list, no requests are forwarded.

    -   **Blacklist**: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.

 |
    |**Access Control List**|Select an access control list as the whitelist or the blacklist. **Note:** An IPv6 instance can only bind IPv6 access control lists and an IPv4 instance can only bind IPv4 access control lists. For more information, see [Configure an access control list](intl.en-US/Archives/User Guide (Old Console)/Access control/Configure an access control list.md#).

 |
    |**Enable Peak Bandwidth Limit**| Select whether to configure the listening bandwidth.

 If the SLB instance is billed by bandwidth, you can set different peak bandwidths for different listeners to limit the traffic passing through the listeners. The sum of the peak bandwidths of all listeners under an instance cannot exceed the bandwidth of that instance.

 By default, all listeners share the bandwidth of the SLB instance.

 **Note:** Instances billed by traffic have no peak bandwidth limit by default.

 |
    |**Idle Timeout**|Specify the idle connection timeout in seconds. Value range: 10 to 900.|
    |**Listener Name**|Configure the name of the listener.|
    |**Get Client Source IP Address**|The backend server of a Layer-4 listener can directly obtain the real IP address of the client.|
    |**Automatically Enable Listener after Creation**|Choose whether to enable the listener after the listener is configured. The listener is enabled by default.|

2.  Click **Next**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15580599547421_en-US.png)


## Step 3 Add backend servers {#section_vqk_zmn_42b .section}

You need to add backend servers to process requests. You can use the default server group configured for the instance, or configure a VServer group or an active/standby server group for the listener. For more information, see [Backend server overview](intl.en-US/User Guide/Backend servers/Backend server overview.md#).

In this topic, select **Default Server Group**.

1.  Select **Default Server Group** and then click **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155805995510030_en-US.png)

2.  Select the ECS instances to add and then click **Add to Selected Server List**. Click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15580599557499_en-US.png)

3.  Configure the ports and weights of the added backend servers.
    -   Port

        The port opened on a backend server \(ECS instance\) to receive requests. The port number is in the range of 1 to 65535. Ports of backend servers can be the same in an SLB instance.

    -   Weight

        The weight of a backend server \(ECS instance\). An ECS instance with a higher weight will receive more requests.

        **Note:** If the weight is set to 0, no requests will be sent to the ECS instance.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15580599557504_en-US.png)

4.  Click **Next**.

## Step 4 Configure health checks {#section_oj3_mnn_42b .section}

SLB checks the service availability of backend servers \(ECS instances\) by performing health checks. The health check function improves the overall availability of your services and avoids the impact of backend server failures. Click **Modify** to change health check configurations. For more information, see [Configure health checks](intl.en-US/User Guide/Health check/Configure health checks.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155805995510032_en-US.png)

## Step 5 Submit the configurations {#section_hwm_qnn_42b .section}

To confirm the listener configurations, complete these steps:

1.  On the Submit page, check listener configurations. You can click **Modify** to change the configurations.
2.  Click **Submit**.
3.  On the Submit page, click **OK** after the configurations are successful.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155805995510033_en-US.png)


After the configurations are successful, you can view the created listener on the **Listeners** page.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/155805995510034_en-US.png)

## What to do next {#section_or1_14n_42b .section}

-   [Configure health checks](intl.en-US/User Guide/Health check/Configure health checks.md#).
-   [Manage a default server group](intl.en-US/User Guide/Backend servers/Manage a default server group.md#).
-   [Manage a VServer group](intl.en-US/User Guide/Backend servers/Manage a VServer group.md#).
-   [Manage an active/standby server group](intl.en-US/User Guide/Backend servers/Manage an active__standby server group.md#).
-   [Configure access control](intl.en-US/User Guide/Access control/Configure access control.md#).

