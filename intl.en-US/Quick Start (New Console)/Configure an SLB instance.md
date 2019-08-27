# Configure an SLB instance {#task_bh5_dll_vdb .task}

This topic describes how to add listeners and backend servers to a Server Load Balancer \(SLB\) instance. After you create an SLB instance, you must configure it before it can distribute traffic. Specifically, you need to add at least one listener and one group of backend servers to the instance.

1.  Log on to the [SLB console](https://partners-intl.console.aliyun.com/#/slb).
2.  On the Server Load Balancer page, find the target SLB instance and click **Configure Listener**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15668724277514_en-US.png)

3.  On the Protocol and Listener tab, configure the listening rule according to the following information and use the default values for the remaining configurations. 
    -   **Select Listener Protocol**: In this example, select **TCP**.
    -   **Listening Port**: the frontend protocol and port used to receive requests and forward the requests to backend servers.

        In this example, enter the port number **80**.

    -   **Enable Peak Bandwidth Limit**: You can set a peak bandwidth to limit the service capabilities that applications on the ECS instances can provide.

        In this example, you do not need to set the peak bandwidth because the target SLB instance is billed by traffic.

    -   **Scheduling Algorithm**: SLB supports the following scheduling algorithms. In this example, select **Round-Robin \(RR\)**.

        -   Weighted Round-Robin \(WRR\): Distributes requests according to the weights of backend servers. Servers with higher weights receive more requests.
        -   Weighted Least Connections \(WLC\): In addition to the weights of backend ECS servers, the number of connections also contributes to scheduling changes. A server with a higher weight value receives more connections. If the weights of two backend servers are the same, the server with the least number of connections receives more requests.
        -   Round-Robin \(RR\): Requests are distributed evenly and sequentially to backend ECS servers.
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15668724287515_en-US.png)

4.  Click **Next**. On the Backend Servers tab, click Default Server Group, and then click **Add More**. 

    1.  On the Available Servers page, select the ECS instances ECS1 and ECS2 and click **Next: Set Weight and Port**.
    2.  Configure ports and weights for the added backend servers. 
        -   Port: the ports opened on backend ECS instances to receive requests. They can be the same in an SLB instance. In this example, set the backend port numbers to 80.
        -   Weight: An ECS instance with a higher weight receives a larger number of requests. The default value is 100 and we recommend that you use the default value.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15668724297516_en-US.png)

5.  Click **Next** to configure health checks. In this example, use default health check configurations. 

    With health check enabled, when an ECS instance is declared as unhealthy, SLB distributes requests to other healthy ECS instances and restores service to the original instance when it is healthy again.

6.  Click **Next**. On the Submit page, click **Submit**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15668724307517_en-US.png)

7.  Click **OK**. Go back to the Server Load Balancer page and click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15668724317518_en-US.png). 

    When the health check status of the backend server is **Normal**, it indicates that the backend server can process forwarded client requests.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15701/15668724317519_en-US.png)

8.  In the web browser, enter the IP address of the SLB instance to test the service. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15668724327447_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15668724327448_en-US.png)


