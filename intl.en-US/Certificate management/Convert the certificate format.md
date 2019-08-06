# Convert the certificate format {#concept_w2s_kqn_vdb .concept}

Server Load Balancer supports PEM certificates only. Certificates in other formats must be converted to the PEM format before they can be uploaded to Server Load Balancer. We recommend that you use Open SSL for conversion.

## Convert DER to PEM {#section_zhr_h5b_wdb .section}

DER: This format is usually used on a Java platform. The certificate file suffix is generally . der, . cer, or . crt.

-   Run the following command to convert the certificate format:

    ``` {#codeblock_q1x_yps_w0z}
    openssl x509 -inform der -in certificate.cer -out certificate.pem
    ```

-   -   Run the following command to convert the private key:

    ``` {#codeblock_zfj_y6c_ar5}
    openssl rsa -inform DER -outform PEM -in privatekey.der -out privatekey.pem
    ```


## Convert P7B to PEM {#section_vj4_t5b_wdb .section}

P7B: This format is usually used in a Windows server and Tomcat.

Run the following command to convert the certificate format:

``` {#codeblock_tmc_tu2_wt2}
openssl pkcs7 -print_certs -in incertificate.p7b -out outcertificate.cer
```

## Convert PFX to PEM {#section_jhg_w5b_wdb .section}

PFX: This format is usually used in a Windows server.

-   Run the following command to extract the certificate:

    ``` {#codeblock_nbi_8uz_huq}
    openssl pkcs12 -in certname.pfx -nokeys -out cert.pem
    ```

-   Run the following command to extract the private key:

    ``` {#codeblock_l0g_cn2_arq}
    openssl pkcs12 -in certname.pfx -nocerts -out key.pem -nodes
    ```


