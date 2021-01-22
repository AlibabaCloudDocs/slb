---
keyword: [负载均衡, 批量升级]
---

# 批量升级SLB实例

本文介绍如何使用Python SDK批量升级SLB实例规格。

## 背景信息

在华北3（张家口）创建一个名为SLB\_TEST1的SLB实例，主可用区为cn-zhangjiakou-a，备可用区为cn-zhangjiakou-b，实例计费类型为按量计费，规格为slb.s1.small，其他参数使用默认值。实例创建成功后，升级该实例并删除实例。

## 前提条件

1.  获取AccessKey。

    确保您已经有了用于身份验证的AccessKey ID和AccessKey Secret。如果尚未获取AK，参见查询获取[获取AccessKey](/cn.zh-CN/传统型负载均衡CLB/开发指南/API参考/获取AccessKey.md)。

2.  下载[Alibaba Cloud SLB SDK for Python](https://open.aliyun.com/sdk?language=python&product=slb)。

3.  进入setup.py所在的目录，执行以下命令，完成环境初始化配置。

    ```
    python setup.py install
    ```


## 升级实例

1.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb文件夹。

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
    # 调用查询负载均衡实例列表的API
    from aliyunsdkslb.request.v20140515 import DescribeLoadBalancersRequest
    # 调用查询负载均衡实例详情的API
    from aliyunsdkslb.request.v20140515 import DescribeLoadBalancerAttributeRequest
    # 调用创建SLB实例API
    from aliyunsdkslb.request.v20140515 import CreateLoadBalancerRequest
    # 调用修改SLB规格的API
    from aliyunsdkslb.request.v20140515 import ModifyLoadBalancerInstanceSpecRequest
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
    创建slb实例->查询实例列表->批量升级规格
    '''
    
    
    def create_load_balancer(params):
        '''
        create_load_balancer：创建slb实例
        官网API参考链接：https://help.aliyun.com/document_detail/27577.html
        '''
        try:
            # 设置创建SLB实例的调用参数
            request = CreateLoadBalancerRequest.CreateLoadBalancerRequest()
            # 负载均衡实例的主可用区ID
            request.set_MasterZoneId(params["master_zone_id"])
            # 负载均衡实例的备可用区ID
            request.set_SlaveZoneId(params["slave_zone_id"])
            # 负载均衡实例的名称
            request.set_LoadBalancerName(params["load_balancer_name"])
            # 负载均衡实例的规格
            request.set_LoadBalancerSpec(params["load_balancer_spec"])
            # 负载均衡实例的计费类型
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
    
    
    def describe_load_balancers(params):
        '''
        describe_load_balancers：查询已创建的SLB列表
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                # 设置添加默认服务器组的调用参数
                request = DescribeLoadBalancersRequest.DescribeLoadBalancersRequest()
                # 负载均衡实例的Name
                request.set_LoadBalancerName(params["load_balancer_name"])
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
    
    
    def describe_load_balancer_attribute(load_balancer_id):
        '''
        describe_load_balancer_attribute：查询指定负载均衡实例的详细信息
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = DescribeLoadBalancerAttributeRequest.DescribeLoadBalancerAttributeRequest()
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
            finally:
                counter += 1
    
    
    def modify_load_balancer_instance_spec(params):
        '''
        modify_load_balancer_instance_spec：修改负载均衡的实例规格
        '''
        counter = 0
        while counter < TRY_TIME:
            try:
                request = ModifyLoadBalancerInstanceSpecRequest.ModifyLoadBalancerInstanceSpecRequest()
                # 负载均衡实例的ID
                request.set_LoadBalancerId(params["load_balancer_id"])
                # SLB的规格
                request.set_LoadBalancerSpec(params["load_balancer_spec"])
                # 是否自动付费
                request.set_AutoPay(params["auto_pay"])
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
        params["load_balancer_name"] = "SLB_TEST1"
        # 设置新建SLB实例的计费类型为按量计费
        params["pay_balancer_type"] = "PayOnDemand"
        # 设置新建SLB实例的规格
        params["load_balancer_spec"] = "slb.s1.small"
    
        # 创建slb实例
        # 获取create_load_balancer函数返回值，load_balancer_json为结果的json串
        create_load_balancer_json = create_load_balancer(params)
        # 打印 load_balancer_json结果，其中"create_load_balancer"是对json串起的名字
        CommonUtil.log("create_load_balancer", create_load_balancer_json)
        # 查询已创建负载均衡实例
        load_balancers_json = describe_load_balancers(params)
        CommonUtil.log("describe_load_balancers", load_balancers_json)
        for load_balancer in load_balancers_json["LoadBalancers"]["LoadBalancer"]:
            # 查询负载均衡实例详细信息 判断是否为共享型规格
            load_balancer_json = describe_load_balancer_attribute(load_balancer["LoadBalancerId"])
            CommonUtil.log("describe_load_balancer_attribute", load_balancer_json)
            if 'LoadBalancerSpec' in load_balancer_json:
                # 设置修改SLB实例的规格的参数
                modify_params = {}
                # SLB实例的ID
                modify_params["load_balancer_id"] = load_balancer["LoadBalancerId"]
                # SLB实例规格
                modify_params["load_balancer_spec"] = "slb.s2.small"
                # 是否自动付费
                modify_params["auto_pay"] = True
                result_json = modify_load_balancer_instance_spec(modify_params)
                CommonUtil.log("modify_load_balancer_instance_spec", result_json)
        # 删除slb实例
        # 删除返回的LoadBalancerId对应的SLB实例
        load_balancer_json = delete_load_balancer(create_load_balancer_json["LoadBalancerId"])
        # 打印 load_balancer_json结果
        CommonUtil.log("delete_load_balancer", load_balancer_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    ```


**相关文档**  


[实例概述](/cn.zh-CN/传统型负载均衡CLB/用户指南/实例/实例概述.md)

[负载均衡实例FAQ](/cn.zh-CN/传统型负载均衡CLB/用户指南/实例/FAQ/负载均衡实例FAQ.md)

[性能保障型实例FAQ](/cn.zh-CN/传统型负载均衡CLB/用户指南/实例/FAQ/性能保障型实例FAQ.md)

[ModifyLoadBalancerInstanceSpec](/cn.zh-CN/传统型负载均衡CLB/开发指南/API参考/负载均衡实例/ModifyLoadBalancerInstanceSpec.md)

