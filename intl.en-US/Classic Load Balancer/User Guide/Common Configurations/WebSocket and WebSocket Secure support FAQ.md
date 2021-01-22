# WebSocket and WebSocket Secure support FAQ

WebSocket is a new HTML5 protocol for full-duplex communication between clients and servers. It supports real-time communication and reduces the consumption of server resources and bandwidth. WebSocket Secure is the encrypted version of WebSocket.

## Introduction to WebSocket and WebSocket Secure

WebSocket is a new HTML5 protocol for full-duplex communication between clients and servers. It supports real-time communication and reduces the consumption of server resources and bandwidth. Similar to HTTP, WebSocket uses an established TCP connection to transmit data. However, it is different from HTTP.

One major difference between WebSocket and HTTP is that WebSocket is a two-way communication protocol. After a connection is established, a WebSocket server and client can send or receive data between each other similar to a socket. The WebSocket server and client must complete a handshake to establish a WebSocket connection.

WebSocket Secure is the encrypted version of WebSocket.

## Background information about WebSocket and WebSocket Secure

New web applications emerge as the Internet develops. These applications, such as live video streaming and online chat rooms, require that servers have real-time pushing capabilities. To implement pushing, a large number of websites used the polling technique. Based on the polling technique, the browser sends HTTP requests to the server at specific intervals, such as every second. Then, the server returns the most recent data to the browser of the client. One disadvantage of this technique is that bandwidth resources are wasted. The browser must constantly send requests to the server, and the HTTP request header is long and does not contain a large amount of valid data.

To solve this problem, HTML5 defines WebSocket, which helps save server and bandwidth resources and facilitates real-time communication. WebSocket supports full-duplex communication between clients and servers and allows a server to send requests to a client.

The following figure shows how a client interacts with a server by using WebSocket.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7173498951/p3247.png)

## How to enable WebSocket and WebSocket Secure for an SLB instance

No configuration is required. HTTP listeners support WebSocket and HTTPS listeners support WebSocket Secure by default.

**Note:** You must upgrade the SLB instance to a guaranteed-performance instance. For more information, see [Guaranteed-performance instance FAQ](/intl.en-US/Classic Load Balancer/User Guide/Instance/FAQ/Guaranteed-performance instance FAQ.md).

## Supported regions

WebSocket and WebSocket Secure are available in all regions.

## Limits

The following section describes the limits for WebSocket and WebSocket Secure:

-   SLB is connected to backend ECS instances by using HTTP/1.1. We recommend that you use web servers that support HTTP/1.1 for backend ECS instances.
-   If no message interactions exist between an SLB instance and backend ECS instances within 60 seconds, the connection is terminated. If you need to maintain the connection, enable Keepalive to ensure a message interaction at the frequency of once every 60 seconds.

## Billing

WebSocket and WebSocket Secure are free of charge.

