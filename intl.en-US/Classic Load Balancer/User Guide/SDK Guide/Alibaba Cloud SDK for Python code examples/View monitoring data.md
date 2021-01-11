# View monitoring data

This topic describes how to use SLB SDK for Python to collect monitoring metrics of a Server Load Balancer \(SLB\) instance and set alert rules.

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


In this topic, the following steps are performed:

-   Create an SLB instance in the China \(Zhangjiakou\) region. Set the name of the SLB instance to SLB1, set the primary zone to cn-zhangjiakou-a, and set the secondary zone to cn-zhangjiakou-b.
-   Create a TCP listener for the SLB instance. Set the frontend port that the SLB instance uses to port 80 and set the backend port that receives requests to port 80. Then, set the health check protocol to TCP and add the ECS instances that are deployed in the China \(Zhangjiakou\) region to the default server group. Set the weights of both ECS instances to 100. Network traffic is then forwarded by the SLB instance to the ECS instances.
-   Query the QPS usage of the created SLB instance.
-   Create an alert rule. When the average QPS usage of the created SLB instance is greater than or equal to 35, an alert is triggered.
-   Delete the SLB instance.

1.  In the directory to which the SDK is downloaded, open the folder $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb.

2.  Open slb\_monitor.py in the editor. Set the ACS\_CLIENT parameter to configure user identity verification and set other parameters based on your actual needs. Then, save the file and exit.

    **Note:** The SDK verifies the identity of every user. You can set the AcsClient parameter in a constants file and invoke the constants file when you need it.

    ```
    # encoding=utf-8
    import sys
    import json
    import uuid
    
    #Import AcsClient to verify the identity of the API caller.
    from aliyunsdkcore.client import AcsClient
    #Use the exception handling module of Alibaba Cloud SDK.
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    #Handle exceptions.
    from sdk_lib.exception import ExceptionHandler
    #Import the API operation for creating an SLB instance.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerRequest
    #Import the API operation for adding a default server group.
    from aliyunsdkslb.request.v20140515 import AddBackendServersRequest
    #Import the API operation for creating a TCP listener.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerTCPListenerRequest
    #Import the Cloud Monitor API operation for querying the latest monitoring data of an SLB instance.
    from aliyunsdkcms.request.v20190101 import DescribeMetricLastRequest
    #Import the Cloud Monitor API operation for creating an alert rule for an SLB instance.
    from aliyunsdkcms.request.v20190101 import PutResourceMetricRuleRequest
    #Import the API operation for deleting an SLB instance.
    from aliyunsdkslb.request.v20140515 import DeleteLoadBalancerRequest
    #Import logs at the command-line interface.
    from sdk_lib.common_util import CommonUtil
    
    #Set the parameters for user identity verification.
    ACS_CLIENT = AcsClient(
        'your-access-key-id',  # your-access-key-id
        'your-access-key-secret',  # your-access-key-secret
        'cn-zhangjiakou',  # your-region-id
    )
    #Set the number of retries after a failure.
    TRY_TIME = 3
    
    '''
    Create an SLB instance -> Create a TCP listener -> Add backend servers ->
    Query the number of concurrent connections on the port of the SLB instance -> Create an alert rule
    '''
    
    
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
    
    
    def describe_metric_last(params):
        '''
        describe_metric_last: queries the latest monitoring data of an SLB instance.
        For more information about the API operation, visit https://help.aliyun.com/document_detail/51939.html.
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = DescribeMetricLastRequest.DescribeMetricLastRequest()
                #The namespace of the service. This indicates the service to which the monitoring data belongs.
                request.set_Namespace(params["project"])
                #The name of the metric.
                request.set_MetricName(params["metric_name"])
                #Filtering items.
                request.set_Dimensions(params['dimensions'])
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
            finally:
                counter += 1
    
    
    def put_resource_metric_rule(params):
        '''
        put_resource_metric_rule: creates an alert rule for one or more instances at a time.
        For more information about the API operation, visit https://help.aliyun.com/document_detail/114934.html.
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = PutResourceMetricRuleRequest.PutResourceMetricRuleRequest()
                #The ID of the alert rule. The IDs of alert rules are generated by callers to ensure uniqueness. You can specify an existing ID to modify the corresponding alert rule or specify a new ID to create an alert rule.
                request.set_RuleId(uuid.UUID)
                #The namespace of the service. For more information, refer to the projects of different services.
                request.set_Namespace(params["name_space"])
                #The contact group. Multiple contact groups must be separated with commas (,).
                request.set_ContactGroups(params["ContactGroups"])
                #The name of the alert rule.
                request.set_RuleName(params["name"])
                #The name of the metric corresponds to the service. For more information, see the metrics defined for each service.
                request.set_MetricName(params["metric_name"])
                #The list of instances that are associated with the alert rule.
                request.set_Resources(params["dimensions"])
                #The method for aggregating critical-level alerts.
                request.set_EscalationsCriticalStatistics(params["statistics"])
                #The comparison operator of the threshold for critical-level alerts.
                request.set_EscalationsCriticalComparisonOperator(params["comparison_operator"])
                #The threshold for triggering critical alerts.
                request.set_EscalationsCriticalThreshold(params["threshold"])
                #The number of attempts for resending a critical-level alert.
                request.set_EscalationsCriticalTimes(3)
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
        #Set the primary zone of the new SLB instance to cn-zhangjiakou-b.
        params["slave_zone_id"] = "cn-zhangjiakou-b"
        #Set the name of the new SLB instance to SLB1.
        params["load_balancer_name"] = "SLB1"
        #Set the billing method of the new SLB instance to pay-as-you-go.
        params["pay_balancer_type"] = "PayOnDemand"
    
        #Set the IDs and weights of the ECS instances to be added to the default server group.
        params["backend_servers"] = [{"ServerId": "i-8vbfus6jnwjp1c2*****", "Weight": "100"},
                                     {"ServerId": "i-8vbfus6jnwjp1c2*****", "Weight": "100"}]
    
        #Set parameters of the TCP listener.
        #Set the frontend port to port 80.
        params["listener_port"] = 80
        #Set the backend port that receives requests to port 80.
        params["backend_server_port"] = 80
        #Set the health check protocol to TCP.
        params["listener_health_check"] = "tcp"
        #Set the maximum bandwidth of the TCP listener to -1. This indicates that the maximum bandwidth is not limited.
        params["listener_bandwidth"] = -1
    
        #Set parameters of the collected metric.
        #Set the service to which the monitoring data belongs.
        params["project"] = "acs_slb_dashboard"
        #Set the name of the metric.
        params["traffic_tx_new"] = "InstanceQpsUtilization"
    
        #Set parameters of the alert rule to be created.
        #Set the service to which the alert rule belongs.
        params["name_space"] = "acs_slb_dashboard"
        #Set the name of the alert rule.
        params["name"] = "slb_alarm"
        #Set the name of the metric for the SLB instance in the alert rule.
        params["metric_name"] = "InstanceQpsUtilization"
        #Set the aggregation method.
        params["statistics"] = "Average"
        #Set the comparison operator of the alert rule to greater than or equal to (≥).
        params["comparison_operator"] = "GreaterThanOrEqualToThreshold"
        #Set the alert threshold.
        params["threshold"] = 35
    
        #Create an SLB instance.
        #Obtain the returned value of create_load_balancer. load_balancer_json is the returned value in a JSON string.
        load_balancer_json = create_load_balancer(params)
        #Print the returned value of load_balancer_json. create_load_balancer is the name of the JSON string.
        CommonUtil.log("create_load_balancer", load_balancer_json)
    
        #The ID of the SLB instance.
        params["load_balancer_id"] = load_balancer_json["LoadBalancerId"]
    
        #Create a TCP listener.
        result_json = create_tcp_listener(params)
        CommonUtil.log("create_tcp_listener", result_json)
    
        #Add backend servers.
        result_json = add_backend_servers(params)
        CommonUtil.log("add_backend_servers", result_json)
    
        #Query the queries per second (QPS) usage of an SLB instance.
        params["dimensions"] = '[{"instanceId":"' + load_balancer_json["LoadBalancerId"] + '"}]'
        result_json = describe_metric_last(params)
        CommonUtil.log("describe_metric_last", result_json)
    
        #Create an alert rule.
        params["metric_name"] = "InstanceQpsUtilization"
        #The name of the contact group.
        params["ContactGroups"] = "test_contact_groups"
        result_json = put_resource_metric_rule(params)
        CommonUtil.log("put_resource_metric_rule", result_json)
    
        #Delete an SLB instance.
        #Delete the SLB instance with the returned LoadBalancerId.
        load_balancer_json = delete_load_balancer(load_balancer_json["LoadBalancerId"])
        #Print the returned value of load_balancer_json.
        CommonUtil.log("delete_load_balancer", load_balancer_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

3.  Switch to the directory where the slb\_monitor.py file is stored and run the following command to view the monitoring data:

    ```
    python slb_monitor.py
    ```

    The following output is returned:

    ```
    ---------------------------create_load_balancer---------------------------
    {
      "VpcId": "",
      "AddressIPVersion": "ipv4",
      "LoadBalancerName": "SLB1",
      "ResourceGroupId": "rg-axxxxxxxxxx",
      "VSwitchId": "",
      "RequestId": "661DDF49-FD2B-46C1-8E38-FDE5E62C8448",
      "Address": "39.xx.xx.xx4",
      "NetworkType": "classic",
      "LoadBalancerId": "lb-8vbtxxxxxxxxxxx1hn"
    }
    
    ---------------------------create_tcp_listener---------------------------
    {
      "RequestId": "7ED453FF-7DF6-4F4F-81A0-670EED9EB997"
    }
    
    ---------------------------add_backend_servers---------------------------
    {
      "RequestId": "4B730606-BD44-4A6B-BE9E-118E9606B064",
      "BackendServers": {
        "BackendServer": [
          {
            "ServerId": "i-8xxxxxxxxxxf4z",
            "Type": "ecs",
            "Weight": 100
          },
          {
            "ServerId": "i-8xxxxxxxxxxxxx",
            "Type": "ecs",
            "Weight": 100
          }
        ]
      },
      "LoadBalancerId": "lb-8xxxxxxxxxxxxxx"
    }
    
    ---------------------------describe_metric_last---------------------------
    {
      "Code": "200",
      "Period": "60",
      "RequestId": "15FD2461-FD94-451F-ABE3-D281DB453161",
      "Datapoints": "[]"
    }
    
    ---------------------------put_resource_metric_rule---------------------------
    {
      "Code": "200",
      "Data": "53547DF14168E368073BE8E34E1522DE25854224",
      "RequestId": "8652E53F-74AD-413B-B2D9-103BFE557FAC",
      "Success": true
    }
    
    ---------------------------delete_load_balancer---------------------------
    {
      "RequestId": "D6CCD259-41C2-4D5C-A644-19A0E96F1D4C"
    }
    ```


