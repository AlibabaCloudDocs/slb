# SetListenerAccessControlStatus {#doc_api_Slb_SetListenerAccessControlStatus .reference}

Enables or disables the access control function for a listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetListenerAccessControlStatus) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetListenerAccessControlStatus| The name of this action.

 Value: **SetListenerAccessControlStatus**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|AccessControlStatus|String|Yes|open\_white\_list| Indicates whether to enable access control. Valid values:

 -   **open\_white\_list**: Enable a whitelist for access control.
-   **close**: Disable access control.

 **Note:** When the access control function is enabled, you must configure a whitelist of IP addresses. Otherwise, no access is allowed.

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-8vb86hxixo8lvsja86jaz| The ID of the SLB instance.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetListenerAccessControlStatus
&AccessControlStatus=open_white_list
&ListenerPort=80
&LoadBalancerId=lb-8vb86hxixo8lvsja86jaz
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetListenerAccessControlStatusResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</SetListenerAccessControlStatusResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#section_deg_xo2_orx .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

