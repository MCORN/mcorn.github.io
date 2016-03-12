---
title: Setting up a PPTP server on DD-WRT
updated: 2016-03-12 18:02
---

Very easy to set-up and quite a few [tutorials](http://www.howtogeek.com/51772/how-to-setup-a-vpn-server-using-a-dd-wrt-router/) on the internet but the Server IP and Client IP settings puzzled me for a while so adding this as a reminder.
Here is my set-up:

![](/assets/attachments/DD-WRT-PPTPServer.png)

The Server IP and Client IP combination determines what you will be able to do once logged to the VPN (without going into having to set up routes).

* If you set the Server IP to the original address of the router on the LAN (in my case, 192.168.1.1), once logged to the VPN, you will be able to access the router and that's it.
* If you set Server IP and Client IP to another subnet (for example 192.168.111.1), you will have access to the LAN but not the WAN.
* If you set Server ID and Client IP to the same subnet than your LAN (although you have to set those addresses to a range than can't be attributed via DHCP), then you will have access to both LAN and WAN.