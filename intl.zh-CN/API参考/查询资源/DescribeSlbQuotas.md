# DescribeSlbQuotas {#doc_api_879858 .reference}

使用DescribeSlbQuotas查询负载均衡的资源约束。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Slb&api=DescribeSlbQuotas)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeSlbQuotas|要执行的操作，取值：**DescribeSlbQuotas**。

 |
|RegionId|String|是|cn-hangzhou|要查询资源约束的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Quotas| | |资源限制列表。如果某个值没有返回，表示没有特殊配置，请根据使用限制查询默认值。

 |
|└Comment|String|Max number of Server certificates per region|资源约束项的说明。

 |
|└Max|String|20|资源约束项的最大值。

 |
|└QuotaName|String|server-cers-per-region|资源约束名称。

 |
|RequestId|String|22D5D4F8-2DFF-4F73-BA1A-D5D840B2C800|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?Action=DescribeSlbQuotas
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeSlbQuotasResponse>
  <RequestId>22D5D4F8-2DFF-4F73-BA1A-D5D840B2C800</RequestId>
  <Quotas>
    <Quota>
      <Comment>Max number of SLB instances per account</Comment>
      <Max>60</Max>
      <QuotaName>slbs-per-user</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of Server certificates per region</Comment>
      <Max>100</Max>
      <QuotaName>server-cers-per-region</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of Client CA certificates per region</Comment>
      <Max>100</Max>
      <QuotaName>client-ca-cers-per-region</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of SLB instances that a single backend server can be attached to</Comment>
      <Max>50</Max>
      <QuotaName>slbs-per-backendserver</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of backend servers can be attached to a single SLB instance</Comment>
      <Max>200</Max>
      <QuotaName>backendservers-per-slb</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of listeners per SLB instance</Comment>
      <Max>50</Max>
      <QuotaName>listeners-per-slb</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of forwarding rule per listener</Comment>
      <Max>40</Max>
      <QuotaName>rules-per-listener</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of extension domains per listener</Comment>
      <Max>3</Max>
      <QuotaName>domain-extensions-per-listener</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of access control lists per region</Comment>
      <Max>50</Max>
      <QuotaName>acls-per-region</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of listeners that an single access control list can be attached to</Comment>
      <Max>50</Max>
      <QuotaName>listeners-per-acl</QuotaName>
    </Quota>
    <Quota>
      <Comment>Max number of entries per access control list</Comment>
      <Max>300</Max>
      <QuotaName>entries-per-acl</QuotaName>
    </Quota>
  </Quotas>
</DescribeSlbQuotasResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"22D5D4F8-2DFF-4F73-BA1A-D5D840B2C800",
	"Quotas":{
		"Quota":[
			{
				"Comment":"Max number of SLB instances per account",
				"Max":60,
				"QuotaName":"slbs-per-user"
			},
			{
				"Comment":"Max number of Server certificates per region",
				"Max":100,
				"QuotaName":"server-cers-per-region"
			},
			{
				"Comment":"Max number of Client CA certificates per region",
				"Max":100,
				"QuotaName":"client-ca-cers-per-region"
			},
			{
				"Comment":"Max number of SLB instances that a single backend server can be attached to",
				"Max":50,
				"QuotaName":"slbs-per-backendserver"
			},
			{
				"Comment":"Max number of backend servers can be attached to a single SLB instance",
				"Max":200,
				"QuotaName":"backendservers-per-slb"
			},
			{
				"Comment":"Max number of listeners per SLB instance",
				"Max":50,
				"QuotaName":"listeners-per-slb"
			},
			{
				"Comment":"Max number of forwarding rule per listener",
				"Max":40,
				"QuotaName":"rules-per-listener"
			},
			{
				"Comment":"Max number of extension domains per listener",
				"Max":3,
				"QuotaName":"domain-extensions-per-listener"
			},
			{
				"Comment":"Max number of access control lists per region",
				"Max":50,
				"QuotaName":"acls-per-region"
			},
			{
				"Comment":"Max number of listeners that an single access control list can be attached to",
				"Max":50,
				"QuotaName":"listeners-per-acl"
			},
			{
				"Comment":"Max number of entries per access control list",
				"Max":300,
				"QuotaName":"entries-per-acl"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

