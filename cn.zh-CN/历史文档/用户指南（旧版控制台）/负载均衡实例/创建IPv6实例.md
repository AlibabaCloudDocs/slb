# 创建IPv6实例 {#task_uz2_kjz_c2b .task}

负载均衡SLB支持创建IPv6实例。创建后，系统会为实例分配一个公网IPv6地址，可以被互联网上的IPv6客户端访问。

**说明：** 

-   目前，仅有华东1地域的E、F两个可用区支持创建IPv6实例且实例类型必须为性能保障型实例。
-   互联网IPv6网络大环境还处于建设初期，当前可能存在部分线路访问不通，如有请工单反馈，同时IPv6公测期间，不提供SLA保障。

**IPv6介绍**

IPv6是Internet Protocol Version 6的缩写，其中Internet Protocol译为互联网协议。IPv6是IETF（互联网工程任务组，Internet Engineering Task Force）设计的用于替代现行版本IP协议（IPv4）的下一代IP协议，通过将IPv4中32位的地址长度扩展为128位，使得地址空间扩大了79,228,162,514,264,337,593,543,950,336倍。使用IPv6，可以让全世界的每一粒沙子都能分配到一个IP地址。

**SLB IPv6 特点**

负载均衡IPv6支持有以下特点：

-   平滑迁移IPv6，业务无感知

    IPv6 SLB后端可以直接挂载使用IPv4地址的ECS，无需对原有系统做改造，就可以平滑地将业务迁移到IPv6。

    通过新增IPv6入口，对原有IPv4业务无任何影响，仅需要在业务总量增加的情况下，适量对后端ECS进行横向扩容即可。

-   IPv6访问控制让业务部署更加安全可靠

    阿里云负载均衡SLB支持IPv6访问控制，您可以根据业务需要灵活地配置访问控制策略。

    -   访问控制黑名单可有效阻断恶意地址对负载均衡业务的访问。
    -   访问控制白名单仅允许白名单中授权的地址访问负载均衡业务。

1.   登录[负载均衡管理控制台](https://slbnew.console.aliyun.com/#/list/cn-hangzhou)。 
2.  选择**实例** \> **实例管理**。 
3.  在实例管理页面，单击左上角的**创建负载均衡**。 
4.   配置负载均衡实例，IP版本选择**IPv6**。 其他配置和普通实例配置相同，参考[SLB实例配置说明](cn.zh-CN/用户指南/负载均衡实例/创建负载均衡实例.md#table_ivr_hjn_vdb)。

    **说明：** 目前，仅有华东1地域的E、F两个可用区支持创建IPv6实例且实例类型必须为性能保障型实例。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/14794/6261_zh-CN.png)

5.   返回实例列表页面，查看已创建的IPv6实例。 

创建后，系统会为该实例分配一个IPv6地址。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/14794/6262_zh-CN.png)

