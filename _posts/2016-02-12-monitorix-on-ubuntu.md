---
title: Monitorix on Ubuntu 14.04
updated: 2016-02-12 22:32
---

Because it is nice to know what is going on on my Ubuntu server without having to log in and run commands in the terminal, I have been looking at web dashboards (see [previous post](home-network-web-server)) and decided to have a go at [Monitorix](http://www.monitorix.org/).
Installing it is painless by adding the relevant [repository](http://apt.izzysoft.de/ubuntu/dists/generic/) and then running the couple of instructions [here](http://www.monitorix.org/doc-debian.html).
Once up and running, I fiddled a bit to add my disks to get the information I wanted: temperature and space. I was first thrown off because I expected both data to display in the "Disk" section once enabled but this displays only the temperature component. The disk usage actually displays in the "Filesystem Usage" section. To enable the different sections and add the disks to the different sections for monitoring, it pays to read the [instructions](http://www.monitorix.org/documentation.html).
So that was fine working off the built-in HTTP server but I wanted to serve it from the Apache instance that is already running on my server and that proved rather more complicated. The [FAQ entry](http://www.monitorix.org/faq.html#Q120) refered to a template config file at /usr/share/doc/monitorix/monitorix-apache.conf, which didn't help all that much.
What I had to do in the end to get it to work properly (on a stock Apache 2.4 instance):

* Run the following command

```
sudo a2enmod cgi

```
* Add the following to my default VirtualHost in /etc/apache2/sites-available/000-default.conf

```
Alias /monitorix /var/lib/monitorix/www
ScriptAlias /monitorix-cgi /var/lib/monitorix/www/cgi
<Directory /var/lib/monitorix/www/cgi/>
    DirectoryIndex monitorix.cgi
    AddHandler cgi-script .cgi .pl
    Options +FollowSymLinks +ExecCGI
    order deny,allow
    allow from all
</Directory>
<Directory /var/lib/monitorix/www>
        Options Indexes Includes FollowSymLinks
</Directory>
```
* Add the following to /etc/apache2/apache2.conf

```
<Directory /var/lib/monitorix/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>
```