# Why am I unable to access the SLB instance? {#concept_wzy_kyc_xdb .concept}

This tutorial describes the causes for why the client cannot access an SLB instance and the troubleshooting methods.

**Note:** In this example, the frontend port of the SLB instance is 80, the backend port of the ECS instance is 80, and the intranet IP address of the ECS instance is 10.11.192.1. You must configure the port and intranet IP address according to your actual situation.

|No.|Causes|Resolutions|
|---|------|-----------|
|1|For Layer-4 SLB service, a backend ECS instance cannot directly provide service for clients and function as the backend server of the SLB service at the same time.|-|
|2|Health check exception.|For more information, see [Troubleshoot the health check exception of a Layer-4 listener \(TCP/UDP\)](intl.en-US/FAQ/Troubleshoot the health check exception of a Layer-4 listener (TCP__UDP).md#) and [Troubleshoot a health check exception of a Layer-7 listener \(HTTP/HTTPS\)](intl.en-US/FAQ/Troubleshoot a health check exception of a Layer-7 listener (HTTP__HTTPS).md#).|
|3|Using FTP, tftp, h323, sip and related protocols through SLB is not supported.| -   For a Linux system, you can configure the forwarding of Port 22 and use sftp to connect and transmit data.
-   You can attach an EIP to an FTP server to provide external FTP service through the EIP cut-through mode.

 |
|4|The intranet firewall of the server does not allow Port 80.|You can run the following commands to temporarily disable the firewall.-   For a Windows server, run:

`firewall.cpl`

-   For a Linux server, run:

`/etc/init.d/iptables stop`


|
|5|Backend port exception.| -   For Layer-4 SLB service, the backend port is normal if you receive a response after performing the telnet test.

Example: Use `telnet 10.11.192.1 80` to test.

-   For Layer-7 SLB service, the HTTP status code must be a status code that indicates a normal condition, such as 200. The test methods are as follows:
    -   Windows: Access the intranet IP address of the ECS instance directly from the ECS instance to check if access is normal.

Example: `http://10.11.192.1` 

    -   Linux: Use the `curl -I` command to check if the status is `HTTP/1.1 200 OK`.

Example: `curl -I 10.11.192.1`


 |
|6|The rp\_filter feature conflicts with the policy route of the bottom-layer LVS of SLB.| 1.  Log on to the ECS instance of the Linux system added to the SLB.
2.  Edit the /etc/sysctl.conf file and set the following three parameters in the system configuration file to 0.

    ```
 net.ipv4.conf.default.rp_filter = 0
 net.ipv4.conf.all.rp_filter = 0
 net.ipv4.conf.eth0.rp_filter = 0
    ```

3.  Run the `sysctl -p` command to make the configurations take effect.

 |
|7|Listener exception| Run the following command on the server. If you can see the monitoring information of 10.1.1.192.1: 80, or the monitoring information of 0.0.0.0: 80, the listening function of the ports is normal.

-   For a Windows server, run:

`netstat -ano | findstr :80`

-   For a Linux server, run:

`netstat -anp | grep :80`


 |
|8|No listener is added to the SLB instance.|Configure a listener. For more information, see [Configure a listener](../../../../../intl.en-US/Archives/User Guide (Old Console)/Listener/Listeners overview.md#).|
|9|The SLB cannot be accessed through the domain name. Therefore, an error may occur in domain name resolution.|-|
|10|Exception of the local network of the client or exception of the intermediate link of the service provider.|Perform access tests on the service port of SLB in different regions and network environments.If the exception only occurs when it is accessed from the local network, the problem is caused by a network exception. In this case, you can do further troubleshooting and analysis through ongoing ping tests or MTR route tracing.

|
|11|The client IP address is blocked by Alibaba Cloud Security.| 1.  Visit `http://ip.taobao.com` in the network environment of the client to obtain the public IP of the client network.
2.  Add the IP address to the SLB whitelist to allow access from the IP address.

**Note:** This operation may pose security risks. Ensure that the IP does not launch malicious attacks on the SLB.


 |
|12|When the SLB returns to Anti-DDoS Basic after using Anti-DDoS Pro, the whitelist is not disabled.|Disable the ACL whitelist.|
|If the problem persists, open a ticket and submit the following details so that we can help you solve the problem more efficiently:-   The ID of the SLB instance or the IP address of the SLB service.
-   The public IP of the client obtained when you visit `ip.taobao.com`.
-   Screenshots of ping and MTR route tracing tests performed by the client using the IP address of the SLB service.

|

