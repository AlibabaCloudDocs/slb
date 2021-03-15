# 创建和删除SLB实例

本文介绍如何使用Python SDK创建一个SLB实例，创建成功后删除该实例。

在开始运行示例脚本前，您需要确保已完成以下准备工作：

1.  因为使用Python SDK创建SLB实例会产生实例费，所以确保您的阿里云账户金额不少于100元。
2.  获取AccessKey。

    确保您已经有了用于身份验证的AccessKey ID和AccessKey Secret。如果尚未获取AK，参考查询获取[获取AccessKey](/intl.zh-CN/传统型负载均衡CLB/CLB开发指南/API参考/获取AccessKey.md)。

3.  下载阿里云负载均衡python SDK场景示例的[SLB Python Example库](https://github.com/aliyun/aliyun-openapi-python-sdk-examples)。
4.  进入setup.py所在的目录，执行如下命令，完成环境初始化配置。

    ```
    python setup.py install
    ```


在华北3（张家口）地域创建一个名为SLB1的SLB实例，主可用区为cn-zhangjiakou-a，备可用区为cn-zhangjiakou-b，实例计费类型为按量计费，规格为slb.s1.small，监听的带宽峰值为1Mbps，其他参数使用默认值。实例创建成功后，删除该实例。

1.  在下载的SDK目录中，打开aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb文件夹。

2.  使用编辑器打开slb\_quick\_start.py文件，您需要配置用户鉴权参数ACS\_CLIENT，其他参数根据实际情况配置后，保存退出。

    **说明：** 因为用户鉴权是每个SDK必须执行的操作，所以可以在常量文件中配置AcsClient参数的值，在场景代码中调用常量文件。

    ```
    # encoding=utf-8
    import sys
    import json
    
    # 调用AcsClient参数进行身份验证
    from aliyunsdkcore.client import AcsClient
    # 使用阿里云官方sdk的异常处理模块
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    # 调用上传证书的API
    from aliyunsdkslb.request.v20140515 import UploadServerCertificateRequest
    # 调用创建SLB实例API
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerRequest
    # 调用添加默认服务器组API
    from aliyunsdkslb.request.v20140515 import AddBackendServersRequest
    # 调用创建HTTPS监听的API
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerHTTPSListenerRequest
    # 调用修改HTTPS监听的API
    from aliyunsdkslb.request.v20140515 import SetLoadBalancerHTTPSListenerAttributeRequest
    # 调用删除SLB实例API
    from aliyunsdkslb.request.v20140515 import DeleteLoadBalancerRequest
    ##异常处理逻辑
    from sdk_lib.exception import ExceptionHandler
    # 命令行导入日志
    from sdk_lib.common_util import CommonUtil
    
    # 用户身份鉴权参数配置
    ACS_CLIENT = AcsClient(
        'your-access-key-id',  # your-access-key-id
        'your-access-key-secret',  # your-access-key-secret
        'cn-zhangjiakou',  # your-region-id
    )
    # 失败重试次数
    TRY_TIME = 3
    '''
    创建slb实例->上传服务器证书->创建https监听->上传新的服务器证书
    ->循环修改https监听配置
    '''
    
    
    def create_load_balancer(params):
        '''
        create_load_balancer：创建slb实例
        官网API参考链接：alibabacloud.com/help/zh/doc-detail/27577.htm
        '''
        try:
            # 设置创建SLB实例的调用参数
            request = CreateLoadBalancerRequest.CreateLoadBalancerRequest()
            request.set_MasterZoneId(params["master_zone_id"])
            request.set_SlaveZoneId(params["slave_zone_id"])
            request.set_LoadBalancerName(params["load_balancer_name"])
            request.set_PayType(params["pay_balancer_type"])
            # 发送调用请求并接收返回数据
            response = ACS_CLIENT.do_action_with_exception(request)
            response_json = json.loads(response)
            # 返回结果
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
                # 设置添加默认服务器组的调用参数
                request = AddBackendServersRequest.AddBackendServersRequest()
                # 负载均衡实例的ID
                request.set_LoadBalancerId(params["load_balancer_id"])
                # 要添加的后端服务器列表
                request.set_BackendServers(params["backend_servers"])
                # 发送调用请求并接收返回数据
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                # 返回结果
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
                # 要上传的公钥证书
                request.set_ServerCertificate(params["server_certificate"])
                # 需要上传的私钥
                request.set_PrivateKey(params["private_key"])
                # 发送调用请求并接收返回数据
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                # 返回结果
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
                # 负载均衡实例的ID
                request.set_LoadBalancerId(params["load_balancer_id"])
                # 监听的带宽峰值
                request.set_Bandwidth(params["bandwidth"])
                # 负载均衡实例前端使用的端口
                request.set_ListenerPort(params["listener_port"])
                # 是否开启健康检查
                request.set_HealthCheck(params["health_check"])
                # 是否开启会话保持
                request.set_StickySession(params["sticky_session"])
                # 负载均衡实例后端使用的端口
                request.set_BackendServerPort(params["backend_server_port"])
                # 服务器证书的ID
                request.set_ServerCertificateId(params["server_certificate_id"])
                # 发送调用请求并接收返回数据
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                # 返回结果
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
                # 负载均衡实例的ID
                request.set_LoadBalancerId(params["load_balancer_id"])
                # 监听的带宽峰值
                request.set_Bandwidth(params["bandwidth"])
                # 负载均衡实例前端使用的端口
                request.set_ListenerPort(params["listener_port"])
                # 是否开启健康检查
                request.set_HealthCheck(params["health_check"])
                # 是否开启会话保持
                request.set_StickySession(params["sticky_session"])
                # 服务器证书的ID
                request.set_ServerCertificateId(params["server_certificate_id"])
                # 发送调用请求并接收返回数据
                response = ACS_CLIENT.do_action_with_exception(request)
                response_json = json.loads(response)
                # 返回结果
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
            # 设置删除SLB实例的调用参数
            request = DeleteLoadBalancerRequest.DeleteLoadBalancerRequest()
            # 负载均衡实例的ID
            request.set_LoadBalancerId(load_balancer_id)
            # 发送调用请求并接收返回数据
            response = ACS_CLIENT.do_action_with_exception(request)
            response_json = json.loads(response)
            # 返回结果
            return response_json
        except ServerException as e:
            ExceptionHandler.server_exception(e)
        except ClientException as e:
            ExceptionHandler.client_exception(e)
    
    
    def main():
        params = {}
        # 设置创建SLB实例的参数
        # 设置新建SLB实例的主可用区为cn-zhangjiakou-a
        params["master_zone_id"] = "cn-zhangjiakou-a"
        # 设置新建SLB实例的备可用区为cn-zhangjiakou-b
        params["slave_zone_id"] = "cn-zhangjiakou-b"
        # 设置新建SLB实例的名称为SLB1
        params["load_balancer_name"] = "SLB1"
        # 设置新建SLB实例的计费类型为按量计费
        params["pay_balancer_type"] = "PayOnDemand"
    
        # 设置添加到默认服务器组的ECS的实例ID和权重
        params["backend_servers"] = [{"ServerId": "i-8vbe8yixxxxxxxxxxxxxw", "Weight": "100"},
                                     {"ServerId": "i-8vbe8yxxxxxxxxxxxxxj9v", "Weight": "100"}]
    
        # 设置上传服务器证书的参数
    
        # 设置创建HTTPS监听的参数
        # 关闭健康检查
        params["health_check"] = "off"
        # 设置监听的带宽峰值
        params["bandwidth"] = 6
        # 负载均衡实例前端使用的端口
        params["listener_port"] = 80
        # 设置负载均衡实例后端使用的端口
        params["backend_server_port"] = 443
        # 关闭会话保持
        params["sticky_session"] = "off"
    
        # 创建slb实例
        # 获取create_load_balancer函数返回值，load_balancer_json为结果的json串
        load_balancer_json = create_load_balancer(params)
        # 打印 load_balancer_json结果，其中"create_load_balancer"是对json串起的名字
        CommonUtil.log("create_load_balancer", load_balancer_json)
    
        # 上传服务器证书
        # 要上传的公钥证书
        params["server_certificate"] = "-----BEGIN CERTIFICATE-----xxxxxxx-----END CERTIFICATE-----"
        params["private_key"] = "-----BEGIN RSA PRIVATE KEY-----xxxxxxxxxxx-----END RSA PRIVATE KEY-----"
        result_json = upload_server_certificate(params)
        CommonUtil.log("upload_server_certificate", result_json)
        params["server_certificate_id"] = result_json["ServerCertificateId"]
    
        # slb实例id
        params["load_balancer_id"] = load_balancer_json["LoadBalancerId"]
    
        # 创建https监听
        result_json = create_https_listener(params)
        CommonUtil.log("create_https_listener", result_json)
    
        # 上传新的服务器证书
        # 要上传的新公钥证书
        params["server_certificate"] = "-----BEGIN CERTIFICATE-----xxxxxxx-----END CERTIFICATE-----"
        params["private_key"] = "-----BEGIN RSA PRIVATE KEY-----xxxxxxxxxxx-----END RSA PRIVATE KEY-----"
        result_json = upload_server_certificate(params)
        CommonUtil.log("upload_server_certificate", result_json)
        params["server_certificate_id"] = result_json["ServerCertificateId"]
    
        # 修改https监听配置
        result_json = set_https_listener_attribute(params)
        CommonUtil.log("set_https_listener_attribute", result_json)
    
        # 删除slb实例
        # 删除返回的LoadBalancerId对应的SLB实例
        load_balancer_json = delete_load_balancer(load_balancer_json["LoadBalancerId"])
        # 打印 load_balancer_json结果
        CommonUtil.log("delete_load_balancer", load_balancer_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

3.  进入slb\_quick\_start.py所在的目录，执行如下命令，运行创建和删除SLB实例示例。

    ```
    python slb_quick_start.py
    ```

    系统显示类似如下：

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


