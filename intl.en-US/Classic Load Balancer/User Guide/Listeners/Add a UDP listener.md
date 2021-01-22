# Add a UDP listener

This topic describes how to add a UDP listener to an SLB instance. UDP is applicable to services that prioritize real-time content delivery over reliability, such as video chats and real-time quotes. You can add a UDP listener to forward UDP requests.

An SLB instance is created. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).

Before you configure a UDP listener, take note of the following items:

-   Ports 250, 4789, and 4790 of a UDP listener are reserved and therefore are unavailable for your configuration.
-   Fragmented packets are not supported.
-   The UDP listeners of an SLB instance in the classic network do not allow you to view source IP addresses.
-   The following operations take five minutes to take effect if they are performed for a UDP listener:
    -   Remove backend servers
    -   Set the weight of a backend server to 0 after it is detected unhealthy
-   IPv6 addresses have longer IP headers than IPv4 addresses. When you create a UDP listener for an IPv6 SLB instance, make sure that the maximum transmission unit \(MTU\) size of the network interface controller \(NIC\) on each backend server \(ECS instance in most cases\) that communicates with the SLB instance is not greater than 1,200 bytes. Otherwise, oversized packets may be discarded. The configuration files of some applications need to be modified based on the MTU size.

    If you use a TCP, HTTP, or HTTPS listener, you do not need to perform additional configuration steps because TCP supports automatic maximum segment size \(MSS\) adjustment.


## Step 1: Start the listener configuration wizard

To start the listener configuration wizard, perform the following operations:

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancers**.

3.  Select the region of the target SLB instance.

4.  Use one of the following methods to start the listener configuration wizard:

    -   On the Server Load Balancers page, find the target SLB instance and then click **Configure Listener** in the Actions column.

        ![Configure Listener-private](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1213359951/p149143.png)

    -   On the Server Load Balancers page, click the ID of the target SLB instance. On the Listener tab, click **Add Listener**.

        ![Add Listener](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1213359951/p7399.png)


## Step 2: Configure the UDP listener

To configure the UDP listener, perform the following operations:

1.  In the Protocol and Listener step, configure the following parameters.

    |Parameter|Description|
    |:--------|:----------|
    |**Select Listener Protocol**|Select the protocol of the listener. In this example, select **UDP**. |
    |**Listening Port**|Set the listening port that is used to receive requests and forward them to backend servers. Valid values: 1 to 65535.

**Note:** You can set the same listening port for TCP and UDP listeners that are added to the same SLB instance. However, you must first apply for **the privilege to use the beta function of configuring the same ports in TCP/UDP listeners** on the [Quota Management](https://slb.console.aliyun.com/slb/quota) page in the SLB console. This feature is now in public preview and is supported in the following regions. In other cases, the listening port numbers must be unique.

    -   UAE \(Dubai\)
    -   Australia \(Sydney\)
    -   UAE \(Dubai\)
    -   UK \(London\)
    -   Germany \(Frankfurt\)
    -   US \(Silicon Valley\)
    -   US \(Virginia\)
    -   Indonesia \(Jakarta\)
    -   Japan \(Tokyo\)
    -   India \(Mumbai\)
    -   Singapore \(Singapore\)
    -   Malaysia \(Kuala Lumpur\)
    -   China \(Hong Kong\)
    -   China \(Shenzhen\)
    -   China \(Hohhot\)
    -   China \(Qingdao\)
    -   China \(Chengdu\)
    -   China \(Zhangjiakou\)
    -   China \(Shanghai\) |
    |**Advanced**|
    |**Scheduling Algorithm**|SLB supports four scheduling algorithms: RR, WRR, WLC, and CH.    -   **Weighted Round-Robin \(WRR\)**: Backend servers with a higher weight receive more requests than those with a lower weight.
    -   **Round-Robin \(RR\)**: Requests are sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: Requests are distributed based on the combination of the weights and active connections of backend servers. Requests are distributed to the backend server with the least number of active connections. If two backend servers have the same weight, requests are forwarded to the backend server with fewer connections.
    -   **Consistent Hash \(CH\)**:
        -   **Source IP**: the source IP hash. Requests from the same source IP address are scheduled to the same backend server.
        -   **Tuple**: a quadruple hash that consists of the source IP address, destination IP address, source port number, and destination port number. Requests with the same quadruple are scheduled to the same backend server.
        -   **QUIC ID**: the hash that is based on Quick UDP Internet Connections \(QUIC\) IDs. Requests that contain the same QUIC ID are scheduled to the same backend server.

**Note:** The QUIC protocol is implemented based on [draft-ietf-quic-transport-10](https://datatracker.ietf.org/doc/draft-ietf-quic-transport/10/) and is rapidly evolving. Therefore, compatibility is not guaranteed for all QUIC versions. We recommend that you perform tests before you apply the protocol to the production environment. |
    |**Enable Access Control**|Specify whether to configure the listener to restrict access.|
    |**Access Control Method**|Select an access control method after you enable access control.

    -   **Whitelist**: Only the requests from the IP addresses or CIDR blocks in the specified ACL are forwarded. You can use the whitelist feature when you want to allow access from specified IP addresses.

Risks may arise if you specify an ACL as a whitelist. After a whitelist is enabled, only IP addresses contained in the whitelist can access the SLB listener. If a whitelist is enabled without any IP addresses specified, the SLB listener forwards all requests.

    -   **Blacklist**: Requests from the IP addresses or CIDR blocks in the specified ACL are not forwarded. You can use the blacklist feature when you want to deny access from specified IP addresses.

If a blacklist is enabled without any IP addresses specified, the SLB listener forwards all requests. |
    |**Access Control List**|Select an ACL that is used as the whitelist or blacklist of the listener. **Note:** IPv6 instances can be associated only with IPv6 ACLs, and IPv4 instances can be associated only with IPv4 ACLs. For more information, see [Creates an access control list](/intl.en-US/Classic Load Balancer/User Guide/Access control/Access control lists/Create an access control list.md). |
    |**Enable Peak Bandwidth Limit**|You can switch on this option and then set a bandwidth limit for the listener.

If an SLB instance incurs fees based on the bandwidth, you can set different peak bandwidth values for different listeners to limit the amount of traffic that flows in each listener. The sum of the peak bandwidth values of all listeners added to an SLB instance cannot exceed the bandwidth of this SLB instance.

By default, this feature is disabled and all listeners share the bandwidth of the SLB instance.

**Note:** If an SLB instance incurs fees based on the amount of transmitted data, no peak bandwidth limit is applied by default. |
    |**Obtain Client Source IP Address**|Backend servers of a UDP listener can directly obtain the actual IP addresses of clients. **Note:** UDP listeners of an SLB instance in the classic network do not allow you to view source IP addresses. |
    |**Automatically Enable Listener After Creation**|Specify whether to start the listener after the listener is configured. By default, the listener is started after configuration.|

2.  Click **Next**.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4527498951/p7426.png)


## Step 3: Add backend servers

After you configure the listener, you must add backend servers to process client requests. You can add backend servers to the default server group, or create VServer groups or primary/secondary server groups and then add servers to them. For more information, see [Backend server overview](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Backend server overview.md).

Backend servers are added to the default server group in this example.

1.  Select **Default Server Group** and click **Add More**.

    ![Add backend servers to the default server group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p10030.png)

2.  Select ECS instances \(backend servers\) that you want to add, and then click **Next**.

    ![Configure weights](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p7499.png)

3.  Configure weights for the added backend servers.

    A backend server with a higher weight receives more requests.

    **Note:** If the weight of a backend server is set to 0, the backend server does not receive new requests.

4.  Click **Add**. On the **Default Server Group** tab, configure ports for the backend servers.

    Set a port for each backend server to receive requests. Valid values: 1 to 65535. You can specify the same port for multiple backend servers of an SLB instance.

5.  Click **Next**.


## Step 4: Configure the health check

SLB checks the availability of backend servers by performing the health check. The health check feature improves the availability of frontend services by minimizing downtime caused by health issues of backend servers. Click **Modify** to configure advanced health check settings. For more information, see [Health check overview](/intl.en-US/Classic Load Balancer/User Guide/Health check/Health check overview.md).

Click **Next**.

## Step 5: Confirm the settings

Complete the following steps to confirm and apply the listener settings:

1.  In the Submit step, check the configuration. You can click **Modify** to modify configuration settings.

2.  Click **Submit**.

3.  In the Configure Successful dialog box, click **OK**.

    You can check the created listener on the Listener tab.


**References**  


[Configure health check](/intl.en-US/Classic Load Balancer/User Guide/Health check/Configure health check.md)

[Add ECS instances to the default server group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Default server groups/Add ECS instances to the default server group.md)

[Add ECS instances to a VServer group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/VServer groups/Add ECS instances to a VServer group.md)

[Add ECS instances to a primary/secondary server group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Active/standby server groups/Add ECS instances to a primary/secondary server group.md)

[t15686.md\#](/intl.en-US/Classic Load Balancer/User Guide/Access control/Configure access control.md)

[CreateLoadBalancerUDPListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/UDP listeners/CreateLoadBalancerUDPListener.md)

