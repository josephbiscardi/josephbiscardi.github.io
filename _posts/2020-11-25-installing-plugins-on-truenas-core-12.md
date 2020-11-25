---
title: 'Setting up Home Media Server on TrueNAS Core 12 using plugins'
date: 2020-11-25
permalink: /posts/2020/11/installing-plugins-on-truenas-core-12/
tags:
  - truenas
  - plex
  - media server
---


Prerequisites
-----
1. Plugins installed for Plex, Radarr/Sonarr, Jackett & Transmission
2. A working VPN connection that allows OpenVPN(PIA, NordVPN, etc)
3. SSH Access


Creating datasets 
-----
1. Create a dataset to hold your mount points on your jails, for example I named my set 'testmedia'. After, create data sets under your created data sets. I created 'radarr', 'sonarr', 'jackett' and 'transmission'. 
pic
2. Next, we want to set permissions to make sure the content is able to be read and writable. 
3. Click on 3 dots beside the first data set you created and click on 'Edit Permissions' 
pic
4. Once the permission window is open, click on 'Use ACL Manager' 
5. From the ACL Manager, create a Custom ACL and set the ACL list to use the user '971' with Full Control, Inherit, apply recursive set and apply to child data sets
pic
        *You can ignore the error about not finding the user '971' 

Plex 
-----
1. SSH into your TrueNAS and access the command line of your plex jail
```
iocage console [plex jail name]
```

2. Make a directory that will locally hold your content. I chose /media/data as my directory
```
mkdir /media/data
```
3. This new directory will need to have read/write permissions for the user and group 'plex' which should have been created during the plugin installation. 
To do this, you want to use the command chown -R plex:plex on the file path, so for my example /media/data. 
```
chown -R plex:plex /media/data/
```
4. To check the permissions, you can use ls -l on the your /media directory to check the permissions of the /data directory. 
```
ls -l /media/
```
pic
5. After you verified the permissions, stop the jail and open 'Mount Points' 
6. Add a new mount point that connects the transmission data set and your directory that was created in Step 2. 
pic
9. Lastly, navigate to the web gui http://JAIL_IP:32400 and go through the server setup
10. On the 'Media Library' section find your directory you created in step 2.

Transmission 
-----


Radarr
-----

Sonarr
-----


Jackett 
-----


