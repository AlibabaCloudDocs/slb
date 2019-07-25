# Configure Layer-4 SLB listeners {#concept_vsd_vpn_vdb .concept}

## Layer-4 listener overview {#section_tzl_ms5_vdb .section}

-   TCP protocol

    A connection-oriented protocol. A reliable connection must be established with the peer side before data can be sent and received. Applicable to scenarios with high requirements on reliability and data accuracy, but with tolerance for low speed, such as file transmission, sending or receiving emails, remote logon, and web applications without special requirements.

-   UDP protocol

    A non-connection-oriented protocol. Before sending data, UDP directly performs data packet transmission instead of making three handshakes with the other party. It does not provide error recovery or data retransmission. Applicable to scenarios with preference for real-time content over reliability, such as video chats and pushes of real-time financial quotations.

    Note the following limitations when configuring the UDP protocol listeners:

    -   The maximum number of connections per listener: 100,000.
    -   Currently, does not support fragmented packages.
    -   Obtaining the real IP address for the UDP protocol in the classic network is not supported.
    -   In the following two scenarios, the UDP protocol listener configuration takes five minutes to take effect:
        -   Remove the backend ECS instances.
        -   Set the weight of a backend ECS instance to zero.

## Layer-4 listener configurations {#section_ats_xq5_vdb .section}

|Configuration|Description|
|:------------|:----------|
|**Front-end Protocol \[Port\]**|The front-end protocol and port used to receive connection requests and forward the requests to backend servers.When configuring a layer-4 listener, select TCP or UDP. The port number is 1-65535.

**Note:** The front-end ports in a Server Load Balancer instance must be unique.

|
|**Backend Protocol \[Port\]**|The open port on the backend ECS instance for receiving requests.The backend protocol is the same as the front-end protocol, and the port number is 1-65535.

**Note:** The back-end ports in a Server Load Balancer instance can be the same.

|
|**Peak Bandwidth**|For Load Balancing instances with bandwidth charges, you can set different bandwidth peaks for different listeners to limit the traffic that you listen. The sum of the peak bandwidth of all listeners under an instance cannot exceed the bandwidth of that instance.When the listen bandwidth is not restricted, the total bandwidth of each listening shared instance. For more details, refer to [Share bandwidht](intl.en-US/User Guide/Listener/Shared instance bandwidth.md#).

|
|**Scheduling Algorithm**|Server Load Balancer supports three scheduling algorithms: round robin, weighted round robin \(WRR\), and weighted least connections \(WLC\).-   Round Robin: Requests are evenly and sequentially distributed to the backend ECS servers.
-   Weighted Round Robin \(WRR\): Backend servers with higher weights receive more requests than those with smaller weights.
-   Weighted Least Connections \(WLC\): Servers with a higher weight will receive a larger percentage of live connections at any one time. If the weights are the same, the system directs network connections to the server with the fewest established connections.

|
|**Use Server Group**|If used, you can manage backend servers in the listener dimension. A server group contains multiple backend servers with different ports.**Note:** Using the server group, you can configure different listeners with different server groups. Therefore, the listener can forward requests to specified backend servers. If you do not configure a VServer group, the listener will forward the requests to the backend server pool. For more information, see [Add backend ECS instances.](intl.en-US/User Guide/Backend servers/Add default servers.md#).

|
|**Sever Group Type**|After enabling the server group function, select the type of server group to be used:-   VServer group: A group of ECS instances added as backend servers. The port numbers of the backend servers in a VServer group can be different. With VServer group, you can distribute traffic to specified backend servers and configure the domain name/URL forwarding rules to distribute traffic based on the request domains and URLs. For more information, see [Create VServer groups](intl.en-US/User Guide/Backend servers/Create a VServer group.md#).
-   Master-Slave server group: A group of two ECS instances, one is a master server and the other one is the slave server. When you have traditional primary-backup demands, you can choose this type. When the master server works normally, traffic will go to the master server. When the master server goes down, traffic will go to the slave server. You can use the master-slave server group to avoid service interruptions. For more information, see [Create master-slave server groups](intl.en-US/User Guide/Backend servers/Create a master-slave server group.md#).

|
|**Automatically Activate Listener after Creation**|Choose whether to activate the listener once the listener is created. The default setting is Activated.|

|Advanced settings|Description|
|:----------------|:----------|
|**Obtain Real IP**|For layer-4 listeners, you can directly get the real IP of the client.**Note:** Obtaining real IP function is not supported by the classic network Server Load Balancer instance with the UDP protocol.

|
|**Session persistence**|Choose whether to enable session persistence. If enabled, all requests from a client are sent to the same backend server for the duration of the session.For TCP listeners, session persistence is based on IP addresses. Requests from the same IP address are forwarded to the same backend server.

**Note:** Session persistence is not supported for UDP listeners.

|
|**Enable Access Control **|Specify whether to enable the access control function.|
|**Access Control Method**| Select an access control method after enabling the access control function:

 -   Whitelist: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

-   Blacklist: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded.

It applies to scenarios where the application only denies access from some specific IP addresses.


 |
|**Select an Access Control List**|Select an access control list as the whitelist or the blacklist. For more information, see [Configure an access control list](intl.en-US/User Guide/Access control/Configure an access control list.md#).|

