# TagResources

调用TagResources为指定的资源列表统一创建并绑定标签。

**说明：** 单个实例最多可绑定20条标签。绑定标签前，阿里云会校验资源已有标签数量，超过限制值会返回报错信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=TagResources&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|TagResources|要执行的操作。

 取值：**TagResources**。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例所在的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。 |
|ResourceId.N|RepeatList|是|lb-bp16qjewdsunr41m1\*\*\*\*|资源ID，N的取值范围为**1**~**20**。 |
|ResourceType|String|是|instance|资源类型定义，取值：

 -   **instance**：负载均衡实例 。
-   **certificate**：证书。
-   **acl**：访问控制。 |
|Tag.N.Key|String|否|FinanceDept|实例的标签键。N的取值范围：**1**~**20**。一旦传入该值，则不允许为空字符串。

 最多支持64个字符，不能以`aliyun`和`acs:`开头，不能包含`http://`或者`https://`。 |
|Tag.N.Value|String|否|FinanceJoshua|实例的标签值。N的取值范围：**1**~**20**。一旦传入该值，可以为空字符串。

 最多支持128个字符，不能以`aliyun`和`acs:`开头，不能包含`http://`或者`https://`。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|C46FF5A8-C5F0-4024-8262-B16B639225A0|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=TagResources
&RegionId=cn-hangzhou
&ResourceId.1=lb-bp16qjewdsunr41m1****
&ResourceType=instance
&Tag.1.Key=FinanceDept
&Tag.1.Value=FinanceJoshua
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<TagResourcesResponse>
  <RequestId>C46FF5A8-C5F0-4024-8262-B16B639225A0</RequestId>
</TagResourcesResponse>
```

`JSON` 格式

```
{
	"RequestId":"C46FF5A8-C5F0-4024-8262-B16B639225A0"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

