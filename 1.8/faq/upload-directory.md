---
layout: page
title:  "Upload Directory"
categories: [faq]
---

## Upload directory

When uploading your forum data to your webserver, you may have accidentally uploaded the actual "Upload" directory instead of just uploading the contents of that directory. While there is nothing wrong with this, it does give you a strange looking URL, and on Linux webservers, can cause unexpected 404 errors due to the directory name having an uppercase U, and most users typing URLs in pure lowercase.

### This page will guide you through removing this extra directory from your forum URL; there are two sections:
* The first is for if you have not yet installed MyBB.
* The second is for if you have installed MyBB, but would now like to remove the directory.

#### Since your MyBB forum has not yet been installed, the process for removing the directory is simple:

* Using your FTP client, select the contents of the "Upload" directory you uploaded previously.
* With the contents selected, drag this selection onto the directory you want the contents to appear in, generally this will be the directory above the "Upload" directory.
* Just wait for the files to move and then delete the now empty "Upload" directory from your webserver.
* You can now proceed to install your MyBB forum.

#### Because your MyBB forum has been installed, there are a few extra steps that must be completed. The process is still relatively simple:

* Go to your forum's Admin Control Panel and set your "Board Closed" setting to "Yes".
* Using your FTP client, select the contents of the "Upload" directory you uploaded previously.
* With the contents selected, drag this selection onto the directory you want the contents to appear in, generally this will be the directory above the "Upload" directory.
* Wait for the files to move and then delete the now empty "Upload" directory from your webserver.
* With this done, go back to your forum's Admin Control Panel (using your new URL - your old URL without the "Upload" part) and set your "Board URL" to reflect the new url. You may also have to change your cookie settings depending on how they were previously set-up.
* With that done you can now set your forum's "Board Closed" setting back to "No".
