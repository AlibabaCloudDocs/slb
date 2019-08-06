# DeleteAccessControlList {#doc_api_Slb_DeleteAccessControlList .reference}

Deletes an access control list.

**Note:** An access control list can be deleted only after it is disassociated from a listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DeleteAccessControlList) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteAccessControlList| The name of this action. Value: **DeleteAccessControlList**

 |
|AclId|String|Yes|acl-bp1l0kk4gxce43kz\*\*\*\*\*\*| The ID of the access control list to be deleted.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the access control list belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA49| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteAccessControlList
&AclId=acl-bp1l0kk4gxce43kz******
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DeleteAccessControlListResponse>
  <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
</DeleteAccessControlListResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

## Error codes {#section_pat_a9j_b9g .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

