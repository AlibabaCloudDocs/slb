# DeleteServerCertificate {#doc_api_1088687 .reference}

删除服务器证书。

**说明：** 如果指定删除的证书被引用，无法删除。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DeleteServerCertificate)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteServerCertificate|要执行的操作，取值：**DeleteServerCertificate**

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|ServerCertificateId|String|是|123157xxxxxxx\_166f8204689\_1714763408\_709981430|服务器证书ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DeleteServerCertificate
&ServerCertificateId=1231579xxxxxx3_166f8204689_1714763408_709981430
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteServerCertificateResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteServerCertificateResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

