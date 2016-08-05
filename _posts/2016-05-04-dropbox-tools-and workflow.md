---
title: Dropbox Tools and Workflow for photos
updated: 2016-05-04 21:19
---

## Camera Upload - Android
From the Dropbox Android app itself, uploads images and videos directly to the ``` /Camera Uploads ``` folder in Dropbox.
Main shortcoming is that, unlike the Google Image application, it doesn't offer the option to delete synced images from device automatically.

## SortMyBox
URL: https://www.sortmybox.com/
Description: Free service,  moves content from a specific folder in Dropbox based on a set of rules.
Shortcoming is that it doesn't allow to run the set of rules against more than one source folder.
I have currently defined the folder as ``` /Apps/Attachments ``` and set up a rule for .png, .jpg and .gif files to be moved to the ``` /Camera Uploads ``` folder.

## SendToDropbox
URL: https://sendtodropbox.com/account
Description: Free service, sets up an email address to send emails to for the attachments to be uploaded to an Attachments folder in your Dropbox folder ( ``` /Apps/Attachments ```, against which I run the SortMyBox service).
Very handy for a) your wife's phone which isn't linked to your Dropbox account, b) family events for example, just give out the email address for everybody to send you their pics.

## SortPhotos
Use [sortphotos](https://github.com/andrewning/sortphotos) to move photos from ``` /Camera Uploads ``` to main Photos folder (in sub folders with date in correct format), exact command is below. 

```
python sortphotos.py -c /home/mathieu/Documents/temp3/source /home/mathieu/Documents/temp3/target --sort %Y-%m-%d --rename %Y_%m%d_%H%M
```

Note: for fixing incorrect timestamps in the pictures' metadata(on Ubuntu), https://hvdwolf.github.io/pyExifToolGUI/

## Extra Steps
To finalize the worfklow, from time to time, I still need to:
* Manually delete pictures from phone(s) since they are automatically uploaded to Dropbox
* Manually run the sortphotos script to move and organize the pictures from the Camera Uploads folder to the main Pictures. Rather than run it manually, I can (and should) run this as a cron job on my server against the local Dropbox folders.


