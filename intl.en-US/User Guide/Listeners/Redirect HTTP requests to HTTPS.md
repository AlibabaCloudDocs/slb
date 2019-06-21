# Redirect HTTP requests to HTTPS {#task_u4c_xmc_wfb .task}

HTTPS is the secure version of HTTP. With HTTPS, the data sent between the browser and the server is encrypted. Server Load Balancer \(SLB\) supports redirecting HTTP requests to HTTPS to facilitate whole-site HTTPS deployment. Redirecting HTTP requests to HTTPS is supported in all regions.

An HTTPS listener is created. For more information, see [Add an HTTPS listener](intl.en-US/User Guide/Listeners/Add an HTTPS listener.md#).

The redirection function is supported only by the new version SLB console.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/).
2.  Select the region of the target SLB instance.
3.  On the Server Load Balancer page, click the ID of the target SLB instance.
4.  Click the Listeners tab and then click **Add Listener**.
5.  In the Configure Server Load Balancer dialog box, select **HTTP** as the listener protocol and configure the listening port.
6.  In the Advanced section, turn on **Redirection** and select the target HTTPS listener. 

    The target listener can be an HTTPS listener with any port in the SLB instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64564/156108713532571_en-US.png)

7.  Click **Next**.
8.  Check the configurations and click **Submit**.
9.  Click **OK**. 

    After the redirection function is enabled, all HTTP requests will be redirected to the selected HTTPS listener and distributed according to the listener configurations of the HTTPS listener.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64564/156108713532572_en-US.png)


