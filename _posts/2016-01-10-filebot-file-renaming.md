---
title: File Renaming Using Filebot
updated: 2016-01-10 21:42
---

In order for files to be indexed properly by the Fire TV, I need to get the naming consistent. In comes Filebot, which does exactly that and has a very nice terminal/command line implementation - see http://www.filebot.net/cli.html.

# Installing Filebot

In order to run Filebot on Ubuntu server 12.04, Java needs to be upgraded to Java 8 , see [here](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html) for the way to do it. Then follow the second half of [this script](http://whatswhat.no/computer/linux/linux-server/603-ubuntu-server-install-filebot) to install filebot itself.

# Running Filebot

See [bash script](https://github.com/MCORN/scripts/blob/master/bash/rename_move.sh) in the repo.
