# Troubleshoot ECS instance exceptions {#concept_u5c_f2d_xdb .concept}

After you enable health check of Server Load Balancer, when one backend ECS instance is declared as unhealthy, requests are forwarded to other normal ECS instances. When the faulty ECS instance becomes normal, Server Load Balancer forwards requests to the ECS instance again.

For Layer-7 SLB service, when an ECS instance is declared as unhealthy, you can troubleshoot the ECS instance from the following aspects:

-   Make sure you can directly access your service through the ECS instance.
-   Ensure the backend port you configured in the listener is opened on the backend server.
-   Check whether the backend ECS instance has installed a firewall or other security protection software. This type of software may easily block the local IP address of the Server Load Balancer service, and thus disable the communication between the Server Load Balancer service and the backend server.
-   Check whether the Server Load Balancer health check parameters are correctly set. We recommend that you use default health check parameters.
-   We recommend that you use a static page for health check. If the page you use for health check isn't the default homepage of the backend ECS instance, you must enter the URL of the health check page in health check configurations. We recommend that you use simple html page for health check and the page is only used for checking the response. We do not recommend that you use dynamic scripting languages such as php.
-   Check whether the backend ECS instance has high loads, which slow the ECS instance's response in offering services.

Besides, because the Layer-7 SLB service communicates with the backend ECS instance through intranet, the ECS instance must listen intranet or all-network ports. You can check the ECS instance using the following methods:

1.  Check whether the listening function is normal.

    If the frontend port is 80 and the backend port is 80, the intranet IP of the ECS instance is 10.11.192.1. Run the following command on the server. If you can see the monitoring information of 10.1.1.192.1: 80, or the monitoring information of 0.5.0.0: 80, the listening function of the ports is normal.

    -   Run the following command on the Windows server: `netstat -ano | findstr :80`
    -   Run the following command on the Linux server: `netstat -anp | grep :80`
2.  Check whether the intranet firewall of the server allows port 80. You can disable the firewall temporarily to do the test. Enter the following command to disable the firewall.
    -   Windows: `firewall.cpl`
    -   Linux: `/etc/init.d/iptables stop`
3.  Check whether the backend port is normal.
    -   For Layer-4 SLB service, the backend port is normal if you receive response after performing the telnet test. In this tutorial, use `telnet 10.11.192.1 80` to do the test.
    -   For Layer-7 SLB service, the HTTP status code must be a status code that indicates a normal condition, such as 200. The test methods are as follows:
        -   Windows: Directly access the intranet IP of the ECS instance. In this tutorial, access [http://10.11.192.1](http://10.11.192.1/).
        -   Linux: Use the `curl -I` command to check if the status is HTTP/1.1 200 OK. In this tutorial, use `curl -I 10.11.192.1`.

