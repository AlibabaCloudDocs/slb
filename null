# 获取客户端真实IP

您可以通过设置负载均衡的7层监听服务获取客户端真实IP地址。

七层负载均衡（HTTP/HTTPS协议）服务需要对应用服务器进行配置，然后使用`X-Forwarded-For`的方式获取客户端的真实IP地址。真实的客户端IP存放在HTTP头部的X-Forwarded-For字段，格式如下：

```
X-Forwarded-For: 用户真实IP, 代理服务器1-IP， 代理服务器2-IP，...
```

当使用此方式获取客户端真实IP时，获取的第一个地址就是客户端真实IP。

**说明：** 负载均衡的HTTPS监听是在负载均衡服务上的加密控制，后端仍旧使用HTTP协议，因此，在Web应用服务器上配置HTTPS和HTTP监听没有区别。

## 配置IIS7/IIS8服务器

1.  [下载](https://img.alicdn.com/tfscom/TB1R64PLVXXXXaaXVXXXXXXXXXX.rar?spm=a2c4g.11186623.2.5.z475ev&file=TB1R64PLVXXXXaaXVXXXXXXXXXX.rar)并解压 F5XForwardedFor文件。

2.  根据自己的服务器操作系统版本将x86\\Release或x64\\Release目录下的F5XFFHttpModule.dll和F5XFFHttpModule.ini拷贝到某个目录，例如C:\\F5XForwardedFor\\。确保IIS进程对该目录有读取权限。

3.  打开**IIS管理器**，双击**模块**功能。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2714029951/p3132.png)

4.  单击**配置本机模块**，然后在弹出的对话框中，单击**注册**。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2714029951/p3133.png)

5.  添加下载的.dll文件。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2714029951/p3135.png)

6.  为添加的两个文件授权允许运行ISAPI和CGI扩展。

    **说明：** 确保您已经安装了ISAPI和CGI应用程序。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2714029951/p3136.png)

7.  重启IIS服务器，等待配置生效。


## 配置Apache服务器

1.  执行如下命令，安装Apache的一个第三方模块mod\_rpaf。

    ```
     wget https://github.com/gnif/mod_rpaf/archive/v0.6.0.tar.gz
     tar zxvf mod_rpaf-0.6.tar.gz
     cd mod_rpaf-0.6
     /alidata/server/httpd/bin/apxs -i -c -n mod_rpaf-2.0.so mod_rpaf-2.0.c
    ```

2.  修改Apache的配置文件/alidata/server/httpd/conf/httpd.conf，在最末尾添加以下配置信息。

    ```
     LoadModule rpaf_module modules/mod_rpaf-2.0.so
     RPAFenable On
     RPAFsethostname On
     RPAFproxy_ips  <IP_address>
     RPAFheader X-Forwarded-For
    ```

    **说明：** 如果您要获取代理服务器的地址，可以将代理服务器的网段添加到`RPAFproxy_ips <IP_address>`，如负载均衡的IP地址段100.64.0.0/10（100.64.0.0/10 是阿里云保留地址，其他用户无法分配到该网段内，不会存在安全风险）和高防IP地址段。多个IP地址段用逗号分隔。

3.  添加完成后重启Apache。

    ```
    /alidata/server/httpd/bin/apachectl restart
    ```


## 配置Nginx服务器

1.  执行如下命令，安装http\_realip\_module。

    ```
     wget http://nginx.org/download/nginx-1.0.12.tar.gz
     tar zxvf nginx-1.0.12.tar.gz
     cd nginx-1.0.12
     ./configure --user=www --group=www --prefix=/alidata/server/nginx --with-http_stub_status_module --without-http-cache --with-http_ssl_module --with-http_realip_module
     make
     make install
     kill -USR2 `cat /alidata/server/nginx/logs/nginx.pid`
     kill -QUIT `cat /alidata/server/nginx/logs/ nginx.pid.oldbin`
    ```

2.  执行如下命令，打开nginx.conf文件。

    ```
    vi /alidata/server/nginx/conf/nginx.conf
    ```

3.  在以下配置信息后添加新的配置字段和信息。

    ```
     fastcgi connect_timeout 300;
     fastcgi send_timeout 300;
     fastcgi read_timeout 300;
     fastcgi buffer_size 64k;
     fastcgi buffers 4 64k;
     fastcgi busy_buffers_size 128k;
     fastcgi temp_file_write_size 128k;
    ```

    需要添加的配置字段和信息为：

    ```
     set_real_ip_from IP_address;
     real_ip_header X-Forwarded-For;
    ```

    **说明：** 如果您要获取代理服务器的地址，可以将代理服务器的网段添加到`set_real_ip_from <IP_address>`，如负载均衡的IP地址段100.64.0.0/10（100.64.0.0/10 是阿里云保留地址，其他用户无法分配到该网段内，不会存在安全风险）和高防IP地址段。多个IP地址段用逗号分隔。

4.  执行如下命令，重启Nginx。

    ```
    /alidata/server/nginx/sbin/nginx -s reload
    ```


