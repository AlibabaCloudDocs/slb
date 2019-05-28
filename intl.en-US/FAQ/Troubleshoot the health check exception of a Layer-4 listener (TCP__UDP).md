# Troubleshoot the health check exception of a Layer-4 listener \(TCP/UDP\) {#task_j5n_rgz_xfb .task}

The health check function is used to determine whether your backend servers are normal. When a health check exception occurs, it generally means that your backend server is abnormal. The exception may also be caused by incorrect health check configurations. This topic describes how to troubleshoot a health check exception of a Layer-4 \(TCP/UDP\) listener.

1.  Ensure that the backend server does not block the CIDR block 100.64.0.0/10 through iptables or other third-party firewalls or security software. 

    The SLB instance communicates with backend servers by using IP addresses in the reserved CIDR block 100.64.0.0/10. If the CIDR block is blocked, a health check exception occurs and the SLB instance cannot work normally.

2.  Run the telnet command to test the backend server. 
    1.  Log on to the SLB console and click the ID of the target SLB instance. On the **Listeners** tab page, click **Configure** in the **Actions** column of the target listener. Then you can view the health check configurations. 

        By default, the port of the backend server is used as the **Health Check Port**. You can also set the port manually. In this example, the port of the backend server, namely port 80, is used.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65040/155905290333070_en-US.png)

    2.  Run the following command to connect to the health check port. The health check port configured on the SLB instance must be the same as the listening port on the backend server. 

        `telnet 172.17.58.131 80`

        In this example, 172.17.58.131 is the intranet IP address of the backend server, and 80 is the health check port. By default, the port of the backend server is used as the health check port. You can configure the health check port according to your actual situation.

        -   In normal conditions, `Connected to xxx.xxx.xxx.xxx` is returned. This indicates that the port on the backend server is working \(listening\) normally and the health check is normal, as shown in the following figure.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65040/155905290333071_en-US.png)

        -   Exception example: Assume you do not change the listener configurations of the SLB instance but stop the listening process of port 80 on the backend server. Then, if you run the telnet command, the system prompts that the host cannot be connected. This means that the health check exception occurs if the listening process of port 80 stops, as shown in the following figure.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65040/155905290333072_en-US.png)

3.  Layer-4 listeners also support HTTP health checks. To use HTTP health checks, see [Troubleshoot a health check exception of a Layer-7 listener \(HTTP/HTTPS\)](reseller.en-US/FAQ/Troubleshoot a health check exception of a Layer-7 listener (HTTP__HTTPS).md#). The method for troubleshooting HTTP health check exceptions is the same for Layer-4 listeners and Layer-7 listeners.

