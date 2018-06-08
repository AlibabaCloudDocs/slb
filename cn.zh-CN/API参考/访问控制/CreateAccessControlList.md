# CreateAccessControlList {#reference_n2r_h4v_tdb .reference}

创建访问控制策略组。

您可以创建多个访问控制策略组，每个策略组可包含多个IP地址条目或IP地址段条目。访问控制策略组的限制如下：

|资源|默认限制|
|:-|:---|
|每个地域单账号可创建的访问控制策略组个数|50|
|单账号每次可添加的IP地址条目个数|50|
|每个访问控制策略组可包含的条目个数|300|
|每个监听可绑定的访问控制策略组个数|50|

## 请求参数 {#section_n4h_pyx_5db .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：CreateAccessControlList

|
|RegionId|String|是|访问控制策略组的地域ID。|
|AclName|String|是|访问控制策略组名称。|

## 返回参数 {#section_ehc_jzx_5db .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|AclId|String|访问控制策略组ID。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

```
https://slb.aliyuncs.com/?Action=CreateAccessControlList
&RegionId=us-west-1
&AclName=group1
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <CreateAccessControlListResponse>
      <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
      <AclId>acl-rj9xpxzcwxrukois65yw3</AclId>
    </CreateAccessControlListResponse>
    ```

-   JSON格式

    ```
    {
        "AclId": "acl-rj9xpxzcwxrukois65yw3",
        "RequestId": "988CB45E-1643-48C0-87B4-928DDF77EA49"
    }
    ```


