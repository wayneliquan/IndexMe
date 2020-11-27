Nginx 反向代理后如何获取real IP.

1. 4层反向代理。

   开启proxy_protocol on;

   默认发送`PROXY TCP4 来源IP 本地IP 来源Port 本地Port`

    `PROXY TCP4 192.168.1.101 192.168.1.100 48208 8000`

   ```
   # 当前Nginx服务器所在地IP为192.168.1.100
   stream {
   	upstream wayne_api {
   		server 192.168.1.101:8000;
   	}
   	server {
   		listen 8000;
           proxy_pass wayne_api;
           proxy_protocol on;
   	}
   }
   ```

   

2. 7层（HTTP）反向代理。

   

   ngx_http_realip_module

   http://nginx.org/en/docs/http/ngx_http_realip_module.html

   ```
   server {
   	listen 80;
       server_name  localhost;
       index index.html index.htm index.php;
       #include deny.ip;
       access_log /data/nginx.access.log;
       location ~ .* {
       	proxy_pass http://192.168.180.20;
           proxy_set_header X-Real-IP $remote_addr;
           proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
           #proxy_set_header X-Forward-For $remote_addr;
           proxy_set_header Host $host;
           set_real_ip_from  192.168.180.0/24;
           set_real_ip_from 192.168.181.0/24;
           real_ip_header    X-Forwarded-For;
           real_ip_recursive on;
       }
   }
   ```

   

3. 

