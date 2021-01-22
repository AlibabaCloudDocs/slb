# Manage TLS security policies

When you create or configure an HTTPS listener for a guaranteed-performance server load balancer \(SLB\) instance, you can select from a variety of TLS security policies.

When you create or configure an HTTPS listener, you can modify the advanced settings in the **SSL Certificates** step and select a TLS security policy. For more information, see [Add an HTTPS listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTPS listener.md).

![Configure the listener](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7553598951/p11859.png)

A TLS security policy contains available TLS protocols and supported cipher suites.

## TLS security policies

|Security policy|Feature|Supported TLS version|Supported cipher suite|
|---------------|-------|---------------------|----------------------|
|tls\_cipher\_policy\_1\_0|Provides optimal compatibility and basic security|TLSv1.0, TLSv1.1, and TLSv1.2|ECDHE-ECDSA-AES128-GCM-SHA256, ECDHE-ECDSA-AES256-GCM-SHA384, ECDHE-ECDSA-AES128-SHA256, ECDHE-ECDSA-AES256-SHA384, ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-ECDSA-AES128-SHA, ECDHE-ECDSA-AES256-SHA, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA|
|tls\_cipher\_policy\_1\_1|Provides high compatibility and standard security|TLSv1.1 and TLSv1.2|ECDHE-ECDSA-AES128-GCM-SHA256, ECDHE-ECDSA-AES256-GCM-SHA384, ECDHE-ECDSA-AES128-SHA256, ECDHE-ECDSA-AES256-SHA384, ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-ECDSA-AES128-SHA, ECDHE-ECDSA-AES256-SHA, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA|
|tls\_cipher\_policy\_1\_2|Provides high compatibility and advanced security|TLSv1.2|ECDHE-ECDSA-AES128-GCM-SHA256, ECDHE-ECDSA-AES256-GCM-SHA384, ECDHE-ECDSA-AES128-SHA256, ECDHE-ECDSA-AES256-SHA384, ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256,AES256-SHA256, ECDHE-ECDSA-AES128-SHA, ECDHE-ECDSA-AES256-SHA, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA|
|tls\_cipher\_policy\_1\_2\_strict|Supports only perfect forward secrecy \(PFS\) cipher suites and provides premium security.|TLSv1.2|ECDHE-ECDSA-AES128-GCM-SHA256, ECDHE-ECDSA-AES256-GCM-SHA384, ECDHE-ECDSA-AES128-SHA256, ECDHE-ECDSA-AES256-SHA384, ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, ECDHE-ECDSA-AES128-SHA, ECDHE-ECDSA-AES256-SHA, ECDHE-RSA-AES128-SHA, and ECDHE-RSA-AES256-SHA|
|tls\_cipher\_policy\_1\_2\_strict\_with\_1\_3 **Note:** TLSv1.3 is supported in the following regions:

-   UK \(London\)
-   China \(Qingdao\)
-   China \(Hohhot\)
-   China \(Chengdu\)
-   Japan \(Tokyo\)
-   India \(Mumbai\)
-   Australia \(Sydney\)
-   Malaysia \(Kuala Lumpur\)
-   US \(Silicon Valley\)
-   US \(Virginia\)
-   Germany \(Frankfurt\)
-   UAE \(Dubai\)

|Supports only perfect forward secrecy \(PFS\) cipher suites and provides premium security.|TLSv1.2 and TLSv1.3|TLS\_AES\_128\_GCM\_SHA256, TLS\_AES\_256\_GCM\_SHA384, TLS\_CHACHA20\_POLY1305\_SHA256, TLS\_AES\_128\_CCM\_SHA256, TLS\_AES\_128\_CCM\_8\_SHA256, ECDHE-ECDSA-AES128-GCM-SHA256, ECDHE-ECDSA-AES256-GCM-SHA384, ECDHE-ECDSA-AES128-SHA256, ECDHE-ECDSA-AES256-SHA384, ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, ECDHE-ECDSA-AES128-SHA, ECDHE-ECDSA-AES256-SHA, ECDHE-RSA-AES128-SHA, and ECDHE-RSA-AES256-SHA|

## Cipher suites supported by different TLS security policies

|Security policy|tls\_cipher\_policy\_1\_0|tls\_cipher\_policy\_1\_1|tls\_cipher\_policy\_1\_2|tls\_cipher\_policy\_1\_2\_strict|tls\_cipher\_policy\_1\_2\_strict\_with\_1\_3|
|---------------|-------------------------|-------------------------|-------------------------|---------------------------------|---------------------------------------------|
|TLS|-|1.2/1.1/1.0|1.2/1.1|1.2|1.2|1.2 and 1.3|
|CIPHER|ECDHE-RSA-AES128-GCM-SHA256|✔|✔|✔|✔|✔|
|ECDHE-RSA-AES256-GCM-SHA384|✔|✔|✔|✔|✔|
|ECDHE-RSA-AES128-SHA256|✔|✔|✔|✔|✔|
|ECDHE-RSA-AES256-SHA384|✔|✔|✔|✔|✔|
|AES128-GCM-SHA256|✔|✔|✔|-|-|
|AES256-GCM-SHA384|✔|✔|✔|-|-|
|AES128-SHA256|✔|✔|✔|-|-|
|AES256-SHA256|✔|✔|✔|-|-|
|ECDHE-RSA-AES128-SHA|✔|✔|✔|✔|✔|
|ECDHE-RSA-AES256-SHA|✔|✔|✔|✔|✔|
|AES128-SHA|✔|✔|✔|-|-|
|AES256-SHA|✔|✔|✔|-|-|
|DES-CBC3-SHA|✔|✔|✔|-|-|
|TLS\_AES\_128\_GCM\_SHA256|-|-|-|-|✔|
|TLS\_AES\_256\_GCM\_SHA384|-|-|-|-|✔|
|TLS\_CHACHA20\_POLY1305\_SHA256|-|-|-|-|✔|
|TLS\_AES\_128\_CCM\_SHA256|-|-|-|-|✔|
|TLS\_AES\_128\_CCM\_8\_SHA256|-|-|-|-|✔|
|ECDHE-ECDSA-AES128-GCM-SHA256|-|-|-|-|✔|
|ECDHE-ECDSA-AES256-GCM-SHA384|-|-|-|-|✔|
|ECDHE-ECDSA-AES128-SHA256|-|-|-|-|✔|
|ECDHE-ECDSA-AES256-SHA384|-|-|-|-|✔|
|ECDHE-ECDSA-AES128-SHA|-|-|-|-|✔|
|ECDHE-ECDSA-AES256-SHA|-|-|-|-|✔|

