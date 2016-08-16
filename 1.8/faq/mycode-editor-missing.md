---
layout: page
title:  "Missing MyCode (BBCode) Editor"
categories: [faq]
description: "Common solutions for when the MyBB editor is not showing."
---

## About Missing MyCode (BBCode) Editor Bug

Many MyBB users report their MyBB editor is missing due to various reasons which we'll cover here.

Before we start, we need to be sure that the MyBB editor is actually enabled on your account and for the entire board.

To enable the MyCode editor for the entire board: Go to `Admin CP -> Configuration -> Settings -> Clickable Smilies and BB Code -> Clickable MyCode Editor` and tick **ON**

If the above setting is on but you still can't see the MyCode editor **but** everyone else can, then you most likely don't have it enabled through your User CP.

To enable it in your User CP, go to `User CP -> Edit Options -> Other Options` and tick **"Show the MyCode formatting options on the posting pages."**

Now if you have both settings enabled and you still can't see the MyCode editor, then you are most likely missing something. Below are some additional problems/solutions, ordered by most likely to cause or fix the issue, respectively.

### CloudFlare

**Skip this solution if you are not using CloudFlare.**

    Log in to your CloudFlare dashboard
    Edit Settings
    Click on Performance tab
    Disable Rocket Loader and/or Auto Minify

### Theme Editor Style

Go to `Admin CP -> Templates & Styles -> Themes -> <Your theme> -> Editor style` Change it to *Office*

**If this solution works, then it means that there's a problem with your editor theme files.**

### Reupload SCEditor

Reupload the entire `sceditor` folder to `jscripts/sceditor`.

### Fourth Solution (Template Issue)

Go to `Admin CP -> Templates & Styles -> Templates -> <Your theme> -> New Thread Templates -> newthread` and `Admin CP -> Templates & Styles -> Templates -> <Your theme> -> New Reply Templates -> newreply`.

Make sure you have `{$codebuttons}` right after `<textarea id="message" name="message" rows="20" cols="70" tabindex="2" >{$message}</textarea>` in newreply template and right after `<textarea name="message" id="message" rows="20" cols="70" tabindex="2">{$message}</textarea>` in newthread template.

### Revert Templates

*This solution is only valid if the editor went missing after you upgraded or downgraded your forum.*

Find updated templates for your current theme and revert them to original.

Go to `Admin CP -> Templates & Styles -> Templates -> Find Updated Templates`

### SQL Query to Force Re-Enable the Editor for All Users

If the codebuttons are showing for you and only few members are unable to see it, then you can run the following query to enable "Show the MyCode formatting options on the posting pages" for the whole board through this SQL query:

```php
UPDATE `mybb_users` SET `showcodebuttons` = '1' WHERE `showcodebuttons` = '0'
```
** Note: Make sure you back up your database before running any SQL queries manually.**

** Make sure to change the `mybb_` table prefix in the example to whatever your table prefix is.**
