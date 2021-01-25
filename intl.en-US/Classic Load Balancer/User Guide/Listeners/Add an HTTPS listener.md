# Add an HTTPS listener

This topic describes how to add an HTTPS listener to a Server Load Balancer \(SLB\) instance. HTTPS is applicable to applications that require encrypted data transmission. You can add an HTTPS listener to an SLB instance to forward HTTPS requests.

An SLB instance is created. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).

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


## Step 2: Configure the HTTPS listener

To configure the HTTPS listener, perform the following operations:

1.  In the Protocol and Listener step, configure the following parameters.

    |Parameter|Description|
    |:--------|:----------|
    |**Select Listener Protocol**|Select the protocol of the listener. In this example, select **HTTPS**. |
    |**Backend Protocol**|The backend protocol used by HTTPS listeners is **HTTP**.|
    |**Listening Port**|Set the listening port used to receive requests and forward them to backend servers. Valid values: 1 to 65535.

**Note:** The HTTP listening ports must be unique in an SLB instance. |
    |**Listener Name**|Enter a name for the listener.|
    |**Advanced**|
    |**Scheduling Algorithm**|SLB supports three scheduling algorithms: RR, WRR, and WLC.     -   **Weighted Round-Robin \(WRR\)**: Backend servers with a higher weight receive more requests than those with a lower weight.
    -   **Round-Robin \(RR\)**: Requests are sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: Requests are distributed based on the combination of the weights and active connections of backend servers. If two backend servers have the same weight, requests are forwarded to the backend server with fewer connections. |
    |**Enable Session Persistence**|Specify whether to enable session persistence.

After session persistence is enabled, the listener forwards all requests from the same client to a specific backend server for the duration of a session.

HTTP implements cookie-based session persistence. SLB allows you to use the following methods to process cookies:

    -   **Insert cookie**: You need to specify only the cookie timeout period.

SLB inserts a cookie \(SERVERID\) into the first HTTP or HTTPS response packet that is sent to a client. The next request from the client contains this cookie, and the listener distributes this request to the recorded backend server.

    -   **Rewrite cookie**: You can specify the cookie to be inserted into an HTTP or HTTPS response to meet your specific needs. You must maintain the timeout period and lifecycle of this cookie on the backend server.

SLB overwrites the original cookie with a new cookie when the new cookie is specified. The next time the client carries the new cookie to access SLB, the listener distributes the request to the recorded backend server. For more information, see [Configure session persistence rules](/intl.en-US/Classic Load Balancer/FAQ/Configure cookie in the backend server.md). |
    |**Enable HTTP/2**|Select whether to enable HTTP/2.0 for the frontend protocol.|
    |**Enable Access Control**|Specify whether to configure the listener to restrict access. After you enable access control, you can allow access from specific IP addresses or block access from specific IP addresses. |
    |**Access Control Method**|Select an access control method after you enable access control.

    -   **Whitelist**: Only the requests from the IP addresses or CIDR blocks in the specified ACL are forwarded. You can use the whitelist feature when you want to allow access from specified IP addresses.

Risks may arise if you specify an ACL as a whitelist. After a whitelist is enabled, only IP addresses contained in the whitelist can access the SLB listener. If a whitelist is enabled without any IP addresses specified, the SLB listener forwards all requests.

    -   **Blacklist**: Requests from the IP addresses or CIDR blocks in the specified ACL are not forwarded. You can use the blacklist feature when you want to deny access from specified IP addresses.

If a blacklist is enabled without any IP addresses specified, the SLB listener forwards all requests. |
    |**Access Control List**|Select an ACL that is used as the whitelist or blacklist of the listener. **Note:** IPv6 instances can be associated only with IPv6 ACLs, while IPv4 instances can be associated only with IPv4 ACLs. For more information, see [Create an access control list](/intl.en-US/Classic Load Balancer/User Guide/Access control/Access control lists/Create an access control list.md). |
    |**Enable Peak Bandwidth Limit**|You can switch on this option and then set a bandwidth limit for the listener.

If an SLB instance incurs fees based on the bandwidth, you can set different peak bandwidth values for different listeners to limit the amount of traffic that flows in each listener. The sum of the peak bandwidth values of all listeners added to an SLB instance cannot exceed the bandwidth of this SLB instance.

By default, this feature is disabled and all listeners share the bandwidth of the SLB instance.

**Note:** If an SLB instance incurs fees based on the amount of transmitted data, no peak bandwidth limit is applied by default. |
    |**Idle Timeout**|Specify the idle timeout period of connections. Unit: seconds. Valid values: 1 to 60. If no request is received during the idle timeout period, SLB closes the connection and restarts the connection when the next request is received.

This feature is available in all regions. |
    |**Request Timeout**|Specify the request timeout period. Unit: seconds. Valid values: 1 to 180. If no response is received from the backend server during the request timeout period, SLB sends an HTTP 504 error code to the client.

This feature is available in all regions. |
    |**Enable Gzip Compression**|Specifies whether to enable compression for a specific file type. Gzip supports the following file types: text/xml, text/plain, text/css, application/javascript, application/x-javascript, application/rss+xml, application/atom+xml, and application/xml. |
    |**Add HTTP Header Fields**|Select one or more custom HTTP header fields that you want to add:     -   Use the `X-Forwarded-For` header field to retrieve the IP addresses of clients.
    -   Use the `X-Forwarded-Proto` header field to retrieve the listener protocol used by the SLB instance.
    -   Use the `SLB-IP` header field to retrieve the public IP address of the SLB instance.
    -   Use the `SLB-ID` header field to retrieve the ID of the SLB instance. |
    |**Obtain Client Source IP Address**|HTTP listeners use the X-Forwarded-For header field to obtain the actual IP addresses of clients.|
    |**Automatically Enable Listener After Creation**|Specifies whether to start the listener immediately after the listener is configured. By default, the listener is started after configuration.|

2.  Click **Next**.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p10035.png)


## Step 3: Configure an SSL certificate

To add an HTTPS listener, you must upload a server certificate or CA certificateand select a TLS security policy.

**Note:** SLB supports the following public key algorithms:

-   RSA 1024
-   RSA 2048
-   RSA 4096
-   ECDSA P-256
-   ECDSA P-384
-   ECDSA P-521

|Certificate|Description|Required for one-way authentication|Required for mutual authentication|
|:----------|:----------|:----------------------------------|:---------------------------------|
|Server certificate|The certificate that is used to identify the server. The server certificate allows your browser to verify whether the server-sent certificate is signed and issued by a trusted certification authority \(CA\).

|Yes. You must upload the server certificate to the certificate management system of SLB.

|Yes. You must upload the server certificate to the certificate management system of SLB. |
|Client certificate|The certificate that is used to identify the client. The server identifies the client by checking the certificate sent by the client. You can sign a client certificate with a self-signed CA certificate.

|No|Yes. You must install the client certificate on the client. |
|CA certificate|The server uses a CA certificate to verify the signature on the client certificate. If the certificate cannot be verified, the connection request is rejected.|No|Yes You must upload the CA certificate to the certificate management system of SLB. |
|**TLS security policy**|Only guaranteed-performance instances support TLS security policies. A TLS security policy specifies the TLS protocol version that supports HTTPS communication and the matching encryption algorithm suite. For more information, see [Manage TLS security policies](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Manage TLS security policies.md).

|Yes.|Yes.|

Before you upload a certificate, take note of the following items:

-   The uploaded certificate must be in the PEM format.
-   After you upload the certificate to SLB, SLB can manage the certificate and you do not need to bind the certificate to backend servers.
-   It may take some time to activate an HTTPS listener because the certificate must be uploaded, loaded, and verified. It can take up to three minutes for an HTTPS listener to be activated.
-   The ECDHE cipher suites used by HTTPS listeners support forward secrecy but do not support the security enhancement parameters required by DHE cipher suites. As a result, strings that contain the `BEGIN DH PARAMETERS` field in a PEM certificate file cannot be uploaded. For more information, see [Certificate requirements](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Certificate requirements.md).
-   HTTPS listeners of guaranteed-performance SLB instances support SNI. For more information, see [Add an additional certificate](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Domain name extensions/Add an additional certificate.md).
-   The session ticket timeout period of HTTPS listeners is 300 seconds.
-   The actual amount of traffic generated on an HTTPS listener is larger than the billed traffic amount because some traffic is used for handshaking.
-   If a large number of new connections are established, a large amount of traffic is generated.

1.  Select an uploaded server certificate, or click **Create Server Certificate** to upload a server certificate.

    For more information, see [Certificate overview](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Create a certificate/Certificate overview.md).

2.  To enable HTTPS mutual authenticationor configure a TLS security policy, click **Modify** next to Advanced.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p47905.png)

3.  Turn on Enable Mutual Authentication, and select an uploaded CA certificate or click **Create CA Certificate** to upload a CA certificate.

    You can use a self-signed CA certificate. For more information, see [Certificate overview](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Create a certificate/Certificate overview.md).

4.  Select a TLS security policy. For more information, see [Manage TLS security policies](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Manage TLS security policies.md).


## Step 4: Add backend servers

After you configure the listener, you must add backend servers to process client requests. You can add backend servers to the default server group, or create VServer groups or primary/secondary server groups and then add servers to them. For more information, see [Backend server overview](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Backend server overview.md).

The default server group is used in the example.

1.  Select **Default Server Group** and click **Add More**.

    ![Add backend servers to the default server group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p10030.png)

2.  In the **My Servers** panel, select ECS instances as the backend servers that you want to add and click **Next**.

    ![Configure weights](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p7499.png)

3.  In the **Configure Ports and Weights** step, configure weights for the added backend servers. A backend server that has a higher weight receives more requests.

    **Note:** If the weight of an IDC server is set to 0, the IDC server no longer receives new requests.

4.  Click **Add**. On the Default Server Group tab, configure ports for the backend servers. Valid values: 1 to 65535.

    You can specify the same port for multiple backend servers of an SLB instance.

5.  Click **Next**.


## Step 5: Configure the health check

SLB checks the availability of backend servers by performing the health check. The health check feature improves the availability of frontend services by minimizing downtime caused by health issues of backend servers. Click **Modify** to configure advanced health check settings. For more information, see [Health check overview](/intl.en-US/Classic Load Balancer/User Guide/Health check/Health check overview.md).

## Step 6: Confirm the settings

Submit the configurations by performing the following operations:

1.  In the Submit step, check the configuration. You can click **Modify** to modify configuration settings.

2.  Click **Submit**.

3.  In the Configure Successful dialog box, click **OK**.

    You can check the created listener on the Listener tab.


**References**  


[Add ECS instances to the default server group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Default server groups/Add ECS instances to the default server group.md)

[Add ECS instances to a VServer group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/VServer groups/Add ECS instances to a VServer group.md)

[Add ECS instances to a primary/secondary server group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Active/standby server groups/Add ECS instances to a primary/secondary server group.md)

[Overview](/intl.en-US/Classic Load Balancer/User Guide/Access control/Configure access control.md)

[Forward requests based on domain names or URLs](/intl.en-US/Tutorials/Forward requests based on domain names or URLs.md)

[Add an additional certificate](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Domain name extensions/Add an additional certificate.md)

[CreateLoadBalancerHTTPSListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTPS listeners/CreateLoadBalancerHTTPSListener.md)

