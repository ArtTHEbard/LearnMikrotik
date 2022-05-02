---
title: Virtual Machine Setup
---

# Virtual Machine Setup

## LearnMikrotik

## Virtual Machine Setup
In case your buisness does not yet have their Mikrotik router, or rather you want to dive into our guides to see if Mikrotik is for you, then this guide will go over how to
create your own virtual version of a Mikrotik router.  

## VMWare Player
The first step is to obtain software to support a virtual machine. We recommend VMWare Player.
* Select this link to download the VirutalBox installer: [VirtualBox](https://customerconnect.vmware.com/en/downloads/details?downloadGroup=WKST-PLAYER-1623-NEW&productId=1039&rPId=85399#product_downloads)
* Once the file is finished downloading, run it to install VirtualBox.
* Select next through the various menus, and install the program. 

## Mikrotik RouterOS VM Image
The next step is to obtain the files required to run a Mikrotik VM. 
* Grab the RouterOS image from this link: [RouterOS](https://download.mikrotik.com/routeros/7.2.2/chr-7.2.2.ova)

## Create the VM
* In VMWare Player, Select New from the main menu. Select I will install the operating system later. 
  * for Type, select "Other/Other"
  * Enter "Mikrotik" for the Name.
  * Set Max Disk Size to 4GB.
  * For Hard Disk, select "Use an existing virtual hard disk file"
    * In the next menu, select the "Add" option.
  * Select "Create".
* With the New VM created, select the Edit VM button. 
* Select the Add button
  * Select "Hard Disk"
  * Select IDE
  * Select Use Existing Virtual Disk
  * Select the VMDK you downloaded.
  * If there is a popup asking to convert the image, select convert.
  * Select the Hard Disk 1 entry in the list of devices, and select Remove. 
* Power on the VM by selecting the Run button. 
* Wait for the system to finish loading. 
* 
