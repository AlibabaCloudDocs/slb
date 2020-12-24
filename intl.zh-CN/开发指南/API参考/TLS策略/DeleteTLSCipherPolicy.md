# DeleteTLSCipherPolicy

调用DeleteTLSCipherPolicy删除TLS策略。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DeleteTLSCipherPolicy&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteTLSCipherPolicy|要执行的操作。取值：**DeleteTLSCipherPolicy**。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例地域ID。 |
|TLSCipherPolicyId|String|是|tls-bp1lp2076qx4ebridp\*\*\*\*\*\*|TLS策略实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteTLSCipherPolicy
&RegionId=cn-hangzhou
&TLSCipherPolicyId=tls-bp1lp2076qx4ebridp******
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteTLSCipherPolicyResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteTLSCipherPolicyResponse>
```

`JSON` 格式

```
{"RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

