# Configure cookie in the backend server {#concept_hzq_sj5_vdb .concept}

Server Load Balancer provides session persistence function. With session persistence enabled, Server Load Balancer can distribute requests from the same client to the same backend server during the session period.

For layer-4 listeners, session persistence is based on the IP address. The listener of Server Load Balancer forwards requests from the same IP address to the same backend server. For layer-7 listeners, session persistence is based on cookies.

If you choose to rewrite the cookie, you must configure the cookie on the backend server. Suppose there are two domain names under your Server Load Balancer service: vip.a.com and img.a.com. If you want to configure session persistence for vip.a.com, you can set the cookie name to name, and set a cookie of which the key is name for vip.a.com on the backend server.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4164/15382791713120_en-US.png)

Follow the instructions in this section to set cookies on a backend server.

## Apache  {#section_mkj_35v_wdb .section}

1.  Open the httpd.conf file and make sure that the following line is not commented.

    ```
    LoadModule usertrack_module modules/mod_usertrack.so
    ```

2.  Add the following configurations in the VirtualHost file.

    ```
     CookieName name
     CookieExpires "1 days"
     CookieStyle Cookie
     CookieTracking on
    ```


## Nginx {#section_rkx_p5v_wdb .section}

Configure the cookie as follows.

```
server {
    listen 8080;
    server_name wqwq.example.com;
    location / {
      add_header Set-Cookie name=xxxx;
        root html;
        index index.html index.htm;
    }
}
```

## Lighttpd {#section_cpx_s5v_wdb .section}

Configure the cookie as follows.

```
    server.modules  = ( "mod_setenv" )
    $HTTP["host"] == "test.example.com" {
          server.document-root = "/var/www/html/"
          setenv.add-response-header = ( "Set-Cookie" => "name=XXXXXX"      }
    }
```

