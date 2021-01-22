Redirect HTTP requests to HTTPS 
====================================================

This topic describes how to make configurations to redirect HTTP requests to HTTPS. HTTPS is the secure version of HTTP. Server Load Balancer (SLB) supports redirecting HTTP requests to HTTPS to facilitate whole-site HTTPS deployment. Redirecting HTTP requests to HTTPS is available in all regions.
redirect requests from port 80 to port 443 redirection redirect HTTP requests to HTTPS

Prerequisites
-------------

An HTTPS listener is created. For more information, see [Add an HTTPS listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTPS listener.md).

Context
-------

In the following process, HTTP 80 requests are redirected to HTTPS 443.
**Note** This feature is available only when you create an HTTP listener in the new SLB console.

Procedure
---------

1. Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb/).

   
{#console1}
2. In the top navigation bar, select the region where the SLB instance is deployed.

   

3. On the **Instances** page, find the SLB instance and click its ID.

   

4. Click the **Listener** tab and then click **Add Listener** .

   

5. In the **Protocol and Listener** step, set Select Listener Protocol to **HTTP** and Listening Port to **80** .

   

6. Click **Modify** next to **Advanced** .

   

7. Enable **Redirection** and set Target Port to **HTTPS:443** .

   ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7191019951/p10550.png) 

8. Click **Next** .

   

9. In the Confirm step, click **Submit** and then click **OK** .

   After the redirection feature is enabled, all HTTP requests will be redirected to the HTTPS listener and forwarded based on the listener configurations of the HTTPS listener.
   ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2023965061/p68797.png) 



