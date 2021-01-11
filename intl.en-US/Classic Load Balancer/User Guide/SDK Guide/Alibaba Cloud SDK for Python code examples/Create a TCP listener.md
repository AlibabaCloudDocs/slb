# Create a TCP listener

This topic describes how to use SLB SDK for Python to create a TCP listener for an SLB instance and then delete the SLB instance.

Two Elastic Compute Service \(ECS\) instances are created in the China \(Zhangjiakou\) region. Both ECS instances are in the **Running** state.

Before you run the following code in script mode, make sure that the following requirements are met:

1.  Your account has a balance of at least CNY 100 so that you can be charged the instance fee when you use SLB SDK for Python to create an SLB instance.
2.  An AccessKey pair is obtained.

    An AccessKey ID and an AccessKey secret that are used to verify your identity are obtained. For more information about how to obtain an AccessKey pair, see [Obtain an AccessKey pair](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Obtain an AccessKey pair.md).

3.  The [SLB Python example library](https://github.com/aliyun/aliyun-openapi-python-sdk-examples) for implementing SLB features with Alibaba Cloud SLB SDK for Python is downloaded.
4.  Go to the directory where setup.py is stored and run the following command to initialize the environment:

    ```
    python setup.py install
    ```


In this example, the following configurations are used:

-   Create an SLB instance in the China \(Zhangjiakou\) region. Set the name of the SLB instance to SLB1, set the primary zone to cn-zhangjiakou-a, and set the secondary zone to cn-zhangjiakou-b. Then, set the billing method of the SLB instance to pay-as-you-go and set the type of the SLB instance to slb.s1.small. For other parameters, use the default settings.
-   Add the ECS instances that are created in the China \(Zhangjiakou\) region to the default server group. Network traffic is then forwarded by the SLB instance to the ECS instances. Then, set the weights of both ECS instances to 100.
-   Create a TCP listener. Set the frontend port that is used by the SLB instance to port 80 and set the backend port that is used to receive requests to port 80. Then, set the health check protocol to TCP. The maximum bandwidth of the listener is not limited. For other parameters, use the default settings.
-   After the TCP listener is created, remove the ECS instances from the default server group and delete the created SLB instance.

1.  In the directory to which the SDK is downloaded, open the folder $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb.

2.  Open slb\_create\_tcp\_listener.py in the editor. Set the ACS\_CLIENT parameter to configure user identity verification and set other parameters based on your actual needs. Then, save the file and exit.

    **Note:** The SDK verifies the identity of every user. You can set the AcsClient parameter in a constants file and call the constants file when you need it.

    ```
    # encoding=utf-8
    import json
    import sys
    
    #Import AcsClient to verify the identity of the API caller.
    from aliyunsdkcore.client import AcsClient
    #Use the exception handling module of Alibaba Cloud SDK.
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    #Import the API operation for creating an SLB instance.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerRequest
    #Import the API operation for adding a default server group.
    from aliyunsdkslb.request.v20140515 import AddBackendServersRequest
    #Import the API operation for creating a TCP listener.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerTCPListenerRequest
    #Import the API operation for removing ECS instances from the default server group.
    from aliyunsdkslb.request.v20140515 import RemoveBackendServersRequest
    #Import the API operation for deleting an SLB instance.
    from aliyunsdkslb.request.v20140515 import DeleteLoadBalancerRequest
    #Print logs at the command-line interface.
    from sdk_lib.common_util import CommonUtil
    #Handle exceptions.
    from sdk_lib.exception import ExceptionHandler
    
    '''
    Create an SLB instance -> Add backend servers -> Create a TCP listener -> Remove backend servers -> Delete the SLB instance.
    '''
    #Configure the parameters of the client.
    ACS_CLIENT = AcsClient(
        'your-access-key-id',  # your-access-key-id
        'your-access-key-secret',  # your-access-key-secret
        'cn-zhangjiakou',  # your-region-id
    )
    
    TRY_TIME = 3
    
    
    def create_load_balancer(params):
        '''
        create_load_balancer: creates an SLB instance.
        For more information about the API operation, visit https://help.aliyun.com/document_detail/27577.html.
        '''
        try:
            #Set the API request parameters for creating an SLB instance.
            request = CreateLoadBalancerRequest.CreateLoadBalancerRequest()
            request.set_MasterZoneId(params["master_zone_id"])
            request.set_SlaveZoneId(params["slave_zone_id"])
            request.set_LoadBalancerName(params["load_balancer_name"])
            request.set_PayType(params["pay_balancer_type"])
            request.set_LoadBalancerSpec(params["load_balancer_spec"])
            #Make an API request and receives a response.
            response = ACS_CLIENT.do_action_with_exception(request)
            response_json = json.loads(response)
            #API response.
            return response_json
        except ServerException as e:
            ExceptionHandler.server_exception(e)
        except ClientException as e:
            ExceptionHandler.client_exception(e)
    
    
    def add_backend_servers(params):
        '''
        add_backend_servers: adds backend servers.
        For more information about the API operation, visit https://help.aliyun.com/document_detail/27632.html.
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                #Set the API request parameters for creating a default server group.
                request = AddBackendServersRequest.AddBackendServersRequest()
                #The ID of the SLB instance.
                request.set_LoadBalancerId(params["load_balancer_id"])
                #The list of backend servers to be added.
                request.set_BackendServers(params["backend_servers"])
                #Make an API request and receives a response.
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #API response.
                return response_json
            except ServerException as e:
                if ExceptionHandler.server_exception(e):
                    return e
            except ClientException as e:
                if ExceptionHandler.client_exception(e):
                    return e
            finally:
                counter += 1
    
    
    def create_tcp_listener(params):
        '''
        create_tcp_listener: creates a TCP listener.
        For more information about the API operation, visit https://help.aliyun.com/document_detail/27594.html.
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                #Set the API request parameters for creating a TCP listener.
                request = CreateLoadBalancerTCPListenerRequest.CreateLoadBalancerTCPListenerRequest()
                #The ID of the SLB instance.
                request.set_LoadBalancerId(params["load_balancer_id"])
                #The frontend port that is used by the SLB instance.
                request.set_ListenerPort(params["listener_port"])
                #The backend port that is used by the SLB instance.
                request.set_BackendServerPort(params["backend_server_port"])
                #The health check protocol of the listener.
                request.set_HealthCheckType(params["listener_health_check"])
                #Set the maximum bandwidth of the listener.
                request.set_Bandwidth(params["listener_bandwidth"])
                #Make an API request and receives a response.
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #API response.
                return response_json
            except ServerException as e:
                if ExceptionHandler.server_exception(e):
                    return e
            except ClientException as e:
                if ExceptionHandler.client_exception(e):
                    return e
            finally:
                counter += 1
    
    
    def remove_backend_servers(params):
        '''
        add_backend_servers: removes backend servers.
        For more information about the API operation, visit https://help.aliyun.com/document_detail/27633.html.
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                #Set the API request parameters for removing backend servers.
                request = RemoveBackendServersRequest.RemoveBackendServersRequest()
                #The ID of the SLB instance.
                request.set_LoadBalancerId(params["load_balancer_id"])
                #The list of backend servers to be removed.
                request.set_BackendServers(params["backend_servers"])
                #Make an API request and receives a response.
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #API response.
                return response_json
            except ServerException as e:
                if ExceptionHandler.server_exception(e):
                    return e
            except ClientException as e:
                if ExceptionHandler.client_exception(e):
                    return e
            finally:
                counter += 1
    
    
    def delete_load_balancer(load_balancer_id):
        '''
        delete_load_balancer: deletes an SLB instance.
        For more information about the API operation, visit https://help.aliyun.com/document_detail/27579.html.
        '''
        try:
            #Set the API request parameters for deleting an SLB instance.
            request = DeleteLoadBalancerRequest.DeleteLoadBalancerRequest()
            #The ID of the SLB instance.
            request.set_LoadBalancerId(load_balancer_id)
            #Make an API request and receives a response.
            response = ACS_CLIENT.do_action_with_exception(request)
            response_json = json.loads(response)
            #API response.
            return response_json
        except ServerException as e:
            ExceptionHandler.server_exception(e)
        except ClientException as e:
            ExceptionHandler.client_exception(e)
    
    
    def main():
        params = {}
    
        #Set the parameters of the SLB instance to be created.
        #Set the primary zone of the new SLB instance to cn-zhangjiakou-a.
        params["master_zone_id"] = "cn-zhangjiakou-a"
        #Set the secondary zone of the new SLB instance to cn-zhangjiakou-b.
        params["slave_zone_id"] = "cn-zhangjiakou-b"
        #Set the name of the new SLB instance to SLB1.
        params["load_balancer_name"] = "SLB1"
        #Set the billing method of the new SLB instance to pay-as-you-go.
        params["pay_balancer_type"] = "PayOnDemand"
        #Set the type of the new SLB instance to slb.s1.small.
        params["load_balancer_spec"] = "slb.s1.small"
        #Set the IDs and weights of the ECS instances to be added to the default server group.
        params["backend_servers"] = [{"ServerId": "i-8vbe8yi8krxxxxxxxxxxw", "Weight": "100"},
                                     {"ServerId": "i-8vbe8yi8kccxxxxxxxxxv", "Weight": "100"}]
    
        #Set parameters for the TCP listener.
        #Set the frontend port to port 80.
        params["listener_port"] = 80
        #Set the backend port that is used to receive requests to port 80.
        params["backend_server_port"] = 80
        #Set the health check protocol to TCP.
        params["listener_health_check"] = "tcp"
        #Set the maximum bandwidth of the TCP listener to -1. This indicates that the maximum bandwidth is not limited.
        params["listener_bandwidth"] = -1
    
        #Create an SLB instance.
        #Obtain the returned value of create_load_balancer. load_balancer_json is the returned value in a JSON string.
        load_balancer_json = create_load_balancer(params)
        #Print the returned value of load_balancer_json. create_load_balancer is the name of the JSON string.
        CommonUtil.log("create_load_balancer", load_balancer_json)
    
        #The ID of the SLB instance.
        params["load_balancer_id"] = load_balancer_json["LoadBalancerId"]
    
        #Add backend servers.
        load_balancer_json = add_backend_servers(params)
        CommonUtil.log("add_backend_servers", load_balancer_json)
    
        #Create a TCP listener.
        load_balancer_json = create_tcp_listener(params)
        CommonUtil.log("create_tcp_listener", load_balancer_json)
    
        #Remove backend servers.
        load_balancer_json = remove_backend_servers(params)
        CommonUtil.log("remove_backend_servers", load_balancer_json)
    
        #Delete an SLB instance.
        #Delete the SLB instance with the returned LoadBalancerId.
        load_balancer_json = delete_load_balancer(load_balancer_json["LoadBalancerId"])
        #Print the returned value of load_balancer_json.
        CommonUtil.log("delete_load_balancer", load_balancer_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

3.  Go to the directory where slb\_create\_tcp\_listener.py is stored and run following command to create a TCP listener:

    ```
    python slb_create_tcp_listener.py
    ```

    The following output is returned:

    ```
    ---------------------------create_load_balancer---------------------------
    {
      "VpcId": "",
      "AddressIPVersion": "ipv4",
      "LoadBalancerName": "SLB1",
      "ResourceGroupId": "rg-acfmxazb4pxxxxx",
      "VSwitchId": "",
      "RequestId": "8E72DFDD-E510-4D65-9063-F47B62DE9887",
      "Address": "39.98.xx.xx",
      "NetworkType": "classic",
      "LoadBalancerId": "lb-8vbjd6pzphvjoq29xxxxx"
    }
    
    ---------------------------add_backend_servers---------------------------
    {
      "RequestId": "F6BF0E0B-5837-48A3-9CEC-2EE2CED5293A",
      "BackendServers": {
        "BackendServer": [
          {
            "ServerId": "i-8vbe8yi8krqri2axxxxx",
            "Type": "ecs",
            "Weight": 100
          },
          {
            "ServerId": "i-8vbe8yi8krqri2xxxxxx",
            "Type": "ecs",
            "Weight": 100
          }
        ]
      },
      "LoadBalancerId": "lb-8vbjd6pzphvjoq29xxxxx"
    }
    
    ---------------------------create_tcp_listener---------------------------
    {
      "RequestId": "6FF090BD-DF9F-49C6-84A6-30F2D9F88489"
    }
    
    ---------------------------remove_backend_servers---------------------------
    {
      "RequestId": "F7D62969-D7F0-4022-95FA-1710DA448B6A",
      "BackendServers": {
        "BackendServer": []
      },
      "LoadBalancerId": "lb-8vbjd6pzphvjoq29xxxxx"
    }
    
    ---------------------------delete_load_balancer---------------------------
    {
      "RequestId": "1A8CB48F-8242-49A9-9958-E762B1E9BA4D"
    }
    ```


