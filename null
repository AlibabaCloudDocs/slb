---
keyword: [TLS安全策略, HTTPS监听, 自定义策略, 系统默认策略]
---

# TLS安全策略

您在创建和配置HTTPS监听时，支持使用TLS安全策略。TLS安全策略包含自定义策略和系统默认策略。

## 系统默认策略

|安全策略|特点|支持的TLS版本|支持的加密算法套件|
|----|--|--------|---------|
|**tls\_cipher\_policy\_1\_0**|兼容性最好，安全性较低|TLSv1.0、TLSv1.1和TLSv1.2|加密算法套件只要被任何一个传入的TLS版本支持即可，例如您如果选择了TLSv1.3，那么加密算法套件列表必须包含TLSv1.3支持的加密算法套件。-   TLSv1.0和TLSv1.1 支持：
    -   ECDHE-ECDSA-AES128-SHA
    -   ECDHE-ECDSA-AES256-SHA
    -   ECDHE-RSA-AES128-SHA
    -   ECDHE-RSA-AES256-SHA
    -   AES128-SHA
    -   AES256-SHA
    -   DES-CBC3-SHA
-   TLSv1.2支持：
    -   ECDHE-ECDSA-AES128-SHA
    -   ECDHE-ECDSA-AES256-SHA
    -   ECDHE-RSA-AES128-SHA
    -   ECDHE-RSA-AES256-SHA
    -   AES128-SHA
    -   AES256-SHA
    -   DES-CBC3-SHA
    -   ECDHE-ECDSA-AES128-GCM-SHA256
    -   ECDHE-ECDSA-AES256-GCM-SHA384
    -   ECDHE-ECDSA-AES128-SHA256
    -   ECDHE-ECDSA-AES256-SHA384
    -   ECDHE-RSA-AES128-GCM-SHA256
    -   ECDHE-RSA-AES256-GCM-SHA384
    -   ECDHE-RSA-AES128-SHA256
    -   ECDHE-RSA-AES256-SHA384
    -   AES128-GCM-SHA256
    -   AES256-GCM-SHA384
    -   AES128-SHA256
    -   AES256-SHA256
-   TLSv1.3支持：
    -   TLS\_AES\_128\_GCM\_SHA256
    -   TLS\_AES\_256\_GCM\_SHA384
    -   TLS\_CHACHA20\_POLY1305\_SHA256
    -   TLS\_AES\_128\_CCM\_SHA256
    -   TLS\_AES\_128\_CCM\_8\_SHA256 |
|**tls\_cipher\_policy\_1\_1**|兼容性较好，安全性较好|TLSv1.1和TLSv1.2|
|**tls\_cipher\_policy\_1\_2**|兼容性较好，安全性很高|TLSv1.2|
|**tls\_cipher\_policy\_1\_2\_strict**|仅支持前向安全的加密套件，安全性极高|TLSv1.2|
|**tls\_cipher\_policy\_1\_2\_strict\_with\_1\_3**|仅支持前向安全的加密套件，安全性极高|TLS1.2及TLS1.3|

## 自定义策略

完成以下操作，创建自定义策略。

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb)。

2.  在左侧导航栏，选择**应用型负载均衡ALB** \> **TLS安全策略**。

3.  在TLS安全策略页面，单击自定义策略页签下的**创建自定义策略**。

4.  完成以下配置，然后单击**创建**。

    |配置|说明|
    |--|--|
    |**名称**|输入自定义策略名称。长度为2~128个英文或中文字符，必须以大小字母或中文开头，可包含数字、英文句点（.）、下划线（\_）和短划线（-）。|
    |**选择最低版本**|选择最低TLS安全策略版本：    -   **TLS 1.0及以上**
    -   **TLS 1.1及以上**
    -   **TLS 1.2及以上** |
    |**启用TLS 1.3版本**|选择是否启用TLS 1.3版本。**注意：** 如果启用TLS 1.3版本，请至少选择一个TLS 1.3的加密算法套件，否则可能无法成功建立连接。 |
    |**选择加密算法套件**|选择TLS版本支持的加密算法套件。关于TLS版本支持的加密算法套件的更多信息，请参见[系统默认策略](#section_k1z_hpr_x7e)。|


## TLS安全策略差异说明

|安全策略|tls\_cipher\_policy\_1\_0|tls\_cipher\_policy\_1\_1|tls\_cipher\_policy\_1\_2|tls\_cipher\_policy\_1\_2\_strict|tls\_cipher\_policy\_1\_2\_strict\_with\_1\_3|
|----|-------------------------|-------------------------|-------------------------|---------------------------------|---------------------------------------------|
|TLS|-|1.2/1.1/1.0|1.2/1.1|1.2|1.2|1.2及1.3|
|CIPHER|ECDHE-RSA-AES128-GCM-SHA256|√|√|√|√|√|
|ECDHE-RSA-AES256-GCM-SHA384|√|√|√|√|√|
|ECDHE-RSA-AES128-SHA256|√|√|√|√|√|
|ECDHE-RSA-AES256-SHA384|√|√|√|√|√|
|AES128-GCM-SHA256|√|√|√|-|-|
|AES256-GCM-SHA384|√|√|√|-|-|
|AES128-SHA256|√|√|√|-|-|
|AES256-SHA256|√|√|√|-|-|
|ECDHE-RSA-AES128-SHA|√|√|√|√|√|
|ECDHE-RSA-AES256-SHA|√|√|√|√|√|
|AES128-SHA|√|√|√|-|-|
|AES256-SHA|√|√|√|-|-|
|DES-CBC3-SHA|√|√|√|-|-|
|TLS\_AES\_128\_GCM\_SHA256|-|-|-|-|√|
|TLS\_AES\_256\_GCM\_SHA384|-|-|-|-|√|
|TLS\_CHACHA20\_POLY1305\_SHA256|-|-|-|-|√|
|TLS\_AES\_128\_CCM\_SHA256|-|-|-|-|√|
|TLS\_AES\_128\_CCM\_8\_SHA256|-|-|-|-|√|
|ECDHE-ECDSA-AES128-GCM-SHA256|-|-|-|-|√|
|ECDHE-ECDSA-AES256-GCM-SHA384|-|-|-|-|√|
|ECDHE-ECDSA-AES128-SHA256|-|-|-|-|√|
|ECDHE-ECDSA-AES256-SHA384|-|-|-|-|√|
|ECDHE-ECDSA-AES128-SHA|-|-|-|-|√|
|ECDHE-ECDSA-AES256-SHA|-|-|-|-|√|

**说明：** 表格中，√表示支持，-表示不涉及。

