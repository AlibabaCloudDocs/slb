# HTTP/2协议支持常见问题 {#concept_oyq_hh5_vdb .concept}

## 什么是HTTP/2？ {#section_a3f_yzx_wdb .section}

HTTP/2（Hypertext Transfer Protocol Version 2）是超文本传输协议的第二版，向下兼容HTTP1.X协议版本，同时带来性能的大幅提升。

与HTTP/1.X相比HTTP/2的优势如下：

-   多路复用 \(Multiplexing\): 多路复用允许同时通过单一的HTTP/2连接发起多重的请求-响应消息。
-   二进制分帧与首部压缩: 提升了数据在网络中传输的效率。
-   服务端推送\(Server Push\): 服务端可以主动往客户端推送数据，以减少请求次数提升效率。
-   除此以外还有流量控制、主动重置请求、请求优先级等众多特性使得Web服务性能得以大幅提升，如下图所示。
-   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4294/15586048093266_zh-CN.png)


## 如何在阿里云负载均衡上启用HTTP/2协议？ {#section_mnn_31y_wdb .section}

无需配置，HTTPS监听上默认支持HTTP/2协议。

**说明：** 需要将实例升级为性能保障型实例。详细参见[如何使用负载均衡性能保障型实例](../../../../intl.zh-CN/常见问题/常见问题/如何使用负载均衡性能保障型实例？.md#)。

负载均衡HTTPS监听会侦测客户端发起的握手报文ClientHello中的ALPN字段，进行协议版本的协商。若客户端ClientHello报文中没有携带ALPN字段，则按照HTTP/1.x的请求逻辑来处理，反之，按照HTTP/2的请求逻辑处理。

**说明：** HTTP/2协议仅在HTTPS监听上支持，不支持明文HTTP/2\(HTTP/2 Cleartext\)。

## 支持的地域 {#section_onn_31y_wdb .section}

全部地域已支持HTTP/2协议。

## 使用限制 {#section_pnn_31y_wdb .section}

HTTP/2协议支持的约束如下：

-   HTTP/2协议仅在HTTPS监听上支持，不支持明文HTTP2\(HTTP/2 Cleartext\)
-   当前HTTP/2只启用在客户端到SLB之间的链路，SLB到后端服务器之间的连接依然是HTTP/1.X
-   HTTP/2的请求会统计到监听/实例的QPS中，与HTTP/1.X的QPS请求统一计数
-   在HTTP/2链路中所有后端发给SLB的回应，根据协议要求，会将head中所有字段的名称改为小写字母，如Content-Type会被改写为content-type
-   单个连接支持的最大并发stream数为128
-   HTTP/2的连接超时时间为180秒，没有例外

## 收费政策 {#section_rnn_31y_wdb .section}

HTTP/2协议支持不额外收取费用。

