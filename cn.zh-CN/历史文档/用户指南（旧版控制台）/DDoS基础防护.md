# DDoS基础防护 {#concept_qtj_cqn_vdb .concept}

负载均衡控制台可以查看公网负载均衡实例的云盾阈值。

**说明：** 该功能目前已在青岛、北京、杭州、上海、深圳、香港、新加坡、美东和美西地域上线。

## DDoS基础防护介绍 {#section_cnq_p3c_wdb .section}

阿里云免费为负载均衡服务提供最高5G的DDoS基础防护。如下图所示，所有来自Internet的流量都要先经过云盾再到达负载均衡，云盾会针对常见的攻击进行清洗过滤。云盾DDoS基础防护可以防御SYN Flood、UDP Flood、ACK Flood、ICMP Flood 和DNS Flood等DDoS攻击。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/2870_zh-CN.jpeg)

云盾DDoS基础防护根据公网负载均衡实例的带宽设定清洗阈值和黑洞阈值。当入方向流量达到阈值上限时，触发清洗和黑洞：

-   清洗：当来自Internet的攻击流量较大或符合某些特定攻击流量模型特征时，云盾将会针攻击流量启动清洗操作，清洗包括攻击报文过滤、流量限速、包限速等。
-   黑洞：当来自Internet的攻击流量非常大时，为保护整个集群的安全，流量将会被黑洞处理，即所有入流量全部被丢弃。

## 查看防护阈值 {#section_f35_ljc_wdb .section}

使用子账号登录阿里云控制台后，若无法在控制台上查看防护阈值，需要先对子账号授权。详情参见[授予云盾基础防护只读权限](#section_c4n_wjc_wdb)。

完成以下操作查看防护阈值：

1.  登录[负载均衡管理控制台](https://slbnew.console.aliyun.com/?spm=a2c4g.11186623.2.6.XSuumL#/list/cn-hangzhou)。
2.  选择地域，查看该地域的所有实例。
3.  将鼠标移至目标实例的云盾图标，查看BPS清洗阈值、PPS清洗阈值和黑洞阈值。您可以单击DDoS控制台链接查看更多信息。
    -   BPS清洗阈值：入方向流量超过了BPS清洗阈值时，触发清洗。
    -   PPS清洗阈值：入方向数据包数超过了PPS清洗阈值时，触发清洗。
    -   黑洞阈值：入方向流量超过黑洞阈值时将触发黑洞。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/2871_zh-CN.png)


## 授权云盾基础防护只读权限 {#section_c4n_wjc_wdb .section}

完成以下操作授予子账号只读访问云盾DDoS基础防护\(Anti-DDoS Basic\)的权限：

**说明：** 使用主账号进行授权。

1.  使用主账号登录访问控制RAM管理控制台。
2.  在左侧导航栏，单击**用户管理**，找到目标子账号，然后单击**管理**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/2872_zh-CN.png)

3.  单击**用户授权策略**，然后单击**编辑授权策略**。
4.  在弹出的对话框，在可授权策略列表中搜索**AliyunYundunDDosReadOnlyAccess**，将其加入到已授权策略列表。单击**确定**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/2873_zh-CN.png)


