# SetAccessControlListAttribute {#doc_api_Slb_SetAccessControlListAttribute .reference}

Modifies the name of an access control list.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetAccessControlListAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetAccessControlListAttribute|The name of this action. Value: **SetAccessControlListAttribute**

 |
|AclId|String|Yes|acl-bp1l0kk4gxce43kzet04s|The ID of the access control list to be modified.

 |
|AclName|String|Yes|test1|The name of the access control list to be modified.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the access control list belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AclId|String|acl-bp1l0kk4gxce43kzet04s|The ID of the access control list.

 |
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA49|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetAccessControlListAttribute
&AclId=acl-bp1l0kk4gxce43kzet04s 
&AclName=test1 
&RegionId=cn-hangzhou 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetAccessControlListAttributeResponse> 
  <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId> 
</SetAccessControlListAttributeResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

