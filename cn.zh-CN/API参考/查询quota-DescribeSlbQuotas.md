# 查询quota-DescribeSlbQuotas {#reference_t5v_dbl_s2b .reference}

查询LoadBalancer的资源约束。

## 请求参数 {#section_z4m_1dl_s2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作。取值：DescribeSlbQuotas

|
|RegionId|String|是|需要查询LoadBalancer资源约束的Region，适用于该Region下的所有负载均衡实例。|

## 返回参数 {#section_th5_kdl_s2b .section}

|名称|类型|描述|
|--|--|--|
|Quotas|List|请参见[\#table\_x1x\_k2l\_s2b](#table_x1x_k2l_s2b)。如果某个值没有返回，表示没有特殊配置，请根据[使用限制](https://help.aliyun.com/document_detail/32459.html?spm=a2c4g.11186623.6.543.7OYrpf)查询默认值。

|
|Name|String|资源约束名称。|
|Max|Integer|资源约束项的最大值。|
|Comment|String|资源约束项的说明。|

## Quotas {#section_vyl_k2l_s2b .section}

|限制名称|限制英文名称|英文注解|配置来源|限制范围|规则中心的Action名称|默认值|
|----|------|----|----|----|-------------|---|
|服务器证书数量|server-cers-per-region|`Max number of Server certificates per region`|规则中心|Region单用户|certNum|100|
|CA证书数量上限|client-ca-cers-per-region|`Max number of Client CA certificates per region`|规则中心|Region 单用户|certNum|100|
|一个rs可以关联最大SLB的数量|slbs-per-backendserver|`Max number of SLB instances that a single backend server can be attached to`|规则中心|Region 中单SLB实例|vm\_lbs\_quota|50|
|SLB后端可以挂载最大rs的数量|backendservers-per-slb|`Max number of backend servers can be attached to a single SLB instance`|规则中心|Region 中单SLB实例|lb\_vms\_quota|200|
|SLB监听上限|listeners-per-slb|`Max number of listeners per SLB instance`|规则中心|Region 中单SLB实例|listenquato|50|
|SLB的URL转发规则|rules-per-listener|`Max number of forwarding rule per listener`|规则中心|Region 中单SLB实例|viprulequota|20|
|SNI扩展域名数量|domain-extensions-per-listener|`Max number of extension domains per listener`|规则中心|单实例+监听|domain\_extension\_count|3|
|每个地域单账号可创建的访问控制策略组个数|acls-per-region|`Max number of access control lists per region`|规则中心|Region 账号|max\_acl\_number\_per\_region|50|
|每个ACL规则可以关联监听的个数|listeners-per-acl|`Max number of listeners that an single access control list can be attached to`|规则中心|单监听|acl\_max\_vip\_quota|50|
|每个访问控制策略组可包含的条目个数|entries-per-acl|`Max number of entries per access control list`|规则中心|单策略组|acl\_entry\_quota|300|
|SLB购买数量|slbs-per-user|`Max number of SLB instances per account`|​用户标签|global|slb.num|60|

## 示例 {#section_qjx_rsp_42b .section}

**请求示例**

```

https://slb.aliyuncs.com?Action=DescribeSlbQuotas
&RegionId=cn-hangzhou
&<公共请求参数>
```

```

https://slb.aliyuncs.com?Action=DescribeSlbQuotas
&RegionId=cn-hangzhou
&<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8" ?>
    	<RequestId>980F7B6D-EF5F-40AF-BA92-A743149AA79D</RequestId>
    	<Quotas>
    		<Quota>
    			<Comment>Max number of Server certificates per region</Comment>
    			<Max>100</Max>
    			<QuotaName>server-cers-per-region</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of Client CA certificates per region</Comment>
    			<Max>100</Max>
    			<QuotaName>client-ca-cers-per-region</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of SLB instances that a single backend server can be attached to</Comment>
    			<Max>50</Max>
    			<QuotaName>slbs-per-backendserver</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of backend servers can be attached to a single SLB instance</Comment>
    			<Max>200</Max>
    			<QuotaName>backendservers-per-slb</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of listeners per SLB instance</Comment>
    			<Max>50</Max>
    			<QuotaName>listeners-per-slb</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of forwarding rule per listener</Comment>
    			<Max>20</Max>
    			<QuotaName>rules-per-listener</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of extension domains per listener</Comment>
    			<Max>3</Max>
    			<QuotaName>domain-extensions-per-listener</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of access control lists per region</Comment>
    			<Max>50</Max>
    			<QuotaName>acls-per-region</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of listeners that an single access control list can be attached to</Comment>
    			<Max>50</Max>
    			<QuotaName>listeners-per-acl</QuotaName>
    		</Quota>
    		<Quota>
    			<Comment>Max number of entries per access control list</Comment>
    			<Max>300</Max>
    			<QuotaName>entries-per-acl</QuotaName>
    		</Quota>
    	</Quotas>
    ```

-   JSON格式

    ```
    {
        "RequestId": "980F7B6D-EF5F-40AF-BA92-A743149AA79D", 
        "Quotas": {
            "Quota": [
                {
                    "Comment": "Max number of Server certificates per region", 
                    "Max": 100, 
                    "QuotaName": "server-cers-per-region"
                }, 
                {
                    "Comment": "Max number of Client CA certificates per region", 
                    "Max": 100, 
                    "QuotaName": "client-ca-cers-per-region"
                }, 
                {
                    "Comment": "Max number of SLB instances that a single backend server can be attached to", 
                    "Max": 50, 
                    "QuotaName": "slbs-per-backendserver"
                }, 
                {
                    "Comment": "Max number of backend servers can be attached to a single SLB instance", 
                    "Max": 200, 
                    "QuotaName": "backendservers-per-slb"
                }, 
                {
                    "Comment": "Max number of listeners per SLB instance", 
                    "Max": 50, 
                    "QuotaName": "listeners-per-slb"
                }, 
                {
                    "Comment": "Max number of forwarding rule per listener", 
                    "Max": 20, 
                    "QuotaName": "rules-per-listener"
                }, 
                {
                    "Comment": "Max number of extension domains per listener", 
                    "Max": 3, 
                    "QuotaName": "domain-extensions-per-listener"
                }, 
                {
                    "Comment": "Max number of access control lists per region", 
                    "Max": 50, 
                    "QuotaName": "acls-per-region"
                }, 
                {
                    "Comment": "Max number of listeners that an single access control list can be attached to", 
                    "Max": 50, 
                    "QuotaName": "listeners-per-acl"
                }, 
                {
                    "Comment": "Max number of entries per access control list", 
                    "Max": 300, 
                    "QuotaName": "entries-per-acl"
                }
            ]
        }
    }
    ```


