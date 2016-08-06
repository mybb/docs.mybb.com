---
layout: page
title:  "Plugins"
categories: [administration]
---

## Plugin System
MyBB has one of the most advanced plugin systems found in modern forum software. It takes only minutes to install plugins that can make MyBB suit your needs even better. The active and friendly [MyBB community](https://community.mybb.com) has developed a [large amount of plugins that are ready to use](https://community.mybb.com/forumdisplay.php?fid=102&sortby=lastpost&order=desc&datecut=9999&prefix=28); amongst them are plugins to show all unanswered threads, extend the forum statistics, show the permissions a user has in a forum, and more.

If a plugin you need doesn't already exist, then you can [post a plugin request in the MyBB Community Forums](https://community.mybb.com/forum-65.html), and perhaps someone will have the spare time to develop it for you.

## Installing Plugins
Most plugins will come with their own documentation on where the files included should go! If the mod does not come with documentation and contains a single php file then that file should be uploaded to `MyBB Root Folder/inc/plugins`.

If the plugin still lacks documentation on where the files go, but there are directories such as `jscripts`, `inc`, or `admin` at the root of the plugin download's folder, then upload the files within those directories to the respective folders of your MyBB installation.

If you then browse to `Admin Control Panel -> Configuration -> Plugins` you will see the plugin that you have recently uploaded listed. Click the Install or Activate links to install the plugin.

## Uninstalling Plugins
Uninstalling plugins has never been so easy! Simply navigate to `Admin Control Panel -> Configuration -> Plugins` and you will see either a Deactivate and/or Uninstall button. Click whichever one appears and your plugin will be uninstalled.

Note: When clicking `Uninstall`, database information stored by the plugin is often deleted. `Deactivate` usually just stops the plugin from displaying information and running on pages. It is important to know this distinction, as not knowing it could result in data loss.

If uninstalling the plugin permanantly, you should then delete all the files that you uploaded for this plugin to ensure that it is no longer part of your MyBB Installation. To find out what files the plugin included, download a new copy of the plugin from the [Extend site](https://community.mybb.com/mods.php).

## Reporting a Plugin
If you find that the plugin you are using contains a security exploit or any other severe issues which will affect other users (*please note that this does not include bugs or glitches that only affect the way the plugin operates*), browse to the [MyBB Extend site](https://community.mybb.com/mods.php), and browse to the plugin which you wish to report and click the Report link on the right and side and include as much detail as you can.

It is vital that you report the plugin, as it will ensure that any other MyBB sites do not encounter the same vulnerability or issue that you have.