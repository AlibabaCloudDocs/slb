# DescribeVServerGroups

调用DescribeVServerGroups查询服务器组列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeVServerGroups&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVServerGroups|要执行的操作。

 取值：**DescribeVServerGroups**。 |
|LoadBalancerId|String|是|lb-bp1o94dp5i6ea\*\*\*\*\*\*\*|负载均衡实例ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |
|IncludeRule|Boolean|否|false|返回关联的转发规则信息。

 默认值：**false**。 |
|IncludeListener|Boolean|否|false|返回关联的监听信息。

 默认值：**false**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。 |
|VServerGroups|Array| |后端服务器列表。 |
|VServerGroupId|String|rsp-0bfucwuotx|服务器组ID。 |
|VServerGroupName|String|Group3|服务器组名称。 |
|AssociatedObjects|Struct| |关联信息。 |
|Listeners|Array| |监听列表。 |
|Protocol|String|tcp|监听协议。 |
|Port|Integer|80|监听端口。 |
|Rules|Array| |转发规则列表。 |
|RuleId|String|123|转发规则ID。 |
|Domain|String|www.example.com|请求域名。 |
|Url|String|/example|访问路径。 |
|RuleName|String|test|转发规则名称。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeVServerGroups
&LoadBalancerId=lb-bp1o94dp5i6ea*******
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

