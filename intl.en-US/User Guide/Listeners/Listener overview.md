# Listener overview {#concept_xvg_qmn_vdb .concept}

After creating a Server Load Balancer instance, you need to configure a listener for it. The listener checks connection requests and then distributes them to backend servers according to the configured rules.

Alibaba Cloud provides Layer-4 \(TCP and UDP protocols\) and Layer-7 \(HTTP and HTTPS protocols\) load balancing services. Select the protocol based on your business needs:

|Protocol|Description|Scenarios|
|:-------|:----------|:--------|
|TCP| -   A connection-oriented protocol. A reliable connection must be established with the peer end before data can be sent and received.
-   Source address-based session persistence.
-   The source address is visible at the network layer.
-   Fast data transmission.

 | -   Applicable to scenarios with high requirements on reliability and data accuracy but with tolerance for low speeds, such as file transmission, sending or receiving e-mails, and remote logon.
-   Web applications without special requirements.

 For more information, see [Add a TCP listener](intl.en-US/User Guide/Listeners/Add a TCP listener.md#). 

 |
|UDP| -   A non-connection-oriented protocol. Before sending data, UDP directly performs data packet transmission instead of making three handshakes with the other party. It does not provide error recovery and data retransmission.
-   Fast data transmission, however, the reliability is relatively low.

 | Applicable to scenarios with preference for real-time content over reliability, such as video chats and pushes of real-time financial quotations.

 For more information, see [Add a UDP listener](intl.en-US/User Guide/Listeners/Add a UDP listener.md#). 

 |
|HTTP| -   An application layer protocol mainly used to package data.
-   Cookie-based session persistence.
-   Use X-Forward-For to obtain the source IP address.

 | Applicable to applications that need to recognize data content, such as web applications and small-sized mobile games.

 For more information, see [Add an HTTP listener](intl.en-US/User Guide/Listeners/Add an HTTP listener.md#). 

 |
|HTTPS| -   Similar to HTTP, but with an encrypted connection that prevents unauthorized access.
-   Unified certificate management service. Users can upload certificates to the Server Load Balancer and the decryption operations are completed directly on the Server Load Balancer

 | Applications requiring encrypted transmission

 For more information, see [Add an HTTPS listener](intl.en-US/User Guide/Listeners/Add an HTTPS listener.md#). 

 |

**Note:** Server Load Balancer supports HTTP/2 and WSS/WS protocols in all regions now. For more information, see [HTTP/2 FAQ](../../../../intl.en-US/FAQ/FAQ/HTTP__2 support FAQ.md#) and [WS/WSS FAQ](../../../../intl.en-US/FAQ/WS and WSS support FAQs.md#).

