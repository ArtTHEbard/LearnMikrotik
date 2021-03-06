---
title: Lesson 4
---

# Lesson 4

## LearnMikrotik

## Guest Wifi Portal Login

## Video

{% embed url="https://youtu.be/N859yOCmLeU" %}

## Docs

### Captive Wifi Portal

In this lesson, we are creating a captive wifi portal that guests will need to visit in order to connect to your guest wifi. This allows for the convience of having an open wifi network, while still securing your connection against unauthorized access.

#### Creating a Login Hotspot

* In the left hand bar, select IP.
* In the left dropdown menu, select Hotspot.
* Select the Servers tab from the top ribbon, and select the Hotspot setup button. Use the following settings:
  * Select the Guest-Bridge we made in the last guide for the Interface option.
  * Enter the local Guest address we created in the last guide (most likely 10.10.1.1)
  * For the Address Pool Section, ensure that the pool is prefilled with the local Guest Address pool (most likely 10.10.1.2-10.10.1.254)
  * Select None for Select Certificate.
  * Leave the SMTP server as 0.0.0.0.
  * In the DNS Servers menu, select the down arrow and type 8.8.8.8 in the field.
  * Enter Hotspot.Guest.Login for the DNS Name
  * Enter Guest for the name of the Local Hotspot User
    * Create a strong password to use as your Guest login password.
  * In the top ribbon, select USer Profiles. Select the new Guest User. Under the Shared User section, enter the amount of people you want to be able to connect to your wifif at once.
* Back in the main Servers tab, double click into the newly created Hotspot.
  * Under the DHCP pool field, select the address pool that is linked to your guest network.
* Finally, we need to remove the password from the guest network, as the login is now being moved to the captive portal rather than the initial Wifi connection.
  * Navigate to the Wireless menu on the left hand column. Select the Security Profiles tab from the top ribbon.
  * Select the Guest security profile from the options.
  * Under the Mode dropdown, select None.
  * Select Apply. The router may require you to log back in.
* After all this is complete, you should now have an open Guest Wifi network, that sends users to a login page after connection has occurred!
