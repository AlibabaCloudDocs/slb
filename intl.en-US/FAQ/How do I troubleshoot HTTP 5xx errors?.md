# How do I troubleshoot HTTP 5xx errors? {#concept_lqf_v1d_xdb .concept}

After a Server Load Balancer \(SLB\) instance is configured, errors such as 500 Internal Server Error, 502 Bad Gateway, and 504 Gateway Timeout may occur. These errors can be caused by the blockage of the service provider, Alibaba Cloud blockage caused by abnormal client activities, wrong configurations of the SLB instance, health check failures, or failures in accessing web applications on the backend ECS instances.

This topic lists the causes, resolutions, and troubleshooting steps of these problems.

1.  [Possible causes and resolutions](#ol_srv_w1d_xdb)
    -   [The source site domain name is not put on record or it is not configured with any Layer-7 forwarding rule in Anti-DDoS Pro or security network.](#1)
    -   [The source IP address of the client is blocked by Alibaba Cloud Security.](#2)
    -   [The source IP address is blocked by the security protection software of the backend ECS instance.](#3)
    -   [Parameters of the Linux kernel of the backend ECS instance are configured wrong.](#4)
    -   [The performance of the backend ECS instance reaches a bottleneck.](#5)
    -   [SLB reports 502 errors due to health check failures.](#6)
    -   [The health check is normal but the web application reports 502 errors.](#7)
    -   [The HTTP header is too long.](#8)
2.  [Troubleshooting](#section_tgb_4cd_xdb)
3.  [Open a ticket](#section_gyl_vcd_xdb)

## Possible causes and resolutions {#section_xrv_w1d_xdb .section}

1.  The source site domain name is not put on record or it is not configured with any Layer-7 forwarding rule in Anti-DDoS Pro or security network.

    Resolution: Put the domain name on record. If the SLB instance is in Anti-DDoS Pro or security network, configure corresponding domain name-based forwarding rules.

2.  The source IP address of the client is blocked by Alibaba Cloud Security.

    Test if the same problem occurs to clients of other service providers. If not, the problem is generally caused by the blockage of the service provider.

    Resolution: Open a ticket to Alibaba Cloud who decides if there is blockage through packet capture. If so, contact the service provider to solve the problem.

3.  The source IP address is blocked by the security protection software of the backend ECS instance.

    100.64.0.0/10（100.64.0.0/10 is reserved by Alibaba Cloud, and will not be used by any user, there is no security risk \)is the IP address range of SLB servers and is mainly used for health checks and request forwarding. If security software or a firewall inside the system is installed, add the IP address range to the whitelist to avoid 500 or 502 errors.

    Resolution: Add the SLB IP address range to the whitelist of the antivirus or firewall software, or unload the software to test if the problem is caused by the blockage of the software.

4.  Parameters of the Linux kernel of the backend ECS instance are configured wrong.

    If the backend ECS instance uses the Linux system, you need to disable the rp\_filter parameters in system kernel when you change the Layer-7 listener to a Layer-4 listener.

    Set the values of the following parameters in the system configuration file /etc/sysctl.conf to zero, and then run `sysctl -P`.

    ```
     net.ipv4.conf.default.rp_filter = 0
     net.ipv4.conf.all.rp_filter = 0
     net.ipv4.conf.eth0.rp_filter = 0
    ```

5.  The performance of the backend ECS instance reaches a bottleneck.

    High CPU utilization or no extra bandwidth may cause access exceptions.

    Resolution: Check the performance of the backend ECS instance and solve performance bottlenecks. If the overall system capacity is insufficient, you can increase the number of backend ECS instances.

6.  SLB reports 502 errors due to health check failures.

    For more information about health check failures, see [Resolve health check failures](intl.en-US/FAQ/What can I do if my ECS instance is declared unhealthy after I enable health checks for Server Load Balancer?.md#).

    Also, 502 errors occur if the health check function of SLB is disabled and the web service in the backend server cannot process HTTP requests.

7.  The health check is normal but the web application reports 502 errors.

    The 502 Bad Gateway error message indicates that SLB can forward requests from the client to the backend servers, but the web application in the backend ECS instance cannot process the requests. Therefore, you must check the configurations and running status of the web application in the backend server. For example, the time used by the web application to process HTTP requests exceeds the timeout value of SLB. For Layer-7 listeners, if the time used by the backend server to process PHP requests exceeds proxy\_read\_timeout of 60 seconds, SLB reports 504 Gateway Timeout. For Layer-4 listeners, the timeout value is 900 seconds.

    Resolution: Make sure that the web service and related services run normally. Check if PHP requests are processed properly, and optimize the processing of PHP requests by the backend server. Take Nginx+php-fpm as an example:

    1.  The number of PHP requests being processed has reached the limit.

        If the total number of PHP requests being processed in the server has reached the limit set by max\_children in php-fpm, and more PHP requests are being sent to the server, then 502 or 504 errors may occur:

        -   If existing PHP requests in the backend server are processed timely and new PHP requests can be processed, no error occurs.
        -   If existing PHP requests are not processed timely and new PHP requests must wait to be processed, when the value of fastcgi\_read\_timeout of Nginx is exceeded, a 504 Gateway Timeout error occurs.
        -   If existing PHP requests are not processed in a timely manner and new PHP requests must wait to be processed, when the value of request\_terminate\_timeout in Nginx is exceeded, a 502 Bad Gateway error occurs.
    2.  If the PHP script execution time exceeds the limit, namely, the time used by php-fpm to process PHP scripts exceeds the value of request\_terminate\_timeout in Nginx, a 502 error occurs and the following error log is shown in Nginx logs:

        ```
        [error] 1760#0: *251777 recv() failed (104: Connection reset by peer) while reading response header from upstream, client: xxx.xxx.xxx.xxx, server: localhost, request: “GET /timeoutmore.php HTTP/1.1”, upstream: “fastcgi://127.0.0.1:9000”
        ```

    3.  The health check is performed on static pages. Errors occur when exceptions are detected in the process handling dynamic requests. For example, php-fpm is not running.
8.  The HTTP header is too long.

    An HTTP header that is too long may make SLB unable to process relevant data, resulting in 502 errors.

    Resolution: Decrease the amount of data transmitted by the header or switch to the TCP listener.

9.  The service access logic is inappropriate.

    Make sure that no backend ECS instance in SLB accesses the public IP address of SLB. If the backend server accesses its own port through the IP address of SLB, the requests may be scheduled to the server itself based on the scheduling rules of SLB. This will lead to an infinite loop, thus resulting in 500 or 502 errors for the requests.

    Resolution: Make sure that SLB is correctly used and no backend ECS instance is accessing the public IP address of SLB.


## Troubleshooting {#section_tgb_4cd_xdb .section}

-   Check the screenshot of 500, 502, or 504 error to determine the cause of the error. The cause of the error could be with SLB, Anti-DDoS or security network, or backend ECS instance configurations.
-   If Anti-DDoS or security network is used, make sure that the Layer-7 forwarding rules are correctly configured.
-   Check whether the problem occurs in all clients. If not, check whether the client indicating an error has been blocked by Alibaba Cloud Security. Also, check whether the domain name or IP address of SLB is intercepted by the service provider.
-   Check the status of SLB and whether there are any health check failures in any backend ECS instances. If so, resolve the detected health check failure.
-   Associate the service address of SLB with the IP address of the backend server by using the hosts file on the client. If a 5xx error occurs at intervals, the error is probably caused by inappropriate configurations of a backend ECS instance.
-   Change the Layer-7 SLB instance to a Layer-4 SLB instance to see whether the problem occurs again.
-   Check the performance of backend ECS servers and whether there is performance bottleneck of the CPU, memory, disk, or bandwidth.
-   If it is determined that the error is due to the backend server, check whether there are any related errors in web server logs of the backend ECS instance. Check whether the web service is running normally and whether the web access logic is correct. Test by uninstalling anti-virus software on the server and restarting the server.
-   Check whether the TCP kernel parameters of the Linux system on the backend ECS instance are correctly configured.

![](images/3349_en-US.jpg)

## Open a ticket {#section_gyl_vcd_xdb .section}

Perform the preceding troubleshooting procedures step by step and record the test results in detail. Provide the test results when you open a ticket so that the technical support can help you solve the problem as soon as possible.

If the problem persists, consult Alibaba Cloud after-sales technical support.

