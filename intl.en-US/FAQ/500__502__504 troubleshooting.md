# 500/502/504 troubleshooting {#concept_lqf_v1d_xdb .concept}

After an SLB instance is configured, errors such as 500 Internal Server Error, 502 Bad Gateway and 504 Gateway Timeout may occur. They can be caused by the blockage of the service provider, Alibaba Cloud blockage caused by abnormal client activities, wrong configurations of the SLB instance, health check failure, failure in accessing web applications on the backend ECS instances and more.

This document lists the causes, resolutions and troubleshooting steps of these problems.

1.  [Potential causes and resolutions](#ol_srv_w1d_xdb)
    -   [The source site domain name is not put on record or it is not configured with any Layer-7 forwarding rule in Anti-DDoS Pro or security network.](#1)
    -   [The source IP address of the client is blocked by Alibaba Cloud Security](#2)
    -   [The source IP address is blocked by the security protection software of the backend ECS instance](#3)
    -   [Parameter error of the Linux kernel of the backend ECS instance](#4)
    -   [Performance bottleneck of the backend ECS instance](#5)
    -   [SLB reports 502 error due to health check failure](#6)
    -   [The health check is normal but the web application reports 502 error](#7)
    -   [The HTTP header is too long](#8)
2.  [Troubleshooting](#section_tgb_4cd_xdb)
3.  [Open a ticket](#section_gyl_vcd_xdb)

## Potential causes and resolutions {#section_xrv_w1d_xdb .section}

1.  The source site domain name is not put on record or it is not configured with any Layer-7 forwarding rule in Anti-DDoS Pro.

    Resolution: Put the domain name on record. If the SLB instance is in Anti-DDoS Pro or security network, configure corresponding domain name rules.

2.  The source IP address of the client is intercepted by Alibaba Cloud Security

    Test if the problem occurs to clients of other carriers. If not, the problem is generally caused by the blockage of the service provider.

    Resolution: Open a ticket to Alibaba Cloud after-sales personnel who decides if there is blockage through packet capture. If so, contact the service provider to solve the problem.

3.  Blocked by the security protection software of the backend ECS instance

    100.64.0.0/10（100.64.0.0/10 is reserved by Alibaba Cloud, and will not be used by any user, there is no security risk \)The IP address belongs to the IP address range of the SLB server and is mainly used for health check and request forwarding. If security software or a firewall inside the system is installed, add the IP address to the whitelist to avoid 500 or 502 error.

    Resolution: Configure a whitelist for antivirus or firewall software, or unload the software to perform quick test.

4.  Parameter error of the Linux kernel of the backend ECS instance

    If the backend ECS instance is using the Linux system, disable the rp\_filter feature in system kernel parameters when changing the Layer-7 listener to a Layer-4 listener.

    Set the values of the following parameters in the system configuration file /etc/sysctl.conf to zero, and then run `sysctl -P`.

    ```
     net.ipv4.conf.default.rp_filter = 0
     net.ipv4.conf.all.rp_filter = 0
     net.ipv4.conf.eth0.rp_filter = 0
    ```

5.  Performance bottleneck of the backend ECS instance

    High CPU utilization or no extra bandwidth may cause access exceptions.

    Resolution: Check the performance of the backend ECS instance to solve performance bottlenecks. If the overall system capacity is insufficient, you can increase the number of backend ECS instances.

6.  SLB reports 502 error due to health check failure

    For more information, see [Resolve health check failures](reseller.en-US/Miscellaneous/Troubleshooting/Troubleshoot ECS instance exceptions.md#).

    Besides, 502 error also occurs if the health check function of SLB is disabled and the web service in the backend server cannot process HTTP requests.

7.  The health check is normal but the web application reports 502 errors

    The 502 Bad Gateway error message indicates that SLB can forward requests from the client to the backend servers, but the web application in the backend ECS instance cannot process the requests. Therefore, you must check the configurations and running status of the web application in the backend server. For example, the time used by the web application to process HTTP requests exceeds the timeout value of SLB. For Layer-7 listeners, if the time used by the backend server to process PHP requests exceeds the proxy\_read\_timeout of 60 seconds, SLB reports 504 Gateway Time-out. For Layer-4 listeners, the timeout value is 900 seconds.

    Resolution: Make sure that the web service and related services run normally. Check if PHP requests are processed properly, and optimize the processing of PHP requests by the backend server. Take Nginx+php-fpm as an example:

    1.  The number of PHP requests being processed has reached the limit.

        If the total number of PHP requests being processed in the server has reached the limit set by max\_children in php-fpm, and more PHP requests are being sent to the server, then 502 or 504 errors may occur:

        -   If existing PHP requests in the backend server are processed timely and new PHP requests can be processed successively, no error occurs.
        -   If the existing PHP requests are not processed timely and new PHP requests remain in a waiting mode, when the value of fastcgi\_read\_timeout of Nginx is exceeded, a 504 Gateway timeout error occurs.
        -   If the existing PHP requests are not processed in a timely manner and new PHP requests remain in a waiting mode, when the value of request\_terminate\_timeout in Nginx is exceeded, a 502 Bad Gateway error occurs.
    2.  If the PHP script execution time exceeds the limit, namely, the time used by php-fpm to process PHP scripts exceeds the value of request\_terminate\_timeout in Nginx, a 502 error occurs and the following error log is shown in Nginx logs:

        ```
        [error] 1760#0: *251777 recv() failed (104: Connection reset by peer) while reading response header from upstream, client: xxx.xxx.xxx.xxx, server: localhost, request: “GET /timeoutmore.php HTTP/1.1”, upstream: “fastcgi://127.0.0.1:9000”
        ```

    3.  The health check is performed on static pages. Errors occur when exceptions are detected in the process handling dynamic requests. For example, php-fpm is not running.
8.  The HTTP header is too long

    An HTTP header that is too long may make SLB unable to process relevant data, resulting in 502 errors.

    Resolution: Decrease the amount of data transmitted by the header or change the Layer-7 listener to a Layer-4 listener.

9.  Problem of service access logic

    Make sure that no backend ECS instance in SLB accesses the public IP of SLB. When the backend server accesses its own port through the IP address of SLB, the requests may be scheduled to the server itself based on the scheduling rules of SLB. This will lead to an infinite loop, thus resulting in 500 or 502 error for the requests.

    Resolution: Make sure SLB is correctly used and that no backend ECS instance is accessing the public IP of SLB.


## Troubleshooting {#section_tgb_4cd_xdb .section}

-   Check the screenshot of 500/502/504 error to determine the cause of the error. The cause of the error could be with SLB, Anti-DDoS or security network, or backend ECS instance configurations.
-   If Anti-DDoS or security network is used, make sure that the Layer-7 forwarding rules are correctly configured.
-   Check whether the problem occurs in all clients. If not, check whether the client indicating an error has been blocked by Alibaba Cloud Security. Also, check whether the domain name or IP of SLB is intercepted by the service provider.
-   Check the status of SLB and whether there are any health check failures in any backend ECS instances. If so, resolve the detected health check failure.
-   Bind the service address of SLB to the IP address of the backend server by using the hosts file on the client. If a 5XX error occurs at intervals, it is possible that a backend ECS server is not correctly configured.
-   Change the Layer-7 SLB instance to a Layer-4 SLB instance to see whether the problem occurs again.
-   Check the performance of backend ECS servers and whether there is performance bottleneck of the CPU, memory, disk, or bandwidth.
-   If it is determined that the error is due to the backend server, check whether there are any related errors in web server logs of the backend ECS instance. Check whether the web service is running normally and whether the web access logic is correct. Test by uninstalling anti-virus software on the server and restarting the server.
-   Check whether the TCP kernel parameters of the Linux system on the backend ECS instance are correctly configured.

## Open a ticket {#section_gyl_vcd_xdb .section}

Perform the troubleshooting procedures step by step and record the test results in detail. Provide the test results when you open the ticket so that our after-sales technical support can help you solve the problem as soon as possible.

If the problem persists, contact Alibaba Cloud after-sales technical support.

