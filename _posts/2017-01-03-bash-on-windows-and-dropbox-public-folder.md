---
title: Bash On Windows And Dropbox Public Folder
updated: 2017-01-03 18:31
---

I run Windows 10 on my work machine and have installed [Bash on Windows](http://www.windowscentral.com/how-install-bash-shell-command-line-windows-10) just for a play around really.

Then came the announcement that Dropbox was dropping the Public folder, which is going to become a regular private folder. I use the fact that Dropbox serves any HTML content within that Public folder to run a link directory type HTML page with all the links I need for work. As it relies on Javascript and CSS files also present in the folder, I can't just open the page from my local Dropbox folder in Chrome or Firefox because of the security settings. And I want it to somewhat look pretty all the same.

Now I was looking at a lightweight HTML web server to run on my laptop to serve the page and because I have dabbled in python, I knew about SimpleHTTPServer but having to install python on the laptop just for that was annoying until I remembered that a) Bash on Windows would already have python installed, b) Bash on Windows can access local files while you can run bash commands from Windows as well... 

So I decided to have a bash command running at startup launching python SimpleHTTPServer from within my Dropbox Public folder.

# Running python SimpleHTTPServer from Bash on Windows serving the Dropbox Public folder content
```bash
cd /mnt/c/users/mat/Dropbox/Public
python -m SimpleHTTPServer 8600 2>&1 > /dev/null
```
*suppressing the output is a must in order for the batch windows not to stay open when you start the webserver from Windows*

I saved this code into a bash file at `~/httpweb.sh` as

```bash
#!/bin/bash
cd /mnt/c/Users/Mat/Dropbox/Public
python -m SimpleHTTPServer 8600 > /dev/null 2>&1
```

# Running the command from Windows
```cmd
bash -c "~/httpweb.sh"
``` 

I saved this code into a batch file called startHTTPWeb.bat as

```cmd
@echo off
start bash -c "~/httpweb.sh"
```

# Getting the code to run at startup
I copied the bat file from above into Windows Startup folder and the easiest way to find the folder is to run the command `shell:startup`.


