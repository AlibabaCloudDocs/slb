# HTTP/2 support FAQ {#concept_oyq_hh5_vdb .concept}

## What is HTTP/2? {#section_a3f_yzx_wdb .section}

HTTP/2 \(Hypertext Transfer Protocol Version 2\) is the second version of Hypertext Transfer Protocol \(HTTP\). It is compatible with HTTP/1.X and has significant performance improvement.

Compared with HTTP/1.X, HTTP/2 has the following advantages:

-   Multiplexing: Allows multiple request-response messages to be initiated simultaneously over a single HTTP/2 connection.
-   Binary framing and header compression: Improves the efficiency of data transmission in the network.
-   Server push: The server actively sends data to the client to reduce the number of requests, which improves efficiency.
-   Additionally, features such as flow control, active request resetting, and request priority greatly improve the performance of web services, as shown in the following figure.
-   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4294/15586048113266_en-US.png)


## How to enable HTTP/2 on Server Load Balancer of Alibaba Cloud? {#section_mnn_31y_wdb .section}

No configuration is required. HTTP/2 is supported by HTTPS listeners by default.

**Note:** You must upgrade the instance to a guaranteed-performance instance. For more information, see [How to use guaranteed-performance instances](../../../../intl.en-US/FAQ/FAQ/How to use guaranteed-performance Server Load Balancer instances?.md#).

The Server Load Balancer HTTPS listener detects the ALPN field in the handshake message ClientHello sent from the client to negotiate the protocol version. If the ALPN field is not included in the ClientHello message, HTTP/1.x is used to handle the request. If the ALPN field is included, HTTP/2 is used.

**Note:** HTTP/2 only supports HTTPS listeners and does not support HTTP/2 Cleartext.

## Supported regions {#section_onn_31y_wdb .section}

The HTTP/2 support is available in all regions.

## Limits {#section_pnn_31y_wdb .section}

The limits for HTTP/2 support are as follows:

-   HTTP/2 only supports HTTP listeners and does not support HTTP/2 Cleartext.
-   Currently HTTP/2 is enabled only on the link between the client and Server Load Balancer. The connection between Server Load Balancer and the backend servers still uses HTTP/1. X.
-   The requests of HTTP/2 are counted into the QPS of the listener/instance together with the QPS of HTTP/1.X requests.
-   For HTTP/2, the head field in the response sent from the backend server to SLB is changed to lowercase, for example, Content-Type is changed to content-type.
-   A single connection can support up to 128 concurrent streams.
-   The connection timeout value of HTTP/2 is 180 seconds.

## Billing {#section_rnn_31y_wdb .section}

HTTP/2 support is free of charge.

