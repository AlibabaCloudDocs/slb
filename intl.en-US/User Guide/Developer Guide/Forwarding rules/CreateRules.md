# CreateRules

Creates forwarding rules for HTTP and HTTPS listeners.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=CreateRules&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateRules|The operation that you want to perform.

Set the value to **CreateRules**. |
|ListenerPort|Integer|Yes|443|The frontend listener port that is used by the Server Load Balancer \(SLB\) instance.

Valid values:**1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1ca0zt07t934w\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is created.

You can call the**DescribeRegions** operation to query region IDs. |
|RuleList|String|Yes|\[\{"RuleName":"Rule2","Domain":"test.com","VServerGroupId":"rsp-bp114ni\*\*\*\*\*\*"\}\]|The forwarding rules that you want to add. A maximum of 10 forwarding rules can be added in each API request. Each forwarding rule contains the following parameters:

-   **RuleName**: Required. The name of the forwarding rule. The value must be of STRING type. The name of the forwarding rule must be 1 to 40 characters in length and can contain only letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). Forwarding rule names must be unique within each listener.
-   **Domain**: Optional. The value must be of STRING type. The domain name that is associated with the forwarding rule. You must specify at least this parameter or **URL**.
-   **Url**: Optional. The value must be of STRING type. This parameter specifies the requested URL. It must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), %? number signs \(\#\), and ampersands \(&\). The URL must start with a forward slash \(/\) and cannot contain only a forward slash \(/\). You must specify at least this parameter or **Domain**.
-   **VServerGroupId**: Required. The value must be of STRING type. The ID of the destination vServer group that is specified in the forwarding rule.

You must specify at least one of the following parameters: Domain and Url. You can also specify both. The combination of Domain and Url must be unique within a listener. |
|ListenerProtocol|String|No|https|The frontend listener protocol that is used by the SLB instance.

**Note:** This parameter is required when listeners that use different protocols listen on the same port. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Rules|Array| |The forwarding rules. |
|Rule| | | |
|RuleId|String|rule-bp12jzy0\*\*\*\*\*|The ID of the forwarding rule. |
|RuleName|String|Rule2|The name of the forwarding rule. |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=CreateRules
&ListenerPort=443
&LoadBalancerId=lb-bp1ca0zt07t934w******
&RegionId=cn-hangzhou
&RuleList=[{"RuleName":"Rule2","Domain":"test.com","VServerGroupId":"rsp-bp114ni******"}]
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateRulesResponse>
      <RequestId>D63E42FB-F963-4EE5-9B32-05602BF351F3</RequestId>
      <Rules>
            <Rule>
                  <RuleId>rule-bp12jzy******</RuleId>
                  <RuleName>Rule3</RuleName>
            </Rule>
      </Rules>
</CreateRulesResponse>
```

`JSON` format

```
{
    "RequestId": "D63E42FB-F963-4EE5-9B32-05602BF351F3", 
    "Rules": {
        "Rule": [
            {
                "RuleId": "rule-bp12jzy******", 
                "RuleName": "Rule3"
            }
        ]
    }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|DomainExist|rule with same domain and url already exists in specified vip|The error message returned because a forwarding rule with the same domain name and URL is already created for the listener.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

