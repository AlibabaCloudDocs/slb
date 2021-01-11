# Create an SLB instance and then delete the SLB instance

This topic describes how to use SLB SDK for Python to create a Server Load Balancer \(SLB\) instance and then delete the SLB instance.

Before you run the following code in script mode, make sure that the following requirements are met:

1.  Your account has a balance of at least CNY 100 so that you can be charged the instance fee when you use SLB SDK for Python to create an SLB instance.
2.  An AccessKey pair is obtained.

    An AccessKey ID and an AccessKey secret that are used to verify your identity are obtained. For more information about how to obtain an AccessKey pair, see [Obtain an AccessKey pair](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Obtain an AccessKey pair.md).

3.  The [SLB Python example library](https://github.com/aliyun/aliyun-openapi-python-sdk-examples) for implementing SLB features with Alibaba Cloud SLB SDK for Python is downloaded.
4.  Go to the directory where setup.py is stored and run the following command to initialize the environment:

    ```
    python setup.py install
    ```


Create an SLB instance in the China \(Zhangjiakou\) region. Set the name of the SLB instance to SLB1, set the primary zone to cn-zhangjiakou-a, and set the secondary zone to cn-zhangjiakou-b. Then, set the billing method of the SLB instance to pay-as-you-go, set the type of the SLB instance to slb.s1.small, and set the maximum bandwidth of the listener to 1 Mbit/s. For other parameters, use the default settings. After the SLB instance is created, delete the SLB instance.

1.  In the directory to which the SDK is downloaded, open the folder $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb.

2.  Open slb\_quick\_start.py in the editor. Set the ACS\_CLIENT parameter to configure user identity verification and set other parameters based on your actual needs. Then, save the file and exit.

    **Note:** The SDK verifies the identity of every user. You can set the AcsClient parameter in a constants file and invoke the constants file when you need it.

    ```
    # encoding=utf-8
    import sys
    import json
    
    #Import AcsClient to verify the identity of the API caller.
    from aliyunsdkcore.client import AcsClient
    #Use the exception handling module of Alibaba Cloud SDK.
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    #Import the API operation for uploading a certificate.
    from aliyunsdkslb.request.v20140515 import UploadServerCertificateRequest
    #Import the API operation for creating an SLB instance.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerRequest
    #Import the API operation for adding a default server group.
    from aliyunsdkslb.request.v20140515 import AddBackendServersRequest
    #Import the API operation for creating an HTTPS listener.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerHTTPSListenerRequest
    #Import the API operation for modifying an HTTPS listener.
    from aliyunsdkslb.request.v20140515 import SetLoadBalancerHTTPSListenerAttributeRequest
    #Import the API operation for deleting an SLB instance.
    from aliyunsdkslb.request.v20140515 import DeleteLoadBalancerRequest
    ##Handle exceptions.
    from sdk_lib.exception import ExceptionHandler
    #Import logs from the command-line interface.
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
    Create an SLB instance -> Upload a server certificate -> Create an HTTPS listener -> Upload a new server certificate
    -> Modifies the configuration of the HTTPS listener in loops
    '''
    
    
    def create_load_balancer(params):
        '''
        create_load_balancer: creates an SLB instance.
        For more information about the API operation, visit https://www.alibabacloud.com/help.aliyun.com/document_detail/27577.html
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
    
    
    def upload_server_certificate(params):
        '''
        upload_server_certificate: uploads a server certificate.
    
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = UploadServerCertificateRequest.UploadServerCertificateRequest()
                #The public key certificate to be uploaded.
                request.set_ServerCertificate(params["server_certificate"])
                #The private key file to be uploaded.
                request.set_PrivateKey(params["private_key"])
                #Make an API request and receives a response.
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #API response.
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
            finally:
                counter += 1
    
    
    def create_https_listener(params):
        '''
        create_https_listener: creates an HTTPS listener.
    
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = CreateLoadBalancerHTTPSListenerRequest.CreateLoadBalancerHTTPSListenerRequest()
                #The ID of the SLB instance.
                request.set_LoadBalancerId(params["load_balancer_id"])
                #The maximum bandwidth of the listener.
                request.set_Bandwidth(params["bandwidth"])
                #The frontend port that is used by the SLB instance.
                request.set_ListenerPort(params["listener_port"])
                #Specify whether to enable health checks.
                request.set_HealthCheck(params["health_check"])
                #Specify whether to enable session persistence.
                request.set_StickySession(params["sticky_session"])
                #The backend port that is used by the SLB instance.
                request.set_BackendServerPort(params["backend_server_port"])
                #The ID of the server certificate.
                request.set_ServerCertificateId(params["server_certificate_id"])
                #Make an API request and receives a response.
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #API response.
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
            finally:
                counter += 1
    
    
    def set_https_listener_attribute(params):
        '''
        set_https_listener_attribute: modifies the configurations of an HTTPS listener.
    
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = SetLoadBalancerHTTPSListenerAttributeRequest.SetLoadBalancerHTTPSListenerAttributeRequest()
                #The ID of the SLB instance.
                request.set_LoadBalancerId(params["load_balancer_id"])
                #The maximum bandwidth of the listener.
                request.set_Bandwidth(params["bandwidth"])
                #The frontend port that is used by the SLB instance.
                request.set_ListenerPort(params["listener_port"])
                #Specify whether to enable health checks.
                request.set_HealthCheck(params["health_check"])
                #Specify whether to enable session persistence.
                request.set_StickySession(params["sticky_session"])
                #The ID of the server certificate.
                request.set_ServerCertificateId(params["server_certificate_id"])
                #Make an API request and receives a response.
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #API response.
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
        #Set the parameters of the SLB instance to be created.
        #Set the primary zone of the new SLB instance to cn-zhangjiakou-a.
        params["master_zone_id"] = "cn-zhangjiakou-a"
        #Set the secondary zone of the new SLB instance to cn-zhangjiakou-b.
        params["slave_zone_id"] = "cn-zhangjiakou-b"
        #Set the name of the new SLB instance to SLB1.
        params["load_balancer_name"] = "SLB1"
        #Set the billing method of the new SLB instance to pay-as-you-go.
        params["pay_balancer_type"] = "PayOnDemand"
    
        #Set the IDs and weights of the ECS instances to be added to the default server group.
        params["backend_servers"] = [{"ServerId": "i-8vbe8yixxxxxxxxxxxxxw", "Weight": "100"},
                                     {"ServerId": "i-8vbe8yxxxxxxxxxxxxxj9v", "Weight": "100"}]
    
        #Set the parameters of the server certificate to be uploaded.
    
        #Set the parameters of the HTTPS listener to be created.
        #Disable health checks.
        params["health_check"] = "off"
        #Set the maximum bandwidth of the listener.
        params["bandwidth"] = 6
        #The frontend port that is used by the SLB instance.
        params["listener_port"] = 80
        #Set the backend port that is used by the SLB instance.
        params["backend_server_port"] = 443
        #Disable session persistence.
        params["sticky_session"] = "off"
    
        #Create an SLB instance.
        #Obtain the returned value of create_load_balancer. load_balancer_json is the returned value in a JSON string.
        load_balancer_json = create_load_balancer(params)
        #Print the returned value of load_balancer_json. create_load_balancer is the name of the JSON string.
        CommonUtil.log("create_load_balancer", load_balancer_json)
    
        #Upload a server certificate.
        #The public key certificate to be uploaded.
        params["server_certificate"] = "-----BEGIN CERTIFICATE-----xxxxxxx-----END CERTIFICATE-----"
        params["private_key"] = "-----BEGIN RSA PRIVATE KEY-----xxxxxxxxxxx-----END RSA PRIVATE KEY-----"
        result_json = upload_server_certificate(params)
        CommonUtil.log("upload_server_certificate", result_json)
        params["server_certificate_id"] = result_json["ServerCertificateId"]
    
        #The ID of the SLB instance.
        params["load_balancer_id"] = load_balancer_json["LoadBalancerId"]
    
        #Create an HTTPS listener.
        result_json = create_https_listener(params)
        CommonUtil.log("create_https_listener", result_json)
    
        #Upload a new server certificate.
        #The new public key certificate to be uploaded.
        params["server_certificate"] = "-----BEGIN CERTIFICATE-----xxxxxxx-----END CERTIFICATE-----"
        params["private_key"] = "-----BEGIN RSA PRIVATE KEY-----xxxxxxxxxxx-----END RSA PRIVATE KEY-----"
        result_json = upload_server_certificate(params)
        CommonUtil.log("upload_server_certificate", result_json)
        params["server_certificate_id"] = result_json["ServerCertificateId"]
    
        #Modify the configurations of an HTTPS listener.
        result_json = set_https_listener_attribute(params)
        CommonUtil.log("set_https_listener_attribute", result_json)
    
        #Delete an SLB instance.
        #Delete the SLB instance with the returned LoadBalancerId.
        load_balancer_json = delete_load_balancer(load_balancer_json["LoadBalancerId"])
        #Print the returned value of load_balancer_json.
        CommonUtil.log("delete_load_balancer", load_balancer_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

3.  Go to the directory where the slb\_quick\_start.py file is stored and run the following command to create an SLB instance and then delete the SLB instance:

    ```
    python slb_quick_start.py
    ```

    The following output is returned:

    ```
    
    ---------------------------create_load_balancer---------------------------
    {
      "VpcId": "",
      "AddressIPVersion": "ipv4",
      "LoadBalancerName": "SLB1",
      "ResourceGroupId": "rg-acfmxxxxxxxxxy",
      "VSwitchId": "",
      "RequestId": "070A9361-EA2B-4A4E-91E8-F70C1E47866A",
      "Address": "172.16.XX.XX",
      "NetworkType": "classic",
      "LoadBalancerId": "lb-8vbninnfxxxxxxxxxxxxx"
    }
    
    ---------------------------delete_load_balancer---------------------------
    {
      "RequestId": "4825E5BB-5131-4A1E-AF67-0EF3E8E5B323"
    }
    ```


