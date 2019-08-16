# Modify the weight of a backend server {#task_1597074 .task}

After you add a backend server to the default server group, you can modify the weight of the backend server.

1.  Log on to the [Server Load Balancer console](https://partners-intl.console.aliyun.com/#/slb). 
2.  On the Server Load Balancer page, select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the Default Server Group tab.
5.  Rest the pointer over the weight value of the target backend server, and then click the displayed pencil icon. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16425/15659445257470_en-US.png)

6.  Modify the weight and then click **OK**. A backend server with a higher weight receives more requests.

    **Note:** If the weight is set to 0, no request is sent to the backend server.


**More information**  


[SetBackendServers](../reseller.en-US/Developer Guide/Backend servers/SetBackendServers.md#)

