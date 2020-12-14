# DescribeMasterSlaveServerGroups

Queries backend servers in a primary/secondary server group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DescribeMasterSlaveServerGroups&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeMasterSlaveServerGroups|The operation that you want to perform.

 Set the value to **DescribeMasterSlaveServerGroups**. |
|LoadBalancerId|String|Yes|lb-bp14zi0n66zpg6o\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is created. |
|IncludeListener|Boolean|No|false|Specifies whether to return the information of the associated listeners. Default value: **false**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|MasterSlaveServerGroups|Array| |The list of backend servers in the primary/secondary server group. |
|MasterSlaveServerGroup| | | |
|MasterSlaveServerGroupId|String|rsp-0bfuc\*\*\*\*\*\*|The ID of the primary/secondary server group. |
|MasterSlaveServerGroupName|String|Group3|The name of the primary/secondary server group. |
|AssociatedObjects|Struct| |The related information. |
|Listeners|Array| |The list of listeners. |
|Listener| | | |
|Port|Integer|80|The listening port. |
|Protocol|String|tcp|The listener protocol. |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=DescribeMasterSlaveServerGroups
&LoadBalancerId=lb-bp14zi0n66zpg6o******
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeMasterSlaveServerGroupsResponse>
      <RequestId>2631BB5E-B576-4925-BDED-07A66D23E5DE</RequestId>
      <MasterSlaveServerGroups>
	    <MasterSlaveServerGroup>
		      <MasterSlaveServerGroupId>rsp-bp1ro3mw******</MasterSlaveServerGroupId>
		      <MasterSlaveServerGroupName>test</MasterSlaveServerGroupName>
	    </MasterSlaveServerGroup>
      </MasterSlaveServerGroups>
</DescribeMasterSlaveServerGroupsResponse>
```

`JSON` format

```
{
    "RequestId": "265989FE-136B-4D6A-B549-FD40E7", 
    "MasterSlaveServerGroups": {
        "MasterSlaveServerGroup": [
            {
                "MasterSlaveServerGroupId": "rsp-bp1nly******", 
                "MasterSlaveServerGroupName": "Primary/secondary server group 1", 
                "AssociatedObjects": {
                    "Listeners": {
                        "Listener": [ ]
                    }
                }
            }
        ]
    }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

