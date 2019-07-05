# Add a TCP listener {#concept_xvg_qmn_vdb .concept}

This topic describes how to add a TCP listener to a Server Load Balancer \(SLB\) instance. The TCP protocol is applicable to scenarios with high requirements on reliability and data accuracy but with tolerance for low speed, such as file transmission, sending or receiving emails, and remote logons. You can add a TCP listener to forward requests from the TCP protocol.

## Prerequisites {#section_brc_4p5_vdb .section}

[Create an SLB instance](intl.en-US/User Guide/Server Load Balancer instance/Create an SLB instance.md#).

## Step 1 Open the listener configuration wizard {#section_p32_zln_42b .section}

To open the listener configuration wizard, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**.
3.  Select the region of the target SLB instance.
4.  Select one of the following methods to open the listener configuration wizard:
    -   On the Server Load Balancer page, find the target SLB instance and then click **Configure Listener** in the **Actions** column.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/156231476710004_en-US.png)

    -   On the Server Load Balancer page, click the ID of the target SLB instance. On the Listeners page, click **Add Listener**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16161/15623147687399_en-US.png)


## Step 2 Configure the TCP listener {#section_mhj_lmn_42b .section}

To configure the TCP listener, follow these steps:

1.  On the Protocol and Listener page, configure the TCP listener according to the following information.

    |Configuration|Description|
    |:------------|:----------|
    |**Select Listener Protocol**|Select the protocol type of the listener. In this topic, select **TCP**.

 |
    |**Listening Port**|The listening port used to receive requests and forward the requests to backend servers. The port number is in the range of 1 to 65535.

 **Note:** UDP and TCP listener port numbers can be the same in the following regions. However, you must first apply for the **privilege to use the beta function of configuring the same ports in TCP/UDP listeners** on the [Quota Management](https://slb.console.aliyun.com/slb/quota) page of the SLB console. In other cases, the listener port numbers must be unique.

    -   UAE \(Dubai\)
    -   Australia \(Sydney\)
    -   UAE \(Dubai\)
    -   UK \(London\)
    -   Germany \(Frankfurt\)
    -   US \(Silicon Valley\)
    -   USA \(Virginia\)
    -   Indonesia \(Jakarta\)
    -   Japan \(Tokyo\)
    -   India \(Mumbai\)
    -   Singapore
    -   Malaysia \(Kuala Lumpur\)
    -   Hong Kong
    -   China \(Shenzhen\)
    -   China \(Hohhot\)
    -   China \(Qingdao\)
    -   China \(Chengdu\)
    -   China \(Zhangjiakou\)
    -   China \(Shanghai\)
 |
    |**Advanced configurations**|
    |**Scheduling Algorithm**|SLB supports four scheduling algorithms: round robin, weighted round robin \(WRR\), weighted least connections \(WLC\), and consistent hash.     -   **Weighted Round-Robin \(WRR\)**: Backend servers with higher weights receive more requests.
    -   **Round-Robin \(RR\)**: Requests are evenly and sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: A server with a higher weight receives more requests. When the weight values of two backend servers are the same, the backend server with a smaller number of connections is more likely to be polled.
    -   **Consistent Hash \(CH\)**:

        -   **Source IP**: the consistent hash based on source IP addresses. Requests from the same source IP address are scheduled to the same backend server.
        -   **Tuple**: the consistent hash based on four factors: source IP address + destination IP address + source port + destination port. The same streams are scheduled to the same backend server.
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
    |**Enable Session Persistence**|Select whether to enable session persistence. If you enable session persistence, all session requests from the same client are sent to the same backend server.

 For TCP listeners, session persistence is based on IP addresses. Requests from the same IP address are forwarded to the same backend server.

 |
    |**Enable Access Control**|Select whether to enable the access control function.|
    |**Access Control Method**| Select an access control method after you enable the access control function:

     -   **Whitelist**: Only requests from IP addresses or CIDR blocks in the selected access control list are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling a whitelist poses some risks to your services. After a whitelist is configured, only the IP addresses in the list can access the SLB listener. If you enable the whitelist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

    -   **Blacklist**: Requests from IP addresses or CIDR blocks in the selected access control list are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

 |
    |**Access Control List**|Select an access control list as the whitelist or the blacklist. **Note:** An IPv6 instance can only be associated with IPv6 access control lists and an IPv4 instance can only be associated with IPv4 access control lists. For more information, see [Configure an access control list](intl.en-US/Archives/User Guide (Old Console)/Access control/Configure an access control list.md#).

 |
    |**Enable Peak Bandwidth Limit**| Select whether to configure the listening bandwidth.

 If the SLB instance is charged based on bandwidth, you can set different peak bandwidth values for different listeners to limit the traffic passing through the listeners. The sum of the peak bandwidth values of all listeners under an SLB instance cannot exceed the bandwidth value of that SLB instance.

 By default, all listeners share the bandwidth of the SLB instance.

 **Note:** SLB instances billed by traffic have no peak bandwidth limit by default.

 |
    |**Idle Timeout**|Specify the idle connection timeout period. Value range: 10 to 900. Unit: seconds.|
    |**Listener Name**|Enter a name for the TCP listener to be added.|
    |**Get Client Source IP Address**|Backend servers of a Layer-4 listener can directly obtain the source IP addresses of clients.|
    |**Automatically Enable Listener after Creation**|Choose whether to start the listener after the listener is configured. The listener is started by default.|

2.  Click **Next**.

## Step 3 Add backend servers {#section_vqk_zmn_42b .section}

After configuring the listener, you need to add backend servers to process requests. You can use the default server group configured for the SLB instance, or configure a VServer group or an active/standby server group for the listener. For more information, see [Backend server overview](intl.en-US/User Guide/Backend servers/Backend server overview.md#).

In this topic, use the default server group.

1.  Select **Default Server Group** and then click **Add More**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/156231476810030_en-US.png)

2.  Select the ECS instances to add, and then click **Next: Set Weight and Port**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15623147687499_en-US.png)

3.  Configure ports and weights for the added backend servers.
    -   Port

        The port opened on the backend server \(ECS instance\) to receive requests. The port number is in the range of 1 to 65535. Ports of backend servers can be the same in an SLB instance.

    -   Weight

        The weight of the backend server \(ECS instance\). An ECS instance with a higher weight receives more requests.

        **Note:** If the weight is set to 0, no requests will be sent to the ECS instance.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15623147687504_en-US.png)

4.  Click **Next**.

## Step 4 Configure health checks {#section_oj3_mnn_42b .section}

SLB checks the service availability of backend servers by performing health checks. The health check function improves the overall availability of your services and avoids the impact of backend server failures. Click **Modify** to change health check configurations. For more information, see [Configure health checks](intl.en-US/User Guide/Health check/Configure health checks.md#).

## Step 5 Submit the configurations {#section_hwm_qnn_42b .section}

To confirm the listener configurations, follow these steps:

1.  On the Submit page, check the listener configurations. You can click **Modify** to change the configurations.
2.  Click **Submit**.
3.  On the Submit page, click **OK** after the configurations are successful.

After the configurations are successful, you can view the created listener on the **Listeners** page.

## Related operations {#section_or1_14n_42b .section}

-   [Configure health checks](intl.en-US/User Guide/Health check/Configure health checks.md#)
-   [Manage a default server group](intl.en-US/User Guide/Backend servers/Manage a default server group.md#)
-   [Manage a VServer group](intl.en-US/User Guide/Backend servers/Manage a VServer group.md#)
-   [Manage an active/standby server group](intl.en-US/User Guide/Backend servers/Manage an active__standby server group.md#)
-   [Configure access control](intl.en-US/User Guide/Access control/Configure access control.md#)

