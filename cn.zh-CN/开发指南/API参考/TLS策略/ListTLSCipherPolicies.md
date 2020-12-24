# ListTLSCipherPolicies

调用ListTLSCipherPolicies查询TLS策略。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=ListTLSCipherPolicies&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListTLSCipherPolicies|要执行的操作，取值：**ListTLSCipherPolicies**。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例地域ID。 |
|TLSCipherPolicyId|String|是|tls-bp1lp2076qx4e\*\*\*\*\*\*bridp|TLS策略ID。 |
|Name|String|否|tls-policy\*\*\*\*\*-test|TLS策略名称。长度为2~128个英文或中文字符，必须以大小字母或中文开头，可包含数字、英文句点（.）、下划线（\_）和短划线（-）。 |
|IncludeListener|Boolean|否|false|是否返回关联的监听信息。取值：**true**或**false**（默认）。 |
|NextToken|String|否|cae\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*f0a|用来标记当前开始读取的位置，设置为空表示从头开始。 |
|MaxItems|Integer|否|20|本次读取的最大TLS策略数，取值：**1**~**100**。用户传入为空时，默认值为**20**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IsTruncated|Boolean|false|是否结束。取值：

 -   **true**：表示当前页是最后一页。
-   **false**：表示还有下一页。 |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|用来标记当前开始读取的位置，设置为空表示从头开始。 |
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。 |
|TLSCipherPolicies|Array of TLSCipherPolicy| |TLS策略列表。 |
|Ciphers|List|ECDHE-ECDSA-AES128-SHA|支持的加密套件，具体依赖TLSVersions的取值。

 TLSv1.0和TLSv1.1 支持：

 -   ECDHE-ECDSA-AES128-SHA
-   ECDHE-ECDSA-AES256-SHA
-   ECDHE-RSA-AES128-SHA
-   ECDHE-RSA-AES256-SHA
-   AES128-SHA AES256-SHA
-   DES-CBC3-SHA

 TLSv1.2支持：

 -   ECDHE-ECDSA-AES128-SHA
-   ECDHE-ECDSA-AES256-SHA
-   ECDHE-RSA-AES128-SHA
-   ECDHE-RSA-AES256-SHA
-   AES128-SHA AES256-SHA
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
-   AES128-SHA256 AES256-SHA256

 TLSv1.3支持：

 -   TLS\_AES\_128\_GCM\_SHA256
-   TLS\_AES\_256\_GCM\_SHA384
-   TLS\_CHACHA20\_POLY1305\_SHA256
-   TLS\_AES\_128\_CCM\_SHA256
-   TLS\_AES\_128\_CCM\_8\_SHA256 |
|CreateTime|Long|1608273800000|创建时间的时间戳。 |
|InstanceId|String|tls-bp1lp2076qx4e\*\*\*\*\*\*bridp|TLS策略实例ID。 |
|Name|String|tls-policy\*\*\*\*\*-test|TLS策略名称。 |
|RelateListeners|Array of RelateListener| |关联的监听。 |
|LoadBalancerId|String|lb-bp1b6c719dfa08ex\*\*\*\*\*|负载均衡实例ID。 |
|Port|Integer|80|监听端口。取值：**1**~**65535**。 |
|Protocol|String|HTTPS|监听协议。取值：**TCP**、**UDP**、**HTTP**或**HTTPS**。 |
|Status|String|normal|TLS策略实例状态。取值：

 -   **configuring**：配置中。
-   **normal**： 正常。 |
|TLSVersions|List|TLSv1.0|支持的TLS协议版本。 |
|TotalCount|Integer|1000|本次请求条件下的TLS策略总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListTLSCipherPolicies
&RegionId=cn-hangzhou
&TLSCipherPolicyId=tls-bp1lp2076qx4e******bridp
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListTLSCipherPoliciesResponse>
  <TotalCount>1000</TotalCount>
  <NextToken>caeba0bbb2be03f84eb48b699f0a****</NextToken>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
  <TLSCipherPolicies>
        <Status>normal</Status>
        <InstanceId>tls-bp1lp2076qx4e******bridp</InstanceId>
        <CreateTime>1608273800000</CreateTime>
        <Name>tls-policy*****-test</Name>
  </TLSCipherPolicies>
  <TLSCipherPolicies>
        <RelateListeners>
              <LoadBalancerId>lb-bp1b6c719dfa08ex*****</LoadBalancerId>
              <Protocol>HTTPS</Protocol>
              <Port>80</Port>
        </RelateListeners>
  </TLSCipherPolicies>
  <TLSCipherPolicies>
        <Ciphers>ECDHE-ECDSA-AES128-SHA</Ciphers>
        <TLSVersions>TLSv1.0</TLSVersions>
  </TLSCipherPolicies>
  <IsTruncated>false</IsTruncated>
</ListTLSCipherPoliciesResponse>
```

`JSON` 格式

```
{"TotalCount":"1000",
"NextToken":"caeba0bbb2be03f84eb48b699f0a****",
"RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984",
"TLSCipherPolicies":
[
    {
        "Status":"normal",
    "InstanceId":"tls-bp1lp2076qx4e******bridp",
    "CreateTime":"1608273800000",
    "Name":"tls-policy*****-test"
    },
    {
        "RelateListeners":[
        {
            "LoadBalancerId":"lb-bp1b6c719dfa08ex*****",
            "Protocol":"HTTPS",
            "Port":"80"
            }
            ]
            },
            {
                "Ciphers":"ECDHE-ECDSA-AES128-SHA",
                "TLSVersions":"TLSv1.0"
                }
                ],
                "IsTruncated":"false"}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

