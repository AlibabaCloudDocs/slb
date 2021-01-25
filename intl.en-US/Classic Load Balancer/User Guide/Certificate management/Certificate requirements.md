# Certificate requirements

Server Load Balancer \(SLB\) supports only certificates in the PEM format. Before you upload a certificate, make sure that the certificate content, certificate chain, and private key conform to the corresponding format requirements.

## Certificates issued by a root CA

If the certificate was issued by a root certification authority \(CA\), the received certificate is the only one that needs to be uploaded to SLB. In this case, the website configured with this certificate is regarded as a trusted website, and does not require additional certificates.

The certificate must meet the following format requirements:

-   The certificate must start with `-----BEGIN CERTIFICATE-----` and end with -----END CERTIFICATE-----.
-   Each line \(except the last line\) must contain 64 characters. The last line can contain 64 or fewer characters.
-   The certificate content cannot contain spaces.

The following figure shows a sample certificate in the PEM format issued by a root CA.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8313359951/p2839.jpg)

## Certificates issued by an intermediate CA

If the certificate was issued by an intermediate CA, the received certificate file contains multiple certificates. You must upload both the server certificate and the required intermediate certificates to SLB.

The format of the certificate chain must meet the following requirements:

-   The server certificate must be put first and the content of the one or more required intermediate certificates must be put underneath without blank lines between the certificates.
-   The certificate content cannot contain spaces.
-   Blank lines are not allowed between the certificates. Each line must contain 64 characters. For more information, see [RFC 1421](https://tools.ietf.org/html/rfc1421).
-   Certificates must conform to the corresponding format requirements. Generally, the intermediate CA provides instructions about the certificate format when certificates are issued. The certificates must conform to the format requirements.

The following section provides a sample certificate chain.

```
    -----BEGIN CERTIFICATE-----
    -----END CERTIFICATE-----
    -----BEGIN CERTIFICATE-----
    -----END CERTIFICATE-----
    -----BEGIN CERTIFICATE-----
    -----END CERTIFICATE-----
```

## Public keys of certificates

SLB supports the following public key algorithms:

-   RSA 1024
-   RSA 2048
-   RSA 4096
-   ECDSA P-256
-   ECDSA P-384
-   ECDSA P-521

## RSA private keys

When you upload a server certificate, you must upload the private key of the certificate.

An RSA private key must meet the following format requirements:

-   The private key must start with `-----BEGIN RSA PRIVATE KEY-----` and end with -----END RSA PRIVATE KEY-----, and these parts must also be uploaded.
-   Blank lines are not allowed in the content. Each line \(except the last line\) must contain 64 characters. The last line can contain 64 or fewer characters. For more information, see [RFC 1421](https://tools.ietf.org/html/rfc1421).

You may use an encrypted private key. For example, the private key starts with `-----BEGIN PRIVATE KEY-----` and ends with -----END PRIVATE KEY-----, or starts with `-----BEGIN ENCRYPTED PRIVATE KEY-----` and ends with -----END ENCRYPTED PRIVATE KEY-----. The private key may also contain `Proc-Type: 4,ENCRYPTED`. In this case, you must first run the following command to convert the private key:

```
openssl rsa -in old_server_key.pem -out new_server_key.pem
```

The following figure shows a sample RSA private key.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8313359951/p2840.jpg)

## EC private keys

**Note:** EC private keys are only supported in the UK \(London\) region.

When you upload a server certificate, you must upload the private key of the certificate.

An EC private key must meet the following format requirements:

-   The private key must start with `-----BEGIN EC PARAMETERS-----` and end with -----END EC PARAMETERS-----, and these parts must also be uploaded.
-   Blank lines are not allowed in the content. Each line \(except the last line\) must contain 64 characters. The last line can contain 64 or fewer characters. For more information, see [RFC 1421](https://tools.ietf.org/html/rfc1421).

You may use an encrypted private key. For example, the private key starts with `-----BEGIN EC PRIVATE KEY-----` and ends with -----END EC PRIVATE KEY-----, or contains `Proc-Type: 4,ENCRYPTED`. In this case, you must first run the following command to convert the private key:

```
openssl ec -in old_server_key.pem -out new_server_key.pem
```

The following section provides a sample EC private key.

```
-----BEGIN EC PARAMETERS-----
Bggq**********Bw==
-----END EC PARAMETERS-----
-----BEGIN EC PRIVATE KEY-----
MHcCAQEEICo9b+vQUhqFUWgWjE0YY4h0b3bE/udcubxVwcVY99MuoAoGCCqGSM49
AwEHoUQDQgAEgpla3Bj9rX**********4xz0SHsuQc/7XBmgmrMpAmE80c0DR
5HcMHFxRPtGLv22T62e5KqN1W3uN9Hplgg==
-----END EC PRIVATE KEY-----
```

