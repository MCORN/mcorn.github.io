---
title: Beet on Ubuntu 16.04
updated: 2017-02-18 16:58
---

Because MediaSonic and SubSonic are big Java applications with non negligible memory requirements (and require licenses for use of their APIs), I have been looking around for alternatives and decided to have another go at [Beet](http://beets.io/). So the installation is rather straightforward and the tagging of music files as well but going through the documentation, I stumbled upon the [web plugin](http://beets.readthedocs.io/en/v1.3.17/plugins/web.html). It is rather under-developed right now and as a web interface, rather underwhelming but it also exposes a straightforward API.

So I thought I would have a go at a simplistic front-end querying that API to play music via a web interface as a genre radio. When you load the page, the API is queried via jQuery/Ajax to return all items, you choose a genre and a playlist is constructed with all tracks matching that genre and played one after the other using the [AudioJS](https://kolber.github.io/audiojs/) javascript library.

The hardest part was actually to get over the Cross Domain restrictions between the HTML page and the beet API running by default on port 8337. I ended up setting up an Apache proxy and hardcoding headers for it to work between my development web server on my laptop hosting the index.html page and the beet web plugin running on my music server. Sample of my apache virtual host configuration below for reference.

```
<VirtualHost *:90>
  ServerAdmin webmaster@localhost
  DocumentRoot /home/mathieu/Git/webplay
  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined

  ProxyPreserveHost On
  ProxyPass /beet/ http://localhost:8337/
  ProxyPassReverse / http://localhost:8337/

  Header always set Access-Control-Allow-Origin "*"
  Header always set Access-Control-Allow-Headers "x-requested-with, Content-Type, origin, authorization, accept, client-security-token"
  ServerName localhost
</VirtualHost>
```
As mentioned above, the code is very simplistic so far and the result not very visually appealing but at least it works. Results at [https://github.com/MCORN/webplay]. I will keep playing around, there is a standalone subsonic-lookalike API available at [https://github.com/spl0k/supysonic] that does look intriguing, especially since it would allow to use front-ends already available like [Jamstash](http://jamstash.com/).