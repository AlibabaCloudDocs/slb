# DescribeCACertificates {#doc_api_834969 .reference}

使用DescribeCACertificates查询CA证书列表。

**说明：** 为了保证安全性，只返回证书的指纹和名称，不返回证书的内容。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Slb&api=DescribeCACertificates)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCACertificates|要执行的操作。取值：**DescribeCACertificates**。

 |
|RegionId|String|是|cn-hangzhou|CA证书的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|CACertificateId|String|否|139a00604bd-cn-east-hangzhou-02|CA证书ID。

 |
|OwnerAccount|String|否|testuser@aliyun.com|用户主账号。

 |
|ResourceGroupId|String|否|rg-atstuj3rtoptyui|企业资源组ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CACertificates| | |CA证书信息。

 |
|└CACertificateId|String|139a00604bd-cn-east-hangzhou-02|CA证书ID。

 |
|└CACertificateName|String|test|CA证书名称。

 |
|└RegionId|String|cn-hangzhou|CA证书所属地域。

 |
|└Fingerprint|String|AC:BE:FD|CA证书的指纹。

 |
|└CommonName|String|.example.com|CA证书的域名。

 |
|└CreateTime|String|2017-08-31T02:49:05Z|CA证书的创建时间。

 |
|└CreateTimeStamp|Long|1504147745000|CA证书的创建时间戳。

 |
|└ExpireTime|String|2024-11-21T06:04:25Z|CA证书的过期时间。

 |
|└ExpireTimeStamp|Long|1732169065000|CA证书的过期时间戳。

 |
|└ResourceGroupId|String|rg-atstuj3rtoptyui|企业资源组ID。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?RegionId=cn-hangzhou
&Action=DescribeCACertificates
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCACertificateResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <CACertificates>
    <CACertificate>
      <CACertificateId>139a00604bd-cn-east-hangzhou-01
        </CACertificateId>
      <CACertificateName>bcd
    </CACertificateName>
      <Fingerprint>AB:CB:DE</Fingerprint>
    </CACertificate>
    <CACertificate>
      <CACertificateId>139a00604bd-cn-east-hangzhou-02</CACertificateId>
      <CACertificateName>cde</CACertificateName>
      <Fingerprint>AC:BE:FD</Fingerprint>
    </CACertificate>
  </CACertificates>
</DescribeCACertificateResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	" CACertificates":{
		"CACertificate":[
			{
				"CACertificateName":"bcd",
				"Fingerprint ":"AB:CB:DE",
				"CACertificateId":"139a00604bd-cn-east-hangzhou-01"
			},
			{
				"CACertificateName":"cde",
				"Fingerprint ":"AC:BE:FD",
				"CACertificateId":"282b00102ac-cn-east-hangzhou-02"
			}
		]
	}
}
```

异常返回示例

`JSON` 格式

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"slb-pop.aliyuncs.com",
	"Code":"InvalidParameter"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

