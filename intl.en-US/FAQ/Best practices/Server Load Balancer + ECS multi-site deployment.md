# Server Load Balancer + ECS multi-site deployment {#task_cdy_s4v_wdb .task}

You can build multiple sites on an ECS instance by creating virtual sub-directories. Server Load Balancer supports adding this type of ECS instance as a backend server to forward traffic. Both layer-4 and layer-7 Server Load Balancer support adding multi-site ECS instances and the function is not influenced by session persistence.

This tutorial illustrates how to create a TCP listener and add an ECS instance deployed with two sites.

1.  On the ECS01, create the site www.aaa.com and the site www.bbb.com through creating sub-directories. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792903138_en-US.png)

    The content displayed on the site www.aaa.com is shown as the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792903139_en-US.png)

    The content displayed on the site www.bbb.com is shown as the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792903140_en-US.png)

    You can bind the two domain names to the public IP address of the ECS instance in the local host file and use the browser to visit ww.aaa.com and www.bbb.com. If the preceding contents are displayed, the configuration is successful.

2.  Create a custom image for the ECS01 and use the image to create ECS02 with the same configuration. 
3.  Create an Internet Server Load Balancer instance and add a TCP listener. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792903141_en-US.png)

4.  Add the ECS01 and the ECS02 as backend servers. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792903144_en-US.png)

5.  In the local host file, resolve the domain name www.aaa.com and the domain name www.bbb.com to the public IP address of the Server Load Balancer instance. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792903148_en-US.png)

6.  Enter www.aaa.com and www.bbb.com in the browser. If the corresponding backend services can be accessed, the deployment is successful. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792903152_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792903153_en-US.png)


