将HTTP访问重定向至HTTPS 
=====================================

HTTPS是加密数据传输协议，安全性高。负载均衡支持将HTTP访问重定向至HTTPS，方便您进行全站HTTPS部署。负载均衡已经在全部地域开放了HTTP重定向功能。
80转443 重定向 HTTP到HTTPS

前提条件
----

已创建了HTTPS监听，详情参见[添加HTTPS监听](/cn.zh-CN/传统型负载均衡CLB/CLB用户指南/监听/添加HTTPS监听.md)。

背景信息
----

本教程以将HTTP 80访问重定向转发至HTTPS 443为例。
**说明** 仅负载均衡新版控制台在创建HTTP监听时支持配置监听转发。

操作步骤
----

1. 登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb/)。

   
{#console1}
2. 登录[负载均衡管理控制台](https://partners-intl.aliyun.com/login-required#/slb)。

   
{#console2}
3. 在顶部菜单栏选择负载均衡实例的所属地域。

   

4. 在 **实例管理** 页面，单击目标实例的ID链接。

   

5. 在 **监听** 页签下，单击 **添加监听** 。

   

6. 在 **协议\&监听** 页签下，负载均衡协议选择 **HTTP** ， 监听端口输入 **80** 。

   

7. 单击 **高级配置** 后的 **修改** 。

   

8. 开启 **监听转发** ，选择目的监听为 **HTTPS:443** 。

   ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7614029951/p10550.png) 

9. 单击 **下一步** 。

   

10. 确认后，单击 **提交** ，然后单击 **知道了** 。

    转发开启后，所有来自HTTP的访问都会转发至HTTPS，并根据HTTPS的监听配置进行转发。
    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7614029951/p68797.png) 



