# 负载均衡+ECS多站点部署 {#task_cdy_s4v_wdb .task}

ECS上可以通过设置虚拟子目录搭建多个站点。负载均衡服务支持添加这种类型的ECS实例作为后端服务器，进行流量转发。HTTP和TCP负载均衡服务都可以挂载多站点ECS，并且不受会话保持功能影响。

本教程概述了如何创建一个TCP监听，并挂载两个不同站点的ECS实例。

1.  在ECS01上通过设置虚拟子目录，搭建两个域名为www.aaa.com和www.bbb.com的站点。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792843138_zh-CN.png)

    www.aaa.com的站点内容，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792843139_zh-CN.png)

    www.bbb.com的站点内容，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792843140_zh-CN.png)

    您可以在本地host文件中，将这两个域名和ECS实例的公网IP地址绑定，然后在浏览器中访问ww.aaa.com和www.bbb.com，如果能正常显示设置的网站，则说明配置成功。

2.  为ECS01创建一个自定义镜像，使用该镜像创建一个相同配置的ECS02。 
3.  创建一个公网负载均衡实例，然后添加一个TCP监听。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792843141_zh-CN.png)

4.  添加ECS01和ECS02作为后端服务器。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792843144_zh-CN.png)

5.  在本地host文件中，将www.aaa.com和www.bbb.com这两个域名解析到负载均衡的公网IP地址上。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792843148_zh-CN.png)

6.  在浏览器中输入www.aaa.com和www.bbb.com，如果可以正常访问到对应的后端服务，证明负载均衡服务正常。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792843152_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4167/15382792843153_zh-CN.png)


