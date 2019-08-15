# WS/WSS协议支持FAQ {#concept_yxc_gh5_vdb .concept}

## 什么是WS/WSS？ {#section_xjp_fwx_wdb .section}

WebSocket \(WS\)是HTML5一种新的协议。它实现了浏览器与服务器全双工通信，能更好地节省服务器资源和带宽并达到实时通讯。WebSocket建立在TCP之上，同HTTP一样通过TCP来传输数据，但是它和HTTP最大不同是：

WebSocket是一种双向通信协议，在建立连接后，WebSocket服务器和Browser/Client Agent都能主动的向对方发送或接收数据，就像Socket一样；WebSocket需要类似TCP的客户端和服务器端通过握手连接，连接成功后才能相互通信。

WSS（Web Socket Secure）是WebSocket的加密版本。

## 为何使用WS/WSS？ {#section_yjp_fwx_wdb .section}

随着互联网的蓬勃发展，各种类型的Web应用层出不穷，很多应用要求服务端有能力进行实时推送能力（比如直播间聊天室），以往很多网站为了实现推送技术，所用的技术都是轮询。轮询是在特定的的时间间隔（如每1秒），由浏览器对服务器发出HTTP请求，然后由服务器返回最新的数据给客户端的浏览器。这种传统的模式带来很明显的缺点，即浏览器需要不断地向服务器发出请求，然而HTTP请求可能包含较长的头部，其中真正有效的数据可能只是很小的一部分，显然这样会浪费很多的带宽资源。

在这种情况下，HTML5定义了WebSocket协议，能更好地节省服务器资源和带宽，并且能够更实时地进行通讯。WebSocket实现了浏览器与服务器全双工\(full-duplex\)通信，允许服务器主动发送信息给客户端。

WebSocket协议的交互过程如下图所示。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4293/15658838943247_zh-CN.png)

## 如何在阿里云负载均衡上启用WS/WSS支持？ {#section_azg_kwx_wdb .section}

无需配置，当选用HTTP监听时，默认支持无加密版本WebSocket协议（WS协议）；当选择HTTPS监听时，默认支持加密版本的WebSocket协议（WSS协议）。

**说明：** 需要将实例升级为性能保障型实例。详细参见[性能保障型实例FAQ](intl.zh-CN/常见问题/性能保障型实例FAQ.md#)。

## 支持的地域 {#section_yts_twx_wdb .section}

全部地域都已开放WS/WSS支持。

## 限制 {#section_zts_twx_wdb .section}

WSS/WS协议支持的约束如下：

-   负载均衡与ECS后端服务的连接采用HTTP/1.1，建议后端服务器采用支持HTTP/1.1的Web Server。
-   若负载均衡与后端服务超过60秒无消息交互，会主动断开连接，如需要维持连接一直不中断，需要主动实现保活机制，每60秒内进行一次报文交互。

## 收费政策 {#section_b5s_twx_wdb .section}

WSS/WS协议支持不额外收取费用。

