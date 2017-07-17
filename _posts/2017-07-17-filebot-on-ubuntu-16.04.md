---
title: Filebot on Ubuntu 16.04
updated: 2017-07-17 22:14
---

The latest update of Filebot is installed via snap on the latest version of Ubuntu, which is quite different from everything I have tried before but since I started getting "http://app.filebot.net/data/exclude-blacklist.txt" with Filebot version 4.6, I had to upgrade in order to keep using it.

# What is snap
See [https://www.ubuntu.com/desktop/snappy](https://www.ubuntu.com/desktop/snappy)

# How to install it on Ubuntu 16.04 LTS
```sudo apt-get install snapd```

# Running Filebot in snap
## Location
/snap/bin/filebot

## Setting up interfaces (so filebot is allowed to interact with files under /media)
See [https://github.com/snapcore/snapd/wiki/Interfaces#removable-media](https://github.com/snapcore/snapd/wiki/Interfaces#removable-media) for reference

```sudo snap connect filebot:removable-media core:removable-media```
