## 服务器配置https访问

1. 上腾讯云后台`SSL证书管理`申请免费证书。
2. 等待证书颁发，并下载。
3. 选择用nginx做https

示例nginx配置
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