# CreateAccessControlList {#doc_api_Slb_CreateAccessControlList .reference}

Creates an access control list.

You can create multiple access control lists. Each list can contain multiple IP addresses and CIDR blocks. Before you create an access control list, note the following limits:

-   Each Alibaba Cloud account can create a maximum of 50 access control lists per region.
-   Each Alibaba Cloud account can add a maximum of 50 IP addresses at a time.
-   Each access control list can contain a maximum of 300 IP entries.
-   Each listener can be associated with a maximum of 50 access control lists.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=CreateAccessControlList) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateAccessControlList| The name of this action. Value: **CreateAccessControlList**

 |
|AclName|String|Yes|rule1| The name of the access control list. The name must be unique in a region.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the access control list belongs.

 |
|AddressIPVersion|String|No|ipv4| Optional. The IP version, which can be set to ipv4 or ipv6.

 **Note:** Currently, IPv6 instances are supported only in the following zones: zones E and F in the China \(Hangzhou\) region, zones F and G in the China \(Beijing\) region, all zones in the China \(Shanghai\) region, and zones D and E in the China \(Shenzhen\) region. Also, the IPv6 instances must be performance-guaranteed instances.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AclId|String|acl-rj9xpxzcwxrukois65yw3| The ID of the access control list.

 |
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA49| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateAccessControlList
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

## Error codes {#section_c4a_71l_xvt .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

