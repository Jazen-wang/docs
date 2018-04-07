## 服务器配置https访问

> 最近配置了个人文档日志docute，想放到自己的returngirl.cn的域名下。由于域名没备案一直被封。最近了解到走https 443端口可以绕过域名备案。记录一下配置nginx https的过程。
  
  
1. 上腾讯云后台`SSL证书管理`申请免费证书。
2. 等待证书颁发，并下载。
3. 选择用nginx做https

以配置nginx为例
```nginx
server {
    listen 443;
    server_name returngirl.cn;
    ssl on;
    ssl_certificate /home/ubuntu/returngirl.cn/Nginx/1_returngirl.cn_bundle.crt;
    ssl_certificate_key /home/ubuntu/returngirl.cn/Nginx/2_returngirl.cn.key;
    ssl_session_timeout  5m;
    ssl_protocols  SSLv2 SSLv3 TLSv1;
    ssl_ciphers  ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP;
    ssl_prefer_server_ciphers   on;
    location / {
        root /home/ubuntu/www/docs/;
        index index.html;
  }
  location ~ /.well-known {
        allow all;
  }
}
```
