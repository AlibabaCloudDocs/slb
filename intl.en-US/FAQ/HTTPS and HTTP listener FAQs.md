# HTTPS and HTTP listener FAQs {#concept_ldw_gh5_vdb .concept}

-   [Why are some response header parameters deleted after requests are forwarded by Layer-7 listeners?](#section_iv5_pyx_wdb)
-   [Why is an additional header, namely the Transfer-Encoding: chunked, added to an HTTP request?](#section_kv5_pyx_wdb)
-   [Why do the style sheets fail to load when I open a website through an HTTPS listener?](#section_lv5_pyx_wdb)
-   [Which port number do HTTPS listeners use?](#section_ov5_pyx_wdb)
-   [What types of certificates does SLB support?](#section_pv5_pyx_wdb)
-   [Does SLB support keytool-created certificates?](#section_qv5_pyx_wdb)
-   [Can I use certificates in the PKCS\#12\(PFX\) format?](#section_rv5_pyx_wdb)
-   [Why does a KeyEncryption error occur when uploading certificates?](#section_tv5_pyx_wdb)
-   [What SSL protocol versions are supported by the HTTPS Server Load Balancer service?](#section_vv5_pyx_wdb)
-   [What is the lifetime of an HTTPS session ticket?](reseller.en-US/FAQ/HTTPS and HTTP listener FAQs.md#section_xv5_pyx_wdb)
-   [Can I upload a certificate containing DH PARAMETERS?](reseller.en-US/FAQ/HTTPS and HTTP listener FAQs.md#section_yv5_pyx_wdb)
-   [Do HTTPS listeners support SNI?](#section_zv5_pyx_wdb)
-   [Which HTTP version is used by HTTP and HTTPS listeners to access the backend servers?](#section_aw5_pyx_wdb)
-   [Can backend ECS instances obtain the protocol version used by the client to access the HTTP or HTTPS listener?](#section_bw5_pyx_wdb)
-   [What are the timeout values specified for HTTP and HTTPS listeners?](#section_d44_xyx_wdb)

## Why are some response header parameters deleted after requests are forwarded by Layer-7 listeners? {#section_iv5_pyx_wdb .section}

Symptoms: SLB modifies the values of the Date, Server, X-Pad, X-Accel-Redirect and other parameters in the response headers to achieve session persistence.

Solution:

-   Add a prefix to the custom header, such as xl-server or xl-date.
-   Change the Layer-7 listener to a Layer-4 listener.

## Why is an additional header, namely the Transfer-Encoding: chunked, added to an HTTP request? {#section_kv5_pyx_wdb .section}

Symptoms: After a domain name is resolved into the IP address of a Layer-7 SLB instance, a Transfer-Encoding: chunked field is added in the HTTP request header when accessing the domain name from a local host. However, no such field is found in the request when accessing backend servers directly from the local host.

Layer-7 SLB is based on the Tengine reverse proxy. The Transfer-Encoding field indicates how the Web server encodes the response message body. For example, Transfer-Encoding: chunked indicates the chunked transfer encoding is used.

**Note:** This header is not added in the requests forwarded by Layer-4 listeners, because Layer-4 listeners only distribute traffic.

## Why do the style sheets fail to load when I open a website through an HTTPS listener? {#section_lv5_pyx_wdb .section}

Symptoms:

An HTTP listener and an HTTPS listener are created respectively, and they use the same backend servers. When accessing the website over the HTTP listener with the specified port number, the website is displayed normally. However, the website layout is messy when accessing the website through the HTTPS listener.

Cause:

By default, SLB does not block loading and transferring JavaScript files. The possible reasons are as follows:

-   The certificate is not compatible with the security level of the web browser.
-   The certificate is an unqualified third-party certificate. In this case, contact the certificate issuer to check the certificate.

Solution:

1.  When you open the website, click the prompt in the browser's address bar to load the script.
2.  Add the required certificate to the browser.

## Which port number do HTTPS listeners use? {#section_ov5_pyx_wdb .section}

There are no special requirements on ports. However, we recommend that you use 443 as the port number for HTTPS listeners.

## What types of certificates does SLB support? {#section_pv5_pyx_wdb .section}

SLB supports uploading server certificates and CA certificates in the PEM format.

For the server certificates, you must upload both the certificate content and the private key. For the CA certificates, you only need to upload the certificate content.

## Does SLB support keytool-created certificates? {#section_qv5_pyx_wdb .section}

Yes.

However, you must convert the certificate format to PEM before uploading the certificate to SLB. For more information, see [Convert certificate format](../../../../../reseller.en-US/Archives/User Guide (Old Console)/Certificate management/Convert certificate formats.md#).

## Can I use certificates in the PKCS\#12\(PFX\) format? {#section_rv5_pyx_wdb .section}

Yes.

However, you must convert the certificate format to PEM before uploading the certificate to SLB. For more information, see [Convert certificate format](../../../../../reseller.en-US/Archives/User Guide (Old Console)/Certificate management/Convert certificate formats.md#).

## Why does a KeyEncryption error occur when uploading certificates? {#section_tv5_pyx_wdb .section}

The private key contains incorrect contents. For more information on private key format, see [Certificate formats](../../../../../reseller.en-US/Archives/User Guide (Old Console)/Certificate management/Certificate requirements.md#).

## What SSL protocol versions are supported by the HTTPS Server Load Balancer service? {#section_vv5_pyx_wdb .section}

TLSv1, TLSv1.1, and TLSv1.2.

## What is the lifetime of an HTTPS session ticket? {#section_xv5_pyx_wdb .section}

The lifetime of an HTTPS session ticket is set to 300 seconds.

## Can I upload a certificate containing DH PARAMETERS? {#section_yv5_pyx_wdb .section}

No. The ECDHE method used by HTTPS listeners supports forward secrecy, but does not support uploading the PEM files that contain the security enhancement parameters, such as BEGIN DH PARAMETERS.

## Do HTTPS listeners support SNI? {#section_zv5_pyx_wdb .section}

Yes. SNI \(Server Name Indication\) is an extension to SSL/TLS protocol so that a server can use multiple domain names and certificates. SLB HTTPS supports the SNI function. For more information, see [Configuration tutorial](../../../../../reseller.en-US/Archives/User Guide (Old Console)/Listener/Layer-7 listeners/Domain name extension/Configuration tutorial.md#).

## Which HTTP version is used by HTTP and HTTPS listeners to access the backend servers? {#section_aw5_pyx_wdb .section}

-   When the protocol used by client requests is HTTP/1.1 or HTTP2/0, Layer-7 listeners use HTTP/1.1 to access backend servers.
-   When the protocol used by client requests is neither HTTP/1.1 or HTTP2/0, Layer-7 listeners use HTTP/1.0 to access backend servers.

## Can backend ECS instances obtain the protocol version used by the client to access the HTTP or HTTPS listener? {#section_bw5_pyx_wdb .section}

Yes.

## What are the timeout values specified for HTTP and HTTPS listeners? {#section_d44_xyx_wdb .section}

-   A maximum of 100 requests can be sent continuously in an HTTP persistent connection. The connection is closed when the limit is reached.
-   The timeout between two HTTP or HTTPS requests in an HTTP persistent connection is 15 seconds. The TCP connection is closed when the timeout exceeds 15 seconds. If you want to use the HTTP persistent connection, try to send heartbeat requests within 13 seconds.
-   The timeout for the TCP three-way handshake between SLB and a backend ECS instance is 5 seconds. After the handshake times out, SLB selects the next ECS instance. You can find the timeout by checking the upstream response time in the access logs.
-   The time that SLB waits for the response from an ECS instance is 60 seconds. If the wait time exceeds 60 seconds, a 504 or 408 status code is sent to the client. You can find the timeout by checking the upstream response time in the access logs.
-   The HTTPS session reuse times out after 300 seconds. After the timeout, the client needs to perform the complete SSL handshake process again.

