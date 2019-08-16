# 从SSL证书服务选择 {#task_1597562 .task}

阿里云提供的证书签发服务是指在云上签发各品牌数字证书，实现网站HTTPS化，使网站具备可信、防劫持、防篡改和防监听等特点，并对证书进行统一生命周期管理，简化证书部署。

如果您需要使用SSL证书服务中的证书，您需要登录[SSL证书控制台](https://yundun.console.aliyun.com/?spm=5176.2020520001.106.d20cas.3c474bd31n23aP&p=cas#/cas/home)，购买证书或者上传第三方证书到SSL证书服务。

SSL证书服务详情请参见[SSL证书服务详情](https://www.aliyun.com/product/cas?spm=5176.8142029.security.5.3dbd6d3ezWmWrn)。

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb)。 
2.  在左侧导航栏，单击**证书管理**。
3.  单击**创建证书**，在创建证书页面，选择**从SSL证书服务选择**。 

    ![从SSL证书服务选择](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21331/156595048011881_zh-CN.png)

4.  单击**下一步**，在从SSL证书服务选择页面，设置证书部署地域并从证书列表中选择使用的SSL证书。 证书不支持跨地域使用，如果该证书需要在多个地域使用，选择所有需要的地域。
5.  单击**确定**。

**相关文档**  


[UploadServerCertificate](../intl.zh-CN/API参考/服务器证书/UploadServerCertificate.md#)

