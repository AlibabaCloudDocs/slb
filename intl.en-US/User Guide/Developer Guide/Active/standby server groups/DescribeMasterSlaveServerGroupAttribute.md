# DescribeMasterSlaveServerGroupAttribute

Queries detailed information about a primary/secondary server group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DescribeMasterSlaveServerGroupAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeMasterSlaveServerGroupAttribute|The operation that you want to perform.

 Set the value to **DescribeMasterSlaveServerGroupAttribute**. |
|MasterSlaveServerGroupId|String|Yes|rsp-cige6j\*\*\*\*\*\*|The ID of the primary/secondary server group. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is created. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|MasterSlaveServerGroupId|String|rsp-cige6\*\*\*\*\*\*|The ID of the primary/secondary server group. |
|MasterSlaveServerGroupName|String|Group1|The name of the primary/secondary server group. |
|MasterSlaveBackendServers|Array| |The list of backend servers in the primary/secondary server group. |
|MasterSlaveBackendServer| | | |
|ServerId|String|vm-hrf\*\*\*\*\*\*|The ID of the Elastic Compute Service \(ECS\) instance or elastic network interface \(ENI\). |
|Port|Integer|90|The port that is used by the backend server. |
|Weight|Integer|100|The weight of the backend server. |
|ServerType|String|Slave|The type of backend server. Valid values: **Master and Slave**. Default value: Master. |
|Description|String|The description of the primary/secondary server group.|The description of the primary/secondary server group. |
|Type|String|ecs|The type of backend server. Valid values:

 -   **ecs**: ECS instance. This is the default value.
-   **eni**: ENI. |
|LoadBalancerId|String|lb-14fadafw4343a\*\*\*\*\*\*|The ID of the SLB instance. |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=DescribeMasterSlaveServerGroupAttribute
&MasterSlaveServerGroupId=rsp-cige6j******
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeMasterSlaveServerGroupAttributeResponse>
    <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    <MasterSlaveServerGroupId>rsp-cige6******</MasterSlaveServerGroupId>
    <MasterSlaveBackendServers>
          <MasterSlaveBackendServers>
                <ServerId>vm-sshssh****</ServerId>
                <Port>80</Port>
                <Weight>100</Weight>
                <ServerType>Master</ServerType>
          </MasterSlaveBackendServers>
          <MasterSlaveBackendServers>
                <ServerId>vm-ffff*****</ServerId>
                <Port>90</Port>
                <Weight>100</Weight>
                <ServerType>Slave</ServerType>
          </MasterSlaveBackendServers>
    </MasterSlaveBackendServers>
</DescribeMasterSlaveServerGroupAttributeResponse>
```

`JSON` format

```
{
  "DescribeMasterSlaveServerGroupAttributeResponse": {
    "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
    "MasterSlaveServerGroupId": "rsp-cige6******",
    "MasterSlaveBackendServers": {
      "MasterSlaveBackendServers": [
        {
          "ServerId": "vm-sshssh****",
          "Port": "80",
          "Weight": "100",
          "ServerType": "Master"
        },
        {
          "ServerId": "vm-ffff*****",
          "Port": "90",
          "Weight": "100",
          "ServerType": "Slave"
        }
      ]
    }
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

