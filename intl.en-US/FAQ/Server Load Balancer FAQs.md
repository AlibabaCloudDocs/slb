# Server Load Balancer FAQs {#concept_a4t_1h5_vdb .concept}

-   [Does SLB support HTTP redirection?](#section_qz5_435_vdb)
-   [If I disable NIC, will my SLB service be affected?](#section_wmt_w3x_wdb)
-   [Why are my connections unable to reach the peak bandwidth value?](#section_ggl_fjx_wdb)
-   [What are the timeout values of each listener?](#section_aw5_jlx_wdb)
-   [Why does my SLB connection time out?](reseller.en-US/FAQ/Server Load Balancer FAQs.md#section_hkn_mlx_wdb)
-   [Why does session persistence sometimes fail?](#section_ys4_bwy_bgb)
-   [How can I view the session persistence string?](#section_ysp_1jy_wdb)
-   [How can I test session persistence by using Linux curl?](#section_m2j_3jy_wdb)
-   [If I disconnect my client from SLB before I receive a response from the backend servers, will SLB disconnect from the backend servers?](reseller.en-US/FAQ/Server Load Balancer FAQs.md#section_cw5_pyx_wdb)

## Does SLB support HTTP redirection? {#section_qz5_435_vdb .section}

Yes.

SLB supports redirecting HTTP to HTTPS. For more information, see [Redirect HTTP to HTTPS](../../../../reseller.en-US/Archives/User Guide (Old Console)/Listener/Layer-7 listeners/Redirect HTTP to HTTPS.md#).

## If I disable NIC, will my SLB service be affected? {#section_wmt_w3x_wdb .section}

If the ECS instance has configured a public IP address, disabling the Internet NIC will impact the load balancing service.

The traffic goes through the Internet NIC if the backend ECS is configured with a public IP address. When the Internet NIC is disabled, the returned data packet cannot be sent. We recommend that you do not disable the Internet NIC. But if you have to, you can modify the default route to intranet to avoid the impact on the service. However, you need to consider whether the business is Internet-dependent, such as accessing RDS through the Internet.

## Why are my connections unable to reach the peak bandwidth value? {#section_ggl_fjx_wdb .section}

Because the SLB is deployed in cluster to provide the load balancing service, all requests are distributed evenly on the SLB system servers. Similarly, the specified bandwidth is also evenly distributed to these servers.

The calculation method of the traffic ceiling for a single connection download is: single connection download peak = the configured total bandwidth of Server Load Balancer / \(N-1\). N represents the number of traffic forwarding groups, and the current value is 4. For example, if you have set the bandwidth ceiling to 10 MB in the console, the maximum traffic for downloading of each client is 10/\(4-1\), or 3.33 MB.

Considering the implementation principles of Server Load Balancer, we recommend that you set a reasonable bandwidth peak value for a single listener based on your business conditions and implementation modes to eliminate negative impact and limitations on your external services.

## What are the timeout values of each listener? {#section_aw5_jlx_wdb .section}

-   TCP listener: 900 seconds
-   UDP listener: 90 seconds
-   HTTP listener: 60 seconds
-   HTTPS listener: 60 seconds

## Why does my SLB connection time out? {#section_hkn_mlx_wdb .section}

From the server side, the following situations may cause the connection timeout:

-   The IP address of the SLB instance is protected

    Such as the blackholing and scrubbing, as well as WAF protection.

-   Insufficient client ports

    Lack of client ports may lead to connection failure especially in the stress test. The SLB erases the timestamp attribute of the TCP connection. Therefore, the tw\_reuse parameter does not work and the time\_wait state connection heap causes the lack of the client ports.

    Solution: Do not enable TCP Keepalive for the clients and use the RST packet instead of FIN packet to terminate the connection.

-   The accept queue of the backend server is full

    If the accept queue of the backend server is full, the backend server cannot sent the SYN\_ACK packet. Therefore, the connection times out.

    Resolution: The default value of net.core.somaxconn is 128. Run the `sysctl -w net.core.somaxconn=1024` command to change its value and restart applications on the backend servers.

-   Access the Layer-4 load balancing service from the backend servers

    For the Layer-4 load balancing service, the connection fails if you access the service from a backend server.

-   Improper RST configuration

    If no data is transferred within 900 seconds after the TCP connection is established on the SLB, the system will send the RST packet to the client and the backend server to terminate the connection. If the RST configuration is not correct on the backend server, the backend server may send data to a closed connection, which leads to connection timeout.


## Why does session persistence sometimes fail? {#section_ys4_bwy_bgb .section}

Possible causes for session persistence failure, and corresponding solutions, are described as follows:

-   Make sure that you have enabled session persistence.
-   HTTP/HTTPS listeners cannot insert the cookies needed for session persistence into the 4xx code messages returned by backend servers.

    Solution: Change HTTP/HTTPS listeners to TCP listeners. Session persistence in TCP listeners is based on source client IP addresses, which means cookies can be inserted in backend servers.

-   An HTTP 302 redirect changes the SERVERID string in the session persistence.

    When SLB inserts cookies to backend ECS instances, if the HTTP status code 302 redirect is returned by ECS instances, the SERVERID string in session persistence will be changed, resulting in session persistence failure.

    To verify the cause, check the requests and responses in your browser or by using packet checking software. Then, check whether a 302 code is included in the packets and whether the SERVERID string in the cookie is changed.

    Solution: Use TCP listeners. Session persistence in TCP listeners is based on source client IP addresses, which means cookies can be inserted into backend servers.

-   The timeout period is too short. You need to modify the timeout period to a greater value.

## How can I view the session persistence string? {#section_ysp_1jy_wdb .section}

You can press F12 in your browser to check whether the SERVERID string or any keywords that you specified are included in the response message. Alternatively, you can run `curl www.xxx.com -c /tmp/cookie123` to save the cookie and then run `curl www.xxx.com -b /tmp/cookie123` to visit the cookie.

## How can I test session persistence by using Linux curl? {#section_m2j_3jy_wdb .section}

1.  Create a test page.

    Create a test page on each of the backend ECS instances and make sure that the intranet IP address of the server is displayed on the test page. The following figure shows an example of a test page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4290/15561990883296_en-US.png)

2.  Test using curl.

    In this example, the IP address of the SLB instance running Linux is 1.1.1.1 and the URL of the created page is [http://1.1.1.1/check.jsp](http://1.1.1.1/check.jsp).

    1.  Log on to the Linux server used for the test.
    2.  Run the following command to check the value of the cookie inserted in the server.

        ```
        curl -c test.cookie http://1.1.1.1/check.jsp
        ```

        **Note:** By default, SLB maintains session persistence by inserting cookies. However, curl does not save or send any cookies. Therefore, you must save the corresponding cookie first. Otherwise, the curl test result may mistakenly determine that session persistence has failed.

    3.  Run the following command to continue the test.

        ```
        for ((a=1;a<=30;a++)); 2="" do="" curl="" -b="" 1.cookie=""
                    check.jsp="">/dev/null | grep '10.170.*';sleep 1; done`
        ```

        **Note:** In `a<=30`, `30` is the number of repeated tests and can be changed to your required testing number. In `grep ‘10.170.*’`, `10.170.*` is the IP address to be searched and you can change it to the intranet IP address of your server.

    4.  Check the IP addresses returned by the preceding tests. If they are the same address, then session persistence is working. If the addresses are different, session persistence has failed.

## If I disconnect my client from SLB before I receive a response from the backend servers, will SLB disconnect from the backend servers? {#section_cw5_pyx_wdb .section}

No. SLB does not disconnect from backend servers during read/write operations.

