# How do I troubleshoot a health check exception of a Layer 7 listener \(HTTP/HTTPS\)?

The health check feature is used to determine whether your backend servers are normal. If a health check exception occurs, a backend server is typically abnormal. The exception may also be caused by incorrect health check configurations. This topic describes how to troubleshoot a health check exception of a Layer 7 \(HTTP/HTTPS\) listener.

1.  Make sure that the backend server does not block the CIDR block 100.64.0.0/10 through iptables or other third-party firewalls or security software.

    Server Load Balancer \(SLB\) communicates with backend servers by using IP addresses in the reserved CIDR block 100.64.0.0/10. If the CIDR block is blocked, health check exceptions occur and SLB cannot work normally.

2.  Access the HTTP service on the backend server from the backend server to ensure that the HTTP service works normally.

    1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou/slbs) and check the health check configurations on the listener details page.

        In this example, an HTTP listener is used and the internal IP address of the backend server with the health check exception is 10.0.0.2. The following section describes other health check configurations.

        -   **Health Check Port:** 80
        -   **Health Check Domain Name**: `www.slb-test.com`
        -   **Health Check Path**: `/test.html`
        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1100149751/p33076.png)

    2.  For a Linux server, run the nc or curl command to test the HTTP service on the backend server. Make sure that the configurations of the health check path, health check port, and health check domain name are the same for the HTTP service and the backend server. Otherwise, a health check exception occurs.

        In this example, the nc command is used. Configure the health check path, health check domain name, public IP address, and health check port according to your actual situation.

        ```
        echo -e "HEAD /test.html HTTP/1.0\r\nHost: www.slb-test.com\r\n\r\n" | nc -t 172.17.58.131 80
        ```

        -   In normal conditions, the `200` or `2xx/3xx` status codes are returned, as shown in the following figure:

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1100149751/p33084.png)

        -   Assume that you do not change the listener configurations of the SLB instance but delete the /test.html page from the backend server. Then, when you run the nc command the error code 404, instead of 2xx or 3xx, is returned as shown in the following figure. This error code indicates a health check exception.

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1100149751/p33092.png)


