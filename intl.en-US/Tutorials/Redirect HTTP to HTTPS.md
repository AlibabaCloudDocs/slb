# Redirect HTTP to HTTPS {#task_wwt_jj5_vdb .task}

HTTPS is the secure version of HTTP. With HTTPS, the data sent between the browser and the server is encrypted. Server Load Balancer supports redirecting HTTP requests to HTTPS to facilitate whole-site HTTPS deployment. Redirecting HTTP requests to HTTPS is supported in all regions.

You have created an HTTPS listener. For more information, see [Add an HTTPS listener](../../../../intl.en-US/User Guide/Listeners/Add an HTTPS listener.md#).

In this tutorial, redirecting HTTP 80 requests to HTTPS 443 is taken as an example.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/). 
2.  In the top menu, select the region where the SLB instance is located. 
3.  On the Server Load Balancer page, click the ID of the target SLB instance. 
4.  Click the **Listeners** tab and then click **Add Listener**. 
5.  In the Configure Server Load Balancer dialog box, select **HTTP** as the listener protocol and set the listening port to **80**. 
6.  Enable **Redirection** and select **HTTPS:443** as the target port. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18827/155801006010550_en-US.png)

7.  Click **Next**. 
8.  Confirm and click **Submit**. 

    After the redirection function is enabled, all the HTTP requests will be redirected to the HTTPS listener and distributed according to the listener configurations of the HTTPS listener.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18827/155801006010551_en-US.png)


