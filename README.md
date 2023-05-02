wjlsteelstructure.com-2019
=============

万金隆彩钢制品英文官网2019年版


域名绑定、301转向及nginx配置
-----

新建配置文件: ``sudo nano /etc/nginx/sites-available/wjlsteelstructure.com``

编辑配置文件及保存: 

    server {
      listen 443 ssl http2;
      server_name www.wjlsteelstructure.com;
      ssl_certificate wjlsteelstructure.crt;
      ssl_certificate_key wjlsteelstructure.key;
      index index.html;
      root /srv/wjlsteelstructure.com-2019/_site;
      error_page 404 /Error.html;
      add_header Strict-Transport-Security "max-age=31536000" always;
      add_header Cache-Control "max-age=31536000";
      ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
      ssl_ciphers HIGH:!aNULL:!MD5:!DH;
      gzip on;
      gzip_min_length 1k;
      gzip_buffers 4 16k;
      gzip_http_version 1.1;
      gzip_comp_level 5;
      gzip_types text/html text/css text/xml application/javascript;
      gzip_disable "MSIE [1-6]\.";
      gzip_vary on;
    }
    server {
      listen 443 ssl http2;
      server_name wjlsteelstructure.com;
      ssl_certificate wjlsteelstructure.crt;
      ssl_certificate_key wjlsteelstructure.key;
      return 301 https://www.wjlsteelstructure.com$request_uri;
    }
    server {
      listen 80;
      server_name wjlsteelstructure.com www.wjlsteelstructure.com;
      return 301 https://www.wjlsteelstructure.com$request_uri;
    }

建立链接: ``sudo ln -s /etc/nginx/sites-available/wjlsteelstructure.com /etc/nginx/sites-enabled/``

重启nginx: ``sudo service nginx restart``


下载及生成网站
-----

1. 下载网站源码: ``git clone https://github.com/zackwong/wjlsteelstructure.com-2019.git``

2. 进入源码根目录: ``cd wjlsteelstructure.com-2019``

3. 生成网站: ``jekyll build``


开发者
---------

* Zack Wong &lt;hzzzoo@126.com&gt;

