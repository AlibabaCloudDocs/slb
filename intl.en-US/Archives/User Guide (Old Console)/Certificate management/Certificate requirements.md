# Certificate requirements {#concept_omx_hqn_vdb .concept}

Server Load Balancer only supports certificates in the PEM format. The certificate, certificate chain, and private key must conform to the rules described in this section.

## Certificates issued by a root CA {#section_pgv_4nb_wdb .section}

If the certificate is issued by a root CA, the received certificate is the only one that is required to upload to Server Load Balancer. The website that is configured with the certificate will be trusted by the web browser without configuring additional certificates.

The certificate format must meet the following requirements:

-   The certificate content is placed between `-----BEGIN CERTIFICATE-----, -----END CERTIFICATE-----`. Include the header and footer when uploading the certificate. 
-   Each line except the last must contain exactly 64 characters. The last line can contain 64 or fewer characters.
-   Space is not allowed in the content.

The following is a sample certificate issued by a root CA.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4142/2839_en-US.jpg)

## Certificates issued by an intermediate CA {#section_vyv_vnb_wdb .section}

If a certificate is issued by an intermediate CA, you will obtain multiple intermediate certificates. You must combine the server certificate and the immediate certificate first, and then upload it to Server Load Balancer.

The format of the certificate chain must meet the following requirements:

-   Put the server certificate in the first place and the intermediate certificates in the second place without any space in between.
-   Space is not allowed in the content.
-   Each line except the last must contain exactly 64 characters. The last line must contain 64 or fewer characters. For more information, see [RFC1421](https://tools.ietf.org/html/rfc1421).
-   Conform to the certificate requirements as described in the certificate description. In general, the intermediate CA will provide an instruction about the certificate format when issuing the certificate, the certificate chain must conform to the format requirements.

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

When uploading a server certificate, you also need to upload the private key of the certificate.

The RSA private key format must meet the following requirements:

-   The key is placed between `-----BEGIN RSA PRIVATE KEY-----, -----END RSA PRIVATE KEY-----`. Include the header and footer when uploading the key.
-   Space is not allowed in the content. Each line except the last must contain exactly 64 characters. The last line can contain 64 or fewer characters. For more information, see [RFC1421](https://tools.ietf.org/html/rfc1421).

If your private key is encrypted. For example, the header and footer are `-----BEGIN PRIVATE KEY-----, -----END PRIVATE KEY-----` or `-----BEGIN ENCRYPTED PRIVATE KEY-----, -----END ENCRYPTED PRIVATE KEY-----`, or the private key contains `Proc-Type: 4,ENCRYPTED`, run the following command to convert the private key before uploading it to Server Load Balancer:

```
openssl rsa -in old_server_key.pem -out new_server_key.pem
```

The following is a sample RSA private key.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4142/2840_en-US.jpg)

