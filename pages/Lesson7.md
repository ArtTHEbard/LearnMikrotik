---
title: Lesson 7
---

LearnMikrotik
=====
# SSH Connect
# Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/whm-gAMj7tg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Docs

## Connecting to MikroTik Using SSH
### Step 1: Install Putty
In order to connect to your Mikrotik device using SSH, we need to use Putty. This is a software that utilizes SSH to establish remote terminal sessions. It can be downloaded [here.](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

### Step 2: Generate Keys
Once Putty is installed, search for Putty in your Windwos Search bar, and select the PuttyGen. Select the Generate Key Option. Once the key is generated, set a passcode, and select both the Save Private and Save Public key options. 

### Step 3: Upload keys to Microtik
Once your keys are made, head over to the Mikrotik Webconfig, and select the Files option. Select Upload File, and upload the PUBLIC KEY that you have just made. NOTE: THIS IS VERY IMPORTANT. NEVER SHARE YOUR PRIVATE KEY WITH ANYONE. EVER. 
Once the key is uploaded, navigate to System>Users>SSH Keys and select Import SSH key. Choose one of your created users to attach the key to, in the video we cchose the default admin user but it is recommended to have a seperate and distinct SSH user, select the uploaded public key from the dropdown menu, enter your password if you set one, and hit Import. Once this is done, a new listing showing this info will appear in the SSH Keys menu. 

### Step 4: Connect Using SSH. 
Open the normal Putty application. In the side menu, select Connections> SSH > Auth, and in the Private Key box, select the private key you created. Now, use Putty to connect to your MikroTik router at the IP address you normally connect to the Webconfig with. If everything worked, the connection should authenticate with the SSH keys, and not require a password. 

### Step 5: Disable all unneeded services. 
Another good practicve to employ in this situation is to disable any service on your router that isnt needed in your enviroment. This can be done by selecting the IP > Services menu in the Mikrotik Webconfig, and browsing the list of services shown for ones that arent needed. One example of an unneeded service is telnet, unless your network has a specific use for it.  Disable these services by selecting the "D" button next to their names. 
