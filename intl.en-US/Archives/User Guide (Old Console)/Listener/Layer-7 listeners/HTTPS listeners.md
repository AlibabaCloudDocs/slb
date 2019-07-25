# HTTPS listeners {#concept_o3k_bj5_vdb .concept}

To meet security requirements of data transmission, Server Load Balancer supports HTTPS load balancing.

Note the following when configuring HTTPS listeners:

-   Before configuring HTTPS listeners, you have to prepare the required certificates as shown in the following table. For more information, see [Upload certificates](intl.en-US/User Guide/Certificate management/Upload certificates.md#).

    |Certificate|Description| Required for one-way authentication|Required for two-way authentication|
    |:----------|:----------|:-----------------------------------|:----------------------------------|
    |Server certificate|Used to identify a server.The client uses it to check whether the certificate sent by the server is issued by a trusted center.

|YesThe server certificate must be uploaded to the certificate management system of the Server Load Balancer.

|YesUpload the server certificate to SLB.

|
    |Client certificate|Used to identify a client.The client user can prove its true identity when communicating with the server. You can sign a client certificate with a self-signed CA certificate.

|No|YesInstall the client certificate on clients.

|
    |CA certificate|The server uses the CA certificate to authenticate the CA signature on the client certificate, as part of the authorization before launching a secure connection. If the authentication fails, the connection will be rejected.|No|YesUpload the CA certificate to SLB.

|

-   After uploading certificates to SLB, you can manage the certificates, such as replacing and deleting certificates, on the Server Load Balancer console.
-   It usually takes one to three minutes to activate the HTTPS listener because the uploading, loading, and validation of certificates take some time. Normally it takes effect in one minute but no longer exceeds three minutes.
-   The ECDHE method used by HTTPS listeners supports forward secrecy, but does not support uploading the PEM files that contain the security enhancement parameters, such as `BEGIN DH PARAMETERS`. For more information, see [Certificate formats](intl.en-US/User Guide/Certificate management/Certificate requirements.md#).
-   Currently, Server Load Balancer HTTPS listeners do not support SNI \(Server Name Indication\). You can use TCP listeners instead, and configure SNI on the backend ECS instances.
-   The session ticket of HTTPS listeners is 300 seconds.
-   The actual traffic is larger than the billing traffic because some traffic is used for the protocol handshake.
-   In the case of a large number of new connections, HTTPS listeners consume more traffic.

