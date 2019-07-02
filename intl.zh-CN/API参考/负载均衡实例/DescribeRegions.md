# DescribeRegions {#doc_api_Slb_DescribeRegions .reference}

调用DescribeRegions查询可用地域。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DescribeRegions)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRegions|要执行的操作。

 取值：**DescribeRegions**。

 |
|RegionId|String|是|cn-hangzhou|地域ID。

 |
|AcceptLanguage|String|否|zh-CN|支持的语言。包括以下取值：

 -   中文：zh-CN
-   英文：en-US
-   日文：ja

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Regions| | |地域列表。

 |
|└RegionId|String|cn-beijing|地域ID。

 |
|└LocalName|String|华北2（北京）|地域名称。

 |
|└RegionEndpoint|String|slb.aliyuncs.com|Region服务的Endpoint地址。

 |
|RequestId|String|1651FBB6-4FBF-49FF-A9F5-DF5D696C7EC6|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeRegions
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRegionsResponse>
  <RequestId>3CCA93B7-9590-42D6-8118-9CE3383558A9</RequestId>
  <Regions>
    <Region>
      <RegionId>ap-southeast-1</RegionId>
      <RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
      <LocalName>新加坡</LocalName>
    </Region>
    <Region>
      <RegionId>eu-central-1</RegionId>
      <RegionEndpoint>slb.eu-central-1.aliyuncs.com</RegionEndpoint>
      <LocalName>德国（法兰克福）</LocalName>
    </Region>
    <Region>
      <RegionId>ap-southeast-5</RegionId>
      <RegionEndpoint>slb.ap-southeast-5.aliyuncs.com</RegionEndpoint>
      <LocalName>印度尼西亚（雅加达）</LocalName>
    </Region>
    <Region>
      <RegionId>cn-qingdao</RegionId>
      <RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
      <LocalName>华北1（青岛）</LocalName>
    </Region>
    <Region>
      <RegionId>us-east-1</RegionId>
      <RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
      <LocalName>美国（弗吉尼亚）</LocalName>
    </Region>
    <Region>
      <RegionId>ap-south-1</RegionId>
      <RegionEndpoint>slb.ap-south-1.aliyuncs.com</RegionEndpoint>
      <LocalName>印度（孟买）</LocalName>
    </Region>
    <Region>
      <RegionId>cn-beijing</RegionId>
      <RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
      <LocalName>华北2（北京）</LocalName>
    </Region>
    <Region>
      <RegionId>cn-shanghai</RegionId>
      <RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
      <LocalName>华东2（上海）</LocalName>
    </Region>
    <Region>
      <RegionId>ap-northeast-1</RegionId>
      <RegionEndpoint>slb.ap-northeast-1.aliyuncs.com</RegionEndpoint>
      <LocalName>日本（东京）</LocalName>
    </Region>
    <Region>
      <RegionId>cn-huhehaote</RegionId>
      <RegionEndpoint>slb.cn-huhehaote.aliyuncs.com</RegionEndpoint>
      <LocalName>华北5（呼和浩特）</LocalName>
    </Region>
    <Region>
      <RegionId>cn-shenzhen</RegionId>
      <RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
      <LocalName>华南1（深圳）</LocalName>
    </Region>
    <Region>
      <RegionId>ap-southeast-2</RegionId>
      <RegionEndpoint>slb.ap-southeast-2.aliyuncs.com</RegionEndpoint>
      <LocalName>澳大利亚（悉尼）</LocalName>
    </Region>
    <Region>
      <RegionId>cn-hongkong</RegionId>
      <RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
      <LocalName>香港</LocalName>
    </Region>
    <Region>
      <RegionId>us-west-1</RegionId>
      <RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
      <LocalName>美国（硅谷）</LocalName>
    </Region>
    <Region>
      <RegionId>eu-west-1</RegionId>
      <RegionEndpoint>slb.eu-west-1.aliyuncs.com</RegionEndpoint>
      <LocalName>英国（伦敦）</LocalName>
    </Region>
    <Region>
      <RegionId>me-east-1</RegionId>
      <RegionEndpoint>slb.me-east-1.aliyuncs.com</RegionEndpoint>
      <LocalName>阿联酋（迪拜）</LocalName>
    </Region>
    <Region>
      <RegionId>cn-zhangjiakou</RegionId>
      <RegionEndpoint>slb.cn-zhangjiakou.aliyuncs.com</RegionEndpoint>
      <LocalName>华北3（张家口）</LocalName>
    </Region>
    <Region>
      <RegionId>cn-hangzhou</RegionId>
      <RegionEndpoint>slb.aliyuncs.com</RegionEndpoint>
      <LocalName>华东1（杭州）</LocalName>
    </Region>
    <Region>
      <RegionId>ap-southeast-3</RegionId>
      <RegionEndpoint>slb.ap-southeast-3.aliyuncs.com</RegionEndpoint>
      <LocalName>马来西亚（吉隆坡）</LocalName>
    </Region>
  </Regions>
</DescribeRegionsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"3CCA93B7-9590-42D6-8118-9CE3383558A9",
	"Regions":{
		"Region":[
			{
				"RegionId":"ap-southeast-1",
				"RegionEndpoint":"slb.aliyuncs.com",
				"LocalName":"新加坡"
			},
			{
				"RegionId":"eu-central-1",
				"RegionEndpoint":"slb.eu-central-1.aliyuncs.com",
				"LocalName":"德国（法兰克福）"
			},
			{
				"RegionId":"ap-southeast-5",
				"RegionEndpoint":"slb.ap-southeast-5.aliyuncs.com",
				"LocalName":"印度尼西亚（雅加达）"
			},
			{
				"RegionId":"cn-qingdao",
				"RegionEndpoint":"slb.aliyuncs.com",
				"LocalName":"华北1（青岛）"
			},
			{
				"RegionId":"us-east-1",
				"RegionEndpoint":"slb.aliyuncs.com",
				"LocalName":"美国（弗吉尼亚）"
			},
			{
				"RegionId":"ap-south-1",
				"RegionEndpoint":"slb.ap-south-1.aliyuncs.com",
				"LocalName":"印度（孟买）"
			},
			{
				"RegionId":"cn-beijing",
				"RegionEndpoint":"slb.aliyuncs.com",
				"LocalName":"华北2（北京）"
			},
			{
				"RegionId":"cn-shanghai",
				"RegionEndpoint":"slb.aliyuncs.com",
				"LocalName":"华东2（上海）"
			},
			{
				"RegionId":"ap-northeast-1",
				"RegionEndpoint":"slb.ap-northeast-1.aliyuncs.com",
				"LocalName":"日本（东京）"
			},
			{
				"RegionId":"cn-huhehaote",
				"RegionEndpoint":"slb.cn-huhehaote.aliyuncs.com",
				"LocalName":"华北5（呼和浩特）"
			},
			{
				"RegionId":"cn-shenzhen",
				"RegionEndpoint":"slb.aliyuncs.com",
				"LocalName":"华南1（深圳）"
			},
			{
				"RegionId":"ap-southeast-2",
				"RegionEndpoint":"slb.ap-southeast-2.aliyuncs.com",
				"LocalName":"澳大利亚（悉尼）"
			},
			{
				"RegionId":"cn-hongkong",
				"RegionEndpoint":"slb.aliyuncs.com",
				"LocalName":"香港"
			},
			{
				"RegionId":"us-west-1",
				"RegionEndpoint":"slb.aliyuncs.com",
				"LocalName":"美国（硅谷）"
			},
			{
				"RegionId":"eu-west-1",
				"RegionEndpoint":"slb.eu-west-1.aliyuncs.com",
				"LocalName":"英国（伦敦）"
			},
			{
				"RegionId":"me-east-1",
				"RegionEndpoint":"slb.me-east-1.aliyuncs.com",
				"LocalName":"阿联酋（迪拜）"
			},
			{
				"RegionId":"cn-zhangjiakou",
				"RegionEndpoint":"slb.cn-zhangjiakou.aliyuncs.com",
				"LocalName":"华北3（张家口）"
			},
			{
				"RegionId":"cn-hangzhou",
				"RegionEndpoint":"slb.aliyuncs.com",
				"LocalName":"华东1（杭州）"
			},
			{
				"RegionId":"ap-southeast-3",
				"RegionEndpoint":"slb.ap-southeast-3.aliyuncs.com",
				"LocalName":"马来西亚（吉隆坡）"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidParameter|Illegal parameter, query.namespace is not auth.|query.namespace未授权，请您先授权再操作。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

