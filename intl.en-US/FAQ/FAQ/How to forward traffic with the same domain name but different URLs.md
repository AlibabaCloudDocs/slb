# How to forward traffic with the same domain name but different URLs {#task_nhw_1k5_vdb .task}

In this case, we use four ECSs deployed with Nginx servers as the example to demonstrate how to configure forwarding rules specified by domain name and URL, so as to fulfill traffic forwarding as shown in the following table.

|Frontend requests|Forward traffic to|
|:----------------|:-----------------|
|www.aaa.com/tom|Server SLB\_tom1 and server SBL\_tom2|
|www.aaa.com/jerry|Server SLB\_jerry1 and server SBL\_jerry2|

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4172/15382791913154_en-US.png)

1.  Create an Internet-facing SLB instance. 

    For more information, see [Create a Server Load Balancer instance](../../../../reseller.en-US/User Guide/SLB instances/Create an SLB instance.md#).

2.  Resolve the domain name into the public IP of the SLB instance by using DNS. For convenience, the public IP of the SLB instance is bound to domain name www.aaa.com in the host file in this case.
3.  Create two VServer groups. 
    1.  Locate the newly created target instance in the Server Load Balancer console and click the instance ID to enter the details page. 
    2.  In the left-side navigation pane, click **Server** \> **VServer Group**. 
    3.  Click **Create VServer Group**. 
    4.  In the displayed dialog box, select the backend servers to be added and set ports and weights for them respectively. The ports for ECS instances in the VServer group can be different. In this case, enter **TOM** as the server group name, add server SLB\_tom1 and server SBL\_tom2 into the group, set the port number to 80, and keep the default weight value \(100\).

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4172/15382791913165_en-US.png)

    5.  Repeat the preceding steps to add another VServer group named JERRY, which includes server SLB\_jerry1 and server SBL\_jerry2. 
4.  Add a listener. 
    1.  In the left-side navigation pane, click **Listeners**, and click **Add Listener**. 
    2.  Configure the listener.  In this case, the listener is configured as follows: 
        -   **Frontend protocol \[Port\]: HTTP: 80**
        -   **Backend protocol \[Port\]: HTTP: 80**
        -   **Scheduling algorithm: Round-robin.**
        -   Keep the default values for other configuration items.
    3.  On the Listeners page, click **More** \> **Add Forwarding Rules**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4172/15382791923182_en-US.png)

    4.  On the Forwarding rules page, click **Add Forwarding Rules**. 
    5.  Configure three forwarding rules. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4172/15382791923184_en-US.png)

5.  Test: 
    -   Enter wwww.aaa.com/jerrry in the browser and the following result is returned.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4172/15382791923185_en-US.png)

    -   Enter wwww.aaa.com/tom in the browser and the following result is returned.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4172/15382791923186_en-US.png)

        Enter www.aaa.com in the browser and the following result is returned.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4172/15382791923187_en-US.png)


