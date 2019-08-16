# Troubleshoot a health check exception of a Layer-7 listener \(HTTP/HTTPS\) {#task_o13_vjz_xfb .task}

The health check function is used to determine whether your backend servers are normal. If a health check exception occurs, it generally means that your backend server is abnormal. The exception may also be caused by incorrect health check configurations. This topic describes how to troubleshoot a health check exception of a Layer-7 \(HTTP/HTTPS\) listener.

1.  Ensure that the backend server does not block the CIDR block 100.64.0.0/10 through iptables or other third-party firewalls or security software. 

    The SLB instance communicates with backend servers by using IP addresses in the reserved CIDR block 100.64.0.0/10. If the CIDR block is blocked, a health check exception occurs and the SLB instance cannot work normally.

2.  Access the HTTP service on the backend server from the backend server to ensure that the HTTP service works normally. 
    1.  Log on to the SLB console and click the ID of the target SLB instance. On the Listeners tab page, click Configure in the Actions column of the target listener. Then you can view the health check configurations. 

        In this example, an HTTP listener is used and the intranet IP of the backend server with the health check exception is 10.0.0.2. Other health check configurations are as follows:

        -   **Health Check Port**: 80
        -   **Health Check Domain Name**: `www.slb-test.com`
        -   **Health Check Path**: `/test.html`
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65042/156594093933076_en-US.png)

    2.  The following example uses a Linux environment. Run the nc or curl command to test the HTTP service on the backend server. Ensure that the configurations of health check path, health check port, and health check domain name are the same for the HTTP service and the backend server. Otherwise, a health check exception occurs. In this example, the nc command is used. Configure the health check path, health check domain name, internet IP address, and health check port according to your actual situation.

        ``` {#codeblock_lvt_kt6_08k}
        echo -e "HEAD /test.html HTTP/1.0\r\nHost: www.slb-test.com\r\n\r\n" | nc -t 172.17.58.131 80
        ```

        -   In normal conditions, `200` or `2xx/3xx` is returned, as shown in the following figure.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65042/156594093933084_en-US.png)

        -   Exception example: Assume you do not change the listener configurations of the SLB instance but delete the /test.html page on the backend server. Then, when you run the nc command, the error code 404, instead of 2xx or 3xx, is returned, indicating a health check exception has occurred, as shown in the following figure.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65042/156594093933092_en-US.png)


