# AddAccessControlListEntry {#doc_api_Slb_AddAccessControlListEntry .reference}

Adds IP entries to an access control list.

Each access control list can contain multiple IP addresses and CIDR blocks. Access control lists have the following limits:

-   Each Alibaba Cloud account can add a maximum of 50 IP entries at a time.
-   An access control list can contain a maximum of 300 IP entries.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddAccessControlListEntry) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AddAccessControlListEntry| The name of this action. Value: **AddAccessControlListEntry**

 |
|AclId|String|Yes|acl-bp1l0kk4gxce43kzet04s| The ID of the target access control list.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the access control list belongs.

 |
|AclEntrys|String|No|\[\{"entry":"10.0.0.0/24","comment":"privaterule1"\},\{"entry":"192.168.0.0/16","comment":"privaterule2"\}\]| The IP entries to be added to the access control list. You can add IP addresses or CIDR blocks. Use commas \(,\) to separate multiple IP addresses or CIDR blocks.

 **Note:** You can add a maximum of 50 IP entries at a time.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA4| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Action=AddAccessControlListEntry
&RegionId=cn-hangzhou 
&AclEntrys=[{"entry":"10.0.0.0/24","comment":"privaterule1"},{"entry":"192.168.0.0/16","comment":"privaterule2"}]
&AclId=acl-bp1l0kk4gxce43kzet04s 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<AddAccessControlListEntryResponse> 
  <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId> 
</AddAccessControlListEntryResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

## Error codes {#section_l4x_p8z_oqz .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

