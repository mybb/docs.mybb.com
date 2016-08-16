---
layout: page
title: "Using a CDN with MyBB"
categories: [faq]
description: "Guide on setting up MyBB to pull static files from the CDN of your choice."
---

MyBB 1.8 brings built-in CDN compatibility to MyBB for the first time. This feature allows the loading of static files such as JavaScript, CSS, and images from a CDN of your choice. In this tutorial, we will guide you through the basic setup steps.

Note: Only the basic "pull" type CDNs are supported as of the time this guide was written.

# Setting up your domains/subdomains
When setting up a CDN, you will want to choose a subdomain to use. In the case of this tutorial, we used "s.mybbstuff.com". All the files for this subdomain live in the following path: `/home/euan/webapps/s_mybbstuff_com/`.

Once you have created this subdomain, you should copy your current static files to it. Below is a list of the folders/files you will need to copy across in a default installation of MyBB:

- cache/themes/*
- images/*
- uploads/*
- jscripts/*

# Configuring your CDN
Once these files are copied over, you should now be able to access stylesheets from the specified domain, with this done it is now time to configure your actual CDN. You should pick a provider that you prefer and trust (a list of some are listed below); however for the purposes of this tutorial, we are using "cdn.net".

Once you have signed up for an account with your provider you will need to set up a zone or package.
This is how ours was configured:
![alt text](/assets/images/1.8/cdn-config.png "MyBB CDN settings")

The resource type should be of "pull" type and the origin should be the subdomain we configured earlier (s.mybbstuff.com in my case). You can use any CDN hostname that you desire - most CDN providers will actually give you a subdomain of theirs if you do not wish to configure CNAME DNS records and such. I chose to use cdn.mybbstuff.com just because it looks good.

# Setting up MyBB to use the CDN
Now that our CDN is configured, it's time to change our MyBB settings to make use of it.
Log into your Admin Control Panel and select `Configuration > Settings > Server and Optimization Options`. You will see the CDN settings near the bottom of the page, and can change the settings to suit your needs. In the case of this tutorial, our settings looked like this:

- Use a CDN?: Yes
- URL to use for static files: This is the CDN hostname that you configured in step two. In my case, it is http://cdn.mybbstuff.com
- Path to store static files: This is the path to the subdomain that we set up earlier for static files to be stored. All uploads and stylesheets will be saved here from now on. In my case, the path is "/home/euan/webapps/s_mybbstuff_com"

Once configured, save your settings then reload the forum home page. All of your images, stylesheets and JavaScripts should now be loading from a CDN.
