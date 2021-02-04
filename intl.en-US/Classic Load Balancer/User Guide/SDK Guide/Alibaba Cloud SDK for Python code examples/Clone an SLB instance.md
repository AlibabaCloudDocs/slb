# Clone an SLB instance

This topic describes how to use SLB SDK for Python to clone a Server Load Balancer \(SLB\) instance.

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


In this topic, the following steps are performed to clone an SLB instance:

1.  Create an SLB instance in the China \(Zhangjiakou\) region. Set the name of the SLB instance to SLB1, set the primary zone to cn-zhangjiakou-a, and set the secondary zone to cn-zhangjiakou-b. Then, set the billing method of the SLB instance to pay-as-you-go and set the type of the SLB instance to slb.s1.small. For other parameters, use the default settings.
2.  Add the ECS instances that are created in the China \(Zhangjiakou\) region to the default server group. Network traffic is then forwarded by the SLB instance to the ECS instances. Then, set the weights of both ECS instances to 100.
3.  Create a TCP listener. Set the frontend port that is used by the SLB instance to port 80 and set the backend port that receives requests to port 80. Then, set the health check protocol to TCP. The maximum bandwidth of the listener is not limited. For other parameters, use the default settings.
4.  Query information about SLB1. The information is passed to the request as parameters for cloning an SLB instance.
5.  Clone an SLB instance.
6.  Delete SLB1.
7.  Query information about the cloned SLB instance.
8.  Delete the cloned SLB instance.

1.  In the directory to which the SDK is downloaded, open the folder aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb.

2.  Open the configration\_clone.py file in the editor. Set the ACS\_CLIENT parameter to configure user identity verification and set other parameters based on your actual needs. Then, save the file and exit.

    **Note:** The SDK verifies the identity of every user. You can set the AcsClient parameter in a constants file and invoke the constants file when you need it.

    ```
    #encoding=utf-8
    
    import sys
    import json
    
    
    #Import AcsClient to verify the identity of the API caller.
    from aliyunsdkcore.client import AcsClient
    #Use the exception handling module of Alibaba Cloud SDK.
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    #Print logs at the command-line interface.
    from sdk_lib.common_util import CommonUtil
    #Handle exceptions.
    from sdk_lib.exception import ExceptionHandler
    #Import the API operation for creating an SLB instance.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerRequest
    #Import the API operation for creating a default server group.
    from aliyunsdkslb.request.v20140515 import AddBackendServersRequest
    #Import the API operation for creating a TCP listener.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerTCPListenerRequest
    #Import the API operation for querying information about an SLB instance.
    from aliyunsdkslb.request.v20140515 import DescribeLoadBalancerAttributeRequest
    #Import the API operation for cloning an SLB instance.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerRequest
    #Import the API operation for deleting an SLB instance.
    from aliyunsdkslb.request.v20140515 import DeleteLoadBalancerRequest
    
    #Set the parameters for user identity verification.
    ACS_CLIENT = AcsClient(
        'your-access-key-id',     #your-access-key-id
        'your-access-key-secret',   #your-access-key-secret
        'cn-zhangjiakou',     #your-region-id
    )
    #Set the number of retries after a failure.
    TRY_TIME = 3
    
    def create_load_balancer(params):
        '''
        create_load_balancer: creates an SLB instance.
    
        '''
        try:
            #Set the API request parameters for creating an SLB instance.
            request = CreateLoadBalancerRequest.CreateLoadBalancerRequest()
            request.set_MasterZoneId(params["master_zone_id"])
            request.set_SlaveZoneId(params["slave_zone_id"])
            request.set_LoadBalancerName(params["load_balancer_name"])
            request.set_PayType(params["pay_balancer_type"])
            request.set_LoadBalancerSpec(params["load_balancer_spec"])
            request.set_ClientToken(str(uuid.uuid1()))
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
                request.set_ClientToken(str(uuid.uuid1()))
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
            #The maximum bandwidth of the listener.
                request.set_Bandwidth(params["listener_bandwidth"])
                request.set_ClientToken(str(uuid.uuid1()))
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
    
    #Query information about an SLB instance.
    def describe_load_balancer_attribute(params):
        '''
        describe_load_balancer_attribute: queries detailed information about an SLB instance.
    
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = DescribeLoadBalancerAttributeRequest.DescribeLoadBalancerAttributeRequest()
                #Specify the ID of the SLB instance.
                request.set_LoadBalancerId(params["load_balancer_id"])
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
            finally:
                counter += 1
    
    #Clone an SLB instance.
    def create_load_balancer_clone(params):
        '''
        create_load_balancer: creates an SLB instance.
    
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = CreateLoadBalancerRequest.CreateLoadBalancerRequest()
                #The primary zone.
                request.set_MasterZoneId(params["master_zone_id"])
                #The secondary zone.
                request.set_SlaveZoneId(params["slave_zone_id"])
                #The billing method.
                request.set_PayType(params["pay_balancer_type"])
                #The ID of the resource group.
                request.set_ResourceGroupId(params["resource_group_id"])
                #The IP protocol of the SLB instance.
                request.set_AddressIPVersion(params["address_ip_version"])
                #The network type of the SLB instance.
                request.set_AddressType(params["address_type"])
                #The name of the SLB instance.
                request.set_LoadBalancerName(params["load_balancer_name"])
                request.set_ClientToken(str(uuid.uuid1()))
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
            finally:
                counter += 1
    def delete_load_balancer(load_balancer_id):
        '''
        delete_load_balancer: deletes an SLB instance.
    
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
        #Set the parameters for creating an SLB instance.
        #Set the primary zone of the new SLB instance to cn-zhangjiakou-a.
        params["master_zone_id"] = "cn-zhangjiakou-a"
        #Set the primary zone of the new SLB instance to cn-zhangjiakou-b.
        params["slave_zone_id"] = "cn-zhangjiakou-b"
        #Set the name of the new SLB instance to SLB1.
        params["load_balancer_name"] = "SLB1"
        #Set the billing method of the new SLB instance to pay-as-you-go.
        params["pay_balancer_type"] = "PayOnDemand"
        #Set the type of the new SLB instance to slb.s1.small.
        params["load_balancer_spec"] = "slb.s1.small"
    
        #Set the IDs and weights of the ECS instances to be added to the default server group.
        params["backend_servers"] = [{"ServerId":"i-8vxxxxx","Weight":"100"},{"ServerId":"i-8vbe8xxxxxxxv","Weight":"100"}]
    
        #Set parameters of the TCP listener.
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
        result_json = create_load_balancer(params)
        #Print the returned value of load_balancer_json. create_load_balancer is the name of the JSON string.
        CommonUtil.log("create_load_balancer", result_json)
    
        #Obtain the ID and name of the SLB instance.
        load_balancer_id = result_json["LoadBalancerId"]
        params["load_balancer_id"] = load_balancer_id
        params["LoadBalancerName"] = result_json["LoadBalancerName"]
    
        #Create a TCP listener.
        result_json = create_tcp_listener(params)
        CommonUtil.log("create_tcp_listener", result_json)
    
        #Query information about an SLB instance.
        result_json = describe_load_balancer_attribute(params)
        CommonUtil.log("describe_load_balancer_attribute", result_json)
        #The information about the created SLB instance.
        params["master_zone_id"] = result_json["MasterZoneId"]
        params["slave_zone_id"] = result_json["SlaveZoneId"]
        params["pay_balancer_type"] = result_json["PayType"]
        params["resource_group_id"] = result_json["ResourceGroupId"]
        params["address_ip_version"] = result_json["AddressIPVersion"]
        params["address_type"] = result_json["AddressType"]
        params["load_balancer_name"] = result_json["LoadBalancerName"]
    
        #Clone an SLB instance based on the configurations of SLB1.
        result_json = create_load_balancer_clone(params)
        CommonUtil.log("create_load_balancer_clone", result_json)
    
        #Obtain the ID of the cloned instance.
        clone_load_balancer_id = result_json["LoadBalancerId"]
    
        #Delete the first SLB instance.
        #Delete the SLB instance with the returned LoadBalancerId.
        result_json = delete_load_balancer(load_balancer_id)
        #Print the returned value of load_balancer_json.
        CommonUtil.log("delete_load_balancer", result_json)
    
        #Query details about the cloned SLB instance.
        params["load_balancer_id"] = clone_load_balancer_id
        result_json = describe_load_balancer_attribute(params)
        CommonUtil.log("describe_load_balancer_attribute", result_json)
    
    
        #Delete the cloned SLB instance.
        #Delete the SLB instance with the returned LoadBalancerId.
        result_json = delete_load_balancer(clone_load_balancer_id)
        #Print the returned value of load_balancer_json.
        CommonUtil.log("delete_load_balancer", result_json)
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

3.  Go to the directory where the configration\_clone.py file is stored and run the following command to clone an SLB instance:

    ```
    python configration_clone.py
    ```

    The following output is returned:

    ```
    ---------------------------create_load_balancer---------------------------
    {
      "VpcId": "",
      "AddressIPVersion": "ipv4",
      "LoadBalancerName": "SLB1",
      "ResourceGroupId": "rg-acfxxxxxxxxxxy",
      "VSwitchId": "",
      "RequestId": "544656CD-4DC9-47CB-B4DA-9371C0098F37",
      "Address": "39.xx.xx.xx",
      "NetworkType": "classic",
      "LoadBalancerId": "lb-8vbermxxxxxxxxx90l"
    }
    
    ---------------------------create_tcp_listener---------------------------
    {
      "RequestId": "4FCAFA1B-A6A8-4AA7-AB26-788C4F1506DA"
    }
    
    ---------------------------describe_load_balancer_attribute---------------------
    ------
    {
      "LoadBalancerStatus": "inactive",
      "HasReservedInfo": "false",
      "InternetChargeType": "paybytraffic",
      "EndTime": "2999-09-08T16:00:00Z",
      "VpcId": "",
      "RegionIdAlias": "cn-zhangjiakou",
      "RegionId": "cn-zhangjiakou",
      "ListenerPortsAndProtocal": {
        "ListenerPortAndProtocal": [
          {
            "ListenerPort": 80,
            "ListenerProtocal": "tcp"
          }
        ]
      },
      "ResourceGroupId": "rg-acfxxxxxxxaiy",
      "CreateTimeStamp": 1551254179000,
      "VSwitchId": "",
      "Address": "39.98.97.43",
      "AddressIPVersion": "ipv4",
      "LoadBalancerSpec": "slb.s1.small",
      "EndTimeStamp": 32493801600000,
      "ListenerPortsAndProtocol": {
        "ListenerPortAndProtocol": [
          {
            "ListenerProtocol": "tcp",
            "ListenerPort": 80
          }
        ]
      },
      "LoadBalancerId": "lb-8vxxxxxxxxxx90l",
      "AddressType": "internet",
      "RequestId": "9D696BEF-18C2-4EFD-92F4-434580964A51",
      "BackendServers": {
        "BackendServer": []
      },
      "MasterZoneId": "cn-zhangjiakou-a",
      "PayType": "PayOnDemand",
      "SlaveZoneId": "cn-zhangjiakou-b",
      "Bandwidth": 5120,
      "LoadBalancerName": "SLB1",
      "NetworkType": "classic",
      "CreateTime": "2019-02-27T07:56:19Z",
      "ListenerPorts": {
        "ListenerPort": [
          80
        ]
      }
    }
    
    ---------------------------create_load_balancer_clone---------------------------
    
    {
      "VpcId": "",
      "AddressIPVersion": "ipv4",
      "LoadBalancerName": "SLB1",
      "ResourceGroupId": "rg-acxxxxxxxxxxiy",
      "VSwitchId": "",
      "RequestId": "0E051B90-1C32-4270-A653-F7FBB03E3E5C",
      "Address": "xx.xx.xx.xx",
      "NetworkType": "classic",
      "LoadBalancerId": "lb-8xxxxxxxxxxxxxx"
    }
    
    ---------------------------delete_load_balancer---------------------------
    {
      "RequestId": "14703145-BC19-4032-A5F5-6DD49AED6885"
    }
    
    ---------------------------describe_load_balancer_attribute---------------------
    ------
    {
      "LoadBalancerStatus": "active",
      "HasReservedInfo": "false",
      "InternetChargeType": "paybytraffic",
      "EndTime": "2999-09-08T16:00:00Z",
      "VpcId": "",
      "RegionIdAlias": "cn-zhangjiakou",
      "RegionId": "cn-zhangjiakou",
      "ListenerPortsAndProtocal": {
        "ListenerPortAndProtocal": []
      },
      "ResourceGroupId": "rg-acfxxxxxxxxxiy",
      "CreateTimeStamp": 1551254182000,
      "VSwitchId": "",
      "Address": "39.98.97.36",
      "AddressIPVersion": "ipv4",
      "MasterZoneId": "cn-zhangjiakou-a",
      "EndTimeStamp": 32493801600000,
      "ListenerPortsAndProtocol": {
        "ListenerPortAndProtocol": []
      },
      "LoadBalancerId": "lb-8vxxxxxxxxxxx",
      "AddressType": "internet",
      "RequestId": "6345BAD4-B7EB-4280-9C7B-BB1324A77E32",
      "BackendServers": {
        "BackendServer": []
      },
      "PayType": "PayOnDemand",
      "SlaveZoneId": "cn-zhangjiakou-b",
      "Bandwidth": 5120,
      "LoadBalancerName": "SLB1",
      "NetworkType": "classic",
      "CreateTime": "2019-02-27T07:56:22Z",
      "ListenerPorts": {
        "ListenerPort": []
      }
    }
    
    ---------------------------delete_load_balancer---------------------------
    {
      "RequestId": "DC7C11D0-E21E-49AE-9695-F0171960D0F1"
    }
    ```


