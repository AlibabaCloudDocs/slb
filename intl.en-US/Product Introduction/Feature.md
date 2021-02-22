# Feature

This topic describes the key features of Apsara Stack SLB and whether Layer-4 SLB and Layer-7 SLB support the features.

In the following table, "✔"Indicates supported, and"-"indicates not supported.

|Feature|Layer-4 SLB|Layer-7 SLB|
|:------|:----------|:----------|
|Scheduling algorithms SLB supports the following scheduling algorithms: round-robin, weighted round-robin \(WRR\), weighted least connections \(WLC\), and consistent hash.

|✔|√ **Note:** Currently, Layer-7 SLB does not support the scheduling algorithm of consistent hash. |
|Health Check SLB uses health checks to inspect the availability of backend servers. If a backend server is declared as unhealthy, the corresponding SLB instance stops distributing inbound traffic to it and distributes the traffic to other healthy backend servers.

|✔|√|
|Session persistence SLB provides session persistence In a session, the SLB instance can distribute all of the requests from the same client to the same backend server.

|✔|√|
|Resource Access Management SLB uses whitelists and blacklists to control access to your applications.

|✔|√|
|High Availability \(HA\) SLB distributes inbound traffic to backend servers across zones. In addition, SLB is deployed in primary/secondary mode in most regions, meaning that an SLB instance is deployed across two zones within the same region. One zone is the primary zone and the other zone is the secondary zone. If the primary zone fails, the SLB instance will automatically fail over to the secondary zone, ensuring the high availability of the SLB service.

|✔|√|
|Security and protection You can use SLB with Apsara Stack Security to defend your applications against up to 5 Gbit/s DDoS attacks.

|✔|√|
|Public and internal network load balancing SLB can be used to balance the traffic load from the Internet or within internal networks. You can create an internal SLB instance to balance traffic within a VPC, or create a public SLB instance to balance traffic coming from the public network.

|✔|√|
|Monitoring You can use CloudMonitor to view the monitoring data of SLB instances such as the number of connections and inbound and outbound traffic volumes.

|✔|√|
|IPv6 support SLB can forward requests from IPv6 clients.

|✔|√|
|Health check logs SLB stores health check logs of backend servers generated within three days by default. You can store all health check logs in OSS for troubleshooting.

|✔|√|
|Domain name forwarding and URL forwarding Layer-7 SLB supports configuration of domain name forwarding rules and URL forwarding rules to forward requests from different domain names or URLs to different backend servers.

|-|✔|
|Certificate management SLB provides a centralized certificate management solution for HTTPS listeners You do not need to upload certificates to backend servers. Deciphering is performed on SLB instances to reduce the CPU utilization of backend servers.

|-|✔|
|SNI support SLB allows you to associate multiple certificates to an HTTPS listener to distribute requests from different domain names to different backend servers.

|-|✔|
|Redirection-based back-to-origin SLB supports redirecting HTTP requests to HTTPS.

|-|✔|
|WS/WSS support WebSocket is a new HTML5 protocol. It provides bidirectional communication channels between clients and servers, saving server resources and bandwidth, and achieving real-time communication.

|-|✔|
|HTTP/2 support HTTP/2 is the second version of HTTP. It is backward compatible with HTTP1.X and significantly improves performance.

|-|✔|

