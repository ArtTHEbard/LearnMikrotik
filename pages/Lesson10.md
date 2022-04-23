---
title: Lesson 10
---

# Lesson 10

## Lesson 10

# LearnMikrotik

## Advanced Topic 2: VLANS & HTTPS Proxies
VLANS and HTTPS proxies are network tools that can be implemented to further segregate and partition your network for various tasks.
As networks grow larger and add more users and functions, seperation within the network becomes more and more important.

### VLANS
VLANS (Virtual Local Area Networks) are solutions for craeting a seperated network if your company is utilizing a seperate network switch.
Documentation about configuring VLANS is specific to the type and brand of switch being utilized by your network, so only the Mikrotik configuration details will be covered in this guide. 

* Navigate to the Interface menu option, and select the VLAN tab.
* Select "Add New"
* FIll out the important fields:
  * Give it a name.
  * Select the Interface that will service the VLAN. Set this to whatever port your network switch is plugged into
  * Give the VLAN a unique VLAN ID. This ID will be used to configure the VLAN ports on the switch. 
  * Leave a comment for organizational purposes. 

### Web Proxy Servers
Web Proxy Servers act as checkpoints for your network traffic as it comes and goes from certain areas of the network, or the network as a whole. These are useful for monitoring select network traffic, as well as establishing traffic rules unique to certain areas of the network. 

* Navigate to the IP > Web Proxy menu option. 
  * Check the enabled box.
  * Set the Source Address to be your forward facing address. 
  * Set max cache size to unlimited, and select the option to cache on disk. 
  * Select OK or Apply

* The next step is to make the proxy transparent. We do this so that users cannot know about proxy server and there will be no extra configuration to the user end. This specific proxy is going to redirect traffic leaving your network to the commonly attacked port 80 to a more easily controlled and monitored port 8080.
  * Go to IP > Firewall and click on NAT tab and then click PLUS SIGN (+) to add new  NAT rule.
  * In General tab, choose Chain = dstnat, Protocol = 6 (tcp) and Port = 80.
  * In Action tab, choose Action = redirect and To Port = 8080.
  * Now click Apply and OK button.

* The next step is to make our new proxy a non-open proxy. This will make it harder for hackers and other malicious actors to utilize the proxy to leverage access to your network. 
  * Go to IP > Firewall and open Filter Rules tab and then click on PLUS SIGN (+) to add new firewall rule.
  * In General tab, choose Chain = input, Address = 0.0.0.0/0, Protocol = 6 (tcp), Dst. Port = 8080, In Interface =       ether1 (WAN Interface Name).
  * In Action tab, choose Action = drop.

### Proxy Security Examples

* Finally, here are a few examples of how to utilize this web proxy to heighten your network controls. These following steps will allow you to block a certain website based on URL. 

* Block specifc website
  * Go to IP > Web Proxy and click on Access button from right side button panel. Web Proxy Access window will        appear. Now click on PLUS SIGN (+) to add new access rule. New Web Proxy Rule window will appear.
  * In this window, type facebook.com in Dst. Host input field and choose deny from Action drop-down menu.
  * Click Apply and OK button.

* Block specific file type downloads
  * Go to IP > Web Proxy and click on Access button from right side button panel. Web Proxy Access window will appear now. 
  * Now click on PLUS SIGN (+) to add new access rule. New Web Proxy Rule window will appear.
  * In this window, Type *.exe in Path input filed and choose deny from Action drop-down menu.
  * Click Apply and then OK button.
