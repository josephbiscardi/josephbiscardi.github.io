---
title: 'Setting up Home Media Server on TrueNAS Core 12 using plugins'
date: 2020-11-25
permalink: /posts/2020/11/installing-plugins-on-truenas-core-12/
tags:
  - truenas
  - plex
  - media server
---



Setting up Home Media Server on TrueNAS Core 12 using plugins
======

Prerequisites
======
1. Plugins installed for Plex, Radarr/Sonarr, Jackett & Transmission
2. A working VPN connection that allows OpenVPN(PIA, NordVPN, etc)
3. SSH Access


Creating datasets 
------
1. Create a dataset to hold your mount points on your jails, for example I named my set 'media'. After, create data sets under your created data sets. I created 'radarr', 'sonarr', 'jackett' and 'transmission'. You can leave these as is or create additional data sets to go under the different sets we created.
![Media Dataset](https://raw.githubusercontent.com/josephbiscardi/josephbiscardi.github.io/master/images/chrome_MTc46Z4LT3.png)
2. Next, we want to set permissions to make sure the content is able to be read and writable. 
3. Click on 3 dots beside the first data set you created and click on 'Edit Permissions' 
4. Once the permission window is open, click on 'Use ACL Manager' 
5. From the ACL Manager, create a Custom ACL and set the ACL list to use the user '972' with Full Control, Inherit and apply recursive set 
------
Plex 
======
1. SSH into your TrueNAS and use the command iocage console [plex jail name] to access the command line of your plex jail
------
2. Make a directory that will locally hold your content. use mkdir to create these folders(eg. mkdir /media/data)
3. This new directory will need to have read/write permissions for the user and group 'plex' which should have been created during the plugin installation. 
To do this, you want to use the command chown -R plex:plex on the file path, so for my example /media/data
-------
4. To check the permissions, you can use ls -l on the file path
----
5. 
