# How do I perform a stress test? {#concept_lqx_1fd_xdb .concept}

## Preparations {#section_unj_cfd_xdb .section}

Before you perform a stress test, we recommend the following:

-   Use short-lived connections to test the forwarding performance of an SLB instance.
-   Enable persistent connections to test the throughput of an SLB instance.
-   Set a small timeout value, for example, five seconds, for the test tool.
-   Build a static web page on backend servers.

We also recommend the following listener configurations:

-   Do not enable session persistence.
-   Disable the health check function.
-   Use at least five clients.

## Alibaba Cloud PTS tool {#section_xnj_cfd_xdb .section}

We recommend that you use [Alibaba Cloud PTS](https://pts.aliyun.com/) as the test tool. We do not recommend Apache Bench \(ab\) because SLB returns inconsistent content lengths when multiple backend servers are tested, and Apache ab uses the content length to determine whether requests are successful. This will result in inaccurate stress test results.

## Example stress test using Alibaba Cloud PTS {#section_ynj_cfd_xdb .section}

In this example, an SLB instance has been created and added with two ECS instances as backend servers. Additionally, a TCP listener and an HTTP listener have been created, and the backend port has been set to 80. The ECS instances are configured with a single-core CPU, 512 MB memory, and CentOS 6.3 \(64-bit\). To perform a stress test, run the following commands as follows:

1.  Install Apache Web Server to provide web services.

    ```
    yum install -y httpd
    ```

2.  Initialize the default home page index.html.

    ```
    echo "testvm" > /var/www/html/index.html
    ```

3.  Start the HTTP service.

    ```
    service httpd start
    ```

4.  Visit the local port 80 to confirm that the web service is available.

    ```
    curl localhost
    ```

5.  Create a test script in PTS and confirm the following parameters are set as recommended in Preparations. Then, start the stress test.
    -   Set the timeout period to five seconds: PTS.HttpUtilities.setTimeout\(5000\)
    -   Disable persistent connections: PTS.HttpUtilities.setKeepAlive\(False\)

## Why is my Layer-7 listener performing poorly during a stress test? {#section_rnj_cfd_xdb .section}

Layer-4 Server Load Balancer \(SLB\) uses LVS \(Linux Virtual Server\) and Keepalived to provide the load balancing service, whereas Layer-7 SLB uses Tengine. In a Layer-4 listener, requests are directly sent to backend servers after being passed through LVS. However, in a Layer-7 listener, requests are sent to Tengine before they are sent to backend servers. Due to this additional step, the performance of a Layer-7 listener is inadequate when compared with a Layer-4 listener.

It may happen that a Layer-7 listener shows poor performance during a stress test. A Layer-7 listener with two ECS instances is surprisingly inferior to a Layer-4 listener with one ECS instance. Except the preceding reason regarding the process, the following situations may also cause low performance of a Layer-7 listener during a stress test:

-   Insufficient client ports

    During a stress test, an insufficient number of client ports causes connection failures. In detail, the timestamp attribute of TCP connections is erased by SLB by default. As a result, tw\_reuse of Linux protocol stack \(reuse of ports in time\_wait state\) does not work, and connections in time\_wait state accumulate.

    Solution: We recommend that you enable persistent connections on clients and use RST \(set SO\_LINGER attribute for sockets\) to close connections, instead of using FIN packets.

-   The backend server accept queue is full

    If the backend server accept queue is full, the backend server does not respond with the syn\_ack packet and the client times out.

    Solution: Run the command `sysctl -w net.core.somaxconn=1024` to change the value of net.core.somaxconn and restart the application on the backend server. The default value of net.core.somaxconn is 128.

-   Excessive connections to backend servers

    When you use a Layer-7 SLB instance, persistent connections are changed to short-lived connections after the connections pass through Tengine due to the design of the network architecture. As a result, there are too many connections sent to the backend server, which leads to poor performance of a Layer-7 SLB instance during a stress test.

-   Limitations from dependencies of backend servers

    If backend servers work normally after requests are sent to them, but the system still exhibits poor performance, it may be caused by the dependencies of the backend servers \(such as inadequate system support from the databases\).

-   Backend servers are unhealthy

    If a backend server is declared as unhealthy after health check results are received, or the health status of the server is unstable, such effects can also lead to poor performance of a Layer-7 SLB instance during a stress test.


