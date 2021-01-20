# Add a TCP listener

This topic describes how to add a TCP listener to an SLB instance. TCP provides reliable and accurate data delivery at relatively low connection speeds and therefore is applicable to services such as file transmission, email sending or receiving, and remote logon. You can add a TCP listener to forward TCP requests.

An SLB instance is created. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).

## Step 1: Configure the TCP listener

Perform the following operations to configure the TCP listener.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancers**.

3.  Select the region of the target SLB instance.

4.  Use one of the following methods to start the listener configuration wizard:

    -   On the Server Load Balancers page, find the target SLB instance and then click **Configure Listener** in the Actions column.

        ![Configure Listener-private](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1213359951/p149143.png)

    -   On the Server Load Balancers page, click the ID of the target SLB instance. On the Listener tab, click **Add Listener**.

        ![Add Listener](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1213359951/p7399.png)

5.  Specify the following information:

    |Parameter|Description|
    |:--------|:----------|
    |**Select Listener Protocol**|Select the protocol of the listener. In this example, select **TCP**. |
    |**Listening Port**|Set the listening port used to receive requests and forward them to backend servers. Valid values: 1 to 65535.

**Note:** You can set the same listening port for TCP and UDP listeners that are added to the same SLB instance. However, you must first apply for **the privilege to use the beta function of configuring the same ports in TCP/UDP listeners** on the [Quota Management](https://slb.console.aliyun.com/slb/quota) page in the SLB console. This feature is now in public preview and is supported in the following regions. In other cases, the listening ports must be unique.

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
    |**Advanced Settings**|
    |**Scheduling Algorithm**|SLB supports four scheduling algorithms: round robin \(RR\), weighted round robin \(WRR\), weighted least connections \(WLC\), and consistent hashing \(CH\).    -   **Weighted Round-Robin \(WRR\)**: Backend servers with higher weights receive more requests.
    -   **Round-Robin \(RR\)**: Requests are evenly and sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: Requests are distributed based on the combination of the weights and active connections of backend servers. Requests are distributed to the backend server with the least number of active connections. If two backend servers have the same number of active connections, the backend server with a higher weight receives more requests.
    -   **Consistent Hash \(CH\)**:
        -   **Source IP**: the source IP hash. Requests from the same source IP address are scheduled to the same backend server.
        -   **Tuple**: the 4-tuple hash consisting of the source IP address, destination IP address, source port number, and destination port number. Requests with the same 4-tuple are scheduled to the same backend server. |
    |**Enable Session Persistence**|Specify whether to enable session persistence.After session persistence is enabled, the listener forwards all requests from the same client to a specific backend server for the duration of a session.

For TCP listeners, session persistence is implemented based on IP addresses. Requests from the same IP address are forwarded to the same backend server. |
    |**Enable Access Control**|Specify whether to configure the listener to restrict access.|
    |**Access Control Method**|Select an access control method after you enable access control.

    -   **Whitelist**: Only the requests from the IP addresses or Classless Inter-domain Routing \(CIDR\) blocks in the specified access control list \(ACL\) are forwarded. You can use the whitelist feature when you want to allow access from specified IP addresses.

Using the whitelist feature may pose risks to your services. The whitelist allows only the traffic from the IP addresses in the specified ACL to access the SLB listener. If the whitelist is used while the corresponding ACL does not contain any IP addresses, the SLB listener prevents all access requests.

    -   **Blacklist**: Requests from the IP addresses or CIDR blocks in the specified ACL are not forwarded. You can use the blacklist feature when you want to deny access from specified IP addresses.

If the blacklist is used while the corresponding ACL does not contain any IP addresses, the SLB listener forwards all access requests. |
    |**Access Control List**|Select an ACL that functions as the whitelist or blacklist of the listener. **Note:** IPv6 instances can only be associated with IPv6 ACLs, and IPv4 instances can only be associated with IPv4 ACLs. For more information, see [Configure an access control list](t4159.md#). |
    |**Enable Peak Bandwidth Limit**|You can switch on this option and then set a bandwidth limit for the listener.

If an SLB instance incurs fees based on the bandwidth, you can set different peak bandwidth values for different listeners to limit the amount of traffic that flows in each listener. The sum of the peak bandwidth values of all listeners added to an SLB instance cannot exceed the bandwidth of this SLB instance.

By default, this feature is disabled and all listeners share the bandwidth of the SLB instance.

**Note:** If an SLB instance incurs fees based on the amount of transmitted data, no peak bandwidth limit is applied by default. |
    |**Idle Timeout**|Specify the idle timeout period of TCP connections. Unit: seconds. Valid values: 10 to 900.|
    |**Listener Name**|Enter a name for the listener.|
    |**Obtain Client Source IP Address**|For Layer-4 listeners, backend servers can directly obtain the actual IP addresses of clients.|
    |**Automatically Enable Listener After Creation**|Specify whether to start the listener after the listener is configured. By default, the listener is started after configuration.|

6.  Click **Next**.


## Step 3: Add backend servers

After you configure the listener, you must add backend servers to process client requests. You can add backend servers to the default server group, or create VServer groups or primary/secondary server groups and then add servers to them. For more information, see [Backend server overview](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Backend server overview.md).

This example adds backend servers to the default server group.

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

[Enable access control](/intl.en-US/Classic Load Balancer/User Guide/Access control/Enable access control.md)

[CreateLoadBalancerTCPListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/TCP listeners/CreateLoadBalancerTCPListener.md)

