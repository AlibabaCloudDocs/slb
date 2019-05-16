# HTTP重定向至HTTPS {#task_wwt_jj5_vdb .task}

HTTPS是加密数据传输协议，安全性高。负载均衡支持将HTTP访问重定向至HTTPS，方便您进行全站HTTPS部署。负载均衡已经在全部地域开放了HTTP重定向功能。

已创建了HTTPS监听，详情参见[添加HTTPS监听](../intl.zh-CN/用户指南/监听/添加HTTPS监听.md#)。

**说明：** 仅负载均衡新版控制台支持监听转发功能。

本教程以将HTTP 80访问重定向转发至HTTPS 443为例。

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb/)。 
2.  在顶部菜单栏选择负载均衡实例的所属地域。 
3.  在实例管理页面，单击目标实例的ID链接。 
4.  在监听页签下，单击**添加监听**。 
5.  在添加监听对话框，负载均衡协议选择**HTTP**， 监听端口输入**80**。 
6.  开启**监听转发**，选择目的监听为**HTTPS:443**。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18827/155800947510550_zh-CN.png)

7.  单击**下一步**。 
8.  确认后，单击**提交**。 

    转发开启后，所有来自HTTP的访问都会转发至HTTPS，并根据HTTPS的监听配置进行转发。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18827/155800947510551_zh-CN.png)


