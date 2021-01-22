# FAQ about SLB

The following questions about Server Load Balancer \(SLB\) are frequently asked:

-   [Does SLB support HTTP redirection?](#section_qz5_435_vdb)
-   [If I disable the public NIC, is my SLB service affected?](#section_wmt_w3x_wdb)
-   [Why are my connections unable to reach their peak bandwidth value?](#section_ggl_fjx_wdb)
-   [What is the connection timeout value of each listener?](#section_aw5_jlx_wdb)
-   [Why does my connection to an SLB instance time out?](#section_hkn_mlx_wdb)
-   [Why does session persistence sometimes fail?](#section_ys4_bwy_bgb)
-   [How do I view the session persistence string?](#section_ysp_1jy_wdb)
-   [How do I test session persistence by using the Linux curl command?](#section_m2j_3jy_wdb)
-   [If I disconnect my client from an SLB instance before I receive a response from the backend servers, does the SLB instance disconnect from the backend servers?](#section_cw5_pyx_wdb)

## Does SLB support HTTP redirection?

Yes, SLB supports HTTP redirection.

For more information, see [Redirect HTTP requests to HTTPS](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Redirect HTTP requests to HTTPS.md).

## If I disable the public NIC, is my SLB service affected?

If the ECS instance is configured with a public IP address, the SLB service is affected if you disable the public NIC.

By default, traffic goes through the public NIC if the backend ECS instance is configured with a public IP address. If the public NIC is disabled, no packets are returned. We recommend that you do not disable the public NIC. However, if it is necessary, you can mitigate impacts on the service by directing the default route to the internal network. You must consider whether your service is Internet-dependent, such as whether ApsaraDB RDS instances need to be accessed over the Internet.

## Why are my connections unable to reach their peak bandwidth value?

SLB instances provide services based on SLB server clusters. All external requests are evenly distributed to SLB system servers. Therefore, the specified peak bandwidth is also evenly distributed to these servers.

The maximum download bandwidth per connection is calculated based on the following formula: Maximum download bandwidth per connection = Specified peak bandwidth of the SLB instance/\(N - 1\). N indicates the number of traffic forwarding groups. Set N to 4. For example, if you set the peak bandwidth to 10 Mbit/s in the SLB console, the maximum download bandwidth value of each client is 10/\(4 - 1\), which equals 3.33 Mbit/s.

We recommend that you set the peak bandwidth value for a single listener based on your service conditions and application modes to avoid impacts on your service.

## What is the connection timeout value of each listener?

-   TCP listener: 900 seconds
-   UDP listener: 90 seconds
-   HTTP listener: 60 seconds
-   HTTPS listener: 60 seconds

## Why does my connection to an SLB instance time out?

This problem may be caused by one of the following reasons:

-   The IP address of the SLB instance is blocked for security reasons.

    The IP address of the SLB instance may be blocked due to traffic blackholing and scrubbing or WAF protection. WAF offers protection by sending RST packets to both the client and the server after a connection is established.

-   The client ports are insufficient.

    Insufficient client ports may lead to connection failures especially in stress tests. By default, SLB erases the timestamp attribute of TCP connections. As a result, tw\_reuse of the Linux protocol stack \(reuse of ports in time\_wait state\) does not work, and connections in time\_wait state accumulate, which results in a lack of client ports.

    Solution: We recommend that you enable persistent connections on clients and use RST packets instead of FIN packets to terminate connections. In this case, you can set the SO\_LINGER socket option.

-   The accept queue of a backend server is full.

    If the accept queue of a backend server is full, the backend server does not respond with the syn\_ack packet and the client times out.

    Solution: Run the `sysctl -w net.core.somaxconn=1024` command to change the value of net.core.somaxconn and restart the application on the backend server. The default value of net.core.somaxconn is 128.

-   The Layer 4 SLB service is accessed from backend servers.

    If you access the Layer 4 SLB service from a backend server, the connection fails. For example, the service is accessed from a backend server by using a concatenated URL.

-   The RST is improperly configured.

    If no data is transferred within 900 seconds after a TCP connection is established on an SLB instance, the SLB instance sends the RST packet to the client and the backend server to terminate the connection. If the RST configuration is incorrect on the backend server, the backend server may send data to the closed connection, which leads to a connection timeout.


## Why does session persistence sometimes fail?

-   Make sure that you have enabled session persistence.
-   HTTP or HTTPS listeners cannot insert the cookies needed for session persistence into the 4xx code messages returned by backend servers.

    Solution: Change HTTP or HTTPS listeners to TCP listeners. TCP listeners implement session persistence based on source client IP addresses. Cookies can be inserted into backend servers and validated to ensure session persistence.

-   An HTTP 302 redirection changes the SERVERID string for session persistence.

    When SLB inserts a cookie into the response of a backend server and the HTTP status code 302 is returned by the backend server, the SERVERID string for session persistence is changed. This results in a session persistence failure.

    To verify the cause, check the requests and responses by using your browser or packet capture software. Then, check whether a 302 code is included in the packets and whether the SERVERID string in the cookie is changed.

    Solution: Change HTTP or HTTPS listeners to TCP listeners. TCP listeners implement session persistence based on source client IP addresses. Cookies can be inserted into backend servers and validated to ensure session persistence.

-   The timeout period is set to a small value. You can modify the timeout period to a greater value.

## How do I view the session persistence string?

You can press F12 in your browser to check whether the SERVERID string or any keywords that you specified are included in the response message. Alternatively, you can run the `curl www.xxx.com -c /tmp/cookie123` command to save a cookie and then run the `curl www.xxx.com -b /tmp/cookie123` command to visit the cookie.

## How do I test session persistence by using the Linux curl command?

1.  Create a test page.

    Create a test page on each of the backend servers and make sure that the internal IP address of the backend server is displayed on the test page. The following figure shows an example of a test page. The internal IP address is used to verify the backend server to which client requests are distributed. You can check whether the internal IP addresses are the same to determine whether session persistence works.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8553598951/p3296.png)

2.  Perform a test by using the curl command in Linux.

    In this example, the IP address of the SLB instance that runs Linux is 1.1.1.1 and the URL of the created page is [http://1.1.1.1/check.jsp](http://1.1.1.1/check.jsp).

    1.  Log on to the Linux server used for the test.
    2.  Run the following command to save the cookies of the test server:

        ```
        curl -c test.cookie http://1.1.1.1/check.jsp
        ```

        **Note:** By default, SLB maintains session persistence by inserting cookies. However, curl does not save or send any cookies. Therefore, you must save the corresponding cookies first. Otherwise, the curl test result may mistakenly determine that session persistence has failed.

    3.  Run the following command to continue the test:

        ```
        for ((a=1;a<=30;a++)); 2="" do="" curl="" -b="" 1.cookie=""
                    check.jsp="">/dev/null | grep '10.170.*';sleep 1; done`
        ```

        **Note:** In a<=30, 30 is the number of repeated tests and can be changed to your required number. In grep '10.170.\*', 10.170. \* is the IP address to be filtered out. You can change it to the internal IP address of a backend ECS instance.

    4.  Check the IP addresses returned by the preceding tests. If they are the same address, session persistence is working. If the addresses are different, session persistence has failed.

## If I disconnect my client from an SLB instance before I receive a response from the backend servers, does the SLB instance disconnect from the backend servers?

No, the SLB instance does not disconnect from the backend servers during read/write operations.

