# DescribeAccessControlLists

调用DescribeAccessControlLists查询已创建的访问控制策略组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeAccessControlLists&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeAccessControlLists|要执行的操作，取值：**DescribeAccessControlLists**。 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。 |
|AclName|String|否|rule1|访问控制策略组名称。访问控制策略组名称。长度限制为1~80个字符，只支持中文、字母、数字和半角句号（.）、短划线（-）、正斜线（/）和下划线（\_）。访问控制策略组名称必须为地域内唯一。 |
|AddressIPVersion|String|否|ipv4|访问控制策略组绑定的实例的IP类型。取值：

 -   **ipv4**：负载均衡实例的IP地址是IPv4类型。
-   **ipv6**：负载均衡实例的IP地址是IPv6类型。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。 |
|ResourceGroupId|String|否|rg-atstuj3rtop\*\*\*\*\*|企业资源组ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Acls|Array of Acl| |查询到的访问控制策略组列表。 |
|Acl| | | |
|AclId|String|acl-bp1l0kk4gxce43k\*\*\*\*\*|访问控制策略组ID。 |
|AclName|String|rule1|访问控制策略组名称。 |
|AddressIPVersion|String|ipv4|关联的负载均衡实例的IP地址类型。 |
|ResourceGroupId|String|rg-jfenf\*\*\*\*\*\*\*\*\*\*\*|资源组ID。 |
|Count|Integer|5|当前页展示的访问控制策略组个数。 |
|PageNumber|Integer|2|实例列表页码，起始值**1**，默认值**1**。 |
|PageSize|Integer|3|单页结果数量。

 默认值：**50**。 |
|RequestId|String|3CB646EF-6147-4566-A9D9-CE8FBE86F971|请求ID。 |
|TotalCount|Integer|3|已创建的访问控制组策略组个数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeAccessControlLists
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeAccessControlListsResponse>
	  <RequestId>3CB646EF-6147-4566-A9D9-CE8FBE86F971</RequestId>
	  <Acls>
		    <Acl>
			      <AclId>acl-bp1j9vn2g7wm9wn0*****</AclId>
			      <AclName>test</AclName>
			      <AddressIPVersion>ipv4</AddressIPVersion>
		    </Acl>
		    <Acl>
			      <AclId>acl-bp1l0kk4gxce43*****</AclId>
			      <AclName>doctest</AclName>
			      <AddressIPVersion>ipv4</AddressIPVersion>
		    </Acl>
	  </Acls>
</DescribeAccessControlListsResponse>
```

`JSON`格式

```
{
    "RequestId": "3CB646EF-6147-4566-A9D9-CE8FBE86F971", 
    "Acls": {
        "Acl": [
            {
                "AclId": "acl-bp1j9vn2g7wm9wn0****", 
                "AclName": "test", 
                "AddressIPVersion": "ipv4"
            }, 
            {
                "AclId": "acl-bp1l0kk4gxce43*****", 
                "AclName": "doctest", 
                "AddressIPVersion": "ipv4"
            }
        ]
    }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

