I have 2 small kids and 2 old identical laptops...

# OS - Lubuntu
[https://lubuntu.net/downloads/]
Why? Because it is derived from Ubuntu, which I am familiar with and because it is light enough to be usable on the hardware. I had to add the forcepae flag to the command for it to install all the same, see Workaround 4 at [https://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present] for reference.

# User access
Because no kids wants to have to type in a password, I created during the installation my own user (password protected), which I log in with, and create a Desktop User level user for each kid, with no password required at login. Now with Lubuntu 18.04, there isn't a UI to allow automatic login so I followed the work-around detailled at [https://askubuntu.com/questions/967837/how-to-enable-autologin-on-lubuntu-16-04-lts-lightdm] to make it happen.
Also, the laptop will be connecting to the wifi (and I don't want the kids to be required to enter a password) so I connect to the wifi under my own, make sure under Wifi Security that it is accessible to all users and make the required changes under IPv4 settings to proxy through OpenDNS (with which I have set-up a kids friendly profile), see [https://support.opendns.com/hc/en-us/articles/228007087-Ubuntu].

# Internet and YouTube access
So Internet access should already be restricted with OpenDNS, but I also install `Enforce SafeSearch` [https://addons.mozilla.org/en-US/firefox/addon/sas/], the default browser being Firefox to be doubly sure, and then for YouTube specifically turn on the Parental Controls as highlighted (here)[https://www.kidguard.com/cell-phone-monitoring-and-gps-tracking/how-to-setup-parental-controls-on-youtube-on-browser-iphone-and-android/].
