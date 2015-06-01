---
layout: page
title:  "Protecting Your MyBB Forum"
categories: [security]
---

## MyBB Updates

One thing we cannot stress enough is to always have your MyBB installation up to date. If you are running an older version, you are open to security vulnerabilities that were already fixed. MyBB takes security very seriously. Whenever a security vulnerability is reported it is patched very quickly and a new release is sent out. You should never skip upgrading, as you will be opening yourself to a security risk that hackers can easily take advantage of.

## Fine Tuning the Admin CP

The Admin CP is the most powerful tool in MyBB. If anyone gains access to it, they can easily deface your forum and get complete control over it. It is therefore important to guarantee that only you or your administrators can access it. For starters you should [rename your Admin CP directory and hide all links to it](http://www.mybbsecurity.net/topic-renaming-the-administrator-directory). Once you have done that it is a good idea to install [Admin CP Honeypot](http://community.mybb.com/thread-94406.html). This will take your previous Admin CP location and install a fake Admin CP, which will record the IP of anyone who tries to login to it and email you a small report.

Now your real Admin CP directory should look something like `Svt06wbowXgMVvFmkFaz` (which you should bookmark or take note of) and the fake Admin CP will be located at `admin` (which will record the details of anyone who tries to access it). To finalize, [you should password protect your real Admin CP with HTTP Basic Auth](http://www.mybbsecurity.net/topic-protecting-the-admin-cp-with-http-basic-auth). Additionally you can add an [extra PIN number in the Admin CP login form](http://www.mybbsecurity.net/topic-add-secret-pin-to-acp-login), but having to go through all of these steps might be a little troublesome if you just want to do some quick edits.

**Nota Bene**: if you change the Admin CP directory and add plugin using it after, you will have to rename the directory in the plugin source before uploading it.

## Administrator Accounts

No matter how hard you try to secure the Admin CP, if people other than yourself have access to it then it really is a risk. You should only allow Admin CP access to people you know well and trust. Do not randomly allow a user of your forum to access it, even if he promises you to install a bunch of cool plugins or themes. Administrators should be selected carefully and reviewed thoroughly. Be **very careful** in who you trust access to the Admin CP to. If you trust no one, then perhaps you're better off as an administrator. In fact, if you don't need help with webmaster or admin tasks it really is best to remain the only administrator.

However, if you need help as an administrator permissions should be limited as much as possible. Distribute tasks between all the accounts. Discuss this with your admins and decide who should take care of what. For example, one of your administrators may be an HTML & CSS guru and could be in charge of making changes to templates and keeping the code clean. The other administrators may not know HTML, so why should they have access to the Templates & Style module? Similarly, if the HTML-guy doesn't like managing users and group permissions, then he definitely doesn't need access to that module. You can configure all of this in Admin CP > Users & Groups > Admin Permissions. Your administrators will be listed there, and you can specify everything they can and cannot access. Be rigorous and only allow access to the parts your administrators really need. As an example, you should probably disable all administrators other than yourself from accessing the database backups section. A backup of your database essentially contains all the information in your forum, which can be quite dangerous in the wrong hands. Provided that you have a proper backup solution (covered later on) there is no need for them to be able to create backups.

## Protect the `inc` Directory

The `inc` directory in your MyBB installation is something that should not be accessible to the end user at all. It contains sensitive information such as your database details (`inc/config.php`). And even though it is almost impossible for hackers to access that data, it's always a good idea to make things extra difficult to access. And the `inc` directory certainly doesn't need to be publicly available. You should therefore protect it completely by [disallowing access to the `inc` directory](http://www.mybbsecurity.net/topic-protecting-the-inc-directory).

## Change the Default Table Prefix

Changing your table prefix can prove to be helpful in certain cases. If a hacker manages to run an SQL query, he can easily destroy your forum completely. But if for some reason he doesn't know what your table prefix is (and therefore doesn't have a table name to query) it would certainly slow him down. Having that said, consider [changing your table prefix](http://www.mybbsecurity.net/topic-security-through-obscurity-changing-the-default-table-prefix).

## Disallow HTML in Posts

Allowing HTML to be used in posts is a terrible, terrible idea. That is why MyBB does not allow it by default. Unless you are absolutely certain that you want to use it (in which case you should install [HTML Purifier](http://mods.mybb.com/view/htmlpurifier)) it should be disabled on all forums. To do this quickly, run the following SQL query.

    UPDATE `mybb_forums` SET `allowhtml` = '0';

Afterwards you should go to Admin CP > Tools & Maintenance > Cache Manager > forums > Rebuild Cache to make sure this change is cached and is applied immediately.

## Hide the Version Number

Displaying which MyBB version you're running is essentially the same as yelling "hey, I'm running this specific version, which contains these specific vulnerabilities". It's an open invitation to hackers. If you're running on the latest version, it's probably nothing to worry about, but there is simply no point in displaying it. To hide it go to Admin CP > Configuration > Settings > Site Details > Show Version Numbers > Off.

## Keep Plugins to a Minimum

The more plugins you have installed, the more code can hackers exploit. Most plugins are fairly secure, but if one of them has a vulnerability, hackers can take advantage of it to get access to your forum. And for that simple reason it is highly recommended to keep the number of plugins to a minimum and only install those that you really need. It's also worth considering the popularity and the author of the plugin. Having that said, to improve your forum's security, we still recommend having a look at our list of [security plugins](http://community.mybb.com/thread-109872.html).

## Secure Other Software

Similarly, if you have other software like WordPress or Drupal installed on your server then you are facing a potential security risk because hackers have even more code to exploit. If they manage to hack your blog or image gallery, it's very possible that they get access to MyBB as well. This doesn't mean you should refrain from installing other software or that WordPress and the like are bad, you simply need to invest a little extra time securing them. Obviously, we can't help you with that, but things like updating the software and using strong passwords are a few key aspects you should keep in mind. For more information you should look up articles on securing the other software you have installed.

## Backup Regularly

None of this stuff matters if a hacker gets access to your database and drops all tables. He probably shouldn't have gotten that far provided that you have secure passwords and all, but if he did and you don't have a backup, you are essentially screwed. You will have to start over. That is why making backups of all your files and your database is **extremely important**. If the task is enabled in Admin CP > Tools & Maintenance > Task Manager, MyBB will backup your forum's database to the `backups` directory. In most cases this is not ideal, as hackers can easily destroy the backups. For a more sophisticated and complete backup solution, refer to the backup section in our list of [security tutorials](http://community.mybb.com/thread-109872.html).
