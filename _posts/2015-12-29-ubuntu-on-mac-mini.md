---
title: Installing Ubuntu 14.04 on Mac Mini
updated: 2015-12-29 21:26
---

Because my 2007 Mac Mini is an Intel Core Duo (and not Intel Core Duo 2), from an OS X prospective, I am stuck on Snow Leopard (10.6.8), which is now unsupported. Because the machine itself is in good nick and a great little piece of kit, I went ahead with installing the latest Ubuntu LTS release, 14.04 at the time of writing. There is no need for a specific "mac" version, I just used the regular i386 desktop image.
After reading through a lot of mostly outdated or just plain confusing guides, this [link](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/) had everything put togther and made it rather straight forward to follow.

4 steps:
- Install [ReFind](http://www.rodsbooks.com/refind/)
- Partition the hard drive (to make space for Ubuntu but keeping OS X around just in case)
- Create a Mac bootable USB key with the Ubuntu ISO following the steps [here](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
- Boot from the USB key through the ReFind menu and install Ubuntu

And that's pretty much it. I got a few errors after applying the updates but that was all sorted by running the below. ReFind defaults to the last option chosen so after you choose Ubuntu the first time, it will start Ubuntu automatically from then on. The Aiport Express network card worked without issue, so did the sound and everything else I looked at.

```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```
