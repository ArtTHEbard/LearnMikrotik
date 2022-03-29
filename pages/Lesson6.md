---
title: Lesson 6
---

LearnMikrotik
=====

# Lesson 6 VPN
## Video
<p aling="center">
 <iframe width="560" height="315" src="https://www.youtube.com/embed/_KUUNUF6wV4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>

## Docs

Having access to a virtual private network allows for secure and safe connections to your network from a remote location. THis is a great way to monitor and manage your router and network from anywhere. Having the option to set up multiple different VPNs give you the freedom of choice to match your needs and configuration. 
***
# Configure OpenVPN Server and Client Config on Mikrotik
##  OpenVPN Server Configuration in MikroTik Router 
The first step is to configure the Server side of OpenVPN. This involves creating TLS Certs, enabling and configuring The server and then creating the OpenVPN users. This will be broken down into the following three steps.

***
## Creating TLS Certs for CA, Server and Client

### CA Cert
* Navigate to the systems menu on the left hand side, and select the "Certificates" menu.
* Select add new certificate (this may be a + sign in some versions)
* Create the CA cert this will be for your certificate authority.
 * Fill out the fields in general being sure to accurately fill in the information about country,State,Locality,Organization and unit. This information will need to match in all of your certs. The Name and common name will be what the certificate is saved as.
 * In the Key Usage tab ensure that only the CRL sign and key cert sign are selected.
 * Once those setting are completed select the sign button and emsure the the CA is selected in the Certificate drop down and the CA CRL host is set to the address of the Mikrotik routers public address.
 * Select the Start button to sign the cert with your CA
* You should now be able to see your CA Cert in the Certificate tab

### Server Cert
* To create the Server Certificate add a new cert form the same menu used for the CA cert.
* Name this cert Server and ensure all of the information matches the CA cert.
* In the Key Usage tab ensure that only the Digital signature, Key enciphement and the TLS server options are selected.
* Select the Sign button and ensure that Server is selected in the Certificate drop down, CA should be selected in the CA tab and no address should be in the CA CRL host menu.
* Select the start button to sign the server Cert.
* You should now be able to see your Server Cert in the Certificate tab

### Client Cert
* To create the Client Certificate add a new cert form the same menu used for the other certs.
* Name this cert Client and fill out the information to match the other certs.
* In the Key Usage tab ensure that only TLS client is selected.
* Select the Sign button and ensure that Client is selected in the Certificate drop down, CA should be selected in the CA tab and no address should be in the CA CRL host menu.
* Select the start button to sign the server Cert.
* You should now be able to see your Client Cert in the Certificate tab

### Exporting Certs

* To export the certs you need to open each cert and select export.
* The exported certs can now be found in the file section located on the left menu select. 
* From here you want to download the cert_export_CA.crt, cert_export_Client.crt and cert_export_Client.key
* Locate these files and note it for later. It will most likely be in downloads.

***
## Enabling and configuring OpenVPN

* On the left menu select PPP then select the interface tab.
* Select the OVPN Server button. from here you can configure and enable your OpenVPN server.
* Enable OpenVPN by ensuring the enable checkbox is marked at the top of the page.
* We set the port to 443 and ensure that mode was set to IP.
* Next we made sure that the Certificate drop down was pointed the Server and the Require Client Certificate box was selected.
* in the Auth section we selected only sha1 and for cipher we selected only aes256
* Once you select OK your OpenVPN server will be up but we still need to configure users and addresses for it to use.

***
## Setting up OpenVPN Address Pools, and Users

### IP Pool Configuration

* As we did in a previous lesson we will be making a new address pool specifically for the VPN users.
* Navigate to IP menu on the left side  and then to the pool tab.
* Select add new pool set the desired name and address pool. For ours we name it VPN_pool and used a different IP address to distinguish it from local traffic. 

### Creating User Profile

* In the left menu  select PPP and then select the profile tab.
* Create a new profile and name it vpn_profile and set its local adress to the vpn_pool we previously created the Local address will need to be the gateway for the vpn_pool set of addresses. 
* Click apply and then OK

### User configuration

* In the PPP menu select the secrets tab and then add a new secret.This new secret will be the VPN User.
* Name the user and add a password, in Services select ovpn and in profile select vpn_profile.
* If you wish to create more users you can do so here.

***
## Configuring OpenVPN for Client computer

### Installing OpenVPN

* To install OpenVPN you need to go to OpenVPNS website and download the OpenVPN installer.
* Ensure you are downloading the correct installer for your operating system.

### Configuring OpenVPN

* Go to the file location for open VPN using file explorer. It should be located in C:\Program Files\OpenVPN
* From here go into sample config and coppy the client configuration file to config and open it using the text editor of your choice, we use notepad. it also needs to be opened using admin mode to save changes.
* From here you need to edit the presets and rename the file to match your settings.
* This is the config file we [used](https://github.com/ArtTHEbard/LearnMikrotik/blob/gh-pages/client%20config.txt) .
* You also need to move the certs that were exported earlier into the configuration file.
* Once this is setup you will be able to use the connect function on OpenVPN to connect to the VPN this will be located in the bottom right on windows.


# SSTP VPN Setup
***

## Configuring and enabling SSTP Server

* This will use the created in the OpenVPN portion of this guide.
* Go to the PPP menu and from there select the interface tab.
* Click the SSTP Server button this will bring you to the configuration and enabling menu.
* Ensure the enable box is checked, ennsure the TCP Port 443 is assigned in the port field, set authentication to on mschap2, Certificate menu should point to Server, set the TLS version to "only-1.2" , uncheck verify client cert, check Force AES and PFS.
* Hit apply and OK and your SSTP server will be up and running with those configurations.
* To create users for this you can do the same thing as above however set the service to sstp.

## SSTP Client Configuration

* On the left side menu select the Interface menu.
* Select the add new button and click SSTP client.
* In the General tab enter your desired name.
* Moved to the Dial out tab and enter the routers public address in the "Connect To" option.
* Port should be set to 443, ensure Verify Server Address from Certificate box is checked as well as PFS, Enter the Username and password for the user you wish to use SSTP, Ensuer only mschap2 is allowed then hit apply and OK.
* SSTP is not up an drunning and you can see the connection in the PPP menu under Active Connections.

# Zero Tier
***

## Registering and Creating a Zero tier Network

* Go to my.zerotier.com and register an account.
* Select the Create A Network button, locate the Network ID for later

## Downloading Zero tier 

* In the System menu and go into the packages tab and select check for updates and ensure your channel is se tot development.
* Now to go mikrotik.com/download and download the extra packages for the 7.2rc4 testing version.
* Unzip the package and extract the zerotier.npk file now go into the files menu and upload that file.
* Reboot your router and you will be able to see the zero tier package.
* We are going to be using the CLI terminal to complete the rest of this setup.

## Installing and Configuring Zero tier

* in the top right select the button that says terminal and enter the following commands.
* "zerotier/enable zt1"
* " zerotier/interface/add network=1d7193940(set this to your ID from earlier)4912b40 instance=zt1 "
* "zerotier/interface/print" This command will verify that it is running.
* These next two commands allow this zerotier through the firewall
* "add action=accept chain=forward in-interface=zerotier1 place-before=0"
* "add action=accept chain=input in-interface=zerotier1 place-before=0"

## Join Computer to  Zero tier

* On the Zerotier website go to download and download it for your desired device.
* Run the installer and open the program.
* Enter your network ID into the join network option and click join network. 
*  On the Zerotier website you can now authorize the new device.

