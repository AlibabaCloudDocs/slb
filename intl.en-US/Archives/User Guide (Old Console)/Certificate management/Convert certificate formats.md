# Convert certificate formats {#concept_w2s_kqn_vdb .concept}

Server Load Balancer supports PEM certificates only. Certificates in other formats must be converted to PEM before they can be uploaded to Server Load Balancer. We recommend that you use Open SSL for conversion.

## Convert DER to PEM {#section_zhr_h5b_wdb .section}

DER: This format is usually used on a Java platform.

-   Run the following command to convert the certificate format.

    ```
    openssl x509 -inform der -in certificate.cer -out certificate.pem
    ```

-   Run the following command to convert the private key.

    ```
    opensslrsa -inform DER -outform PEM -in privatekey.der -out privatekey.pem
    ```


## Convert P7B to PEM {#section_vj4_t5b_wdb .section}

P7B: This format is usually used in Windows Server and Tomcat.

Run the following command to convert the certificate format.

```
openssl pkcs7 -print_certs -in incertificat.p7b -out outcertificate.cer
```

## Convert PFX to PEM {#section_jhg_w5b_wdb .section}

PFX: This format is usually used in Windows Server.

-   Run the following command to extract the certificate format.

    ```
    openssl pkcs12 -in certname.pfx -nokeys -out cert.pem
    ```

-   Run the following command to extract the private key.

    ```
    openssl pkcs12 -in certname.pfx -nocerts -out key.pem -nodes
    ```


