!!! REMINDER: this page should print on one sheet of paper !!!
# Quick Start

## join a code sprint

Even if you do not any team members: join a code sprint.
[You will learn a lot and it's fun.](http://dimaip.github.io/2014/10/05/the-code-sprint/)
Just imagine how easy problems get if there is always someone in the room to ask and discuss.

## start hacking

See [preliminaries](#cha-preliminaries) for the used tools, frameworks you need.

### Install PHP
### Install MySql database

### setup local webserver

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


### checkout the code base

```
mkdir -p /your/local/path
cd /your/local/path
git clone https://github.com/neos/neos-development-distribution.git
cd neos-development-distribution
curl -s https://getcomposer.org/installer | php
php composer.phar install
```

For the full truth see [https://discuss.neos.io/t/development-setup]().

### contribute changes

1. [Create a Fork](https://help.github.com/articles/fork-a-repo/)
2. git remote add fork git@github.com:your-github-fork
3. git checkout -b dev-your-new-feature-or-bug-fix
4. git commit ...
5. git push fork
6. [Create Pull Request](https://help.github.com/articles/creating-a-pull-request/)

For details see [https://discuss.neos.io/t/development-workflow-for-github]().






Where to put: [http://flowframework.readthedocs.org/en/stable/Quickstart/index.html]().