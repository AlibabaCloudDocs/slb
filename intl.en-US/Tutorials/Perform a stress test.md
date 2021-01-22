# Perform a stress test

Layer-4 Server Load Balancer \(SLB\) uses Linux Virtual Server \(LVS\) and Keepalived to provide the load balancing service, whereas Layer-7 SLB uses Tengine.

## Overview

In a Layer-4 listener, requests are directly sent to backend servers after being passed through LVS. However, in a Layer-7 listener, requests are sent to Tengine before they are sent to backend servers. Due to this additional step, the performance of a Layer-7 listener is inadequate when compared with a Layer-4 listener.

A Layer-7 listener may show poor performance during a stress test. A Layer-7 listener connecting to two ECS instances is surprisingly inferior to a Layer-4 listener connecting to one ECS instance. Except the preceding reason regarding the process, the following situations may also cause poor performance of a Layer-7 listener during a stress test:

-   Insufficient client ports

    During a stress test, insufficient client ports cause connection failures. The timestamp attribute of TCP connections is erased by SLB by default. As a result, tw\_reuse of Linux protocol stack \(reuse of ports in time\_wait state\) does not work, and connections in the time\_wait state accumulate.

    Solution: We recommend that you enable persistent connections on clients and use RST \(set the SO\_LINGER attribute for sockets\) to close connections, instead of using FIN packets.

-   Full accept queues on the backend server

    If accept queues are full on the backend server, the backend server does not respond with syn\_ack packets and the client times out.

    Solution: Run the `sysctl -w net.core.somaxconn=1024` command to change the value of net.core.somaxconn and restart the application on the backend server. The default value of net.core.somaxconn is 128.

-   Excessive connections to the backend server

    When you use a Layer-7 SLB instance, persistent connections are changed to short-lived connections after the connections pass through Tengine due to the design of the network architecture. As a result, too many connections are sent to the backend server, which leads to poor performance of a Layer-7 SLB instance during a stress test.

-   Limits from dependencies of the backend server

    If the backend server is normal after requests are sent to the server and the system still exhibits poor performance, it may be caused by the dependencies of the backend server \(such as inadequate system support from the databases\).

-   Unhealthy status of the backend server

    If a backend server is declared as unhealthy after health check results are received, or the health status of the server is unstable, an SLB instance may has poor performance during a stress test.


## Usage notes

Before you perform a stress test, take note of the following points:

-   Use short-lived connections to test the forwarding performance of an SLB instance.

    A stress test is intended to measure the forwarding capability of SLB, in addition to session persistence and balancing capability. Therefore, we recommend that you use short-lived connections to test SLB and backend server processing capabilities. You must check the problem of insufficient client ports.

-   Enable persistent connections to test the throughput of an SLB instance.

    Set a small timeout value \(such as 5 seconds\) for the test tool. If the timeout time is too long, the test result may show an increased average response time. This makes it difficult to determine whether the proper stress test level has been reached. If the timeout time is reduced, the test result indicates the success rate, which makes it easy to determine the stress test level.

-   Build a static web page on the backend server to avoid loss caused by application logic.
-   We also recommend the following listener configurations:
    -   Disable session persistence to avoid the case where most loads are sent to a backend server.
    -   Disable health check to reduce access requests sent to the backend server.
    -   Use five or more clients to test the performance of 5,000 concurrent connections.

## Recommended test tools

We recommend that you do not use Apache Bench \(ab\).

Apache Bench applies 3s, 6s, and 9s interruptions in a progressive manner when a large number concurrent connections exist. Apache Bench uses the content length to determine whether requests are successful. SLB returns inconsistent content lengths when multiple backend servers are tested. This will result in inaccurate stress test results.

We recommend that you use Alibaba Cloud [PTS](https://www.alibabacloud.com/en?spm=5176.7946858.1280361.9.f6fc572dDmyxFF).

PTS allows a great number of concurrent connections. PTS allocates public IP addresses from all over the country, so that the pressure sources are scattered. PTS also integrates Cloud Monitor to view all end-to-end performance data in real time.

## An stress test example

In this example, an SLB instance is created and two ECS instances are added as backend servers. A TCP listener and an HTTP listener are created. The backend port is 80. The ECS instances use 1 vCPU, 512 MiB memory, and CentOS 6.3 \(64-bit\) operating system. Perform the following operations:

1.  Install Apache Web Server to provide web services.

    ```
    yum install -y httpd
    ```

2.  Initialize the default homepage index.html.

    ```
    echo "testvm" > /var/www/html/index.html
    ```

3.  Start the HTTP service.

    ```
    service httpd start
    ```

4.  Access the local port 80 to confirm that the web services are available.

    ```
    curl localhost
    ```

5.  Create a test script in PTS and start the stress test.

