# 配置监听转发（redirect）

HTTPS是加密数据传输协议，安全性高。负载均衡支持将HTTP访问重定向至HTTPS，方便您进行全站HTTPS部署。负载均衡已经在全部地域开放了HTTP重定向功能，并在英国（伦敦）地域支持自定义重定向使用的状态码。

确保您已创建了HTTPS监听。详情请参见[添加HTTPS监听](/cn.zh-CN/传统型负载均衡CLB/用户指南/监听/添加HTTPS监听.md)。

仅负载均衡新版控制台在创建HTTP监听时支持配置监听转发。

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb/)。

2.  在左侧导航栏，选择**实例** \> **实例管理**。

3.  在实例管理页面，单击目标实例的ID链接。

4.  在监听页签下，单击**添加监听**。

5.  在协议&监听对话框，负载均衡协议选择**HTTP**，配置监听端口。

6.  在高级配置区域下，打开**监听转发**开关，选择目的监听。

    此处目的监听可以是该实例下任意端口的HTTPS监听。

    ![协议与监听](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0872129951/p135153.png)

    在英国（伦敦）地域支持配置重定向跳转使用的状态码。

    ![状态码](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0872129951/p94776.png)

7.  单击**下一步**。

8.  确认后，单击**提交**。

9.  单击**知道了**。

    转发开启后，所有来自HTTP的访问都会转发至HTTPS，并根据HTTPS的监听配置进行转发。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0872129951/p32572.png)


