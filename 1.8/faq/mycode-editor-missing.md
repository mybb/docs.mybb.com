---
layout: page
title:  "Missing MyCode (BBCode) Editor"
categories: [faq]
---

## About Missing MyCode (BB Code) Editor Bug

Many MyBB software users report their MyBB editor is missing due to various reasons which I'll cover in this tutorial.
Before we start, we need to be sure that the MyBB editor is actually enabled on your account and for the entire
board.

To enable mycode editor for entire board: Go to Admin CP -> Configuration -> Settings -> Clickable Smilies and BB Code -> Clickable MyCode Editor` and tick **ON**

If the above setting is on but you still can't see the mycode editor **but** everyone else can then most likely you don't have it enabled through your User CP.

To enable it in your User CP, go to `User CP -> Edit Options -> Other Options` and tick **"Show the MyCode formatting options on the posting pages."**

Now if you have both the above settings enabled and you still can't see the mycode editor then you are most likely missing something. Below I'm going to present some solutions in order of most likely the cause of the issue.

### 1st Solution

**Skip this solution if you are not using Cloudflare.**

    Log in to your Cloudflare
    Edit Settings
    Click on Performance tab
    Disable Rocket Loader and/or Auto Minify

### 2nd Solution

Go to `Admin CP -> Templates & Styles -> Themes -> <Your theme> -> Editor Style` Change it to Office 2007

**If this solution works then it means that there's a problem with your editor theme files.**

### 3rd Solution

Reupload `jscripts_themes` folder in `.jscripts/jscripts_themes` and make sure you have a file called `editor.js` in `.jscripts`.

### 4th Solution

Download a fresh copy of MyBB from [MyBB Downloads](http://www.mybb.com/download/)

Then reupload the **codebuttons** folder in `.images` and `.images/themes`.

### 5th Solution

Go to `Admin CP -> Templates & Styles -> Templates -> <Your theme> -> Newthread` and `Admin CP -> Templates & Styles -> Templates -> <Your theme> -> Newreply`.

Make sure you have code `{codebuttons}` Right after `<textarea name="message" id="message" rows="20" cols="70" tabindex="2">{$message}</textarea>`.

### 6th Solution

*This solution is only valid if the editor went missing after you upgraded or downgraded your forum.*

Find updated templates for your current theme and revert them to original.

Go to `Admin CP -> Templates & Styles -> Templates -> Find Updated Templates`

### 7th Solution

Go to `Amdin CP -> Templates & Styles -> Templates -> <Your theme> -> Ungrouped Templates -> Headerinclude`

Add the following at the very end of your headerinclude template:
`<script type="text/javascript">jQuery.noConflict();</script>`

### 8th Solution

If the codebuttons are showing for you and only few members are unable to see it then you can run the following query to enable "Show the MyCode formatting options on the posting pages" for the whole board through this SQL query:

```php
UPDATE `mybb_users` SET `showcodebuttons` = '1' WHERE `showcodebuttons` = '0'
```
