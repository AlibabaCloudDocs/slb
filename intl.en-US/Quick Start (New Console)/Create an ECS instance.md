# Create an ECS instance {#task_bh5_dll_vdb .task}

Before using Server Load Balancer, you must create at least two ECS instances and deploy corresponding applications. You can add the ECS instances to an SLB instance so that they can receive client requests as backend servers.

Follow the instructions in this document to create two ECS instances, ECS01 and ECS02.

1.  Log on to the ECS console. 
2.  In the left-side navigation pane, click **Instances** and then click **Create Instance**. 
3.   On the Elastic Compute Services \(ECS\) page, configure the ECS instance. The following are ECS settings used in this tutorial. You can change the configuration according to your needs.

    -   **Region**: Server Load Balancer does not support cross-region deployment. The region must be the same for the Server Load Balancer instance and the ECS instances.  In this tutorial, select **China East 1**.
    -   **Network Type**: In this tutorial, select **VPC**. Use the default VPC and VSwitch.
    -   **Image**: In this tutorial, select Ubuntu 16.04 64 bit.
    -   **Target**: Set the purchase quantity to **2** and the system automatically creates two ECS instances with the same configurations.
    -   **Assign public IP**: Select to automatically allocate a public IP address to the ECS instance.
    -   **Bandwidth Pricing**: Select billing by bandwidth and set the bandwidth to 1 Mbps.
    -   **Security Group**: The configured security group rules must include Port 22 and Port 80 in the inbound direction.
        -   Port 22 is the SSH remote port used for logging on to the ECS instance.
        -   Port 80 is the web service default port used for accessing the static page built by Apache in [Install static web pages](reseller.en-US/Quick Start (New Console)/Install static web pages.md#).
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15697/15414147747523_en-US.png)

4.   Click **Create Order** to complete the creation. 
5.  Go back to the instances page and click **China \(Hangzhou\)**. The two newly created ECS instances are displayed. Hover the mouse pointer over one instance name and click the displayed pencil icon to change the instance name to ECS01. Then change the other instance name to ECS02. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4105/15414147742204_en-US.png)


