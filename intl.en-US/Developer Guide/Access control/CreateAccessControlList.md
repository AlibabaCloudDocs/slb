# CreateAccessControlList {#doc_api_876090 .reference}

Creates an access control policy group.

You can create multiple access control policy groups, and each group can contain multiple IP addresses or CIDR blocks. Access control policy groups are subject to the following limits:

-   Each Alibaba Cloud account can create a maximum of 50 access control policy groups per region.
-   Each Alibaba Cloud account can add a maximum of 50 IP addresses at a time.
-   Each access control policy group can contain a maximum of 300 items.
-   Each listener can be attached with a maximum of 50 access control policy groups.

## Debug {#apiExplorer .section}

We recommend that you use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers) to call APIs, generate SDK code examples, perform debug operations, and search for APIs.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateAccessControlList| The name of this action. Value: **CreateAccessControlList**

 |
|AclName|String|Yes|rule1| The name of the access control policy group. The name must be unique among all the groups in the same region.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the access control policy group belongs.

 |
|AddressIPVersion|String|No|ipv4| Optional. The IP version, which can be set to ipv4 or ipv6.

 **Note:** Currently, only zones E and F in the China \(Hangzhou\) region, zones G and F in the China \(Beijing\) region, and zone E \(primary zone\) and Zone D \(secondary zone\) in the China \(Shanghai\) region support IPv6 performance-guaranteed instances.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AclId|String|acl-rj9xpxzcwxrukois65yw3| The ID of the access control policy group.

 |
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA49| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}
http(s)://[Endpoint]/?Action=CreateAccessControlList
&AclName=rule1
&RegionId=cn-hangzhou
&<CommonParameters>
			
```

Response examples

`XML` format

``` {#xml_return_success_demo}
<CreateAccessControlListResponse>
  <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
  <AclId>acl-rj9xpxzcwxrukois65yw3</AclId>
</CreateAccessControlListResponse>
			
```

`JSON` format

``` {#json_return_success_demo}
{
	"AclId":"acl-rj9xpxzcwxrukois65yw3",
	"RequestId":"988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

