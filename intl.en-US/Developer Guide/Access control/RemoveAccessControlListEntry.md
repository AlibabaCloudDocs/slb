# RemoveAccessControlListEntry {#doc_api_Slb_RemoveAccessControlListEntry .reference}

Deletes IP entries from an access control list.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=RemoveAccessControlListEntry) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|RemoveAccessControlListEntry| The name of this action. Value: **RemoveAccessControlListEntry**

 |
|AclId|String|Yes|acl-bp1l0kk4gxce43kzet04s| The ID of the target access control list.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the access control list belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|AclEntrys|String|No|\[\{"entry":"10.0.0.0/24","comment":"privaterule1"\}\]| The IP entries to be deleted from the access control list. You can delete IP addresses or CIDR blocks. Use commas \(,\) to separate multiple IP entries.

 **Note**: If the access control list is associated with a listener, you cannot delete all IP entries in the access control list.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA49| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Action=RemoveAccessControlListEntry
&AclId=acl-bp1l0kk4gxce43kzet04s 
&RegionId=cn-hangzhou 
&AclEntrys=[{"entry":"10.0.0.0/24","comment":"privaterule1"}] 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<RemoveAccessControlListEntryResponse> 
  <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId> 
</RemoveAccessControlListEntryResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

## Error codes {#section_p02_5s4_k35 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

