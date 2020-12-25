# Request syntax

Alibaba Cloud Server Load Balancer \(SLB\) allows you to call API operations by initiating HTTP or HTTPS GET requests to specific URLs. Each URL must include request parameters. This topic describes the syntax of HTTP or HTTPS GET requests and provides the endpoint of the SLB API.

## Request syntax

SLB API operations use the Remote Procedure Call \(RPC\) protocol. Requests are created based on the following syntax:

```
http://Endpoint/?Action=xx&Parameters
```

The following example demonstrates how to call the DescribeLoadBalancers operation to create a SLB instance:

**Note:** The following code has been formatted to ease reading.

```
https://slb.aliyuncs.com/?Action=DescribeLoadBalancers
&Format=xml
&Version=2014-05-15
&Signature=xxxx%xxxx%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&TimeStamp=2012-06-01T12:00:00Z
…
```

In this example:

-   Endpoint: the endpoint of the SLB API is slb.aliyuncs.com. You can call the [DescribeRegions](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/DescribeRegions.md) operation to obtain the endpoint corresponds to a specified region.
-   Action: the name of the operation you want to perform. For example, to query created SLB instances, you must set the Action parameter to DescribeLoadBalancers.
-   RegionId: the region where the SLB instance is deployed.
-   Version: the version of the API that you want to use. The current SLB API version is 2014-05-15.
-   Parameters: the request parameters for the operation. Separate multiple parameters with ampersands \(&\).

    Request parameters include common parameters and operation-specific parameters. Common parameters include the API version and authentication information. For more information, see [Common parameters](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTP Requests/Common parameters.md).


