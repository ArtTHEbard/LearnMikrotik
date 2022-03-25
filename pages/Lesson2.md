---
title: Lesson 2
---

LearnMikrotik
=====

# Lesson 2: Router Web Config
## Video
<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/Elex9l8WxUY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>

## Docs

## Using the MikroTik Web Client and WinBox Tools

### **Connecting to your Router**

The first step to configuring your new router is to connect to the Web Tool. 
* First, connect to the new Wifi signal. It should have MikroTik in the name, and end with "FB" or "FC". 
* Next, browse to 192.168.88.1 in a web browser. You will be met with a login. The default password can be found in the included instruction booklet that came with your router. 
![](https://github.com/ArtTHEbard/LearnMikrotik/blob/gh-pages/Login.png)
### Quick Set
![](https://github.com/ArtTHEbard/LearnMikrotik/blob/gh-pages/Quickset.png)
* After you login, select "Quick Set" from the top Menu. There are a few options to consider in this menu:
  * Wireless Protocol should be kept to 802.11.
  * The Network Name can be changed from the Network Name Field.
  * In the Security Box, check "WPA2".
  * Under Encryption, leave "aes ccm" checked. 
  * Use the Wifi Password field to set a strong Wifi Password. 
  * Under the Local Network Section, the IP of the configuration portal can be changed with the IP Address field. 
  * A local DHCP server can also be enabled or disabled. By default, it is enabled with a default range set. It is recommended to leave this setting alone unless there is a specific business related reason to change this. 
  * We will visit the VPN section in a later video. 
  * You can change the routers name with the Router Identity field. 
* Once you are finished making edits select the Apply Configuration button in the bottom right to save your settings. You may need to log back in after this step. 
## WebFig
![](https://github.com/ArtTHEbard/LearnMikrotik/blob/gh-pages/WebFig.png)
WebFig is the browser based tool Mikrotik uses to make configuration changes to its hardware. To access this, select WebFig in the top Menu. Within this section, there are quite a few important menus.  We will cover these in depth in future videos, but here we will give an overview of the most important ones. 
### Wireless
This menu gives an overview of the various wireless channels that the router is putting out. 
### Interfaces
This menu allows you to view the status of the individual wired and wireless interfaces available on the router. 
### System -> Auto Upgrade
This menu allows you to check for router firmware updates, and install any available updates. 
### System -> Certificates
This menu allows you to import certificates to allow for custom security options in your environment. This is an advanced option. 
### System -> Clock
This menu allows you to set the routers internal clock and timezone. 
### System -> Logging
This menu allows you to edit the routers logging preferences. 
### System -> Password
This menu allows you to change the login password for the web console. 
### System -> Reboot
This menu allows you to remotely reboot the router.
### System -> Reset Configuration
This menu allows you to reset all configurations on the router. 
### System -> Shutdown
This menu allows you to remotely shutdown the router. 
### System -> Users
This menu allows you to create new users. This will be covered in a future lesson, but it is HIGHLY advisable to create a new admin user to replace the system default user. 
### Log
This menu allows you to view all system logs the router has collected in terms of edits to configuration, connections, logins, and power information. 
### Tools
This submenu contains a list of tools to monitor and test your environment in various ways. This includes Flood Pings, Graphs, IP Scans, Netwatch, Packet Sniffers, Pings, TelNet, and more. This menu will be covered in a future video. 
## Winbox
![](https://github.com/ArtTHEbard/LearnMikrotik/blob/gh-pages/winbox.png)
The Winbox option will download a executable file to your desktop. Install the file to access Winbox, a local based program to access your router. 
* Use the same IP address used to access the browser WebFig in the Connect To field, and your user/password combo to log in. Hit Connect. 
* You will be able to access all of the menus available on WebFig locally through this program. Useful for monitoring/configuring multiple routers. 
  * NOTE: Winbox has had known issues running on MACOS. Recommended to use this utility on Windows.
