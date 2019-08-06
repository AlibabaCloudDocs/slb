# Layer-7 listener configurations {#concept_r2k_z35_vdb .concept}

SLB supports creating Layer-7 listeners of HTTP protocol or HTTPS protocol.

## Introduction to Layer-7 listeners {#section_o1s_js5_vdb .section}

-   HTTP protocol

    An application layer protocol that packages data. It is applicable to applications that need to recognize data contents, such as web applications and small-sized mobile games.

-   HTTPS protocol

    Similar to HTTP, but with an encrypted connection that prevents unauthorized access. SLB supports both one-way and two-way authentication. Additionally, SLB provides the certificate function. You do not need to manage certificates on the backend server. For more information, see [Add an HTTPS listener](intl.en-US/User Guide/Listener/Layer-7 listeners/HTTPS listeners.md#).


## Configurations of Layer-7 listeners {#section_ksl_rs5_vdb .section}

|Configurations|Description|
|:-------------|:----------|
|**Front-end Protocol \[Port\]**|The front-end protocol and port used to receive connection requests and forward the requests to backend servers.When configuring a layer-7 listener, select HTTP or HTTPS. The port number is in the range of 1-65535. For HTTPS protocol, the port number is 443.

**Note:** The front-end ports of the listeners in an SLB instance must be unique.

|
|**Backend protocol \[Port\]**|The port opened on backend ECS instances for receiving requests.The backend protocol is HTTP and the port number is in the range of 1-65535.

**Note:** The front-end ports within the same Server Load Balancer instance must not be repeated.

|
|**Peak Bandwidth**|If the SLB instance is billed at bandwidth, you can set different bandwidth peaks for different listeners to restrict the traffic through the listeners. The sum of the bandwidth set for all listeners cannot exceed the total bandwidth set for the SLB instance.|
|**Scheduling Algorithm**|Server Load Balancer supports three scheduling algorithms: round robin, weighted round robin \(WRR\), and weighted least connections \(WLC\).-   Round Robin: Requests are evenly and sequentially distributed to the backend ECS servers.
-   Weighted Round Robin \(WRR\): Backend servers with higher weights receive more requests than those with smaller weights.
-   Weighted Least Connections \(WLC\): A server with a higher weight will receive a larger percentage of live connections at any one time. When the weights are the same, the system directs network connections to the server with the fewest established connections.

|
|**Use Server Group**|If used, the listener will forward client requests only to the backend servers in the selected server group.A server group \(VServer group\) contains multiple backend servers with different ports. You can associate different listeners with different server groups. Therefore, the listener can forward requests to specified backend servers. For more information, see [Create a VServer Group](intl.en-US/User Guide/Backend servers/Create a VServer group.md#).

**Note:** Once a server group is configured with a listener, the listener forwards requests to the ECS instances in the selected server group. The ECS instances added to backend server pool will no longer receive requests. If no server group is configured, the listener forwards requests to the backend ECS instances added to the backend server pool. For more information, see [Add backend servers](intl.en-US/User Guide/Backend servers/Add default servers.md#).

|
|**Mutual Authentication**|Choose whether to enable two-way HTTPS authentication. If enabled, you have to upload the server certificate and CA certificate to SLB.If not, only the server certificate is required.

**Note:** This option is only available for HTTPS listeners.

|
|**Server Certificate**|The server certificate used by the client browser to check whether the certificate sent by the server is signed and issued by a trusted center.You can purchase a server certificate from Alibaba Cloud Security Certificate Service, or from other service providers. The server certificate must be uploaded to SLB. For more information, see [Upload certificates](intl.en-US/User Guide/Certificate management/Upload certificates.md#).

**Note:** This option is only available for HTTPS listeners.

|
|**CA Certificate**|The certificate used by the server to verify a client's identity. If the verification fails, connection is denied. The CA certificate is only required when the two-way authentication is enabled. You can use a self-signed CA certificate for verification.  For more information, see [Generate certificates](intl.en-US/User Guide/Certificate management/Generate CA certificates.md#).**Note:** This option is only available for HTTPS listeners.

|
|**Automatically Activate Listener after Creation**|Choose whether to enable listening after the listener is configured. The default setting is enabled.|
|Advanced settings|
|**Obtain Real IP**| For Layer-7 listeners, SLB uses the HTTP header X-Forwarded-For to get the real IP address of the client.|
|**Session Persistence**|If enabled, all session requests from the same client are sent to the same backend server.For Layer-7 listeners, session persistence is based on cookies. The following two methods are supported:

-   **Insert Cookie**: You only need to specify the cookie timeout period.

SLB adds a session cookie to the first response from the backend server and identifies the server which has sent the response. The next request will contain the cookie and the listener will distribute the request to the same backend server.

-   **Rewrite Cookie**: You can set the cookie to insert to the HTTP/HTTPS response according to your needs. You must maintain the timeout period and lifecycle of the cookie on the backend server.

SLB will overwrite the original cookie when it discovers that a new cookie is set. The next time the client carries the new cookie to access SLB, the listener will distribute the request to the previously recorded backend server. For more information, see [Session persistence](../../../../intl.en-US/Best Practices/Configure cookie in the backend server.md#).


See  [Session persistence FAQ](../../../../intl.en-US/FAQ/Session persistence FAQ.md#) for more details.

|
|**Idle Connection Timeout**|Specify the idle connection timeout in seconds. Valid value: 1-60If no request is received during the specified timeout period, Server Load Balancer will close the connection and restart the connection when the next request comes.

This function is available in all regions.

|
|**Request Timeout**|Specify the request timeout in seconds. Valid value: 1-180If no response is received from the backend server during the specified timeout period, Server Load Balancer will stop waiting and send an HTTP 504 error to the client.

This function is available in all regions.

|
|**Gzip Compression**|Choose whether to enable Gzip compression to compress files of specific formats.Now Gzip supports the following file types: text/xml, text/plain, text/css, application/javascript, application/x-javascript application/rss+xml, application/atom+xml and application/xml.

|
|**Additional HTTP Header Fields**|Select the custom HTTP headers that you want to add:-   **Client's Real IP**: Add the `X-Forwarded-For` header to obtain the IP address of the client.
-   **Server Load Balancer Listener Protocol**: Add the `X-Forwarded-Proto` header to obtain the protocol used to connect SLB.
-   **Server Load Balancer Inbound IP**: Add the `SLB-IP` header to obtain the public IP of the SLB instance.
-   **Server Load Balancer Instance ID**: Add the `SLB-ID` header to obtain the ID of the SLB instance.

|
|**Enable Access Control**|Select whether to enable the access control function.|
|**Access Control Method**|Select an access control method after enabling the access control function:-   Whitelist: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling whitelist poses some business risks. If a whitelist is configured, only the IP addresses in the list can access SLB. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

-   Blacklist: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.


|
|**Select an Access Control List**|Select an access control list as the whitelist or the blacklist. For more information, see [Configure an access control list](intl.en-US/User Guide/Access control/Configure an access control list.md#).|

