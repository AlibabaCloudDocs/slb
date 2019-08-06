# HTTP重定向至HTTPS {#task_wwt_jj5_vdb .task}

HTTPS是加密数据传输协议，安全性高。负载均衡支持将HTTP访问重定向至HTTPS，并且不影响您的服务。负载均衡已经在全部地域开放了HTTP重定向功能。

已创建了HTTPS监听。详情参见[配置HTTPS监听](cn.zh-CN/历史文档/用户指南（旧版控制台）/监听/七层监听/HTTPS监听.md#)。

**说明：** 

当前仅支持HTTP 80访问重定向转发至HTTPS 443。

1.  登录[负载均衡管理控制台](https://slbnew.console.aliyun.com/?spm=a2c4g.11186623.2.5.xNrijY)。 
2.  在顶部菜单栏选择负载均衡实例的所属地域。 
3.  在实例管理页面，单击目标实例的ID链接。 
4.  在左侧导航栏，单击**监听**，然后单击**添加监听**。 
5.  在添加监听对话框，前端协议选择**HTTP**, 端口输入**80**。 
6.  开启**监听转发**，然后单击**确认**。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4134/15481775572796_zh-CN.png)

    转发开启后，所有来自HTTP的访问都会转发至HTTPS，并根据HTTPS的监听配置进行转发。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4134/15481775572797_zh-CN.png)


