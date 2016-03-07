---
title: Pasaffe, accessing PasswordSafe3 database files on Ubuntu
updated: 2016-03-07 18:46
---

I use [PasswordSafe](https://pwsafe.org/index.shtml) as my password management tool. No bells and whistles but I am used to it and it works for me.
The official Windows client works well but I have been struggling for an Ubuntu Linux client. The official albeit beta client is only available as 64-bit and [PasswordGorilla](http://www.fpx.de/fp/Software/Gorilla/) has a few annoying quirks (one of them being the menu displayed when single right clicking on an item only stays up while you have the button pressed) so I thought I would give [Pasaffe](https://launchpad.net/pasaffe) a trial. Interface is simple, app is available through the Ubuntu repository and single-right click works as expected. The only downside so far is that I haven't found a way to change the location of the database. As per [this link](https://answers.launchpad.net/pasaffe/+question/284633), the database is created/opened from a fixed location which is

`$HOME/.local/share/pasaffe/pasaffe.psafe3`

Because I have my password file in Dropbox, I just created a symlink from  the Dropbox location to the above location and everything seems to be working beautifully so far.

`ln -s /home/mathieu/Dropbox/Apps/PasswdSafe\ Sync/password.psafe3 pasaffe.psafe3`