# Add a TCP listener

This topic describes how to add a Transmission Control Protocol \(TCP\) listener to a Server Load Balancer \(SLB\) instance. TCP provides reliable and accurate data delivery at relatively low connection speeds. Therefore, TCP is applicable in scenarios such as file transmission, email sending or receiving, and remote logons. You can add a TCP listener to forward TCP requests.

An SLB instance is created. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).

## Step 1: Configure the listener

Perform the following steps to configure the listener.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **Instances** \> **Instances**.

3.  Select the region where the SLB instance is deployed.

4.  Use one of the following methods to open the listener configuration wizard:

    -   On the Instances page, find the SLB instance and click **Configure Listener** in the Actions column.
    -   On the Instances page, click the ID of the SLB instance. On the Listener tab, click **Add Listener**.
5.  Set the following parameters.

    |Parameter|Description|
    |:--------|:----------|
    |**Select Listener Protocol**|Select the protocol of the listener. In this example, **TCP** is selected. |
    |**Listening Port**|Set the listening port used to receive requests and forward them to backend servers. Valid values: 1 to 65535.

**Note:** You can apply for **the permissions to set the same port for TCP and UDP listeners in the same SLB instance** on the [Quota Management](https://slb.console.aliyun.com/slb/quota) page. This feature is in public preview and is supported in the following regions. In other cases, the listening ports must be unique.

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
    -   China \(Shanghai\)
    -   China \(Beijing\)
    -   China \(Hangzhou\) |
    |**Advanced**|
    |**Scheduling Algorithm**|SLB supports the following scheduling algorithms: RR, WRR, WLC, and CH.     -   **Weighted Round-Robin \(WRR\)**: Backend servers with a higher weight receive more requests than those with a lower weight.
    -   **Round-Robin \(RR\)**: Requests are sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: Requests are distributed based on the combination of the weights and active connections of backend servers. If two backend servers have the same weight, the backend server with fewer connections is expected to receive more requests.
    -   **Consistent Hash \(CH\)**:

        -   **Source IP**: the source IP address hash. Requests from the same source IP address are scheduled to the same backend server.
        -   **Tuple**: a quadruple hash that consists of the source IP address, destination IP address, source port number, and destination port number. Requests with the same quadruple are scheduled to the same backend server.
**Note:** The CH algorithm can be used only by guaranteed-performance instances. |
    |**Enable Session Persistence**|Specify whether to enable session persistence. After session persistence is enabled, the listener forwards all requests from the same client to a specific backend server for the duration of a session.

For TCP listeners, session persistence is implemented based on IP addresses. Requests from the same IP address are forwarded to the same backend server. |
    |**Enable Access Control**|Specify whether to enable access control.|
    |**Access Control Method**|Select an access control method after you enable access control.

    -   **Whitelist**: Only the requests from the IP addresses or CIDR blocks in the specified access control list \(ACL\) are forwarded. You can use the whitelist feature when you want to allow access from specified IP addresses.

Using the whitelist feature may pose risks to your services. After the whitelist is enabled, only the IP addresses in the ACL can access the SLB listener. If the whitelist is enabled without any IP addresses specified, the SLB listener does not forward any requests.

    -   **Blacklist**: Requests from the IP addresses or CIDR blocks in the specified ACL are not forwarded. You can use the blacklist feature when you want to deny access from specified IP addresses.

If the blacklist is enabled without any IP addresses specified, the SLB listener forwards all requests. |
    |**Access Control List**|Select an ACL that is used as the whitelist or blacklist of the listener. **Note:** IPv6 instances can be associated only with IPv6 ACLs, while IPv4 instances can be associated only with IPv4 ACLs. For more information, see [Create an access control list](/intl.en-US/Classic Load Balancer/User Guide/Access control/Access control lists/Create an access control list.md). |
    |**Enable Connection Draining**|When connection draining is enabled, connections to the backend server can function as expected for a specific time period after they are removed or fail the health check.|
    |**Connection Draining Timeout**|After you enable connection draining, you can specify the maximum timeout period to keep connections alive before a backend server is removed from an SLB server group. After the backend server is removed or remains unhealthy for the specified time period, SLB terminates the connections to the backend server. Value values: 10 to 900.

Unit: seconds. |
    |**Enable Peak Bandwidth Limit**|Specify whether to set a bandwidth limit for the listener.

For a pay-by-bandwidth SLB instance, you can set different maximum bandwidth values for different listeners to limit listener traffic. The sum of maximum bandwidth values of all listeners that belong to the same SLB instance cannot exceed the bandwidth of this SLB instance.

By default, the bandwidth limit is disabled and all listeners share the bandwidth of the SLB instance.

**Note:** A pay-by-data-transfer SLB instance does not impose limits on its maximum bandwidth. |
    |**Idle Timeout**|Specify the idle timeout for TCP connections. Unit: seconds. Valid values: 10 to 900.|
    |**Listener Name**|Enter a name for the listener.|
    |**Obtain Client Source IP Address**|For Layer 4 listeners, backend servers can directly obtain the actual IP addresses of clients.|
    |**Automatically Enable Listener After Creation**|Specify whether to start the listener immediately after it is configured. By default, the listener is started after it is configured.|

6.  Click **Next**.


## Step 2: Add backend servers

After you configure the listener, you must add backend servers to process client requests. You can add backend servers to the default server group, or create vServer groups or primary/secondary server groups and then add servers to the server groups. For more information, see [Backend server overview](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Backend server overview.md).

The default server group is used in the example.

1.  Select **Default Server Group** and click **Add More**.

    ![Add backend servers to the default server group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p10030.png)

2.  In the **My Servers** panel, select ECS instances as the backend servers that you want to add and click **Next**.

    ![Configure weights](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p7499.png)

3.  On the **Configure Ports and Weights** tab, configure weights for the backend servers. A backend server that has a higher weight receives more requests.

    **Note:** If the weight of a backend server is set to 0, the backend server no longer accepts requests.

4.  Click **Add**. On the Default Server Group tab, configure ports for the backend servers. Valid values: 1 to 65535.

    You can specify the same port for multiple backend servers that belong to the same SLB instance.

5.  Click **Next**.


## Step 3: Configure health checks

SLB checks the availability of Elastic Compute Service \(ECS\) instances that serve as backend servers by performing health checks. The health check feature improves the overall availability of your frontend business and mitigates the impacts of exceptions that occur on backend ECS instances. Click **Modify** to modify the configurations of health checks. For more information, see [Health check overview](/intl.en-US/Classic Load Balancer/User Guide/Health check/Health check overview.md).

## Step 4: Confirm the configurations

Perform the following steps to confirm the configurations.

1.  In the Confirm step, check the configurations. You can click **Modify** to modify the configurations.

2.  After you confirm the configurations, click **Submit**.

3.  In the Configuration Successful message, click **OK**.

    You can check the created listener on the Listener tab.


**References**  


[Add ECS instances to the default server group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Default server groups/Add ECS instances to the default server group.md)

[Add ECS instances to a VServer group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/VServer groups/Add ECS instances to a VServer group.md)

[Overview](/intl.en-US/Classic Load Balancer/User Guide/Access control/Overview.md)

[CreateLoadBalancerTCPListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/TCP listeners/CreateLoadBalancerTCPListener.md)

