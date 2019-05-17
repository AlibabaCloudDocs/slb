# 使用SLB部署HTTPS业务（单向认证） {#concept_apn_dj5_vdb .concept}

要配置HTTPS单向认证的监听，您仅需要在配置监听时上传服务器证书。

## 步骤一 上传服务器证书 {#section_tqs_yw5_vdb .section}

在配置HTTPS监听（单向认证）前，您需要购买服务器证书，并将服务器证书上传到负载均衡的证书管理系统。上传后，无需在后端ECS上进行其它证书配置。

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb)。
2.  在左侧导航栏，选择证书管理，单击**创建证书**。
3.  按照以下信息，配置证书：
    -   证书部署地域: 选择华东1。

        **说明：** 证书的地域和负载均衡实例的地域要相同。

    -   证书类型：选择**服务器证书**。
    -   证书内容和私钥：复制服务器证书的内容和私钥。单击**导入样例**查看合法的证书格式。上传的证书必须是PEM格式，详情查看[证书格式要求](intl.zh-CN/历史文档/用户指南（旧版控制台）/证书管理/证书要求.md#)。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15580579847324_zh-CN.png)

4.  单击**确定**，完成上传。

## 步骤二 配置负载均衡实例 {#section_rc5_sx5_vdb .section}

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb)。
2.  在实例管理页面，单击**创建负载均衡**。
3.  配置负载均衡实例，单击**立即购买**完成支付。

    **说明：** 网络类型选择**公网**，地域选择**华东1**。详细配置信息参考[创建负载均衡实例](intl.zh-CN/历史文档/用户指南（旧版控制台）/负载均衡实例/创建实例.md#)。

4.  创建成功后，返回实例管理页面，选择**华东1**地域。
5.  单击已创建的负载均衡实例ID链接，或者直接单击**监听设置向导**。
6.  在监听页签下，单击**添加监听**。
7.  在协议&监听页签下，完成如下配置。

    -   **选择负载均衡协议**：HTTPS
    -   **监听端口**：443
    -   **调度算法**：轮询（RR）
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16604/155805798410035_zh-CN.png)

8.  单击**下一步**，在SSL证书页签下，选择已经上传的服务器证书。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15580579847326_zh-CN.png)

9.  单击**下一步**，选择默认服务器组，单击**添加**，添加ECS服务器，后端协议监听端口设置为80。
10. 在左侧导航栏，单击**服务器** \> **后端服务器** ，然后单击**添加后端服务器**，添加ECS服务器。

## 步骤三 测试负载均衡服务 {#section_jcf_4y5_vdb .section}

1.  负载均衡实例配置完成后，在实例管理页面，查看健康检查状态。

    当状态为**正常**时，表示后端服务器可以正常接收处理负载均衡监听转发的请求。

2.  在浏览器中输入负载均衡的公网服务地址。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15580579847447_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15580579857448_zh-CN.png)


