---
layout: page
title:  "Cannot Logout"
categories: [faq]
description: "Resolve issues with logging out from your forum."

redirect_from:
- /Help-Cannot_logout.html
---

# Unable to logout

Well, there are three main reasons for this.

The first two relate the following error when clicking the **Logout** link:

 - Your user ID could not be verified to log you out. This may have been because a malicious Javascript was attempting to log you out automatically. If you intended to logout, please click the Logout button at the top menu.

This means that your Logout link doesn't contain an SID and since MyBB 1.2.8, this is required. There are two possible reasons for this:

 1. The board has been updated to a newer version of MyBB but some template information hasn't been updated.
 2. You are using a template designed for a version of MyBB older than 1.2.8 and as such, the logout link is also missing the SID component.

A fix for both of these issues can be found by following the instructions [here](https://community.mybb.com/showthread.php?tid=25210&pid=177101#pid177101) to manually update your templates' Logout link to contain the SID. Note: You will need to do this for every theme that you use on your forum which does not currently contain an SID link.

If after making the above changes you are still unable to logout and are running MyBB 1.2.10. Please try the following:

The third reason could relate to your cookie settings. Either, the Cookie settings for a forum have been changed so that they no longer correspond to the cookies you have stored so that when you click logout, MyBB is attempting to remove cookies which don't exist.

Or, you have some cookies remaining from a previous session (when the Cookie settings were different) and also a set of cookies for this session (with the new cookie settings). In this case, MyBB will clear your new cookies, but not the old ones so you will appear unable to logout.

Please see [Login Problems](/1.8/faq/login/) or [Cookies](/1.8/development/cookies/) to find your correct cookie settings.

In both situations, the best solution is to clear the cookies in your browser.
