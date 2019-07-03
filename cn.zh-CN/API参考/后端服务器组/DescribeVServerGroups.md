# DescribeVServerGroups {#doc_api_Slb_DescribeVServerGroups .reference}

调用DescribeVServerGroups查询服务器组列表。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DescribeVServerGroups)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVServerGroups|要执行的操作。

 取值：**DescribeVServerGroups**。

 |
|LoadBalancerId|String|是|lb-bp1o94dp5i6earr9g6d1l|负载均衡实例ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|IncludeListener|Boolean|否|false|返回关联的监听信息。

 默认值：**false**。

 |
|IncludeRule|Boolean|否|false|返回关联的转发规则信息。

 默认值：**false**。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VServerGroups| | |后端服务器列表。

 |
|└VServerGroupId|String|rsp-0bfucwuotx|服务器组ID。

 |
|└VServerGroupName|String|Group3|服务器组名称。

 |
|└AssociatedObjects| | |关联信息。

 |
|└Listeners| | |监听列表。

 |
|└Port|Integer|80|监听端口。

 |
|└Protocol|String|tcp|监听协议。

 |
|└Rules| | |转发规则列表。

 |
|└Domain|String|www.example.com|请求域名。

 |
|└RuleId|String|123|转发规则ID。

 |
|└RuleName|String|test|转发规则名称。

 |
|└Url|String|/example|访问路径。

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeVServerGroups
&LoadBalancerId=lb-bp1o94dp5i6earr9g6d1l
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVServerGroupsResponse>
  <VServerGroups>
    <VServerGroup>
      <VServerGroupId>rsp-bp12bjrnykyp0</VServerGroupId>
      <VServerGroupName>6</VServerGroupName>
      <AssociatedObjects>
        <Listeners/>
        <Rules/>
      </AssociatedObjects>
    </VServerGroup>
    <VServerGroup>
      <VServerGroupId>rsp-bp16rt0dzbm23</VServerGroupId>
      <VServerGroupName>text2</VServerGroupName>
      <AssociatedObjects>
        <Listeners/>
        <Rules/>
      </AssociatedObjects>
    </VServerGroup>
  </VServerGroups>
  <RequestId>E3F94C66-5DDD-4A6B-B37D-FD237FB31FE6</RequestId>
</DescribeVServerGroupsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"VServerGroups":[
		{
			"VServerGroupId":"rsp-cige6j5e7p",
			"VServerGroupName":"Group1"
		},
		{
			"VServerGroupId":"rsp-6cejjzlld7",
			"VServerGroupName":"Group2"
		},
		{
			"VServerGroupId":"rsp-0bfucwuotx",
			"VServerGroupName":"Group3"
		}
	],
	"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

