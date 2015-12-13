---
title: Borg on Ubuntu 12.04
updated: 2015-12-13 11:22
---

# Installation

I went for the easiest option, which is an all included executable for Linux, available from [here](https://github.com/borgbackup/borg/releases). Download the executable, install in a directory defined in $PATH and you are ready to run borg commands from the terminal.

I also installed [AtticMattic](https://github.com/witten/atticmatic/), which is a python script acting as a wrapper to simplify the actual backup process and scheduling backups from the crontab. For anything else (list or restore backups for example), you will still need to run borg commands themselves. I couldn't figure out where the samples files [/etc/borgmatic/includes](../assets/attachments/borgmatic/includes) and [/etc/borgmatic/config](../assets/attachments/borgmatic/config)) were so I downloaded them from the repo.

# Running
With AttiMattic, just add your own config in the config file and run 

```
borgmattic
```

## Having a look around

The installation of both Borg and AtticMattic is really straightforward, which is a really nice and understated feature in itself. Running the borgmattic command as above above does create a first backup, then re-running the same command does only take a few seconds to create a second backup since nothing has changed in the meantime.

To list the available backups (where /mnt/backup is the location of the backup repo)

```
borg list /mnt/backup
```

Restore a backup by name (will restore in the directory you run the command from)

```
borg extract -v /mnt/backup::ubulaptop-2015-12-13T09:15:56.793268
```

Setting the compression to lzma (the highest type of compression available) doesn't do much for the types of files (.avi and .mjpeg) I tested with (6.6 GB versus 6.7 GB, which was to be expected) and means the backup process does run for a rather long time. I think for my purpose, I may as well not have any compression settings.

The other interesting feature at a glance is that as part of the backup process the integrity of all backup files is actually checked.

There is another Borg addition I haven't looked yet - [BorgWeb](http://borgbackup.github.io/borgweb/) 