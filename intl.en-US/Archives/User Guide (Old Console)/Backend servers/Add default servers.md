# Add default servers {#task_ekq_m4n_vdb .task}

Before using the SLB service, you must add at least one default server.

-   You have [created an SLB instance](reseller.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#).
-   You have created ECS instances and deploy applications to process distributed requests. 

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb). 
2.  On the Server Load Balancer page, select a region. 
3.  Click the ID of the target SLB instance. 
4.  Click the Default Server Group tab. 
5.  Click **Add**.  
6.  On the Servers Not Added page, click **Add**. Then the Available Servers page is displayed.
7.  Click **Add** next to the target ECS instance, or select multiple ECS instances and then click **Add to Selected Server List**. 
8.  In the displayed Available Servers dialog box, specify the weight of the added ECS instance and then click **OK**. An ECS instance with a higher weight will receive a larger number of connection requests. You can set the weight based on the service capabilities of the ECS instances.

    **Note:** If the weight is set to 0, no requests will be sent to the ECS instance.

    The added ECS instances are listed on the **Default Server Group** page. You can remove or change the weights of the added ECS instances.


