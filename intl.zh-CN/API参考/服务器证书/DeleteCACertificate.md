# DeleteCACertificate {#doc_api_Slb_DeleteCACertificate .reference}

调用DeleteCACertificate删除CA证书。

**说明：** 无法删除正在使用的CA证书。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DeleteCACertificate&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteCACertificate|要执行的操作。

 取值：**DeleteCACertificate**。

 |
|RegionId|String|是|cn-hangzhou|CA证书的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|CACertificateId|String|是|123157908xxxxxxx\_15c73d77203\_-986300114\_-2110544xxx|CA证书ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DeleteCACertificate
&RegionId=cn-hangzhou
&CACertificateId=123157908xxxxxxx_15c73d77203_-986300114_-2110544xxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteCACertificateResponse>
	        <RequestId>CEFxxxxx72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
 </DeleteCACertificateResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":" CEFxxxx72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

