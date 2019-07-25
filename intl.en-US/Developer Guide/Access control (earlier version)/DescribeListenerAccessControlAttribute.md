# DescribeListenerAccessControlAttribute {#doc_api_Slb_DescribeListenerAccessControlAttribute .reference}

Queries the access control settings of a listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeListenerAccessControlAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeListenerAccessControlAttribute| The name of this action.

 Value: **DescribeListenerAccessControlAttribute**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to[the list of regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~).

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-8vb86hxixo8lvsja86jaz| The ID of the SLB instance.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AccessControlStatus|String|open\_white\_list| Indicates whether access control is enabled.

 -   **open\_white\_list**: A whitelist for access control is enabled.
-   **close**: Access control is disabled.

 |
|SourceItems|String|1.1.1.1,1.1.1.0/24| The access control list.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeListenerAccessControlAttribute
&ListenerPort=80
&LoadBalancerId=lb-8vb86hxixo8lvsja86jaz
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeListenerAccessControlAttributeResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <AccessControlStatus>open_white_list</AccessControlStatus>
  <SourceItems>1.1.1.1,1.1.1.0/24</SourceItems>
</DescribeListenerAccessControlAttributeResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"SourceItems":"1.1.1.1,1.1.1.0/24",
	"AccessControlStatus":"open_white_list"
}
```

## Error codes {#section_k46_99s_co7 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

