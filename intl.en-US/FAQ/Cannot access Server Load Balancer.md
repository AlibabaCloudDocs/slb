# Cannot access Server Load Balancer {#concept_wzy_kyc_xdb .concept}

When the client cannot access Server Load Balancer, the possible reasons and resolutions are as follows:

1.  If you haven't added any listener to the SLB instance, you can't successfully ping the endpoint of the SLB instance.

    Resolution: Configure listeners. For more information, see [Configure listeners](../../../../reseller.en-US/Archives/User Guide (Old Console)/Listener/Listeners overview.md#).

2.  The backend Linux ECS kernel of Layer-4 SLB isn't correctly configured.

    You must disable the rp\_filter feature of the Linux kernel of the Linux ECS instance added to Layer-4 SLB. Otherwise, the client may not be able to access the endpoint of SLB by using telnet, but the health check is normal.

    Linux's rp\_filter feature is used to implement reverse filtering \(URPF\). It verifies the flow of reverse packets to avoid attacks using a forged IP. However, this feature may conflict with the bottom-layer LVS policy route of SLB and causes access exceptions.

    Resolution: Ensure that the values of the following three parameters in the system configuration files of the backend ECS instance are zero. Edit `/etc/sysctl.conf` and run the `sysctl -p` command the make the configurations take effect.

    ```
     net.ipv4.conf.default.rp_filter = 0
     net.ipv4.conf.all.rp_filter = 0
     net.ipv4.conf.eth0.rp_filter = 0
    ```

3.  The backend Windows ECS parameters of Layer-4 SLB are not correctly configured.

    For Layer-4 SLB service, a backend ECS instance cannot directly provide service for clients and act as the backend server of the SLB service at the same time.

    If the ECS instance act the two roles at the same time, access requests are forwarded to the same ECS instance, which may cause a data access loop and the failure of access from the ECS instance to the SLB service.

    Resolution:

    1.  Install Windows loopback adapter: Right-click**Computer** \> **Property** . On the Control Panel home page, click**Device Manager** \> **Add hardware** \> **Install the hardware that I manually select from the list** \> **Show all devices** , Select the device shown in the following figure and install it.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4298/15399340873341_en-US.png)

    2.  Enable weak host Model, and perform the following command to view idx of all network interfaces.

        ```
        netsh interface ipv4 show interface
        ```

    3.  Configure `weakhostsend=enabled`, `weakhostsend=enabled` for all network interfaces. For example, configure the interface of which the idx is 12 as follows:

        ```
        netsh interface ipv4 set interface 12 weakhostsend=enabled
        netsh interface ipv4 set interface 12 weakhostreceive=enabled
        ```

4.  The local network of the client or the intermediate link of the service provider is abnormal.

    For Internet Server Load Balancer service, client network exceptions or exceptions in the service provider's network between the client and Server Load Balancer may also lead to the failure of access from the client to Server Load Balancer.

    Troubleshoot: Perform access test on the service port of SLB in different regions and network environments. If the exception only occurs when it is accessed from the local network, it is determined that the problem is caused by a network exception. Then you can do further troubleshooting and analysis through ongoing Ping tests or MTR route tracing.

5.  Client IP address is intercepted by Alibaba Cloud Security.

    For Internet Server Load Balancer service, if the client network is a shared network \(all LAN servers share a public IP to access the Internet\). Meanwhile, certain servers in the local network launch malicious attacks such as continuous scanning against IPs of related Alibaba Cloud services due to factors such as being infected by viruses.

    Resolution: You can see the following steps to add the public IP of the local network to the whitelist of SLB:

    1.  Visit http://ip.taobao.com in the network environment of the client to obtain the public IP of the client network.
    2.  Add the IP to the SLB whitelist to allow all requests from the IP to SLB.

        **Note:** This operation may pose security risk. Ensure that the IP in the whitelist does not launch malicious attacks on the SLB.

    If the problem persists, you can provide the following information when opening a ticket so that we can help you solve the problem more efficiently:

    -   The ID of the SLB instance or the IP address of the SLB service.
    -   The public IP of the client obtained when you visit ip.taobao.com.
    -   Screenshots of long-time ping and MTR route tracing tests performed by the client on the IP of the SLB.

