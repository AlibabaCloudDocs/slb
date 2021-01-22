# FAQ about Layer 7 listeners that use HTTPS or HTTP

The following questions about Layer 7 listeners that use HTTPS or HTTP are frequently asked:

-   [Why are some response header parameters deleted after requests are forwarded by Layer 7 listeners?](#section_iv5_pyx_wdb)
-   [Why is an additional header, Transfer-Encoding: chunked, added to an HTTP request?](#section_kv5_pyx_wdb)
-   [Why do the style sheets fail to load when I open a website over an HTTPS listener?](#section_lv5_pyx_wdb)
-   [Which port number do HTTPS listeners use?](#section_ov5_pyx_wdb)
-   [What types of certificates does SLB support?](#section_pv5_pyx_wdb)
-   [Does SLB support keytool-created certificates?](#section_qv5_pyx_wdb)
-   [Can I use certificates in the PKCS\#12 \(PFX\) format?](#section_rv5_pyx_wdb)
-   [Why does a KeyEncryption error occur when I upload certificates?](#section_tv5_pyx_wdb)
-   [What SSL protocol versions are supported by the HTTPS Server Load Balancer service?](#section_vv5_pyx_wdb)
-   [What is the lifetime of an HTTPS session ticket?](#section_xv5_pyx_wdb)
-   [Can I upload a certificate that contains DH PARAMETERS?](#section_yv5_pyx_wdb)
-   [Do HTTPS listeners support SNI?](#section_zv5_pyx_wdb)
-   [Which version of HTTP is used by HTTP and HTTPS listeners to access the backend servers?](#section_aw5_pyx_wdb)
-   [Can backend servers obtain the protocol version used by the client to access the HTTP or HTTPS listener?](#section_bw5_pyx_wdb)
-   [What are the timeout values specified for HTTP and HTTPS listeners?](#section_d44_xyx_wdb)

## Why are some response header parameters deleted after requests are forwarded by Layer 7 listeners?

Symptom: SLB modifies the values of the Date, Server, X-Pad, and X-Accel-Redirect parameters in the response headers to implement session persistence.

Solution:

-   Add a prefix to the custom header, such as xl-server or xl-date.
-   Change Layer 7 HTTP listeners to Layer 4 TCP listeners.

## Why is an additional header, Transfer-Encoding: chunked, added to an HTTP request?

Symptom: After a domain name is resolved to the service address of Layer 7 SLB instance, a Transfer-Encoding: chunked field is added in the HTTP request header when you access the domain name from a local host. However, this field is not found in the request when you access backend servers directly from the local host.

Cause: Layer 7 SLB is based on the Tengine reverse proxy. The Transfer-Encoding field indicates how the web server encodes the response message body. For example, Transfer-Encoding: chunked indicates that chunked transfer encoding is used.

**Note:** This header is not added in the requests forwarded by Layer 4 listeners, because Layer 4 listeners only distribute traffic.

## Why do the style sheets fail to load when I open a website over an HTTPS listener?

Symptom:

An HTTP listener and an HTTPS listener are created, and they use the same backend servers. When you access the website over the HTTP listener with the specified port number, the website is displayed normally. However, the website layout is messy when you access the website over the HTTPS listener.

Cause:

By default, SLB does not block loading and transferring of JavaScript files. This problem may be caused by the following reasons:

-   The certificate is not compatible with the security level of the web browser.
-   The certificate is an unqualified third-party certificate. In this case, contact the certificate issuer to check the certificate.

Solution:

1.  When you open the website, load scripts as prompted by the browser.
2.  Add the required certificate to the browser.

## Which port number do HTTPS listeners use?

HTTPS listeners have no special requirements on ports. However, we recommend that you use 443 as the port number for HTTPS listeners.

## What types of certificates does SLB support?

SLB supports server certificates and CA certificates in the PEM format.

For the server certificates, you must upload both the certificate content and the private key. For the CA certificates, you need to upload only the certificate content.

## Does SLB support keytool-created certificates?

Yes.

You must convert the certificate format to PEM before you upload the certificates to SLB. For more information, see [Convert the certificate format](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Convert the certificate format.md).

## Can I use certificates in the PKCS\#12 \(PFX\) format?

Yes.

You must convert the certificate format to PEM before you upload the certificates to SLB. For more information, see [Convert the certificate format](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Convert the certificate format.md).

## Why does a KeyEncryption error occur when I upload certificates?

The private key contains incorrect contents. For more information about the private key format, see [Certificate requirements](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Certificate requirements.md).

## What SSL protocol versions are supported by the HTTPS Server Load Balancer service?

TLSv1, TLSv1.1, and TLSv1.2.

## What is the lifetime of an HTTPS session ticket?

The lifetime of an HTTPS session ticket is set to 300 seconds.

## Can I upload a certificate that contains DH PARAMETERS?

The ECDHE cipher suites used by HTTPS listeners support forward secrecy but do not support the security enhancement parameters required by DHE cipher suites. As a result, strings that contain the BEGIN DH PARAMETERS field in a PEM certificate file cannot be uploaded.

## Do HTTPS listeners support SNI?

Yes. Server Name Indication \(SNI\) is an extension to the SSL or TLS protocol so that a server can use multiple domain names and certificates. HTTPS listeners support the SNI feature. For more information, see [Add a domain name extension](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Domain name extensions/Add a domain name extension.md).

## Which version of HTTP is used by HTTP and HTTPS listeners to access the backend servers?

-   When the protocol used by client requests is HTTP/1.1 or HTTP2/0, Layer 7 listeners use HTTP/1.1 to access backend servers.
-   When the protocol used by client requests is not HTTP/1.1 or HTTP2/0, Layer 7 listeners use HTTP/1.0 to access backend servers.

## Can backend servers obtain the protocol version used by the client to access the HTTP or HTTPS listener?

Yes, backend servers can obtain the protocol version used by the client to access the HTTP or HTTPS listener.

## What are the timeout values specified for HTTP and HTTPS listeners?

-   A maximum of 100 requests can be sent continuously in an HTTP persistent connection. The connection is closed when the limit is reached.
-   The timeout period between two HTTP or HTTPS requests in an HTTP persistent connection can be set to a value ranging from 1 to 60 seconds. The TCP connection is closed when the timeout period exceeds the specified value. If you want to use the HTTP persistent connection, try to send heartbeat requests within 13 seconds.
-   The timeout period for the TCP three-way handshake between SLB and a backend ECS instance is 5 seconds. After the handshake times out, SLB selects the next ECS instance. You can find the timeout record by checking the upstream response time in the access logs.
-   The time that SLB waits for the response from an ECS instance can be set to a value ranging from 1 to 180 seconds. If the wait time exceeds the specified timeout period, a 504 or 408 status code is sent to the client. You can find the timeout record by checking the upstream response time in the access logs.
-   After 300 seconds, the HTTPS session reuse times out. Then, the client must perform the complete SSL handshake process again.

