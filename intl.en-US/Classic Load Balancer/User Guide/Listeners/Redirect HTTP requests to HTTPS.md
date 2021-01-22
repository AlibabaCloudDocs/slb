# Redirect HTTP requests to HTTPS

This topic describes how to change configurations to redirect HTTP requests to HTTPS. HTTPS is the secure version of HTTP. Server Load Balancer \(SLB\) allows you to redirect HTTP requests to HTTPS, which facilitates whole-site HTTPS deployment. You can redirect HTTP requests to HTTPS in all regions, and customize the status code for redirection in the UK \(London\) region.

An HTTPS listener is created. For more information, see [Add an HTTPS listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTPS listener.md).

This feature is available only when you create an HTTP listener in the new SLB console.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/).

2.  In the left-side navigation pane, choose **Instances** \> **Instances**.

3.  On the Instances page, click the ID of an SLB instance.

4.  On the Listener tab. Click **Add Listener**.

5.  In the Protocol and Listener step, set the listener protocol to **HTTP** and specify a listening port.

6.  In the Advanced section, click Modify. Turn on **Redirection** and select a listener to which you want to redirect requests.

    The listener can be an HTTPS listener with any port in the SLB instance.

    You can set the status code for redirection in the UK \(London\) region.

7.  Click **Next**.

8.  Check the configurations and click **Submit**.

9.  Click **OK**.

    After the redirection feature is enabled, all HTTP requests are redirected to the selected HTTPS listener and distributed based on the configurations of the HTTPS listener.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8553598951/p32572.png)


