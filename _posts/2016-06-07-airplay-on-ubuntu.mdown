---
layout: inner
position: right
title: 'AirPlay On Ubuntu 16.04'
date: 2016-06-07 01:39:00
categories: development
tags: airplay
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'airplay'
---

# AirPlay On Ubuntu 16.04

---

## install

	sudo apt-get install libssl-dev libavahi-client-dev libasound2-dev
	sudo apt-get install avahi-daemon
	sudo apt-get install alsa-utils
	sudo add-apt-repository ppa:dantheperson/shairplay-sync # Ubuntu 16.04
	sudo apt-get install shairport-sync

## config

	sudo vi /etc/shairport-sync.conf

## up service
	
	service shairport-sync start/stop/restart/status

## about
	
	https://github.com/abrasive/shairport
	https://github.com/mikebrady/shairport-sync
	https://launchpad.net/~dantheperson/+archive/ubuntu/shairplay-sync