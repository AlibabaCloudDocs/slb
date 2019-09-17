# 更新HTTPS证书 {#task_spl_rnn_vgb .task}

介绍如何使用Python SDK给一个SLB实例创建一个HTTPS监听，并更新该实例下HTTPS监听使用的服务器证书。

在华北3张家口地域已经有两台状态为**运行中**的ECS实例。

本次示例分为以下几步，为SLB实例添加HTTPS监听，更新HTTPS监听的证书。

1.  在华北3张家口地域创建一个名为SLB1的SLB实例，主可用区为cn-zhangjiakou-a，备可用区为cn-zhangjiakou-b，实例计费类型为按量计费，规格为slb.s1.small，其他配置使用系统默认值。
2.  将张家口地域的两台ECS实例添加到默认服务器组，用来分发流量，ECS实例的后端服务权重都为100。
3.  上传服务器证书。
4.  创建HTTPS监听，SLB实例前端使用的端口为80，后端服务器开放用来接收请求的端口为443，关闭健康检查和会话保持，监听带宽峰值为6Mbps，其他使用默认值。
5.  上传新的服务器证书。
6.  更新新建HTTPS监听的服务器证书。
7.  删除新建的SLB实例。

1.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb文件夹。
2.  使用编辑器打开upload\_server\_certificate.py文件，您需要配置用户鉴权参数ACS\_CLIENT，其他参数根据实际情况配置后，保存退出。 

    **说明：** 因为用户鉴权是每个SDK必须执行的操作，所以可以在常量文件中配置AcsClient参数的值，在场景代码中调用常量文件。

    ``` {#codeblock_9tm_tz3_4l3}
    
    
    #encoding=utf-8
    """
    创建slb实例->上传服务器证书->创建https监听->上传新的服务器证书
    ->循环修改https监听配置
    """
    import sys
    import json
    import uuid
    
    #调用AcsClient参数进行身份验证
    from aliyunsdkcore.client import AcsClient
    #使用阿里云官方sdk的异常处理模块
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    #调用上传证书的API
    from aliyunsdkslb.request.v20140515 import UploadServerCertificateRequest
    #调用创建SLB实例API   
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerRequest
    #调用添加默认服务器组API
    from aliyunsdkslb.request.v20140515 import AddBackendServersRequest
    #调用创建HTTPS监听的API
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerHTTPSListenerRequest
    #调用修改HTTPS监听的API
    from aliyunsdkslb.request.v20140515 import SetLoadBalancerHTTPSListenerAttributeRequest
    #调用删除SLB实例API  
    from aliyunsdkslb.request.v20140515 import DeleteLoadBalancerRequest
    ##异常处理逻辑
    from sdk_lib.exception import ExceptionHandler
    #命令行导入日志
    from sdk_lib.common_util import CommonUtil
    
    #用户身份鉴权参数配置
    ACS_CLIENT = AcsClient(
        'your-access-key-id',     #your-access-key-id
        'your-access-key-secret',   #your-access-key-secret
        'cn-zhangjiakou',     #your-region-id
    )
    #失败重试次数
    TRY_TIME = 3
    
    def create_load_balancer(params):
        '''
        create_load_balancer：创建slb实例
    
        '''
        try:
            #设置创建SLB实例的调用参数
            request = CreateLoadBalancerRequest.CreateLoadBalancerRequest() 
            request.set_MasterZoneId(params["master_zone_id"]) 
            request.set_SlaveZoneId(params["slave_zone_id"]) 
            request.set_LoadBalancerName(params["load_balancer_name"]) 
            request.set_PayType(params["pay_balancer_type"])
            request.set_ClientToken(str(uuid.uuid1()))
            #发送调用请求并接收返回数据
            response = ACS_CLIENT.do_action_with_exception(request)
            response_json = json.loads(response)
            #返回结果    
            return response_json
        except ServerException as e:
            ExceptionHandler.server_exception(e)
        except ClientException as e:
            ExceptionHandler.client_exception(e)
    
    def add_backend_servers(params):
        '''
        add_backend_servers：添加后端服务器
    
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                #设置添加默认服务器组的调用参数
                request = AddBackendServersRequest.AddBackendServersRequest()
                #负载均衡实例的ID
                request.set_LoadBalancerId(params["load_balancer_id"])
                #要添加的后端服务器列表
                request.set_BackendServers(params["backend_servers"])
                request.set_ClientToken(str(uuid.uuid1()))
                #发送调用请求并接收返回数据
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #返回结果
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
        upload_server_certificate：上传服务器证书
    
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = UploadServerCertificateRequest.UploadServerCertificateRequest()
                #要上传的公钥证书
                request.set_ServerCertificate(params["server_certificate"])
                #需要上传的私钥
                request.set_PrivateKey(params["private_key"])
                #发送调用请求并接收返回数据
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #返回结果
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
            finally:
                counter += 1
    
    def create_https_listener(params):
        '''
        create_https_listener：创建HTTPS监听
    
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = CreateLoadBalancerHTTPSListenerRequest.CreateLoadBalancerHTTPSListenerRequest()
                #负载均衡实例的ID
                request.set_LoadBalancerId(params["load_balancer_id"])
                #监听的带宽峰值
                request.set_Bandwidth(params["bandwidth"])
                #负载均衡实例前端使用的端口
                request.set_ListenerPort(params["listener_port"])
                #是否开启健康检查
                request.set_HealthCheck(params["health_check"])
                #是否开启会话保持
                request.set_StickySession(params["sticky_session"])
                #负载均衡实例后端使用的端口
                request.set_BackendServerPort(params["backend_server_port"])
                #服务器证书的ID
                request.set_ServerCertificateId(params["server_certificate_id"])
                #发送调用请求并接收返回数据
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #返回结果
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
            finally:
                counter += 1
    
    def set_https_listener_attribute(params):
        '''
        set_https_listener_attribute：修改HTTPS监听的配置
    
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = SetLoadBalancerHTTPSListenerAttributeRequest.SetLoadBalancerHTTPSListenerAttributeRequest()
                #负载均衡实例的ID
                request.set_LoadBalancerId(params["load_balancer_id"])
                #监听的带宽峰值
                request.set_Bandwidth(params["bandwidth"])
                #负载均衡实例前端使用的端口
                request.set_ListenerPort(params["listener_port"])
                #是否开启健康检查
                request.set_HealthCheck(params["health_check"])
                #是否开启会话保持
                request.set_StickySession(params["sticky_session"])
                #服务器证书的ID
                request.set_ServerCertificateId(params["server_certificate_id"])
                #发送调用请求并接收返回数据
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                #返回结果
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
            finally:
                counter += 1
    
    def delete_load_balancer(load_balancer_id):
        '''
        delete_load_balancer：删除slb实例
    
        '''
        try:
            #设置删除SLB实例的调用参数
            request = DeleteLoadBalancerRequest.DeleteLoadBalancerRequest()
            #负载均衡实例的ID
            request.set_LoadBalancerId(load_balancer_id)
            #发送调用请求并接收返回数据
            response = ACS_CLIENT.do_action_with_exception(request)
            response_json = json.loads(response)
            #返回结果
            return response_json
        except ServerException as e:
            ExceptionHandler.server_exception(e)
        except ClientException as e:
            ExceptionHandler.client_exception(e)
    
    def main():
        params = {}
        #设置创建SLB实例的参数
        #设置新建SLB实例的主可用区为cn-zhangjiakou-a 
        params["master_zone_id"] = "cn-zhangjiakou-a" 
        #设置新建SLB实例的主可用区为cn-zhangjiakou-b 
        params["slave_zone_id"] = "cn-zhangjiakou-b" 
        #设置新建SLB实例的名称为SLB1 
        params["load_balancer_name"] = "SLB1"
        #设置新建SLB实例的计费类型为按量计费
        params["pay_balancer_type"] = "PayOnDemand"
    
        #设置添加到默认服务器组的ECS的实例ID和权重
        params["backend_servers"] = [{"ServerId":"i-8vbe8yixxxxxxxxxxxxxw","Weight":"100"},{"ServerId":"i-8vbe8yxxxxxxxxxxxxxj9v","Weight":"100"}]
    
        #设置上传服务器证书的参数
    
        #设置创建HTTPS监听的参数
        #关闭健康检查
        params["health_check"] = "off"
        #设置监听的带宽峰值
        params["bandwidth"] = 6
        #负载均衡实例前端使用的端口
        params["listener_port"] = 80
        #设置负载均衡实例后端使用的端口
        params["backend_server_port"] = 443
        #关闭会话保持
        params["sticky_session"] = "off"
    
        #创建slb实例
        #获取create_load_balancer函数返回值，load_balancer_json为结果的json串
        load_balancer_json = create_load_balancer(params)
        #打印 load_balancer_json结果，其中"create_load_balancer"是对json串起的名字
        CommonUtil.log("create_load_balancer", load_balancer_json)
    
        #上传服务器证书
        #要上传的公钥证书
        params["server_certificate"] = "-----BEGIN CERTIFICATE-----xxxxxxx-----END CERTIFICATE-----"
        params["private_key"] = "-----BEGIN RSA PRIVATE KEY-----xxxxxxxxxxx-----END RSA PRIVATE KEY----"
        result_json = upload_server_certificate(params)
        CommonUtil.log("upload_server_certificate", result_json)
        params["server_certificate_id"] = result_json["ServerCertificateId"]
    
        #slb实例id
        params["load_balancer_id"] = load_balancer_json["LoadBalancerId"]
    
        #创建https监听
        result_json = create_https_listener(params)
        CommonUtil.log("create_https_listener", result_json)
    
        #上传新的服务器证书
        #要上传的新公钥证书
        params["server_certificate"] = "-----BEGIN CERTIFICATE-----xxxxxxx-----END CERTIFICATE-----"
        params["private_key"] = "-----BEGIN RSA PRIVATE KEY-----xxxxxxxxxxx-----END RSA PRIVATE KEY-----"
        result_json = upload_server_certificate(params)
        CommonUtil.log("upload_server_certificate", result_json)
        #
        params["server_certificate_id"] = result_json["ServerCertificateId"]
    
        #修改https监听配置
        result_json = set_https_listener_attribute(params)
        CommonUtil.log("set_https_listener_attribute", result_json)
    
        #删除slb实例
        #删除返回的LoadBalancerId对应的SLB实例
        load_balancer_json = delete_load_balancer(load_balancer_json["LoadBalancerId"])
        #打印 load_balancer_json结果
        CommonUtil.log("delete_load_balancer", load_balancer_json)
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

3.  进入upload\_server\_certificate.py所在的目录，执行如下命令，运行更新HTTPS证书示例。 

    ``` {#codeblock_vss_x9a_e41}
    python upload_server_certificate.py
    ```

    系统显示类似如下：

    ``` {#codeblock_bix_a1t_ptg}
    ---------------------------create_load_balancer---------------------------
    {
      "VpcId": "",
      "AddressIPVersion": "ipv4",
      "LoadBalancerName": "SLB1",
      "ResourceGroupId": "rg-axxxxxxxxxxxy",
      "VSwitchId": "",
      "RequestId": "1DEF72EE-CA5C-449D-9E97-2CE460DE7F7A",
      "Address": "39.98.97.8",
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


