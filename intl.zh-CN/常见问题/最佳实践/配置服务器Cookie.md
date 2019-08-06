# 配置服务器Cookie {#concept_hzq_sj5_vdb .concept}

负载均衡服务提供会话保持功能。开启会话保持功能后，负载均衡会将会话期间内来自同一客户端的访问请求分发到同一台后端服务器上进行处理。

四层监听的会话保持是基于IP地址的会话保持，负载均衡监听器会将来自同一IP地址的请求转发到同一个后端ECS上；而七层监听是基于Cookie的会话保持。

如果您选择使用重写Cookie的方式，需要在后端服务器上配置Cookie。假如您的负载均衡服务地址下有两个域名：vip.a.com和img.a.com，当您想为vip.a.com配置会话保持时，您可以设置Cookie名称为name，然后在后端服务器上为域名vip.a.com设置key为name的Cookie。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4164/15382791673120_zh-CN.png)

本文档介绍了如何在Apache、Nginx和Lighttpd应用服务器上配置Cookie。

## Apache {#section_mkj_35v_wdb .section}

1.  打开httpd.conf配置文件，确保如下配置没有被注释。

    ```
    LoadModule usertrack_module modules/mod_usertrack.so
    ```

2.  在virtual host中添加以下配置。

    ```
     CookieName name
     CookieExpires "1 days"
     CookieStyle Cookie
     CookieTracking on
    ```


## Nginx {#section_rkx_p5v_wdb .section}

参考以下配置，设置Cookie。

```
server {
    listen 8080;
    server_name wqwq.example.com;
    location / {
      add_header Set-Cookie name=xxxx;
        root   html;
        index  index.html index.htm;
    }
}
```

## Lighttpd {#section_cpx_s5v_wdb .section}

参考以下配置，设置Cookie。

```
    server.modules  = ( "mod_setenv" )
    $HTTP["host"] == "test.example.com" {
          server.document-root = "/var/www/html/"
          setenv.add-response-header = ( "Set-Cookie" => "name=XXXXXX"      }
    }
```

