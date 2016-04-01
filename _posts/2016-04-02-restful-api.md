---
layout: inner
position: right
title: 'restful api'
date: 2016-04-01 16:41:00
categories: development
tags: RESTFUL API
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'RESTFUL API'
---

# RESTFUL API

---

## API Address

	http://<web_site>/api/<resource>

## API Version

	Accept: application/vnd.tony.v1

## Header

	app_platform: android
	app_os_version: 5.0.1
	app_version: 1.0
	app_secret:
	access_token:

## Error
	
	400, 401, 403, 404 
	response:
	{
	    message: "error message"
	}

	422
	response:
	{
	    message: "error message",
	    errors: {
	        name: { message: "Name can not be empty." },
	        email: { message: "Invalid E-mail address." },
	        ...
	  }
	}

## Pages

	page 1
	per  20

## Resources

#### GET

	/Users

	200
	[
	    {
	        "id": 1,
	        "name": "Tony",
	        "email": "i@tony.wiki",
	        "avatar": "http://www.tony.wiki/avatar.jpg",
	        "created_at": "2016-04-01T19:12:34.448Z",
	        "updated_at": "2016-04-01T19:12:34.448Z"
	    },
	    ...
	]

#### GET

	/Users/{id}

	200
	{
	    "id": 1,
	    "name": "Tony"
	    "email": "i@tony.wiki"
	    "avatar": "http://www.tony.wiki/avatar.jpg"
	    "created_at": "2016-04-01T19:12:34.448Z",
	    "updated_at": "2016-04-01T19:12:34.448Z"
	}

#### DELETE

	/Users/{id}
	
	204 No Content


#### PUT

	/Users/{id}

	email=i@tony.wiki

	200
	{
	    "id": 1,
	    "name": "Tony"
	    "email": "i@tony.wiki"
	    "avatar": "http://www.tony.wiki/avatar.jpg"
	    "created_at": "2016-04-01T19:12:34.448Z",
	    "updated_at": "2016-04-01T19:12:34.448Z"
	}

#### POST

	/Users

	name=Tony
	email=i@tony.wiki
	avatar="http://www.tony.wiki/avatar.jpg"

	201 Created

