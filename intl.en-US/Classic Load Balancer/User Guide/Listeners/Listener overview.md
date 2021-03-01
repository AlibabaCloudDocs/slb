# Listener overview

This topic provides an overview of listeners. After you create a Server Load Balancer \(SLB\) instance, you must configure one or more listeners for it. A listener checks for connection requests and then distributes the requests to backend servers based on the forwarding rules that are defined by a specified scheduling algorithm.

SLB provides Layer 4 \(TCP and UDP\) and Layer 7 \(HTTP and HTTPS\) listeners. The following table lists the features and use cases of these listeners.

|Protocol|Feature|Use case|
|:-------|:------|:-------|
|TCP|-   A connection-oriented protocol. A logical connection must be established before data can be sent and received.
-   Source IP address-based session persistence.
-   Source IP addresses readable at the network layer.
-   Fast data transmission

|-   Applicable to scenarios that require high reliability and data accuracy but can tolerate low speeds, such as file transmission, sending or receiving emails, and remote logons.
-   Web applications that do not have special requirements.

For more information, see [Add a TCP listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add a TCP listener.md). |
|UDP|-   A connectionless protocol. UDP transmits data packets directly instead of making a three-way handshake with the other party before UDP sends data. UDP does not provide error recovery or data re-transmission.
-   Fast data transmission but relatively low reliability.

|Applicable to scenarios where real-time transmission is more important than reliability, such as video chats and real-time financial market pushes.

For more information, see [Add a UDP listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add a UDP listener.md). |
|HTTP|-   An application-layer protocol that is used to package data.
-   Cookie-based session persistence.
-   Use X-Forward-For to obtain source IP addresses.

|Applicable to scenarios that require data content to be identified, such as web applications and small mobile games.

For more information, see [Add an HTTP listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTP listener.md). |
|HTTPS|-   Encrypted data transmission that prevents unauthorized access.
-   Centralized certificate management service. You can upload certificates to SLB. The decryption operations are directly completed on SLB.

|Applicable to scenarios that require encrypted transmission.

For more information, see [Add an HTTPS listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTPS listener.md). |

