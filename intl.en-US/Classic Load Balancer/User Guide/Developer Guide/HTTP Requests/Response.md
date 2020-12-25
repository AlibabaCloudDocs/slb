# Response

Responses are returned in the JSON or XML format. The default response format is XML. To change the format, you can set the `Format` parameter in requests. For more information, see [Common parameters](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTP Requests/Common parameters.md). Sample responses provided in API reference are formatted with line feeds and indentations for better readability and clarity. However, the actual responses are not formatted with line feeds or indentations.

## Sample success responses

Each response returns response parameters such as the request ID when the call is successful. The HTTP status code is 2xx.

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? > <! --Result Root Node-->
    <ActionResponse> <! --Return Request Tag-->
        <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId> <! --Return Result Data-->
    </ActionResponse>
    ```

-   JSON format

    ```
    {
        "RequestId": "4C467B38-3910-447D-87BC-AC049166F216" /* Response data */
    }
    ```


## Sample error response

If an error occurs when you call an operation, an error response that consists of the error code, error message, and request ID is returned. The HTTP status code is 4xx or 5xx.

To troubleshoot the error based on the error code, see [Common error codes](#commonErrorCodes) and visit [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs). If the error persists, you can [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) and provide `HostId` and `RequestId` to request technical support from Alibaba Cloud.

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? ><! --Result Root Node-->
    <Error>
        <RequestId>540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx</RequestId> <! --Request ID-->
        <HostId>ecs.aliyuncs.com</HostId> <! --Endpoint-->
        <Code>MissingParameter.CommandId</Code> <! --Error Code-->
        <Message>The input parameter “CommandId” that is mandatory for processing this request is not supplied. </Message> <! -- Error message-->
    </Error>
    ```

-   JSON format

    ```
    {
        "RequestId": "540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx", /* Request ID */
        "HostId": "ecs.aliyuncs.com", /* Service endpoint */
        "Code": "MissingParameter.CommandId", /* Error code */
        <Message>The input parameter “CommandId” that is required for processing this request is not supplied. /* Error message */
    }
    ```


## Common error codes

|Error code|HTTP status code|Error message|
|:---------|:---------------|:------------|
|IdempotentParameterMismatch|400|The request is retried with updated parameters.|
|IllegalTimestamp|400|The input parameter “Timestamp” that is mandatory for processing this request is not supplied.|
|IncompleteSignature|400|The request signature does not conform to Aliyun standards.|
|InsufficientBalance|400|Your account does not have enough balance.|
|InvalidAccessKeyId.NotFound|400|The specified Access Key ID does not exist.|
|InvalidOwner|400|OwnerId and OwnerAccount can’t be used at one API access.|
|InvalidOwnerAccount|400|The specified OwnerAccount is not valid.|
|InvalidOwnerId|400|The specified OwnerId is not valid.|
|InvalidParamater|400|The specified parameter “SignatureMethod” is not valid.|
|InvalidParamater|400|The specified parameter “SignatureVersion” is not valid.|
|InvalidParameter|400|The specified parameter is not valid.|
|InvalidParameter|400|The specified parameter “Action or Version” is not valid.|
|InvalidParameter.IsNull|400|The required parameter must be not null.|
|MissingParameter|400|The input parameter “Action” that is mandatory for processing this request is not supplied|
|MissingParameter|400|The input parameter “AccessKeyId” that is mandatory for processing this request is not supplied|
|MissingParameter|400|The input parameter “Signature” that is mandatory for processing the request is not supplied.|
|MissingParameter|400|The input parameter “TimeStamp” that is mandatory for processing this request is not supplied|
|MissingParameter|400|The input parameter “Version” that is mandatory for processing this request is not supplied|
|SignatureNonceUsed|400|The request signature nonce has been used.|
|Throttling|400|You have made too many requests within a short time; your request is denied due to request throttling.|
|UnsupportedParameter|400|The parameters is unsupported.|
|UnknownError|400|The request processing has failed due to some unknown error.|
|ChargeTypeViolation|403|The operation is not permitted due to charge type of the instance.|
|Forbidden.AccessKeyDisabled|403|The Access Key is disabled.|
|Forbidden.NotSupportRAM|403|This action does not support accessed by RAM mode.|
|Forbidden.RAM|403|User not authorized to operate on the specified resource, or this API doesn’t support RAM.|
|Forbidden.RiskControl|403|This operation is forbidden by Aliyun RiskControl system.|
|Forbidden.SubUser|403|The specified action is not available for you.|
|Forbidden.Unauthorized|403|User not authorized to operate on the specified resource.|
|InvalidAccount.NotFound|403|The specified Account does not exist.|
|InvalidAction|403|Specified action is not valid.|
|InvalidIdempotenceParameter.Mismatch|403|The specified parameters are different from before.|
|InvalidParameter.OwnerAccount|403|OwnerAccount is Invalid.|
|InvalidParameter.ResourceOwnerAccount|403|ResourceOwnerAccount is Invalid.|
|LastTokenProcessing|403|The last token request is processing.|
|MissingParameter|403|The input parameter OwnerId,OwnerAccount that is mandatory for processing this request is not supplied.|
|RealNameAuthenticationError|403|Your account has not passed the real-name authentication yet.|
|UnsupportedHTTPMethod|403|This http method is not supported.|
|InvalidDiskId.NotFound|404|The specified DiskId does not exist.|
|InvalidImageId.NotFound|404|The specified ImageId does not exist.|
|InvalidInstanceId.NotFound|404|The specified InstanceId does not exist.|
|InvalidRegionId.NotFound|404|The specified RegionId does not exist.|
|InvalidSecurityGroupId.NotFound|404|The specified SecurityGroupId does not exist.|
|InvalidSnapshotId.NotFound|404|The specified SnapshotId does not exist.|
|OperationConflict|409|Request was denied due to conflict with a previous request.|
|InternalError|500|The request processing has failed due to some unknown error, exception or failure.|
|ServiceUnavailable|503|The request has failed due to a temporary failure of the server.|
|ServiceUnavailable.RegionMaintaining|503|System maintenance is in progress on the selected region, please wait a few minutes before trying again.|

