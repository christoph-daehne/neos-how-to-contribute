# setup a local web server

## PHP

Install PHP according our [requirements](http://flowframework.readthedocs.org//en/stable/TheDefinitiveGuide/PartII/Requirements.html).

## MySQL

## web server

Add *127.0.0.1 neosbase.dev* to your [hosts file](127.0.0.1 neosbase.dev) and
	install a web server like *nginx* or *apache2*.
  
### nginx

[Install nginx](http://nginx.org/en/docs/install.html) and
  [configure](https://www.linode.com/docs/websites/nginx/how-to-configure-nginx) *http://neosbase.dev* as follows:

```
server {
  listen 80 ;
  root /your/local/path/;
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

### apache2

Install apache2 and configure *http://neosbase.dev* as follows:

```
NameVirtualHost *:80 # if needed

<VirtualHost *:80>
    DocumentRoot "/your/htdocs/Neos-2.1/Web/"
    # skip the following line for development
    SetEnv FLOW_CONTEXT Production
    ServerName neos.demo
</VirtualHost>
```