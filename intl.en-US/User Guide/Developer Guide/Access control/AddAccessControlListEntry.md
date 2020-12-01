# AddAccessControlListEntry

Adds entries to an access control list \(ACL\).

Each ACL can contain one or more IP addresses or CIDR blocks. The limits on ACLs are:

-   The number of IP addresses that can be added to an ACL with each account at a time: 50
-   The maximum number of entries that each ACL can contain: 300

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=AddAccessControlListEntry&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|AddAccessControlListEntry|The operation that you want to perform. Set the value to **AddAccessControlListEntry**. |
|AclId|String|Yes|acl-bp1l0kk4gxce43kze\*\*\*\*\*|The ID of the ACL. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the ACL is created. |
|AclEntrys|String|No|\[\{"entry":"10.0. \*\*.\*\*/24","comment":"privaterule1"\},\{"entry":"192.168. \*\*.\*\*/16","comment":"privaterule2"\}\]|The ACL settings.

 -   entry: the entries that you want to add to the ACL. You can add CIDR blocks. Separate multiple CIDR blocks with commas \(,\).
-   comment: the comment that you want to add to the ACL.

 **Note:** You can add at most 50 entries to an ACL each time. If the entry that you want to add to an ACL already exists, the entry is not added. The entries that you add must be CIDR blocks. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA4|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=AddAccessControlListEntry
&AclId=acl-bp1l0kk4gxce43kze*****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<AddAccessControlListEntryResponse>
    <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
</AddAccessControlListEntryResponse>
```

`JSON` format

```
{
    "RequestId": "988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

