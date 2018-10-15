Greyhole is a Linux-based replacement for the Drive Extender feature of Windows Home Server and allows to pool hard drives to create a redundant storage pool.

# Intro
(https://www.greyhole.net/)

# Wiki
(https://github.com/gboudreau/Greyhole/wiki)

# My install
## Drives
3 drives under /media, Backup1 (1.5TB), Backup2 (1TB) and Backup3 (2TB)
So far one landing zone `media`, one trash zone `Greyhole Trash` and a pool `pool/gh` on Backup3 and a pool `pool/gh` on Backup2. Backup1 already has files that are not part of Greyhole.

## Samba Config 
Under `/etc/samba/smb.conf`, shares to be accessed anonymously.
```
[media]
                    path = /media/Backup3/media
                    create mask = 0755
                    directory mask = 0755
                    read only = no
                    available = yes
                    browseable = yes
                    writable = yes
                    guest ok = yes
                    printable = no
                    dfree command = /usr/bin/greyhole-dfree
                    vfs objects = greyhole

[Greyhole Trash]
                    path = /media/Backup3/trash
                    create mask = 0755
                    directory mask = 0755
                    read only = no
                    available = yes
                    browseable = yes
                    writable = yes
                    guest ok = yes
                    printable = no
                    dfree command = /usr/bin/greyhole-dfree
                    vfs objects = greyhole

```

## Local Admin on port 8062 
PHP built-in server started using cron
`@reboot /usr/bin/php -S 0.0.0.0:8012 /usr/share/greyhole/web-app/index.php > /dev/null 2>&1`

## Shares mounted locally
Under `/mnt/samba/`
