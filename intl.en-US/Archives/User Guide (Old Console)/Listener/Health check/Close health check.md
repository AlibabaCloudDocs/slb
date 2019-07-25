# Close health check {#task_it1_1qn_vdb .task}

If health check is closed, requests may be distributed to unhealthy ECS instances, which can lead to service interruption. In general, we do not recommend closing health check.

**Note:** You can only close health check for HTTP and HTTPS listeners. The health check of UDP and TCP listeners cannot be closed.

1.  Log on to the [SLB console](https://slbnew.console.aliyun.com/#/list/cn-hangzhou). 
2.  On the Instances page, click the ID of the target instance. 
3.  In the left-side navigation pane, click **Listeners**. 
4.  On the Listeners page, click **Configure** next to the target listener. 
5.  In the Configure Listener dialog box, click **Next**. 
6.  Toggle the **Activate health check** switch to **Disable**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4139/2828_en-US.png)


