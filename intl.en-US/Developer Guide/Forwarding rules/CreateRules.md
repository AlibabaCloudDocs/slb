# CreateRules {#doc_api_Slb_CreateRules .reference}

Adds forwarding rules for an HTTP or HTTPS listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=CreateRules) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateRules| The name of this action.

 Value: **CreateRules**

 |
|ListenerPort|Integer|Yes|443| The frontend listener port used by the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1ca0zt07t934wxezyxo| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, call **DescribeRegions**.

 |
|RuleList|String|Yes|\[\{"RuleName":"Rule2","Domain":"test.com","VServerGroupId":"rsp-bp114nimo4kl9"\}\]| The forwarding rules to be added. You can add up to 10 forwarding rules in one request. Each rule contains the following parameters:

 -   **RuleName**: This parameter is required and of the string type. The name of the forwarding rule. The name must be 1 to 40 characters in length and can contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). In a listener, the name of each rule must be unique.
-   **Domain**: This parameter is optional and of the string type. It specifies the domain name associated with the forwarding rule.
-   **Url**: This parameter is optional and of the string type. It specifies the access path, which must be 1 to 80 characters in length and can contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), percent signs \(%\), question marks \(?\), number signs \(\#\), and ampersands \(&\).
-   **VServerGroupId**: This parameter is optional and of the string type. The ID of the destination VServer group of the forwarding rule.

 When you configure a forwarding rule, you must set at least this parameter or the Domain parameter, or both. In a listener, the combination of the two parameters must be unique.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|Rules| | | A list of forwarding rules.

 |
|└RuleId|String|rule-bp12jzy0hvio3| The ID of the forwarding rule.

 |
|└RuleName|String|Rule2| The name of the forwarding rule.

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateRules
&ListenerPort=443
&LoadBalancerId=lb-bp1ca0zt07t934wxezyxo
&RegionId=cn-hangzhou
&RuleList=[{"RuleName":"Rule2","Domain":"test.com","VServerGroupId":"rsp-bp114nimo4kl9"}]
&<CommonParameters>

```

Response examples

`XML` format

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

`JSON` format

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

## Error codes {#section_v9b_oql_ewz .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

