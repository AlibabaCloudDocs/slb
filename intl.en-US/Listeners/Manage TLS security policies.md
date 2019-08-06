# Manage TLS security policies {#concept_pvl_f1v_cfb .concept}

When you add or configure an HTTPS listener for a guaranteed-performance Server Load Balancer \(SLB\) instance, you can select from a variety of TLS security policies and apply one according to your requirements.

You can select a TLS security policy when you set advanced configurations of **SSL Certificates** for an HTTPS listener. For more information, see [Add an HTTPS listener](../../../../reseller.en-US/Listeners/Add an HTTPS listener.md#).

![Configure the listener](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21323/156509653611859_en-US.png)

A TLS security policy contains supported TLS protocol versions and cipher suites.

## TLS security policy {#section_vzd_jdv_cfb .section}

|Security policy|Feature|Supported TLS version|Supported cipher suite|
|---------------|-------|---------------------|----------------------|
|tls\_cipher\_policy\_1\_0|Optimal compatibility and with basic security|TLSv1.0, TLSv1.1, and TLSv1.2|ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA|
|tls\_cipher\_policy\_1\_1|Compatible and with standard security|TLSv1.1 and TLSv1.2|ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA|
|tls\_cipher\_policy\_1\_2|Compatible and with advanced security|TLSv1.2|ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA|
|tls\_cipher\_policy\_1\_2\_strict|Supports only perfect forward secrecy \(PFS\) cipher suites and offers premium security.|TLSv1.2|ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, ECDHE-RSA-AES128-SHA, and ECDHE-RSA-AES256-SHA|
|tls\_cipher\_policy\_1\_2\_strict\_with\_1\_3 **Note:** Currently, TLS1.3 is supported in the following regions:

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

 |Supports only perfect forward secrecy \(PFS\) cipher suites and offers premium security.|TLS1.2 and TLS1.3|TLS\_AES\_128\_GCM\_SHA256, TLS\_AES\_256\_GCM\_SHA384, TLS\_CHACHA20\_POLY1305\_SHA256, TLS\_AES\_128\_CCM\_SHA256, TLS\_AES\_128\_CCM\_8\_SHA256, ECDHE-ECDSA-AES128-GCM-SHA256, ECDHE-ECDSA-AES256-GCM-SHA384, ECDHE-ECDSA-AES128-SHA256, ECDHE-ECDSA-AES256-SHA384, ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, ECDHE-ECDSA-AES128-SHA, ECDHE-ECDSA-AES256-SHA, ECDHE-RSA-AES128-SHA, and ECDHE-RSA-AES256-SHA|

## Algorithm support of different TLS security policies {#section_dls_q2v_cfb .section}

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

