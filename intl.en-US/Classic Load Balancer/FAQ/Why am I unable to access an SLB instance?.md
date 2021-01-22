# Why am I unable to access an SLB instance?

This topic describes why a Server Load Balancer \(SLB\) instance fails to be accessed from a client and how to troubleshoot the issue.

**Note:** In this example, the frontend port number of the SLB instance is 80, the port number of the backend ECS instance is 80, and the internal IP address of the ECS instance is 10.11.192.1. You must configure the ports and internal IP address based on your business requirements.

|No.|Possible cause|Solution|
|---|--------------|--------|
|1|SLB cannot be accessed by backend servers. For Layer 4 SLB, an ECS instance cannot provide services for clients and function as the backend server of the SLB service at the same time.|N/A|
|2|A health check exception occurs.|For more information about how to troubleshoot health check exceptions, see [How do I troubleshoot health check exceptions of a layer-4 \(TCP/UDP\) listener?](/intl.en-US/Classic Load Balancer/FAQ/How do I troubleshoot health check exceptions of a layer-4 (TCP/UDP) listener?.md) and [How do I troubleshoot a health check exception of a Layer 7 listener \(HTTP/HTTPS\)?](/intl.en-US/Classic Load Balancer/FAQ/How do I troubleshoot a health check exception of a Layer 7 listener (HTTP/HTTPS)?.md).|
|3|SLB does not support FTP, TFTP, H.323, and SIP protocols.|-   For a Linux system, you can configure the forwarding of port 22 and use SFTP to connect and transmit data.
-   You can associate an elastic IP address \(EIP\) with an FTP server in cut-through mode to provide external FTP service. For more information, see [Deploy an FTP server by using an EIP](/intl.en-US/Best practices/Deploy an FTP server by using an EIP.md). |
|4|The internal firewall of the server does not allow traffic on port 80.|You can run the following commands to temporarily disable the firewall to perform a test. -   For a Windows server, run the following command:

`firewall.cpl`

-   For a Linux server, run the following command:

`/etc/init.d/iptables stop` |
|5|A backend port exception occurs.|-   For Layer 4 SLB, you can perform a Telnet test. If you receive a response, the backend port functions properly.

For example, you can run the following command to perform a test: `telnet 10.11.192.1 80`.

-   For Layer 7 SLB, you can check the returned HTTP status code. The status code must be a status code that indicates a normal condition, such as 200. You can use the following methods to test whether the backend port is normal:
    -   Windows: Access the internal IP address of the ECS instance to check the connectivity.

Example: `http://10.11.192.1`

    -   Linux: Run the `curl -I` command to check whether the status is `HTTP/1.1 200 OK`.

Example: `curl -I 10.11.192.1` |
|6|The rp\_filter feature conflicts with the policy-based routing mechanism of the Linux Virtual Server \(LVS\) for SLB.|1.  Log on to the ECS instance that is attached to Layer 4 SLB. The ECS instance runs a Linux system.
2.  Edit the /etc/sysctl.conf file and set the following parameters in the system configuration file to 0:

    ```
 net.ipv4.conf.default.rp_filter = 0
 net.ipv4.conf.all.rp_filter = 0
 net.ipv4.conf.eth0.rp_filter = 0
    ```

3.  Run the `sysctl -p` command to make the configurations take effect. |
|7|A listener exception occurs.|Run the following commands on the server. If you can see the listening information of 10.11.192.1:80 or 0.0.0.0: 80, the listening on the port is normal.

-   For a Windows server, run the following command:

`netstat -ano | findstr :80`

-   For a Linux server, run the following command:

`netstat -anp | grep :80` |
|8|No listeners are configured for the SLB instance.|Configure one or more listeners. For more information, see [Listener overview](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Listener overview.md).|
|9|The SLB instance cannot be accessed by using its domain name. This may be caused by an error in domain name resolution.|N/A|
|10|An exception occurs on the on-premises network of the client or the intermediate link of the service provider.|Test the connectivity on the service port of the SLB instance in different regions and network environments. If the exception occurs only when the SLB instance is accessed from the on-premises network, it can be determined that the problem is caused by a network exception. You can perform ping and MTR tests for further troubleshooting and analysis. |
|11|The client IP address is blocked by Alibaba Cloud Security.|1.  Visit `http://ip.taobao.com` in the client network environment to obtain the public IP address of the client.
2.  Add the IP address to the SLB whitelist to allow access from the IP address.

**Note:** This operation may pose security risks. Make sure that the IP addresses in the whitelist do not incur malicious attacks on SLB. |
|12|After you switch from Anti-DDoS Pro or Anti-DDoS Premium to Anti-DDoS Basic, the whitelist is not disabled.|Disable the whitelist.|
|If your problem persists, submit a ticket and provide the following information: -   The ID of the SLB instance or the IP address of the SLB instance
-   The public IP address of the client obtained when you visit `ip.taobao.com`
-   Screenshots of the client running ping and MTR tests by using the IP address of the SLB instance |

