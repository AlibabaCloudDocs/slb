# DescribeSlbQuotas {#doc_api_879858 .reference}

You can call the DescribeSlbQuotas API to query the resource limits on SLB.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=DescribeSlbQuotas) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Name|Type|Required?|Example value|Description|
|----|----|---------|-------------|-----------|
|Action|String|Yes|DescribeSlbQuotas|The action to perform. Valid value: **DescribeSlbQuotas**.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the resource limits you want to query exist.

 You can call the [DescribeRegions](~~27584~~) API to query this parameter.

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|Quotas| | |A list of resource limit items. If no value is returned, there are no special settings. In this case, you can query the default value according to the limits.

 |
|└Comment|String|Max number of Server certificates per region|A comment on the resource limit item

 |
|└Max|String|20|The maximum value of the resource limit item

 |
|└QuotaName|String|server-cers-per-region|The name of the resource limit item

 |
|RequestId|String|22D5D4F8-2DFF-4F73-BA1A-D5D840B2C800|The ID of the request

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Action=DescribeSlbQuotas
&RegionId=cn-hangzhou
&<CommonParameters>

```

Normal response examples

`XML` format

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

`JSON` format

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

## Error codes { .section}

[Click here to view the error codes.](https://error-center.aliyun.com/status/product/Slb)

