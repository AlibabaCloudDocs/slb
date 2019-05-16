# Configure an SLB instance {#task_bh5_dll_vdb .task}

This topic describes how to add listeners and backend servers to a Server Load Balancer \(SLB\) instance. After you create an SLB instance, you must configure it before it can distribute traffic. Specifically, you need to add at least one listener and one group of backend servers to the instance.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb). 
2.  On the Server Load Balancer page, locate the target instance and click **Configure Listener**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15580091967514_en-US.png)

3.  On the Protocol and Listener tab page, configure the listening rule according to the following description and use default values for the remaining configurations. 
    -   **Select Listener Protocol**: In this example, select **TCP**.
    -   **Listening Port**: the frontend protocol and port used to receive requests and forward requests to backend servers. The frontend ports in an SLB instance must be unique.

        In this example, enter the port number **80**.

    -   **Enable Peak Bandwidth Limit**: You can set a peak bandwidth to limit the service capabilities that applications on ECS instances can provide.

        In this example, you do not need to set the peak bandwidth because the instance is billed based on traffic.

    -   **Scheduling Algorithm**: SLB supports the following scheduling algorithms. In this example, select **Round-Robin \(RR\)**.

        -   **Weighted Round-Robin \(WRR\)**: Distributes requests according to the weights of backend servers. Servers that are of higher weights receive more requests.
        -   **Weighted Least Connections \(WLC\)**: In addition to the weights of backend ECS servers, the number of connections also contributes to scheduling changes. A server that is of a higher weight value will receive a larger percentage of live connections at any time. If the weights are the same, the system directs network connections to the server with the least number of established connections.
        -   **Round-Robin \(RR\)**: Requests are distributed evenly across the backend ECS servers sequentially.
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15580091967515_en-US.png)

4.  Click **Next**. 
5.  On the Backend Servers tab page, click Default Server Group, and then click **Add**. 

    1.  On the Available Servers page, select target ECS instances that you want to use as backend servers, and then click **Add to Selected Server List**. 
    2.  Click **OK**. 
    3.  Configure ports and weights for the added backend servers. 
        -   The ports are on the backend opened on ECS instances to receive requests. They can be the same in an SLB instance. In this example, set the backend port numbers to 80.
        -   An ECS instance with a higher weight will receive more requests. The default weight value is 100. We recommend that you use the default value.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15580091967516_en-US.png)

6.  Click **Next** to configure the health check. In this example, use default configurations. 

    With health check enabled, when an ECS instance is declared as unhealthy, SLB distributes requests to other healthy ECS instances and restores service to the original instance when it is healthy again.

7.  Click **Next**. On the Submit page, check the configurations and click **Submit**. 
8.  Click **OK**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15580091967517_en-US.png)

9.  Go back to the Server Load Balancer page and click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15580091967518_en-US.png). 

    When the health check status of a backend server is **Normal**, it indicates that the backend server can process forwarded client requests.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15580091967519_en-US.png)

10. In the web browser, enter the IP address of the SLB instance to test the service. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/155800919641529_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/155800919641536_en-US.png)


