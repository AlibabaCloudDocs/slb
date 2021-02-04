# Create a vServer group

This topic describes how to create a vServer group for a Server Load Balancer \(SLB\) instance. A vServer group contains Elastic Compute Service \(ECS\) instances that function as backend servers. If you associate a vServer group with a listener, the listener distributes requests only to backend servers in the vServer group.

Before you create a vServer group, make sure that the following conditions are met:

-   An SLB instance is created. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).
-   ECS instances are created and applications are deployed on the ECS instances to process requests.

Take note of the following items before you create a vServer group for an SLB instance:

-   ECS instances are added to a vServer group and the corresponding SLB instance must be deployed in the same region.
-   An ECS instance can be added to multiple vServer groups.
-   A vServer group can be associated with multiple listeners of an SLB instance.
-   A vServer group consists of ECS instances and application ports.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  On the Instances page, select the region of the SLB instance for which you want to create a vServer group.

3.  Find the SLB instance and click its instance ID.

4.  Click the VServer Groups tab.

5.  On the VServer Groups tab, click **Create VServer Group**.

6.  On the Create VServer Group page, set the parameters.

    1.  In the **VServer Group Name** field, enter a name for the vServer group.

    2.  Click **Add**. On the My Servers wizard page, select the ECS instances that you want to add.

    3.  Click **Next**.

    4.  Set the Port and Weight parameters for each ECS instance, and then click **Add**.

        Set the Port and Weight parameters based on the following information:

        -   **Port**: The backend port opened on an ECS instance to receive requests.

            You can set the same port number for multiple backend servers of an SLB instance.

        -   **Weight**: An ECS instance with a higher weight receives more requests.

            **Note:** If the weight of an ECS instance is set to 0, the ECS instance no longer receives new requests.

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9213359951/p7368.png)

        You can click ![Batch operations](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4407841851/p76844.png) to specify the ports and weights of the added ECS instances in batches.

        -   **Replicate to Below**: The ports or weights of all servers below the current server are set to the port or weight of the current server.
        -   **Replicate to Above**: The ports or weights of all servers above the current server are set to the port or weight of the current server.
        -   **Replicate to All**: The ports or weights of all servers in the vServer group are set to the port or weight of the current server.
        -   **Reset**: If the port or weight of the current server is cleared, the ports or weights of all servers in the vServer group are also cleared.
7.  Click **Create**.


**Related topics**  


[AddVServerGroupBackendServers](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/VServer groups/AddVServerGroupBackendServers.md)

