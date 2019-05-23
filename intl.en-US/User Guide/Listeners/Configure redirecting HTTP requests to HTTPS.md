# Configure redirecting HTTP requests to HTTPS {#task_u4c_xmc_wfb .task}

HTTPS is the secure version of HTTP. With HTTPS, the data sent between the browser and the server is encrypted. Server Load Balancer supports redirecting HTTP requests to HTTPS to facilitate whole-site HTTPS deployment. Redirecting HTTP requests to HTTPS is supported in all regions.

You have created an HTTPS listener. For more information, see [Add an HTTPS listener](intl.en-US/User Guide/Listeners/Add an HTTPS listener.md#).

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/). 
2.  In the top menu, select the region where the SLB instance is located. 
3.  On the Server Load Balancer page, click the ID of the target SLB instance. 
4.  Click the **Listeners** tab and then click **Add Listener**. 
5.  In the Configure Server Load Balancer dialog box, select **HTTP** as the listener protocol and configure the listening port. 
6.  In the Advanced area, enable **Redirection** and select the target listener. 

    The target listener can be the HTTP listener of any port under the instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64564/155860426932571_en-US.png)

7.  Click **Next**. 
8.  Confirm and click **Submit**. 

    After the redirection function is enabled, all the HTTP requests will be redirected to the HTTPS listener and distributed according to the listener configurations of the HTTPS listener.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64564/155860426932572_en-US.png)


