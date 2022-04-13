---
title: Lesson 8
---

# Lesson 8

## LearnMikrotik

## Backups

## Video

{% embed url="https://youtu.be/AEkNWoLNmDY" %}

## Docs

In this lesson, Connor and I go over the backup capabilities of the Mikrotik routers. The router offers both traditional backups as well as cloud backup capabilities. Due to the options for backups with the router, there is no reason why backups should not be made of router configurations. This safeguard prevents against data loss or theft, while also allowing you to switch between hardware and retain your settings. A intro to Mikrotik logging is also touched upon in the video, however, the extensive documentation for logging capabilities on the devices will be saved for a dedicated video.

### Working with Backups.

Navigate to the Files tab in the WebConfig, Winbox, or the mobile app.

Select the Backup option. Fill in the required fields with a name, encryption method, and password.

When you see the new backup in the list of files, select Download to save the backup to your local computer.

To restore a backup, select the backup from the file list and hit restore. If on new hardware, your downloaded backup will need to be uploaded to the router using the upload file button.

In order to utilize Cloud backups, select the Cloud Backup tab, and select Upload Backups. You can choose to either take a new backup or upload one from the file storage. Using cloud backups allows for the saving of space on the router, as well as protecting from physical damage or theft. The backups are stored in Mikrotik's private datacenter in Latvia, and is not distributed to third parties for storage. Still, take this into consideration before utilizing the Cloud backup solution. Restore backups from the cloud using the same method as local backups.
