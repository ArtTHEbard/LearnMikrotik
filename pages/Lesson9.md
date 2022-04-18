---
title: Lesson 9
---

# Lesson 9

## Lesson 9

### LearnMikrotik

## Advanced topic 1 logging and filtering

### Video

{% embed url="https://youtu.be/cWHV4IYaB1w" %}

### Docs

In this video Sam will be going over logging and filtering. He will be demonstrating how to create a firewall rule that will allow you to filter and monitor indiviudal devices on your network. This video is more open ended with an example of one way to set filters and logs. The technique shown can be used in a variety of ways and we hope you take the time to explore the possibilities for logging and filtering your network. We suggest that the logging and filtering rules be tested as you can quickly create a very large amount of data.

#### Creating a filter rule

* To create a filter rule you need to go into IP and then select firewall on in the left side.
* Create a new firewall rule for our example we are logging all new tcp connections directed towards port 80 and 443.
* to do this we selected, Chain = Forward, Protocol = 6(TCP), DST.Port to 443 and 80, Connection State select new and at the bottom ensure the action is set to logging and give it a description.
* This can be enable and disabled in the firewall rules menu. 


#### Creating USB Storage for Logs

* Step one will be to physically plug a USB in your router.
* Next in your Mikrotik dashboard go into systems and disk on the left side from here look for the name of the device you plugged in. 
* The next step is to go into terminal and input the following command. /system logging action add name=usb target=thenameofdiskfromabovestep disk-file-name=thenameofdiskfromabovestep/log and press enter.
* You will need to mae sure your names are correct and that you may need to format your device to fat32.
* Now go to system then logging, select actions and select your action for weblogging and change filename to your added disk.


