# Update SSL certificates

This topic describes how to use SLB SDK for Python to create an HTTPS listener for a Server Load Balancer \(SLB\) instance and update the server certificate of the HTTPS listener.

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


In this topic, the following steps are performed to create an HTTPS listener and update the server certificate of the HTTPS listener:

1.  Create an SLB instance in the China \(Zhangjiakou\) region. Set the name of the SLB instance to SLB1, set the primary zone to cn-zhangjiakou-a, and set the secondary zone to cn-zhangjiakou-b. Then, set the billing method of the SLB instance to pay-as-you-go and set the type of the SLB instance to slb.s1.small. For other parameters, use the default settings.
2.  Add the ECS instances that are created in the China \(Zhangjiakou\) region to the default server group. Network traffic is then forwarded by the SLB instance to the ECS instances. Then, set the weights of both ECS instances to 100.
3.  Upload a server certificate.
4.  Create an HTTPS listener. Set the frontend port that the SLB instance uses to port 80 and set the backend server that receives requests to port 443. Then, disable health checks and session persistence, and set the maximum bandwidth of the listener to 6 Mbit /s. For other parameters, use the default settings.
5.  Upload a new server certificate.
6.  Update the server certificate of the newly created HTTPS listener.
7.  Delete the SLB instance.

1.  In the directory to which the SDK is downloaded, open the folder aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb.

2.  Open upload\_server\_certificate.py in the editor. Set the ACS\_CLIENT parameter to configure user identity verification and set other parameters based on your actual needs. Then, save the file and exit.

    **Note:** The SDK authenticates the identity of every user. You can set the AcsClient parameter in a constants file and invoke the constants file when you need it.

    ```
    #encoding=utf-8
    
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
    #Import the API operation for creating a default server group.
    from aliyunsdkslb.request.v20140515 import AddBackendServersRequest
    #Import the API operation for creating an HTTPS listener.
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerHTTPSListenerRequest
    #Import the API operation for modifying an HTTPS listener.
    from aliyunsdkslb.request.v20140515 import SetLoadBalancerHTTPSListenerAttributeRequest
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
    
    def log(action, response_json):
        print("---------------------------"+action+"---------------------------")
        print(json.dumps(response_json, indent=2)+'\n')
    
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
            request.set_ClientToken(str(uuid.uuid1()))
            #Make an API request and receives a response.
            response = ACS_CLIENT.do_action_with_exception(request)
            response_json = json.loads(response)
            #API response.
            return response_json
        except ServerException as e:
            return e
        except ClientException as e:
            print(e)
    
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
                return e
            except ClientException as e:
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
                return e
            except ClientException as e:
                return e
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
                return e
            except ClientException as e:
                return e
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
                return e
            except ClientException as e:
                return e
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
            return e
        except ClientException as e:
            return e
    
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
        params["backend_servers"] = [{"ServerId":"i-8vbe8yixxxxxxxxxxxxxw","Weight":"100"},{"ServerId":"i-8vbe8yxxxxxxxxxxxxxj9v","Weight":"100"}]
    
        #Set the parameters of the server certificate to be uploaded.
    
        #Set the parameters of the HTTPS listener to be created.
        #Disable health checks.
        params["health_check"] = "off"
        #Set the maximum bandwidth of the listener.
        params["bandwidth"] = 6
        #Set the frontend port that is used by the SLB instance.
        params["listener_port"] = 80
        #Set the backend port that is used by the SLB instance.
        params["backend_server_port"] = 443
        #Disable session persistence.
        params["sticky_session"] = "off"
    
        #Create an SLB instance.
        #Obtain the returned value of create_load_balancer. load_balancer_json is the returned value in a JSON string.
        load_balancer_json = create_load_balancer(params)
        #Print the returned value of load_balancer_json. create_load_balancer is the name of the JSON string.
        log("create_load_balancer", load_balancer_json)
    
        #Upload a server certificate.
        #The public key certificate to be uploaded.
        params["server_certificate"] = "-----BEGIN CERTIFICATE-----xxxxxxx-----END CERTIFICATE-----"
        params["private_key"] = "-----BEGIN RSA PRIVATE KEY-----xxxxxxxxxxx-----END RSA PRIVATE KEY----"
        result_json = upload_server_certificate(params)
        log("upload_server_certificate", result_json)
        params["server_certificate_id"] = result_json["ServerCertificateId"]
    
        #The ID of the SLB instance.
        params["load_balancer_id"] = load_balancer_json["LoadBalancerId"]
    
        #Create an HTTPS listener.
        result_json = create_https_listener(params)
        log("create_https_listener", result_json)
    
        #Upload a new server certificate.
        #The new public key certificate to be uploaded.
        params["server_certificate"] = "-----BEGIN CERTIFICATE-----xxxxxxx-----END CERTIFICATE-----"
        params["private_key"] = "-----BEGIN RSA PRIVATE KEY-----xxxxxxxxxxx-----END RSA PRIVATE KEY-----"
        result_json = upload_server_certificate(params)
        log("upload_server_certificate", result_json)
        #
        params["server_certificate_id"] = result_json["ServerCertificateId"]
    
        #Modify the configurations of an HTTPS listener.
        result_json = set_https_listener_attribute(params)
        log("set_https_listener_attribute", result_json)
    
        #Delete an SLB instance.
        #Delete the SLB instance with the returned LoadBalancerId.
        load_balancer_json = delete_load_balancer(load_balancer_json["LoadBalancerId"])
        #Print the returned value of load_balancer_json.
        log("delete_load_balancer", load_balancer_json)
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

3.  Go to the directory where the upload\_server\_certificate.py file is stored and run following command to update the HTTPS certificate:

    ```
    python upload_server_certificate.py
    ```

    The following output is returned:

    ```
    ---------------------------create_load_balancer---------------------------
    {
      "VpcId": "",
      "AddressIPVersion": "ipv4",
      "LoadBalancerName": "SLB1",
      "ResourceGroupId": "rg-axxxxxxxxxxxy",
      "VSwitchId": "",
      "RequestId": "1DEF72EE-CA5C-449D-9E97-2CE460DE7F7A",
      "Address": "39.XX.XX.8",
      "NetworkType": "classic",
      "LoadBalancerId": "lb-8vxxxxxxxxxxxf"
    }
    
    ---------------------------upload_server_certificate---------------------------
    {
      "ExpireTimeStamp": 1732169065000,
      "RegionIdAlias": "cn-zhangjiakou",
      "AliCloudCertificateName": "",
      "RegionId": "cn-zhangjiakou",
      "CommonName": "test",
      "ServerCertificateName": "test",
      "ExpireTime": "2024-11-21T06:04:25Z",
      "ResourceGroupId": "rg-axxxxxxxxxxxyy",
      "RequestId": "D6FB8B7C-B0EA-43E7-AD8F-E0201A9E1A13",
      "Fingerprint": "cd:90:1b:7b:49:4d:1d:90:f6:01:de:9a:81:7d:31:a7:38:1d:84:8d",
    
      "AliCloudCertificateId": "",
      "IsAliCloudCertificate": 0,
      "ServerCertificateId": "12xxxxxxxxxxxx3_16xxxxxxxxxx6_-1xxxxxxxx13_-1xxxxxx72"
    }
    
    ---------------------------create_https_listener---------------------------
    {
      "RequestId": "FC70EDC8-06EC-4E1C-97BE-D81571DA23B4"
    }
    
    ---------------------------upload_server_certificate---------------------------
    {
      "ExpireTimeStamp": 1567857600000,
      "RegionIdAlias": "cn-zhangjiakou",
      "AliCloudCertificateName": "",
      "RegionId": "cn-zhangjiakou",
      "CommonName": "doc.aliyun-slb.top",
      "ServerCertificateName": "doc.aliyun-slb.top",
      "ExpireTime": "2019-09-07T12:00:00Z",
      "ResourceGroupId": "rg-acxxxxxxxxxxxxy",
      "RequestId": "913E991F-BCC9-4A3D-9802-19084E2CE271",
      "Fingerprint": "8c:47:1b:a7:8f:02:27:3a:35:7c:e3:47:4a:5f:55:02:ed:e3:57:1e",
    
      "SubjectAlternativeNames": {
        "SubjectAlternativeName": [
          "doc.aliyun-slb.top"
        ]
      },
      "AliCloudCertificateId": "",
      "IsAliCloudCertificate": 0,
      "ServerCertificateId": "12xxxxxxxxxxxx3_16xxxxxxx716_4xxxxxxx4_-14xxxxxxxxxx9"
    }
    
    ---------------------------set_https_listener_attribute-------------------------
    --
    {
      "RequestId": "14275D2B-20F2-4D96-9FC8-7BB2B110155C"
    }
    
    ---------------------------delete_load_balancer---------------------------
    {
      "RequestId": "2A1DF87C-842A-4C1E-AA61-23EB365EB86F"
    }
    ```


