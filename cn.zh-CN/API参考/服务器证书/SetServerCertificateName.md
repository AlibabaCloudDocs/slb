# SetServerCertificateName {#doc_api_Slb_SetServerCertificateName .reference}

调用SetServerCertificateName设置服务器证书名称。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetServerCertificateName&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetServerCertificateName|要执行的操作。

 取值：**SetServerCertificateName**。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|ServerCertificateId|String|是|139a00604ad-cn-east-hangzhou-01|服务器证书ID。

 |
|ServerCertificateName|String|是|abc|服务器证书名称。

 名称长度为 1~80 个英文或中文字符，必须以大小字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FE7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetServerCertificateName
&RegionId=cn-hangzhou
&ServerCertificateId=139a00604ad-cn-east-hangzhou-01
&ServerCertificateName=abc
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetServerCertificateNameResponse>
      <RequestId>CEF72CEB-54B6-4AE8-B225-F876FE7BA984</RequestId>
</SetServerCertificateNameResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FE7BA984"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

