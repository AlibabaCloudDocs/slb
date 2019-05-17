# 后端服务器支持添加ECS弹性网卡ENI {#task_dvk_hbv_4fb .task}

弹性网卡（ENI）是一种可以附加到专有网络VPC类型ECS实例上的虚拟网卡，通过弹性网卡，您可以实现高可用集群搭建、低成本故障转移和精细化的网络管理。性能保障型负载均衡实例后端服务器支持挂载ECS弹性网卡ENI。

负载均衡实例添加后端服务器组时，如果ECS实例绑定多个弹性网卡，支持挂载弹性网卡ENI。

将弹性网卡绑定到ECS实例的方法请参见[绑定弹性网卡](../../../../intl.zh-CN/网络/弹性网卡/绑定弹性网卡.md#)。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155806421714314_zh-CN.png)

**说明：** 仅性能保障型实例后端服务器支持添加弹性网卡ENI。

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb/cn-hangzhou)。
2.  在左侧导航栏，单击**实例管理**，在实例管理页面，单击需要添加后端服务器组的实例ID。
3.  选择后端服务器组类型，默认服务器组、虚拟服务器组和主备服务器组均支持挂载弹性网卡ENI，单击**添加**。
4.  在我的服务器页面，选择后端服务器，可以选择弹性网卡ENI。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155806421714315_zh-CN.png)

5.  单击**加入待添加篮**。
6.  单击**确定**。 

    返回实例管理页面，可以看到挂载了弹性网卡的后端服务器组如下：

    其中，

    -   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155806421714372_zh-CN.png)：表示ECS实例。
    -   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155806421714373_zh-CN.png)：表示弹性网卡ENI。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24484/155806421714320_zh-CN.png)


