# Convert the certificate format

Server Load Balancer \(SLB\) supports PEM certificates only. Certificates in other formats must be converted to the PEM format before they can be uploaded to SLB. We recommend that you use Open SSL for conversion.

## Convert DER to PEM

DER: This format is usually used on a Java platform. The certificate file suffix is generally . der, . cer, or . crt.

-   Run the following command to convert the certificate format:

    ```
    openssl x509 -inform der -in certificate.cer -out certificate.pem
    ```

-   Run the following command to convert the private key:

    ```
    openssl rsa -inform DER -outform PEM -in privatekey.der -out privatekey.pem
    ```


## Convert P7B to PEM

P7B: This format is usually used in a Windows server and Tomcat.

Run the following command to convert the certificate format:

```
openssl pkcs7 -print_certs -in incertificate.p7b -out outcertificate.cer
```

## Convert PFX to PEM

PFX: This format is usually used in a Windows server.

-   Run the following command to extract the certificate:

    ```
    openssl pkcs12 -in certname.pfx -nokeys -out cert.pem
    ```

-   Run the following command to extract the private key:

    ```
    openssl pkcs12 -in certname.pfx -nocerts -out key.pem -nodes
    ```


