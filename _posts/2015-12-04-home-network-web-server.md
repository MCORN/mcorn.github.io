---
title: Home Network - Web Server
updated: 2015-12-04 21:45
---

So what would I need on my home web server?

# General

 I have landed on 2 virtual Apache instances, listening on different ports, one external facing (redirected through the router based on a web address provided by a No-IP free DNS account) and one internal facing. I like that set-up (I can proxy to other web services as required from either one) so why not?

# Internal
1- Landing Page/Link Directory
A basic HTML page with links to other web services on the network. Did I mention I try a lot of stuff and keep forgetting what is installed/where and on what port?

2- Monitoring dashboard

* Disk/OS Monitoring

Out of the list below, I have had success with linfo. It however means I need to have a php server up and running on every machine I want stats for and proxy to each monitoring dashboard from the Link Directory described above. [Monitorix](http://www.monitorix.org/) seems to allow monitoring of remote servers through the one web interface but there doesn't seem to be a package for Tiny Core Linux, which is the only thing I can run on the thinclient. Also looks like a lot of info being displayed. It might however be customizable so worth a trial.

[linfo](http://linfo.sourceforge.net/)
[Linux-Dash](https://github.com/afaqurk/linux-dash)
[PyDash](https://github.com/k3oni/pydash)
[phpSysInfo](http://phpsysinfo.github.io/phpsysinfo/)
[EZServerMonitor](http://ezservermonitor.com/)

* Service Monitoring

[phpServerMonitor](http://www.phpservermonitor.org/)
This appeals from the prospective that it would be able to tell me my media center for example has lost its network connection. It might however be somewhat cumbersome for such a specific purpose, especially since some of the above services also provide service monitoring.

# External 

At this stage, no real purpose, since my blog is now externally hosted?

1- Note Taking?
[Paperwork](https://github.com/twostairs/paperwork)
[Ajour](https://github.com/gopatrik/ajour)

2- Document Management?
[Mollify](http://www.mollify.org/) Interesting from the prospective that I could view the docs online through the web interface.
