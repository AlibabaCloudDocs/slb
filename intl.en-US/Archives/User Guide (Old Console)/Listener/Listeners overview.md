# Listeners overview {#concept_xvg_qmn_vdb .concept}

After creating a Server Load Balancer instance, you need to configure a listener for it. The listener checks connection requests and then distributes them to backend servers according to the configured rules.

As shown in the following figure, the listener contains listener configuration and health check configuration.

## Listener configuration {#section_brc_4p5_vdb .section}

Alibaba Cloud provides layer-4 \(TCP and UDP protocols\) and layer-7 \(HTTP and HTTPS protocols\) load balancing services. Select the protocol based on your business needs:

|Protocol|Description|Scenarios|
|:-------|:----------|:--------|
|[TCP](intl.en-US/User Guide/Listener/Layer-4 SLB Listener./Configure Layer-4 SLB listeners.md#)| -   A connection-oriented protocol. A reliable connection must be established with the peer end before data can be sent and received.
-   Source address-based session persistence.
-   The source address is available at the network layer.
-   Fast data transmission.

 | -   Applicable to scenarios with high requirements on reliability and data accuracy, but with tolerance for low speeds, such as file transmission, sending or receiving e-mails, and remote logon.
-   Web applications without special requirements.

 |
|[UDP](intl.en-US/User Guide/Listener/Layer-4 SLB Listener./Configure Layer-4 SLB listeners.md#)| -   A non-connection-oriented protocol. Before sending data, UDP directly performs data packet transmission instead of making three handshakes with the other party. It does not provide error recovery and data retransmission.
-   Fast data transmission, however, the reliability is relatively low.

 |Applicable to scenarios with preference of real-time content over reliability, such as video chats and pushes of real-time financial quotations.|
|[HTTP](intl.en-US/User Guide/Listener/Layer-7 listeners/Layer-7 listener configurations.md#)| -   An application layer protocol mainly used to package data.
-   Cookie-based session persistence.
-   Use X-Forward-For to obtain the source IP address.

 |Applicable to applications that need to recognize data content, such as web applications and small-sized mobile games.|
|[HTTPS](intl.en-US/User Guide/Listener/Layer-7 listeners/Layer-7 listener configurations.md#)| -   Similar to HTTP, but with an encrypted connection that prevents unauthorized access.
-   Unified certificate management service. Users can upload certificates to the Server Load Balancer and the decryption operations are completed directly on the Server Load Balancer

 |Applications requiring encrypted transmission|

**Note:** HTTP/2 and WSS/WS protocols are available in all regions now. For more information, see [HTTP/2 FAQ](../../../../intl.en-US/FAQ/HTTP/2 support FAQ.md#) and [WS/WSS FAQ](../../../../intl.en-US/FAQ/WS/WSS support FAQ.md#).  

## Health check configuration {#section_yqd_hz2_xdb .section}

Server Load Balancer provides health checks on the backend servers to improve service availability. For more details, see [Health check overview](intl.en-US/User Guide/Listener/Health check/Health check overview.md#) and [Configure health check](intl.en-US/User Guide/Listener/Health check/Health check configurations.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4126/3498_en-US.png)

