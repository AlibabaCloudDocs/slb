# 配置监听转发（redirect） {#task_u4c_xmc_wfb .task}

HTTPS是加密数据传输协议，安全性高。负载均衡支持将HTTP访问重定向至HTTPS，方便您进行全站HTTPS部署。负载均衡已经在全部地域开放了HTTP重定向功能。

已创建了HTTPS监听，详情参见[添加HTTPS监听](intl.zh-CN/用户指南/监听/添加HTTPS监听.md#)。

仅负载均衡新版控制台支持监听转发功能。

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb/)。
2.  在顶部菜单栏选择负载均衡实例的所属地域。
3.  在实例管理页面，单击目标实例的ID链接。
4.  在监听页签下，单击**添加监听**。
5.  在添加监听对话框，负载均衡协议选择**HTTP**，配置监听端口。
6.  在高级配置区域下，开启**监听转发**，选择目的监听。 

    此处目的监听可以是该实例下任意端口的HTTPS监听。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64564/155954005432571_zh-CN.png)

7.  单击**下一步**。
8.  确认后，单击**提交**。
9.  单击**确定**。 

    转发开启后，所有来自HTTP的访问都会转发至HTTPS，并根据HTTPS的监听配置进行转发。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64564/155954005432572_zh-CN.png)


