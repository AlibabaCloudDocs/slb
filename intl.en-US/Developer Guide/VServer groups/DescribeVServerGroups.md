# DescribeVServerGroups {#doc_api_Slb_DescribeVServerGroups .reference}

Queries the list of VServer groups.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeVServerGroups) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeVServerGroups| The name of this action.

 Value: **DescribeVServerGroups**

 |
|LoadBalancerId|String|Yes|lb-bp1o94dp5i6earr9g6d1l| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|IncludeListener|Boolean|No|false| Optional. Indicates whether to return the associated listener information.

 Default value: **false**

 |
|IncludeRule|Boolean|No|false| Optional. Indicates whether to return the associated forwarding rule information.

 Default value: **false**

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VServerGroups| | | A list of VServer groups.

 |
|└VServerGroupId|String|rsp-0bfucwuotx| The ID of the VServer group.

 |
|└VServerGroupName|String|Group3| The name of the VServer group.

 |
|└AssociatedObjects| | | Associated information

 |
|└Listeners| | | A list of associated listeners.

 |
|└Port|Integer|80| The listening port.

 |
|└Protocol|String|tcp| The protocol used by the listener.

 |
|└Rules| | | A list of forwarding rules.

 |
|└Domain|String|www.example.com| The request domain name.

 |
|└RuleId|String|123| The ID of the forwarding rule.

 |
|└RuleName|String|test| The name of the forwarding rule.

 |
|└Url|String|/example| The access path.

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeVServerGroups
&LoadBalancerId=lb-bp1o94dp5i6earr9g6d1l
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

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

`JSON` format

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

## Error codes {#section_nb3_4c6_256 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

