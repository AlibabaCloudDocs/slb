# Features {#concept_sh1_pp4_tdb .concept}

This topic lists key functions of Server Load Balancer \(SLB\) and indicates whether these functions are supported by Layer-4 and Layer-7 SLB instances.

**Note:** "×" indicates that the corresponding function is not supported. "✔" indicates that the corresponding function is supported.

|Function|Layer-4 SLB|Layer-7 SLB|
|:-------|:----------|:----------|
| Scheduling algorithm

 SLB supports round robin, weighted round robin, weighted least connections, and consistent hash.

 |✔|✔|
| Health check

 SLB checks health status of backend servers. If a backend server is declared as unhealthy, SLB will stop distributing traffic to it and distribute incoming traffic to other healthy backend servers.

 |✔|✔|
| Session persistence

 SLB supports session persistence. In a session, SLB can distribute requests from the same client to the same backend server.

 |✔|✔|
| Access control

 SLB supports whitelists and blacklists to control access to your applications.

 |✔|✔|
| High availability

 SLB can forward incoming traffic to backend servers in different zones. Additionally, SLB is deployed in active/standby mode in most regions. It will automatically switch to the backup zone to provide load balancing service if the primary zone is unavailable.

 |✔|✔|
| Security

 Combined with Alibaba Cloud Security, SLB can defend against up to 5 Gbit/s DDoS attacks.

 |✔|✔|
| Internet and intranet load balancing

 SLB provides both Internet and intranet load balancing services. You can create an intranet SLB instance to balance traffic in your VPC network, or create an Internet SLB instance to balance traffic coming from the Internet.

 |✔|✔|
| Monitoring

 With the CloudMonitor service, you can view the monitoring data of SLB, such as the number of connections and inbound and outbound traffic.

 |✔|✔|
| IPv6 support

 SLB is able to forward requests from IPv6 clients.

 |✔|✔|
| Access logs

 With Log Service, you can analyze access logs of an SLB instance to understand the behavior and geographical distribution of users, and troubleshoot problems.

 |×|✔|
| Health check logs

 SLB stores health check logs of backend servers generated within three days by default. You can store all health check logs in OSS for troubleshooting.

 |✔|✔|
| Domain name-based/URL-based forwarding

 Layer-7 SLB supports domain name-based and URL-based forwarding rules to forward requests from different domain names or URLs to different backend servers.

 |×|✔|
| Certificate management

 SLB provides a centralized certificate management service for applications using HTTPS protocols. You do not need to upload certificates to backend servers. Instead, deciphering is performed on SLB to reduce the CPU usage of backend servers.

 |×|✔|
| SNI support

 SLB supports configuring multiple certificates in an HTTPS listener to distribute requests with different domain names to different backend servers.

 |×|✔|
| Redirection

 SLB supports redirecting HTTP requests to HTTPS requests.

 |×|✔|
| WS/WSS support

 WebSocket is a new HTML protocol. It provides bi-directional communication channels between clients and servers, saving server resources and bandwidth, and achieving real-time communication.

 |×|✔|
| HTTP/2 support

 HTTP/2 is the second version of Hypertext Transfer Protocol. It is backward compatible with HTTP1.X and significantly improves performance.

 |×|✔|

