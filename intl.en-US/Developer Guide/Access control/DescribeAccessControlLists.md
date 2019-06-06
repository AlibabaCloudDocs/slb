# DescribeAccessControlLists {#doc_api_Slb_DescribeAccessControlLists .reference}

Queries created access control lists.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeAccessControlLists) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeAccessControlLists|The name of this action. Value: **DescribeAccessControlLists**

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the access control list belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|AclName|String|No|rule1|Optional. The name of the access control list.

 |
|AddressIPVersion|String|No|ipv4|Optional. The IP address type of the SLB instance associated with the access control list. Valid values:

 -   **ipv4**: The IP address type of the SLB instance is IPv4.
-   **ipv6**: The IP address type of the SLB instance is IPv6.

 |
|PageNumber|Integer|No|1|Optional. The page number of the access control list. Default value: 1

 |
|PageSize|Integer|No|10|Optional. The number of rows per page for a paged query. Maximum value: 50. Default value: 10

 |
|ResourceGroupId|String|No|rg-atstuj3rtoptyui|Optional. The ID of the enterprise resource group.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|Acls| | |A list of access control lists that are queried.

 |
|└AclId|String|acl-bp1l0kk4gxce43kzet04s|The ID of an access control list.

 |
|└AclName|String|rule1|The name of the access control list.

 |
|└AddressIPVersion|String|ipv4|The IP address type of the associated SLB instance.

 |
|RequestId|String|B646EF-6147-4566|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Action=DescribeAccessControlLists
&RegionId=cn-hangzhou 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeAccessControlListsResponse> 
  <RequestId>3CB646EF-6147-4566-A9D9-CE8FBE86F971</RequestId> 
  <Acls> 
    <Acl> 
      <AclId>acl-bp1j9vn2g7wm9wn0xassu</AclId> 
      <AclName>test</AclName> 
      <AddressIPVersion>ipv4</AddressIPVersion> 
    </Acl> 
    <Acl> 
      <AclId>acl-bp1l0kk4gxce43kzet04s</AclId> 
      <AclName>doctest</AclName> 
      <AddressIPVersion>ipv4</AddressIPVersion> 
    </Acl> 
  </Acls> 
</DescribeAccessControlListsResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"3CB646EF-6147-4566-A9D9-CE8FBE86F971",
	"Acls":{
		"Acl":[
			{
				"AclId":"acl-bp1j9vn2g7wm9wn0xassu",
				"AclName":"test",
				"AddressIPVersion":"ipv4"
			},
			{
				"AclId":"acl-bp1l0kk4gxce43kzet04s",
				"AclName":"doctest",
				"AddressIPVersion":"ipv4"
			}
		]
	}
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

