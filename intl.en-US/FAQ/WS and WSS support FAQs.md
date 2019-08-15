# WS and WSS support FAQs {#concept_yxc_gh5_vdb .concept}

## What are WS and WSS? {#section_xjp_fwx_wdb .section}

WebSocket is a new HTML5 protocol, which provides full-duplex communication between the browser and the server. This protocol conserves server resources and bandwidth, enabling real-time communication. WebSocket is built on top of TCP and transmits data over TCP like HTTP.

One major difference between WebSocket and HTTP is that WebSocket is a two-way communication protocol. Once the connection is established, both the WebSocket server and the client can send data to or receive data from each other actively like Socket. The WebSocket server and client have to complete a handshake to establish a WebSocket connection.

WebSocket Secure \(WSS\) is the encrypted version of WebSocket.

## Why use WS and WSS? {#section_yjp_fwx_wdb .section}

With the increasing popularity and accessibility of the Internet, a multitude of varied web applications are emerging. Many applications require real-time push capabilities of the server \(such as broadcast rooms and chat rooms\). In the past, many websites used the round robin technique to achieve real-time push. With the round robin technique, the browser sends HTTP requests to the server at specific intervals \(for example, per second\) and the server returns the most recent data to the browser of the client. However, this method has an obvious disadvantage of inefficiency. The browser must send requests constantly to the server. The headers of HTTP requests may be very long with only a few effective messages. Therefore, many bandwidth resources are potentially wasted.

In this situation, HTML5 defines the WebSocket protocol, which can help conserve server resources and bandwidth and facilitate real-time communication. WebSocket provides the full-duplex communication between the browser and the server. This allows the server to send data to the client actively without being solicited by the client.

The communication process of the WebSocket protocol is shown in the following figure:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4293/15658830603247_en-US.png)

## How can I enable WS and WSS on Server Load Balancer? {#section_azg_kwx_wdb .section}

No configuration is required. The HTTP listener supports the WS protocol and the HTTPS listener supports WSS protocol by default.

**Note:** You must upgrade the instance to a guaranteed-performance instance. For more information, see [How to use guaranteed-performance instances](../../../../reseller.en-US/FAQ/FAQ/How to use guaranteed-performance Server Load Balancer instances?.md#).

## Supported regions {#section_yts_twx_wdb .section}

The WS and WSS support is available in all regions.

## Limits {#section_zts_twx_wdb .section}

The limitations for WS and WSS protocol are as follows:

-   Server Load Balancer is connected to backend ECS instances by using HTTP/1.1. We recommend that backend servers use a web server that supports HTTP/1.1.
-   If there is no message interaction between Server Load Balancer and a backend ECS instance within 60 seconds, the connection is terminated. If you need to maintain the connection, enable Keepalive to ensure message interaction at the frequency of once every 60 seconds.

## Billing {#section_b5s_twx_wdb .section}

WS and WSS protocol support is free of charge.

