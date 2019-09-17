# Listener overview {#concept_xvg_qmn_vdb .concept}

After you create a Server Load Balancer \(SLB\) instance, you must configure a listener for it. The listener checks connection requests and then distributes the requests to backend servers according to configured forwarding rules.

Alibaba Cloud provides Layer-4 \(TCP and UDP protocols\) and Layer-7 \(HTTP and HTTPS protocols\) load balancing services. Select the protocol based on your needs.

|Protocol|Description|Scenario|
|:-------|:----------|:-------|
|TCP| -   A connection-oriented protocol. A reliable connection must be established before data can be sent and received.
-   Source IP address-based session persistence.
-   Source IP addresses can be read at the network layer.
-   Fast data transmission.

 | -   Applicable to scenarios where high transmission reliability and data accuracy are required, but some flexibility regarding network latency is permitted, such as file transmission, sending or receiving emails, and remote logons.
-   Web applications that have no special requirements.

 For more information, see [Add a TCP listener](reseller.en-US/Listeners/Add a TCP listener.md#).

 |
|UDP| -   A non-connection-oriented protocol. UDP directly transmits data packets instead of making a three-way handshake with the other party before sending data. It does not provide error recovery and data re-transmission.
-   Fast data transmission, but the reliability is relatively low.

 | Applicable to scenarios with preference to real-time content over reliability, such as video chats and real-time financial quotations.

 For more information, see [Add a UDP listener](reseller.en-US/Listeners/Add a UDP listener.md#).

 |
|HTTP| -   An application layer protocol mainly used to package data.
-   Cookie-based session persistence.
-   Use X-Forward-For to obtain source IP addresses.

 | Applicable to applications that need to recognize data content, such as web applications and small-sized mobile games.

 For more information, see [Add an HTTP listener](reseller.en-US/Listeners/Add an HTTP listener.md#).

 |
|HTTPS| -   Encrypted data transmission that prevents unauthorized access.
-   Unified certificate management service. You can upload certificates to SLB and decryption operations are completed directly on SLB.

 | Applications that require encrypted transmission.

 For more information, see [Add an HTTPS listener](reseller.en-US/Listeners/Add an HTTPS listener.md#).

 |

**Note:** HTTP/2 and WSS/WS protocols are supported by all regions. For more information, see [HTTP/2 support FAQ](../../../../reseller.en-US/FAQ/FAQ/HTTP__2 support FAQ.md#) and [WS and WSS support FAQs](../../../../reseller.en-US/FAQ/WS and WSS support FAQs.md#).

