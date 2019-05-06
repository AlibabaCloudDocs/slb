# DeleteAccessControlList {#doc_api_881525 .reference}

使用DeleteAccessControlList删除访问控制策略组。

**说明：** 只有当要删除的访问控制策略组没有绑定任何监听时，才可以删除。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Slb&api=DeleteAccessControlList)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteAccessControlList|要执行的操作，取值：**DeleteAccessControlList**。

 |
|AclId|String|是|acl-bp1l0kk4gxce43kzet04s|访问控制策略组ID。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA49|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?Action=DeleteAccessControlList
&AclId=acl-bp1l0kk4gxce43kzet04s
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteAccessControlListResponse>
  <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
</DeleteAccessControlListResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

异常返回示例

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

