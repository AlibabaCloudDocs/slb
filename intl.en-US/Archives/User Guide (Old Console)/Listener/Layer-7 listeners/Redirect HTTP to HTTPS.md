# Redirect HTTP to HTTPS {#task_wwt_jj5_vdb .task}

HTTPS is the secure version of HTTP. With HTTPS, the data sent between the browser and the server is encrypted. Server Load Balancer supports redirecting HTTP requests to HTTPS without interrupting your service. The HTTP redirection function is available in all regions.

You have created an HTTPS listener. For more information, see [Add an HTTPS listener](intl.en-US/User Guide/Listener/Layer-7 listeners/HTTPS listeners.md#).

**Note:** 

Currently only redirecting an HTTP 80 request to HTTPS 443 is supported.

1.  Log on to the [SLB](https://slbnew.console.aliyun.com/?spm=a2c4g.11186623.2.5.xNrijY) console. 
2.  Select the region where the SLB instance is located on the top menu. 
3.  On the Instances page, click the ID of the SLB instance. 
4.  In the left-side navigation pane, click **Listeners** and then click **Add Listener**. 
5.  In the Add Listener dialog box, select **HTTP** as the front-end protocol and enter **80** as the port number. 
6.  Enable the **Redirection** function and then click **Confirm**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4134/2796_en-US.png)

    After the redirection function is enabled, all the HTTP requests will be redirected to the HTTPS listener and distributed according to the listener configurations of the HTTPS listener.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4134/2797_en-US.png)


