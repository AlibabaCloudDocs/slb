# Use Open API to configure Server Load Balancer {#task_lkg_vj5_vdb .task}

You have created two ECS instances and granted access to their SSH and Web ports.

In this topic, the request parameters are included in the request URL, and the URL does not include common parameters. For more information, see [API overview](../../../../intl.en-US/.md#).

**Note:** To increase readability, the parameter values of the request URL in this example are not URL-encoded.

```
    server.modules  = ( "mod_setenv" )
    $HTTP["host"] == "test.example.com" {
          server.document-root = "/var/www/html/"
          setenv.add-response-header = ( "Set-Cookie" => "name=XXXXXX"      }
    }
```

1.  Call the CreateLoadBalancer API to create a Server Load Balancer instance. 

    Request:

    ```
    https://slb.aliyuncs.com/?Action=CreateLoadBalancer&RegionId=cn-hangzhou
    ```

    Response:

    ```
     {
     "RequestId":"3DE96B24-E2AB-4DFA-9910-1AADD60E13A5",
     "LoadBalancerId":"LoadBalancerId",
     "Address":"SLBIPAddress"
     }
    ```

2.  Call the CreateLoadBalancerHttpListener API to create an HTTP listener, of which the port is 80, for the Server Load Balancer instance. 

    Request:

    ```
    https://slb.aliyuncs.com/?Action=CreateLoadBalancerHttpListener&LoadBalancerId=LoadBalancerId&ListenerPort=80&BackendServerPort=80&ListenerStatus=active
    ```

3.  Call the SetLoadBalancerStatus API to activate the Server Load Balancer instance. 

    Request:

    ```
    https://slb.aliyuncs.com/?Action=SetLoadBalancerStatus&LoadBalancerId=LoadBalancerId&LoadBalancerStatus=active
    ```

4.  Call the AddBackendServers API to add an ECS instance to the Server Load Balancer instance. 

    Request:

    ```
    https://slb.aliyuncs.com/?Action=AddBackendServers&LoadBalancerId=LoadBalancerId&BackendServers=[{"ServerId":"ECS1InstanceID"}]
    ```

    Response:

    ```
    {
         "RequestId" : "FA2F2172-63F2-409D-927C-86BD1D536F13",
         "LoadBalancerId" : "LoadBalancerId",
         "BackendServers" : {
             "BackendServer" : [
                 {
                     "ServerId" : "ECS1InstanceId",
                     "Weight" : 100
                 }
             ]
         }
     }
    ```

5.  Call the **AddBackendServers** API again to add another ECS instance to the Server Load Balancer instance. 

    Request:

    ```
    https://slb.aliyuncs.com/?Action=AddBackendServers&LoadBalancerId=LoadBalancerId&BackendServers=[{"ServerId":"ECS2InstanceID"}]
    ```

    Response:

    ```
     {
         "RequestId" : "C61FAD0A-2E87-4D0C-80B0-95AB758FCA70",
         "LoadBalancerId" : "LoadBalancerId",
         "BackendServers" : {
         "BackendServer" : [
             {
                 "ServerId" : "ECS1InstanceId",
                 "Weight" : 100
             },
             {
                 "ServerId" : "ECS2InstanceId",
                 "Weight" : 100
              }
           ]
         }
     }
    ```

6.  Call the DescribeLoadBalancerAttribute API to view the configuration of the Server Load Balancer instance. 

    Request:

    ```
    https://slb.aliyuncs.com/?Action=DescribeLoadBalancerAttribute&LoadBalancerId=LoadBalancerId
    ```

    Response:

    ```
     {
         "RequestId" : "4747E9AE-ADFD-412D-B523-C1CBD45A2154",
         "LoadBalancerId" : "LoadBalancerId",
         "Address" : "SLBIPAddress",
         "IsPublicAddress" : "true",
         "ListenerPorts" : {
             "ListenerPort" : [
                 80
             ]
         },
         "BackendServers" : {
             "BackendServer" : [
                 {
                     "ServerId" : "ECS1InstanceId",
                     "Weight" : 100
                 },
                 {
                     "ServerId" : "ECS2InstanceId",
                     "Weight" : 100
                 }
             ]
         }
     }
    ```

    Use your browser to access the IP address of the Server Load Balancer instance to verify whether the service is working.


