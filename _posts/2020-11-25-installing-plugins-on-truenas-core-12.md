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
1. Create a dataset to hold your mount points on your jails. I created a media dataset and sub data sets for jackett, transmission, radarr and sonarr
[](chrome_MTc46Z4LT3.png)
