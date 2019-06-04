# Certificate requirements {#concept_omx_hqn_vdb .concept}

Server Load Balancer \(SLB\) only supports certificates in the PEM format. Before you upload a certificate, make sure that the certificate content, certificate chain, and private key conform to the corresponding format requirements.

## Certificates issued by a root CA {#section_pgv_4nb_wdb .section}

If the certificate is issued by a root CA, the received certificate is the only one required to be uploaded to SLB. In this case, the website that is configured with the certificate will be regarded as a trusted website and does not require additional certificates.

The certificate format must meet the following format requirements:

-   The certificate must start with `-----BEGIN CERTIFICATE-----`, and end with `-----END CERTIFICATE-----`, and both parts must be uploaded together.
-   Each line except the last line must contain exactly 64 characters. The last line can contain 64 or fewer characters.
-   Spaces are not allowed in the certificate content.

The following is a sample certificate issued by a root CA.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4142/15596122012839_en-US.jpg)

## Certificates issued by an intermediate CA {#section_vyv_vnb_wdb .section}

If the certificate is issued by an intermediate CA, you are able to obtain multiple intermediate certificates. You must upload both the server certificate and the required number of immediate certificates to SLB.

The format of the certificate chain must meet the following requirements:

-   Paste the server certificate content first, and then paste the content of the one or more required intermediate certificates directly underneath without any blank lines in between the certificates.
-   Spaces are not allowed in the content.
-   Blank lines are not allowed in the content. Each line must contain exactly 64 characters. For more information, see [RFC1421](https://tools.ietf.org/html/rfc1421).
-   The certificate must conform to the corresponding format requirements. Generally, the intermediate CA will provide instructions about the certificate format when issuing the certificate. The certificate chain must conform to the format requirements.

The following is a sample certificate chain.

```
    -----BEGIN CERTIFICATE-----
    -----END CERTIFICATE-----
    -----BEGIN CERTIFICATE-----
    -----END CERTIFICATE-----
    -----BEGIN CERTIFICATE-----
    -----END CERTIFICATE-----
```

## RSA private key {#section_qgl_znb_wdb .section}

When you upload the server certificate, you also need to upload the private key of the certificate.

The RSA private key format must meet the following requirements:

-   The private key must start with `-----BEGIN RSA PRIVATE KEY-----`, and end with `-----END RSA PRIVATE KEY-----`, and both parts must be uploaded together.
-   Blank lines are not allowed in the content. Each line except the last line must contain exactly 64 characters. The last line can contain 64 or fewer characters. For more information, see [RFC1421](https://tools.ietf.org/html/rfc1421).

If your private key is encrypted \(for example, the content at the beginning and end of the private key is `-----BEGIN PRIVATE KEY-----, -----END PRIVATE KEY-----` or `-----BEGIN ENCRYPTED PRIVATE KEY-----, -----END ENCRYPTED PRIVATE KEY-----`, or the private key contains `Proc-Type: 4,ENCRYPTED`\), you must first run the following command to convert the private key:

```
openssl rsa -in old_server_key.pem -out new_server_key.pem
```

The following is a sample RSA private key.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4142/15596122012840_en-US.jpg)

## EC private key {#section_mb5_a98_j83 .section}

**Note:** Currently, EC private keys are supported only in the UK \(London\) region.

When you upload the server certificate, you also need to upload the private key of the certificate.

The EC private key format must meet the following requirements:

-   The private key must start with `-----BEGIN EC PARAMETERS-----`, and end with `-----END EC PARAMETERS-----`, and both parts must be uploaded together.
-   Blank lines are not allowed in the content. Each line except the last line must contain exactly 64 characters. The last line can contain 64 or fewer characters. For more information, see [RFC1421](https://tools.ietf.org/html/rfc1421).

If your private key is encrypted \(for example, the content at the beginning and end of the private key is `-----BEGIN EC PRIVATE KEY-----, -----END EC PRIVATE KEY-----`, or the private key contains `Proc-Type: 4,ENCRYPTED`\), you must first run the following command to convert the private key:

``` {#codeblock_bsj_oro_u6k}
openssl rsa -in old_server_key.pem -out new_server_key.pem
```

The following is a sample EC private key.

``` {#codeblock_wo7_3cj_9ap}
-----BEGIN EC PARAMETERS-----
Bggq**********Bw==
-----END EC PARAMETERS-----
-----BEGIN EC PRIVATE KEY-----
MHcCAQEEICo9b+vQUhqFUWgWjE0YY4h0b3bE/udcubxVwcVY99MuoAoGCCqGSM49
AwEHoUQDQgAEgpla3Bj9rX**********4xz0SHsuQc/7XBmgmrMpAmE80c0DR
5HcMHFxRPtGLv22T62e5KqN1W3uN9Hplgg==
-----END EC PRIVATE KEY-----
```

