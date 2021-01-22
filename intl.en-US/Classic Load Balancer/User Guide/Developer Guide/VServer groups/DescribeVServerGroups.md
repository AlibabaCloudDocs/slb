# DescribeVServerGroups

Queries the list of VServer groups.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DescribeVServerGroups&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeVServerGroups|The name of this action.

 Value: **DescribeVServerGroups** |
|LoadBalancerId|String|Yes|lb-bp1o94dp5i6ea\*\*\*\*\*\*\*|The ID of the Server Load Balancer \(SLB\) instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs. |
|IncludeRule|Boolean|No|false|Indicates whether to return the information of forwarding rules associated with the VServer groups.

 Default value: **false** |
|IncludeListener|Boolean|No|false|Indicates whether to return the information of listeners associated with the VServer groups.

 Default value: **false** |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |
|VServerGroups|Array| |The list of VServer groups. |
|VServerGroupId|String|rsp-0bfucwuotx|The ID of the VServer group. |
|VServerGroupName|String|Group3|The name of the VServer group. |
|AssociatedObjects|Struct| |The information of associated resources. |
|Listeners|Array| |The list of associated listeners. |
|Protocol|String|tcp|The protocol used by the listener. |
|Port|Integer|80|The port used by the listener. |
|Rules|Array| |The list of associated forwarding rules. |
|RuleId|String|123|The ID of the forwarding rule. |
|Domain|String|www.example.com|The domain name specified in the forwarding rule. |
|Url|String|/example|The URL specified in the forwarding rule. |
|RuleName|String|test|The name of the forwarding rule. |

## Examples

Request example

```
http(s)://[Endpoint]/? Action=DescribeVServerGroups
&LoadBalancerId=lb-bp1o94dp5i6ea*******
&RegionId=cn-hangzhou
&<CommonParameters>
```

Response example

`XML` format

```
<DescribeVServerGroupsResponse>
  <VServerGroups>
        <VServerGroup>
              <VServerGroupId>rsp-bp1oygn******</VServerGroupId>
              <VServerGroupName>k8s/31065/nginx-ingress-lb/kube-system/clust****</VServerGroupName>
              <AssociatedObjects>
                    <Listeners>
            </Listeners>
                    <Rules>
            </Rules>
              </AssociatedObjects>
        </VServerGroup>
        <VServerGroup>
              <VServerGroupId>rsp-bp1i6sn******</VServerGroupId>
              <VServerGroupName>k8s/31605/nginx-ingress-lb/kube-system/clusterid</VServerGroupName>
              <AssociatedObjects>
                    <Listeners>
            </Listeners>
                    <Rules>
            </Rules>
              </AssociatedObjects>
        </VServerGroup>
        <VServerGroup>
              <VServerGroupId>rsp-bp1f85n******</VServerGroupId>
              <VServerGroupName>VSG1</VServerGroupName>
              <AssociatedObjects>
                    <Listeners>
            </Listeners>
                    <Rules>
            </Rules>
              </AssociatedObjects>
        </VServerGroup>
  </VServerGroups>
  <RequestId>31ADDBCD-275F-4C37-B0A3-5DFC8564E686</RequestId>
</DescribeVServerGroupsResponse>
```

`JSON` format

```
{
	"VServerGroups": {
		"VServerGroup": [
			{
				"VServerGroupId": "rsp-bp1oygn******",
				"VServerGroupName": "k8s/31065/nginx-ingress-lb/kube-system/clust****",
				"AssociatedObjects": {
					"Listeners": {
						"Listener": []
					},
					"Rules": {
						"Rule": []
					}
				}
			},
			{
				"VServerGroupId": "rsp-bp1i6sn******",
				"VServerGroupName": "k8s/31605/nginx-ingress-lb/kube-system/clusterid",
				"AssociatedObjects": {
					"Listeners": {
						"Listener": []
					},
					"Rules": {
						"Rule": []
					}
				}
			},
			{
				"VServerGroupId": "rsp-bp1f85n******",
				"VServerGroupName": "VSG1",
				"AssociatedObjects": {
					"Listeners": {
						"Listener": []
					},
					"Rules": {
						"Rule": []
					}
				}
			}
		]
	},
	"RequestId": "31ADDBCD-275F-4C37-B0A3-5DFC8564E686"
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

