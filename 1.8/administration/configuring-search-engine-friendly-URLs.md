---
layout: page
title:  "Configuring Search Engine Friendly URLs"
categories: [administration]

redirect_from:
- /SEF_URLs.html
---

MyBB 1.8 provides built-in support for Search Engine Friendly (SEF) URLs, which can aid in optimizing communities for search engine ranking.

# Requirements

* Apache HTTP server with mod_rewrite enabled **OR** nginx web server

* Apache: Access to server configuration **OR** ability to use `.htaccess` files to override configuration options.

* Nginx: Access to server configuration

# Setup

## Apache (includes cPanel)

1. In `MYBB_ROOT`, rename `htaccess.txt` (provided with all MyBB downloads) to `.htaccess`.
2. Navigate to your MyBB Admin Control Panel -> Configuration -> Server and Optimization Settings. Set `Enable search engine friendly URLs?` to `Enabled` or `Automatic Detection`.
3. Verify that you can browse to various forums and threads without errors.

## nginx

Configuring SEF URLs for an nginx server requires some knowledge of editing a much broader configuration file that controls everything served by the same virtual host.

1. Edit the configuration for the virtual host that serves your MyBB community, then add the following to the `location /` block, ensuring that occurrences of `MyBB` below are replaced with the directory of your MyBB installation, if necessary:

	```
	rewrite ^/MyBB/forum-([0-9]+)\.html$ /MyBB/forumdisplay.php?fid=$1;
	rewrite ^/MyBB/forum-([0-9]+)-page-([0-9]+)\.html$ /MyBB/forumdisplay.php?fid=$1&page=$2;
	rewrite ^/MyBB/thread-([0-9]+)\.html$ /MyBB/showthread.php?tid=$1;
	rewrite ^/MyBB/thread-([0-9]+)-page-([0-9]+)\.html$ /MyBB/showthread.php?tid=$1&page=$2;
	rewrite ^/MyBB/thread-([0-9]+)-lastpost\.html$ /MyBB/showthread.php?tid=$1&action=lastpost;
	rewrite ^/MyBB/thread-([0-9]+)-nextnewest\.html$ /MyBB/showthread.php?tid=$1&action=nextnewest;
	rewrite ^/MyBB/thread-([0-9]+)-nextoldest\.html$ /MyBB/showthread.php?tid=$1&action=nextoldest;
	rewrite ^/MyBB/thread-([0-9]+)-newpost\.html$ /MyBB/showthread.php?tid=$1&action=newpost;
	rewrite ^/MyBB/thread-([0-9]+)-post-([0-9]+)\.html$ /MyBB/showthread.php?tid=$1&pid=$2;

	rewrite ^/MyBB/post-([0-9]+)\.html$ /MyBB/showthread.php?pid=$1;

	rewrite ^/MyBB/announcement-([0-9]+)\.html$ /MyBB/announcements.php?aid=$1;

	rewrite ^/MyBB/user-([0-9]+)\.html$ /MyBB/member.php?action=profile&uid=$1;

	rewrite ^/MyBB/calendar-([0-9]+)\.html$ /MyBB/calendar.php?calendar=$1;
	rewrite ^/MyBB/calendar-([0-9]+)-year-([0-9]+)\.html$ /MyBB/calendar.php?action=yearview&calendar=$1&year=$2;
	rewrite ^/MyBB/calendar-([0-9]+)-year-([0-9]+)-month-([0-9]+)\.html$ /MyBB/calendar.php?calendar=$1&year=$2&month=$3;
	rewrite ^/MyBB/calendar-([0-9]+)-year-([0-9]+)-month-([0-9]+)-day-([0-9]+)\.html$ /MyBB/calendar.php?action=dayview&calendar=$1&year=$2&month=$3&day=$4;
	rewrite ^/MyBB/calendar-([0-9]+)-week-(n?[0-9]+)\.html$ /MyBB/calendar.php?action=weekview&calendar=$1&week=$2;

	rewrite ^/MyBB/event-([0-9]+)\.html$ /MyBB/calendar.php?action=event&eid=$1;
	```

2. Navigate to your MyBB Admin Control Panel -> Configuration -> Server and Optimization Settings. Set `Enable search engine friendly URLs?` to `Enabled` or `Automatic Detection`.
3. Verify that you can browse to various forums and threads without errors.

# Troubleshooting

If the above steps did not work, check your server error log (in cPanel: "Error Log" usually) for any log entries added at the time you tested the changes. Ask your web host for help, or create a support thread on the MyBB Community Forums.
