# SetCACertificateName {#doc_api_Slb_SetCACertificateName .reference}

调用SetCACertificateName设置CA证书名称。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=SetCACertificateName)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetCACertificateName|要执行的操作。

 取值：**SetCACertificateName**。

 |
|RegionId|String|是|cn-hangzhou|CA证书的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|CACertificateId|String|是|139a00604ad-cn-east-hangzhou-01|CA证书ID。

 |
|CACertificateName|String|是|mycacert02|CA证书名称。

 名称长度为1~80个英文或中文字符，必须以大小字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FE7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetCACertificateName
&RegionId=cn-hangzhou
&CACertificateId=139a00604ad-cn-east-hangzhou-01
&CACertificateName=mycacert02
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetCACertificateNameResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FE7BA984</RequestId>
</SetCACertificateNameResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FE7BA984"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

