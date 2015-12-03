---
title: Home Network - Initial Thoughts
updated: 2015-12-03 16:12
---

I have been struggling for a while with putting together my home network. Because let's face it, it matters more and more, all those family photos and digital content in general has to live somewhere. I have a few machines, a mix of old laptops, desktops, NASes and a thinclient and would like to come up to a coherent plan to put it all to work together. I also have a Business Dropbox account (so 1TB data allowance) plus various cloud storage accounts (a free Microsoft Live account, a free Google Drive account and so on).

The best feature of my home network so far is my router, a Linksys modem that runs DD-WRT. It is awesome and lets me for example allowing my kids tablets to connect to the LAN but not the internet from the web console in a couple of clicks.

For the rest, so far a lot of trials and errors and half-finished jobs. Right now, I have an Ubuntu Linux NAS running a Samba server with 5 TB worth of storage space (2+2+1) plus some virtual machines I don't remember what I installed on, a thinclient is running a web server on Tiny Core Linux that hosts an old version of Ghost (blogging platform), another Tiny Core Linux machine running another Samba server with another couple of drives. My photographs are in Dropbox and nowhere locally at the moment (the laptop I synced the pictures to Dropbox in the first place crashed, thank you Windows 10 upgrade! and I had to re-install from scratch). I also have a media center with its own hardrive that also runs a samba server.

So all in all a mess I need to make somewhat coherent. I like to experiment so I will dedicate some machines to that but have a couple of core machines running the services I need in the way I need them is long overdue.

My thoughts so far:
1. In a work environment, it is preferable to have any machine do a single job. It might not be fully possible in a home environment but would certainly makes things easier to remember from the prospective of what does what. So at a minimum, I need three separate machines: one file share, one media center and one hypervisor (abstracting the rest of the "crap" I run/experiment with into virtual machines).
* File Share: the Linux NAS would fit the bill, just remove the virtual machines to have a dedicated storage machine
* Media Center: it is what it is at the moment, it is fairly locked down but works pretty well so I will leave it alone until it is time to upgrade
* Hypervisor: I am not sure of the architecture to go with. I have a machine running VMWare ESXi and that runs pretty well but is annoying from the prospective that in order to install anything, I need to download the ISO to my laptop, then copy it to the hypervisor via FTP (can't download directly from the hypervisor or share the folder via Samba). The other set-up I have experimented with is Ubuntu Server + headless VirtualBox (which is how I run the VMs I currently have on my File Share servers). I don't have anything mission critical as a VM and I can download directly from the box and/or share/mount a folder as a Samba share to easily copy ISOs across the network.
2. I need to connect the fileshare to my Dropbox account so I have a local version of the Dropbox files, mostly the family pics.
3. I want some kind of web server. The thinclient as a web server is perfect from the prospective that its electricity consumption is very low, but Tiny Core Linux can be rather time consuming to set up. So before making a decision on whether to run my web server on the thin client, on another separate physical machine or as a VM on the Hypervisor, I need to figure out what web services I need/want. Something like [PsDash](https://github.com/Jahaja/psdash) for example. To be expanded on.
4. File Share. One dedicated server is great, what about backups though for when it will inevitably fails? Backup and push to Dropbox? Should I then have a dedicated machine to host the Dropbox file? Backup to another machine on the network (we would now potentially be up to 5 machines running pretty much constantly). And what backup tool, regular rsync, something like [Borg](https://github.com/borgbackup/borg)...? To be expanded. 

So yeah, a lot of ideas and not much organization but we might get there eventually... More in a future post.