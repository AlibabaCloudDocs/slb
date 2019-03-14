# CreateRules {#doc_api_1065223 .reference}

调用CreateRules为指定的HTTP或HTTPS监听添加转发规则。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=CreateRules)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateRules|要执行的操作，取值：

 **CreateRules**

 |
|ListenerPort|Integer|是|443|负载均衡实例前端使用的监听端口。

 取值范围：1~65535

 |
|LoadBalancerId|String|是|lb-bp1ca0zt07t934wxezyxo|负载均衡实例ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 您可以通过调用**DescribeRegions**接口查询地域ID。

 |
|RuleList|String|是|\[\{"RuleName":"Rule2","Domain":"test.com","VServerGroupId":"rsp-bp114nimo4kl9"\}\]|要添加的转发规则。一次请求中，最多可添加10条转发规则。每条转发规则包含以下参数：

 -   **RuleName**（必选）：String类型。转发规则名称，长度限制为1~40，只能使用字母、数字和-/.\_这些字符。同一个监听内不同规则的名称必须唯一。
-   **Domain**（可选）： String类型。转发规则关联的请求域名。
-   **Url**（可选）：String类型，可选，访问路径，长度限制为1~80，只能使用字母、数字和-/.%?\#&这些字符。
-   **VServerGroupId**（必选）：String类型。该转发规则的目标虚拟服务器组ID。

 Domain和Url两者必须指定一个，也可以同时指定。Domain和Url的组合在同一个监听内必须唯一。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Rules| | |转发规则列表。

 |
|└RuleId|String|rule-bp12jzy0hvio3|转发规则ID。

 |
|└RuleName|String|Rule2|转发规则名称。

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateRules
&ListenerPort=443
&LoadBalancerId=lb-bp1ca0zt07t934wxezyxo
&RegionId=cn-hangzhou
&RuleList=[{"RuleName":"Rule2","Domain":"test.com","VServerGroupId":"rsp-bp114nimo4kl9"}]
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateRulesResponse>
  <RequestId>D63E42FB-F963-4EE5-9B32-05602BF351F3</RequestId>
  <Rules>
    <Rule>
      <RuleId>rule-bp12jzy0hvio3</RuleId>
      <RuleName>Rule3</RuleName>
    </Rule>
  </Rules>
</CreateRulesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"D63E42FB-F963-4EE5-9B32-05602BF351F3",
	"Rules":{
		"Rule":[
			{
				"RuleId":"rule-bp12jzy0hvio3",
				"RuleName":"Rule3"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

