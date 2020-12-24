# CreateTLSCipherPolicy

调用CreateTLSCipherPolicy创建TLS策略。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=CreateTLSCipherPolicy&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateTLSCipherPolicy|要执行的操作。取值：**CreateTLSCipherPolicy**。 |
|Ciphers.N|RepeatList|是|AES256-SHA256|支持的加密套件列表，具体依赖TLSVersion值。

 TLSv1.0和TLSv1.1 支持：

 -   ECDHE-ECDSA-AES128-SHA
-   ECDHE-ECDSA-AES256-SHA
-   ECDHE-RSA-AES128-SHA
-   ECDHE-RSA-AES256-SHA
-   AES128-SHA
-   AES256-SHA
-   DES-CBC3-SHA

 TLSv1.2支持：

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

 TLSv1.3支持：

 -   TLS\_AES\_128\_GCM\_SHA256
-   TLS\_AES\_256\_GCM\_SHA384
-   TLS\_CHACHA20\_POLY1305\_SHA256
-   TLS\_AES\_128\_CCM\_SHA256
-   TLS\_AES\_128\_CCM\_8\_SHA256 |
|Name|String|是|TLSPolicy-test\*\*\*\*\*|TLS策略名称。长度为2~128个英文或中文字符，必须以大小字母或中文开头，可包含数字、英文句点（.）、下划线（\_）和短划线（-）。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例地域ID。 |
|TLSVersions.N|RepeatList|是|TLSv1.0|支持的TLS协议版本。取值：**TLSv1.0**、**TLSv1.1**、**TLSv1.2**和**TLSv1.3**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。 |
|TLSCipherPolicyId|String|tc-policy\*\*\*\*\*\*|策略ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateTLSCipherPolicy
&Ciphers.1=AES256-SHA256
&Name=TLSPolicy-test*****
&RegionId=cn-hangzhou
&TLSVersions.1=TLSv1.0
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateTLSCipherPolicyResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
  <TLSCipherPolicyId>tc-policy******</TLSCipherPolicyId>
</CreateTLSCipherPolicyResponse>
```

`JSON` 格式

```
{"RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984",
"TLSCipherPolicyId":"tc-policy******"}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

