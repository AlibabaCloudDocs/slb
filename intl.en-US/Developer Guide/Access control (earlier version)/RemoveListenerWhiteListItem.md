# RemoveListenerWhiteListItem {#doc_api_Slb_RemoveListenerWhiteListItem .reference}

Deletes IP addresses from a listener whitelist.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=RemoveListenerWhiteListItem) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|RemoveListenerWhiteListItem| The name of this action.

 Value: **RemoveListenerWhiteListItem**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|ListenerPort|Integer|Yes|80| The listening port.

 |
|LoadBalancerId|String|Yes|lb-8vb86hxixo8lvsja86jaz| The ID of the SLB instance.

 |
|SourceItems|String|Yes|1.1.1.1| The access control list. Both IP addresses and IP address segments \(namely, CIDR blocks\) are supported. Use commas \(,\) to separate multiple IP addresses or CIDR blocks.

 **Note:** If all the IP addresses are deleted, the listener no longer forwards any requests.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=RemoveListenerWhiteListItem
&ListenerPort=80
&LoadBalancerId=lb-8vb86hxixo8lvsja86jaz
&SourceItems=1.1.1.1
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<RemoveListenerWhiteListItemResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</RemoveListenerWhiteListItemResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#section_ozn_uk5_c6p .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

