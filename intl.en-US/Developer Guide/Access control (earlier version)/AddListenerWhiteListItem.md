# AddListenerWhiteListItem {#doc_api_Slb_AddListenerWhiteListItem .reference}

Adds IP addresses to a listener whitelist.

## Debug {#section_m44_g4p_wws .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Slb&api=AddListenerWhiteListItem&type=RPC&version=2014-05-15)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AddListenerWhiteListItem| The name of this action.

 Value: **AddListenerWhiteListItem**

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance.

 |
|LoadBalancerId|String|Yes|139a00604ad-cn-east-hangzhou-01| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou-d| The ID of the region to which the SLB instance belongs.

 |
|SourceItems|String|Yes|1.1.1.1,1.1.1.0/21| The access control list.

 This parameter is valid when the value of the **AccessControlStatus** parameter is **open\_white\_list**.

 Both IP addresses and IP address segments \(namely, CIDR blocks\) are supported. Use commas \(,\) to separate multiple IP addresses or CIDR blocks.

 0.0.0.0 or 0.0.0.0/0 is not allowed. You can call [SetListenerAccessControlStatus](~~27599~~) to set AccessControlStatus to close to disable access control.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=AddListenerWhiteListItem
&ListenerPort=80
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&SourceItems=1.1.1.1,1.1.1.0/21
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<AddListenerWhiteListItemResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</AddListenerWhiteListItemResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#section_l3h_kdq_nj8 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

