# Overview {#concept_ekm_gj1_dfb .concept}

When you configure an HTTPS listener, you can directly use a certificate from Alibaba Cloud SSL Certificates Service or upload a third-party server certificate and CA certificate to Server Load Balancer \(SLB\). After you upload the certificate to SLB, you do not need to configure certificates on backend servers.

SLB supports the following two types of certificates:

-   Certificates issued or hosted by Alibaba Cloud SSL Certificates Service: You can select the required certificate from Alibaba Cloud SSL Certificates Service. When the certificate is about to expire, Alibaba Cloud will send alerts notifying you to renew the certificate to ensure its validity.

    Currently, client CA certificates are not supported.

-   Third-party certificates: To upload a third-party certificate, you must have the public key and private key files of the certificate.

    HTTPS server certificates and client CA certificates are supported.


Before you create a certificate, note the following:

-   If you need to use a certificate in multiple regions, you must select all the required regions when creating the certificate.
-   Each Alibaba Cloud account can create up to 100 certificates.

