# setup a local web server

1. Install MySQL
1. Install PHP according our [requirements](http://flowframework.readthedocs.org//en/stable/TheDefinitiveGuide/PartII/Requirements.html).
2. install your web server, e.g. *nginx* or *apache2*
3. Add *127.0.0.1 neosbase.dev* to your [hosts file]("https://en.wikipedia.org/wiki/Hosts_(file)").
  
## nginx

[Install nginx](http://nginx.org/en/docs/install.html) and
  [configure](https://www.linode.com/docs/websites/nginx/how-to-configure-nginx) *http://neosbase.dev* as follows:

```
server {
  listen 80 ;
  root /your/local/path/neos-development-distribution/Web/;
  server_name neosbase.dev *.neosbase.dev ;

  client_max_body_size 50M;

  error_page 500 502 503 504 /50x.html;

  location ~ \.php$ {
    include /usr/local/etc/nginx/fastcgi_params;
    keepalive_timeout 0;

    fastcgi_pass unix:/usr/local/var/run/php-fpm-www;
  }

  location = / {
    rewrite ^ /index.php;
  }

  try_files $uri $uri/ /index.php?$args;
}
```

## apache2

Install apache2 and [configure](https://httpd.apache.org/docs/trunk/vhosts/) *http://neosbase.dev* as follows:

```
NameVirtualHost *:80 # if needed

<VirtualHost *:80>
    DocumentRoot "/your/local/path/neos-development-distribution/Web/"
    ServerName neosbase.dev
    ServerAlias *.neosbase.dev
</VirtualHost>
```