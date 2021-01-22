# How do I troubleshoot HTTP 5xx errors?

After a Server Load Balancer \(SLB\) instance is configured, errors such as 500 Internal Server Error, 502 Bad Gateway, and 504 Gateway Timeout may occur. These errors can be caused by the blockage from Internet service providers \(ISPs\), blockage from Alibaba Cloud Security for abnormal client activities, configuration errors of the SLB instance, health check failures, or failures in accessing web applications on the backend ECS instances.

This topic lists the causes, solutions, and troubleshooting methods of these problems.

1.  [Possible causes and solutions](#ol_srv_w1d_xdb)
    -   [The origin domain name does not have an ICP license or ICP filing, or no Layer 7 routing methods are configured for the domain name in the Alibaba Cloud anti-DDoS network or security network.](#1)
    -   [The source IP address of the client is blocked by Alibaba Cloud Security.](#2)
    -   [The source IP address is blocked by the security software of the backend ECS instance.](#3)
    -   [Parameters of the Linux kernel of the backend ECS instance are incorrectly configured.](#4)
    -   [The backend ECS instance runs into a performance bottleneck.](#5)
    -   [SLB reports 502 errors due to health check failures.](#6)
    -   [Health checks succeed but 502 errors are reported for web applications.](#7)
    -   [The HTTP header is too long.](#8)
2.  [Troubleshooting](#section_tgb_4cd_xdb)
3.  [Submit a ticket](#section_gyl_vcd_xdb)

## Possible causes and solutions

1.  The origin domain name does not have an ICP license or ICP filing, or no Layer 7 routing methods are configured for the domain name in the Alibaba Cloud anti-DDoS network or security network.

    Solution: Obtain an ICP filing or ICP license for the domain name? If the SLB instance is deployed in the Alibaba Cloud anti-DDoS network or security network, configure corresponding domain name-based routing methods.

2.  The source IP address of the client is blocked by Alibaba Cloud Security.

    Check whether the same problem occurs to clients of other ISPs. If not, the problem is caused by blockage from the ISP.

    Solution: Submit a ticket to Alibaba Cloud technical support personnel, who then capture packets to determine whether the blockage occurs. If the blockage occurs, contact the ISP to solve the problem.

3.  The source IP address is blocked by the security software of the backend ECS instance.

    100.64.0.0/10 is an CIDR block reserved by Alibaba Cloud for SLB servers for health checks and request forwarding. No security risks exist for 100.64.0.0/10. If security software or a firewall inside the system is applied, add this CIDR block to the whitelist of the software or firewall to avoid 500 or 502 errors.

    Solution: Add 100.64.0.0/10 to the whitelist of antivirus or firewall software or uninstall the software to check whether the problem is caused by the blockage from the software.

4.  Parameters of the Linux kernel of the backend ECS instance are incorrectly configured.

    If the backend ECS instance uses the Linux system, you can disable the rp\_filter parameters in the system kernel when you change the Layer 7 listener to a Layer 4 listener.

    Solution: Set the values of the following parameters in the /etc/sysctl.conf system configuration file to 0, and then run `sysctl -p`.

    ```
     net.ipv4.conf.default.rp_filter = 0
     net.ipv4.conf.all.rp_filter = 0
     net.ipv4.conf.eth0.rp_filter = 0
    ```

5.  The backend ECS instance runs into a performance bottleneck.

    High CPU utilization or public bandwidth exhaustion may cause access exceptions.

    Solution: Check the performance of the backend ECS instance and solve performance bottlenecks. If the overall system capacity is insufficient, you can increase the number of backend ECS instances.

6.  SLB reports 502 errors due to health check failures.

    For information about how to troubleshoot health check failures, see [What can I do if my ECS instance is declared unhealthy after I enable health checks for Server Load Balancer?](/intl.en-US/Classic Load Balancer/FAQ/What can I do if my ECS instance is declared unhealthy after I enable health checks for Server Load Balancer?.md)

    Also, 502 errors occur if the health check function of SLB is disabled and the web service in the backend server cannot process HTTP requests.

7.  Health checks succeed but 502 errors are reported for web applications.

    If the 502 Bad Gateway error message indicates that SLB can forward requests from clients to backend servers, but the web applications on the backend servers cannot process the requests, you must check the configurations and running status of the web applications on the backend servers. For example, the time used by a web application to process an HTTP request exceeds the timeout value of SLB.

    For Layer 7 listeners, if the time used by the backend server to process PHP requests exceeds the proxy\_read\_timeout value of 60 seconds, SLB reports 504 Gateway Timeout. For Layer 4 listeners, the timeout value is 900 seconds.

    Solution: Make sure that the web service and related services run normally. Check whether PHP requests are processed properly, and optimize the processing of PHP requests by the backend server. NGINX+PHP-FPM is used in the following example:

    1.  The number of PHP requests that are processed has reached the limit.

        When the total number of PHP requests that are processed in the server has reached the limit set by max\_children in PHP-FPM, 502 or 504 erros may occur if more PHP requests are sent to the server:

        -   If existing and new PHP requests are both processed in a timely manner, no error occurs.
        -   New PHP requests wait to be processed when existing PHP requests are being processed. If the time that a new PHP request waits exceeds the value of fastcgi\_read\_timeout of NGINX, a 504 Gateway Timeout error occurs.
        -   New PHP requests wait to be processed when existing PHP requests are being processed. If the time that a new PHP request waits exceeds the value of request\_terminate\_timeout of NGINX, a 502 Bad Gateway error occurs.
    2.  If the PHP script execution time exceeds the limit, or the time used by PHP-FPM to process PHP scripts exceeds the value of request\_terminate\_timeout in NGINX, a 502 error occurs and the following error entry is shown in NGINX logs:

        ```
        [error] 1760#0: *251777 recv() failed (104: Connection reset by peer) while reading response header from upstream, client: xxx.xxx.xxx.xxx, server: localhost, request: “GET /timeoutmore.php HTTP/1.1”, upstream: “fastcgi://127.0.0.1:9000”
        ```

    3.  The health check is performed on static pages. Errors occur when exceptions are detected in the process that handles dynamic requests. For example, PHP-FPM is not running.
8.  The HTTP header is too long.

    An HTTP header that is too long may make SLB unable to process relevant data, which results in 502 errors.

    Solution: Decrease the amount of data transmitted by the header or switch to the TCP listener.

9.  The service access logic is inappropriate.

    Make sure that no backend ECS instance in SLB accesses the public IP addresses of SLB instances. If a backend ECS instances accesses its own port through the public IP address of the SLB instance to which the ECS instance is added as a backend server, the access request is sent to the backend ECS instance based on the routing methods configured for the SLB instance. This leads to an infinite loop, which results in 500 or 502 errors.

    Solution: Make sure that no backend ECS instance in SLB accesses the public IP addresses of SLB instances.


## Troubleshooting

-   Check the screenshot of the 500, 502, or 504 error to determine the cause of the error. The error may be caused by SLB, Anti-DDoS or security network, or backend ECS instance configurations.
-   If Anti-DDoS or security network is used, make sure that the Layer 7 routing methods are correctly configured.
-   Check whether the problem occurs to all clients. If not, check whether the client that indicates an error has been blocked by Alibaba Cloud Security. Also, check whether the domain name or IP address of SLB is clocked by the ISP.
-   Check the status of SLB instances and whether backend ECS instances fail the health check. If one or more backend ECS instances fail the health check, troubleshoot the failure.
-   Associate the endpoint of SLB with the IP address of the backend server by using the hosts file on the client. If a 5xx error occurs at intervals, the error may be caused by incorrect configurations of a backend ECS instance.
-   Change Layer 7 SLB to Layer 4 SLB to see whether the problem occurs again.
-   Check the performance of backend ECS servers and whether performance bottlenecks of the CPU, memory, disk, or bandwidth exist.
-   If the error is caused by the backend server, check the web server logs of the backend server. Check whether the web service is running normally and whether the web access logic is correct.
-   Check whether the TCP kernel parameters of the Linux system on the backend ECS instance are correctly configured.

## Submit a ticket

Perform the preceding troubleshooting procedures step by step and record the test results in detail. Provide the test results when you submit a ticket so that Alibaba Cloud technical support personnel can help you solve the problem promptly.

If the problem persists, consult Alibaba Cloud technical support personnel.

