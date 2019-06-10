# 创建和删除SLB实例 {#task_tnc_qdm_vgb .task}

介绍如何使用Python SDK创建一个SLB实例，创建成功后删除该实例。

在华北3张家口地域创建一个名为SLB1的SLB实例，主可用区为cn-zhangjiakou-a，备可用区为cn-zhangjiakou-b，实例计费类型为按量计费，规格为slb.s1.small，监听的带宽峰值为1Mbps，其他参数使用默认值。实例创建成功后，删除该实例。

1.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb文件夹。
2.  使用编辑器打开slb\_quick\_start.py文件，您需要配置用户鉴权参数ACS\_CLIENT，其他参数根据实际情况配置后，保存退出。 

    **说明：** 因为用户鉴权是每个SDK必须执行的操作，所以可以在常量文件中配置AcsClient参数的值，在场景代码中调用常量文件。

    ``` {#codeblock_0v1_onb_3r1}
    #encoding=utf-8
    """
    创建slb实例->删除slb实例
    """
    import sys
    import json
    import uuid
    
    
    #调用AcsClient参数进行身份验证
    from aliyunsdkcore.client import AcsClient
    #使用阿里云官方sdk的异常处理模块
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    #调用创建SLB实例API   
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerRequest
    #调用删除SLB实例API  
    from aliyunsdkslb.request.v20140515 import DeleteLoadBalancerRequest
    #异常处理逻辑
    from sdk_lib.exception import ExceptionHandler
    #命令行打印日志  
    from sdk_lib.common_util import CommonUtil
    
    #用户身份验证参数配置
    ACS_CLIENT = AcsClient(
        'your-access-key-id',     #your-access-key-id
        'your-access-key-secret',   #your-access-key-secret
        'cn-zhangjiakou',     #your-region-id
    )
    
    def create_load_balancer(params):
        '''
        create_load_balancer：创建slb实例
        官网API参考链接：https://help.aliyun.com/document_detail/27577.html
        '''
        try:
        #设置调用参数
        request = CreateLoadBalancerRequest.CreateLoadBalancerRequest() 
        request.set_MasterZoneId(params["master_zone_id"]) 
        request.set_SlaveZoneId(params["slave_zone_id"]) 
        request.set_LoadBalancerName(params["load_balancer_name"]) 
        request.set_PayType(params["pay_balancer_type"]) 
        request.set_LoadBalancerSpec(params["load_balancer_spec"]) 
        request.set_Bandwidth(params["balancer_listener_bandwith"])
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
    
    def delete_load_balancer(load_balancer_id):
        '''
        delete_load_balancer：删除slb实例
        官网API参考链接：https://help.aliyun.com/document_detail/27579.html
        '''
        try:
            request = DeleteLoadBalancerRequest.DeleteLoadBalancerRequest()
            #负载均衡实例的ID
            request.set_LoadBalancerId(load_balancer_id)
            response = ACS_CLIENT.do_action_with_exception(request)
            response_json = json.loads(response)
            return response_json
        except ServerException as e:
            ExceptionHandler.server_exception(e)
        except ClientException as e:
            ExceptionHandler.client_exception(e)
    
    def main():
        #设置创建SLB的实例参数值
        params = {} 
        #设置新建SLB实例的主可用区为cn-zhangjiakou-a 
        params["master_zone_id"] = "cn-zhangjiakou-a" 
        #设置新建SLB实例的主可用区为cn-zhangjiakou-b 
        params["slave_zone_id"] = "cn-zhangjiakou-b" 
        #设置新建SLB实例的名称为SLB1 
        params["load_balancer_name"] = "SLB1"
        #设置新建SLB实例的计费类型为按量计费
        params["pay_balancer_type"] = "PayOnDemand"
        #设置新建SLB实例的规格为slb.s1.small
        params["load_balancer_spec"] = "slb.s1.small"
        #监听的带宽峰值为6Mbps
        params["balancer_listener_bandwith"] = "1"
    
        #创建slb实例
        #获取create_load_balancer函数返回值，load_balancer_json为结果的json串
        load_balancer_json = create_load_balancer(params)
        #打印 load_balancer_json结果，其中"create_load_balancer"是对json串起的名字
        CommonUtil.log("create_load_balancer", load_balancer_json)
    
        #删除slb实例
        #删除返回的LoadBalancerId对应的SLB实例
        load_balancer_json = delete_load_balancer(load_balancer_json["LoadBalancerId"])
        #打印 load_balancer_json结果
        CommonUtil.log("delete_load_balancer", load_balancer_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    					
    ```

3.  进入slb\_quick\_start.py所在的目录，执行如下命令，运行创建和删除SLB实例示例。 

    ``` {#codeblock_6bx_fuk_5pv}
    python slb_quick_start.py
    ```

    系统显示类似如下：

    ``` {#codeblock_qur_i5m_usj}
    
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


