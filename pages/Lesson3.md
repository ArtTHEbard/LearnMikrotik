---
title: Lesson 3
---

LearnMikrotik
=====

# Lesson 3: Secure Guest Wifi
## Video
<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/tQ1rX45prKc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>

# Docs

***
## Setting up a Guest Network
### Security Profile
The first step is to create a custom set of settings, referred to as a security profile, that will manage how your network is protected, as well as how it is accessed. 
* Navigate to the Wireless menu on the left hand side, and select the "Security Profiles" tab from the top ribbon.
* Select "Add New": and use the following options:
  * Enter a name for the new security profile, we recommend "Guest".
  * Under Authentication Types, UNSELECT "WPA-PSK", ensure that the only option selected is "WPA2-PSK".
  * In the red box labeled "WPA2-PSK Preshared Key", enter your desired password for the guest network you are creating. We recommend passwords that are at least 8 characters in length, with at least one numerical (1,2,3,etc) and one special character (!,@,#,etc). 
  * Optionally, add a comment for organization.
  * Hit Apply at the top of the page.

### Creating a new WIFI Network
The next step is to create a new WIFI network for guests to use. 
* Still under the Wireless menu, select the Wireless Interfaces tab from the top ribbon. 
* Select "Add New", and in the dropdown menu select "Virtual". Use the following options. 
  * Under name, enter a name for your network. We recommend "Guest" or something similar.
  * Scroll down to the Wireless subsection, and select the "SSID" toggle arrow. 
    * Enter the same name you chose from the Name field. 
  * Under the "Master Interface" dropdown menu, select "wlan 2". 
  * Under the "Security Profile" dropdown menu, select the name of the security profile you created earlier in this guide. 
  * Hit Apply at the top of the page. 

### Create a new bridge
Our next step is to create a separate wireless bridge. A "bridge" is a networking term for the router function that gives devices connected to your network the ability to connect to the internet. For security purposes, we want your guest network to be completely separate from your private network, so this step is necessary for added security.
* Navigate to the Bridge option from the left hand column. 
* Under the Bridge tab in the top ribbon, Select the Add New button. Use the following configuration options. 
  * Enter a name. We recommend "Guest-Bridge" for organizational purposes. 
  * Hit Apply at the top of the page. 
* Move to the Port tab in the top ribbon. Hit Add New. Use the following options. 
  * In the Interface field, ensure that your Guest Wifi is selected. 
  * In the Bridge field, ensure that your Guest Bridge is selected. 
  * Hit Apply and Ok at the top of the page. 

### Setting up a Guest IP block
Our next step is to create a special block of network addresses for your guests to use. This is continuing the trend of complete separation of guest and private networks. 
* Navigate to the IP menu on the left hand column. In the drop down menu that appears, select Addresses. 
* Select Add New. Use the following Options. 
  * Under the Addresses field, enter "10.10.1.1/24"
  * Under the Interface drop down, select the Guest bridge we created. 
  * Make a comment in the Comments field labeling this range as the Guest IP Range. 

### Create a DHCP server
Our next step is to create a dedicated service to provide DHCP to the guest network. DHCP (Dynamic Host Configuration Protocol) is the service that automatically assigns addresses to devices connecting to your network. Having a guest DHCP server ensures that guests cannot obtain addresses belonging to your private network. 
* Navigate to the DHCP Server menu in the left hand column. 
* Select the DHCP Setup button. Use the following settings. 
  * For the DHCP Interface, select the Guest Bridge you created. 
  * Hit Next. 
  * Ensure your DHCP address Space matches the range you created earlier in this guide. 
  * For the Gateway for DHCP Network filed, enter "10.10.1.1".
  * Hit Next three times. 
* Your new DHCP server has been created. Double-click it in the list shown (likely named dhcp1), and rename it to "Guest-DHCP".

### Create Firewall Rules
Now we will create some security rules for the guest network to prevent it from connecting to your private network space. 
* Navigate to the IP menu on the left column.
* Select the Firewall menu in the drop down under IP in the left column.
* Select the Add Rule button. Use the following options. 
  * In the SRC.Address field, enter "10.10.1.0/24". This should be the guest network adderess. 
  * In the DST.Address field, enter "192.168.88.0/24". This should be your private network address. 
  * Near the bottom, select Action, and in the drop down menu that appears, select Drop. 
  * Add a comment noting this as a Guest Wifi Firewall Rule, for organizational purposes. 
* Back in the main Filter Rules tab, locate the new firewall rule you created, and click and drag the rule up to position six, just below the rule labeled "Drop all not coming from LAN".
  * If you have added other firewall rules, this positioning may look different for you. 

***
