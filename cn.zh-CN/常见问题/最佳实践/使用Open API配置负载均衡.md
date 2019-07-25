# 使用Open API配置负载均衡 {#task_lkg_vj5_vdb .task}

您已经创建了两个ECS实例，并授予SSH和Web端口的访问权限。

以下示例中使用URL表示请求参数，并且没有将公共请求参数包含在内。构造完整的请求URL，请参见[负载均衡Open API](../../../../intl.zh-CN/API参考/ API概览.md#)。

**说明：** 为方便阅读，示例中请求URL的参数值没有进行URL编码。

```
    server.modules  = ( "mod_setenv" )
    $HTTP["host"] == "test.example.com" {
          server.document-root = "/var/www/html/"
          setenv.add-response-header = ( "Set-Cookie" => "name=XXXXXX"      }
    }
```

1.  调用CreateLoadBalancer接口创建一个负载均衡实例。 

    请求：

    ```
    https://slb.aliyuncs.com/?Action=CreateLoadBalancer&RegionId=cn-hangzhou
    ```

    响应：

    ```
     {
     "RequestId":"3DE96B24-E2AB-4DFA-9910-1AADD60E13A5",
     "LoadBalancerId":"LoadBalancerId",
     "Address":"SLBIPAddress"
     }
    ```

2.  调用CreateLoadBalancerHttpListener接口为创建好的负载均衡实例添加一个端口为80的HTTP监听。 

    请求：

    ```
    https://slb.aliyuncs.com/?Action=CreateLoadBalancerHttpListener&LoadBalancerId=LoadBalancerId&ListenerPort=80&BackendServerPort=80&ListenerStatus=active
    ```

3.  调用SetLoadBalancerStatus接口激活负载均衡实例。 

    请求：

    ```
    https://slb.aliyuncs.com/?Action=SetLoadBalancerStatus&LoadBalancerId=LoadBalancerId&LoadBalancerStatus=active
    ```

4.  调用AddBackendServers接口将一个ECS实例添加到负载均衡实例中。 

    请求：

    ```
    https://slb.aliyuncs.com/?Action=AddBackendServers&LoadBalancerId=LoadBalancerId&BackendServers=[{"ServerId":"ECS1InstanceID"}]
    ```

    响应

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

5.  再次调用**AddBackendServers**接口将另外一个ECS实例添加到负载均衡实例中。 

    请求：

    ```
    https://slb.aliyuncs.com/?Action=AddBackendServers&LoadBalancerId=LoadBalancerId&BackendServers=[{"ServerId":"ECS2InstanceID"}]
    ```

    响应

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

6.  调用DescribeLoadBalancerAttribute接口查询负载均衡实例的配置信息。 

    请求：

    ```
    https://slb.aliyuncs.com/?Action=DescribeLoadBalancerAttribute&LoadBalancerId=LoadBalancerId
    ```

    响应：

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

    配置完成后，在浏览器中输入负载均衡实例的IP地址，查看服务是否正常。


