!!! REMINDER: this page should print on one sheet of paper !!!
# Quick Start

## join a code sprint

Even if you do not any team members: [join a code sprint](https://www.neos.io/news.html).
You will [learn and have a lot of fun.](http://dimaip.github.io/2014/10/05/the-code-sprint/)
Just imagine how easy problems get if there is always someone in the room to ask and discuss.

## start hacking

You want to known the details: see [preliminaries](TODO: link preliminaries) for the used tools, frameworks you need.
You want to get your hand dirty first: read ahead.

### setup a local webserver

[Install and configure](link to setup-webserver) your local web server.

### checkout the code base

```
mkdir -p /your/local/path
cd /your/local/path
git clone https://github.com/neos/neos-development-distribution.git
cd neos-development-distribution
curl -s https://getcomposer.org/installer | php
php composer.phar install
echo goto http://neosbase.dev/setup and follow the instruction on the screen
```

Check out our [online documentation](http://neos.readthedocs.org/en/stable/GettingStarted/Installation.html)
if you want to know what the command do.

### contribute changes

1. [Create a Fork](https://help.github.com/articles/fork-a-repo/)
2. git remote add fork git@github.com:*your-github-fork*
3. git checkout -b *dev-your-new-feature-or-bug-fix*
4. git commit ...
5. git push fork
6. [Create Pull Request](https://help.github.com/articles/creating-a-pull-request/)

For details see [https://discuss.neos.io/t/development-workflow-for-github]().



