---
layout: page
title:  "Recovering a Hacked Forum"
categories: [security]
---

If your forum was hacked, or you want to know what to do when and if you get hacked, read this guide and follow the instructions precisely. Please note we try to cover every single possible situation. In most cases you won't need to follow all the steps outlined, but it is still highly recommended to do so.

Whenever an SQL query is provided, we assume your table prefix is `mybb_`. If you have a different table prefix remember to replace it in the SQL query.

## Get in Control

### Secure Your Computer

First things first: secure your computer. It is possible that you downloaded something that infected your computer and allowed your forum to be hacked. Therefore it is not safe to do anything else from your computer until it is 100% clean. Even if you were to recover your forum right now it could be useless because the hacker could easily know what you're up to and destroy everything again. Securing your computer is a priority at the moment. If you have another computer that you can use which is not infected then get on it immediately.

However if you don't have another computer lying around or other people to help you then you will have to take care of it right now. If you're using Windows we urge you to run tools like:

- [HitmanPro 3](http://www.surfright.nl/en/hitmanpro)
	+ Somewhat similar to HijackThis. Scans the computer for virus activities or suspicous files that have the characteristics of malware.
- [Kaspersky Virus Removal Tool](http://www.kaspersky.com/antivirus-removal-tool)
	+ Tool to help remove common malware infections, if detected.
- [Malwarebytes](https://www.malwarebytes.com/)
	+ Popular, trusted free solution for malware scanning. Quick definition updates and rigorous detections for more than plain malware.
- [HiJackThis](https://sourceforge.net/projects/hjt/)
	+ Tool that generates a report about system settings and files commonly modified by malware.

Scanning your computer with your own antivirus tools is also a good idea and installing a firewall. We recommend one of the following:

- [Microsoft Security Essentials](https://www.microsoft.com/en-us/download/details.aspx?id=5201)
	+ Simple, lightweight protection, but not a great malware detection rate. Windows 7 or Windows Vista only (its features were built into Windows 8+).
- [Avira Free AntiVirus](https://www.avira.com/en/antivirus)
	+ Standard antimalware software. Not especially great, but it is usually good enough.
- [Comodo Internet Security](https://www.comodo.com/home/internet-security/free-internet-security.php)
	+ Standard antimalware software. Not especially great, but it is usually good enough.
- [ZoneAlarm](https://www.zonealarm.com/)
	+ Inbound intrusion detection system and firewall that is highly customizable, allowing the user to specify what applications can create outbound network connections.

### Secure Your Online Accounts

Once your computer is safe it is highly recommended to reset all of your passwords - every single one. Your admin account might be safe, but the attack could have originated from a hacker gaining access to your email account, thus being able to request a password reset. Having one weak password might compromise everything related to it, therefore it is very important to use a **secure passwords** on all of your online accounts, specifically those related to your website (i.e. FTP, SSH, database, email). A good password can take a human hacker 580 million years to crack, due to how the math of probability works when a greater variety of characters (uppercase, lowercase, numeric, symbols) are used. You can see an example of how the math works with Gibson Research Corporation's [Password Haystacks](https://www.grc.com/haystack.htm) project (don't enter any password you intend to use; that would just be bad form).

Using safe passwords, however, may not be enough. What if someone else gets their hands on it? It is important to store your passwords in a secure place. Writing them on a piece of paper or a txt file is not good enough. We recommend that you use a password manager program, such as [KeePass](http://keepass.info/) or [LastPass](https://lastpass.com/), both of which feature very powerful password generators as well.

**Use two factor authentication wherever possible**, especially if you use the same password in multiple places (which you shouldn't). Two factor authentication helps reduce your vulnerability to weak passwords, key logging, password reuse, phishing and brute force because it means your account can't be accessed even if your password is compromised. If you have a Google Account, consider [enabling two factor authentication](https://googleblog.blogspot.com.au/2011/02/advanced-sign-in-security-for-your.html).

### Restore Your Admin Account

Having audited your computer and reset all your passwords, the first thing you want to do is to check if you have access to the Admin CP and the server. After all, you can't do anything if the hacker kicked you out of the administrator group or changed your permissions.

First let's check if the default administrator group actually has permission to access the Admin CP. To do so, run the following SQL query.

```sql
UPDATE `mybb_usergroups` SET `cancp`= '1' WHERE `gid` = '4';
```

And to make sure your account is in the administrator group, run the following SQL query. Replace `X` with your uid.

```sql
UPDATE `mybb_users` SET usergroup = '4' WHERE uid = 'X';
```

Next, you want to open the `inc/config.php` file in a text editor. Find the code below within that file and make sure your uid is within quotes. If you have multiple administrators, you can separate them with a comma. It is recommended to stick with your uid only for now though.

```php
$config['super_admins'] = '1';
```

Finally, to reset your password, in case the hacker changed it too, run the following SQL query. Remember to replace `X` with your uid and `example` with the desired new password.

```sql
UPDATE `mybb_users` SET `password` = md5('example'), `salt` = '' WHERE `uid` = 'X';
```

### Restrict Access to the Forum

Great! Your admin account is fully restored and all your passwords were reset. Now you can actually start recovering your forum. Well, first we need to make sure the hacker is unable to access your website completely, should he try to do anything else.

You should close the forum using the global switch in settings. Go to Admin CP > Configuration > Board Online / Offline > Board Closed > Yes.

That will prevent the hacker from accessing the front-end, but the website itself is still accessible. If he planted an exploit somewhere else, he might be able to use it. So what you should do now is disallow all visitors, except yourself, from accessing your website. Place the following code in your root `.htaccess` file if you're using apache or inside your site's configuration file server block if you're using nginx. Replace `127.0.0.1` with [your IP address](https://icanhazip.com/).

Apache 2.2:

```
Order deny,allow
Deny from all
Allow from 127.0.0.1
```

Apache 2.4:

```
Require all denied
Require ip 127.0.0.1
```

Nginx:

```
location / {
    allow 127.0.0.1;
    deny  all;
}
```

If you find yourself unable to access your website during this process, it is possible that you have a dynamic IP, in which case you will have to repeat the above procedure whenever your IP changes.

### Check the Logs

To have a better understanding of what happened and what actions were performed, take a little time to go through the logs and review them. To do that, go to `Admin CP > Tools & Maintenance > Logs > Administrator Log`. You might be surprised by what you can find in the logs. These logs can be deleted, so if the hacker deleted them you are out of luck.

But this is just MyBB's side. In addition to checking MyBB's logs, we also recommend that you check your web server's error logs. These are much more useful and detailed. If you don't know where to find the web server error logs, or don't know how to interpret them, get in touch with your web host, who should be able to fill you in on the attack.

## Secure the Forum

### Replace All the Files

To ensure that your MyBB installation is clean and no extra files have been added, you should delete all your files and upload a fresh copy of the latest version of MyBB. You only really need to backup your `inc/config.php` file. And even that should be double checked against the [default structure of the file]({{ site.baseurl }}/Incconfigphp.html). Pay attention to your database details specifically, as well as your admin directory, super admins, etc.

If you have a lot of plugins, images, language packs or custom modifications, you should create a full backup and upload these things later on. Note that it is possible that a vulnerability lies within these files, so make sure to review them carefully. In the future consider using the [Patches](https://mods.mybb.com/view/patches) plugin to edit all of the core files. This makes it incredibly easy to restore patches when you're upgrading or replacing files.

Deleting the files and re-uploading a fresh copy of MyBB also has the benefit of updating to the latest code. If you were running an older version of MyBB - which is why most forums get hacked - you will now be running on code free of any known vulnerabilities. To upgrade your forum, if it wasn't the latest version, follow the [Upgrade]({{ site.baseurl }}/1.8/install/upgrade/) documentation.

### Check CHMOD Permissions

If certain files or folders have unnecessary permissions, you may be up against a security risk. Files and folders should only have the permissions required by MyBB to run. There is no specific recommended set of permissions. It varies from server to server, because they are configured differently. For more information, read the Docs page on [CHMOD permissions](https://docs.mybb.com/1.8/administration/security/file-permissions/) or contact your web host for their recommendations.

### Check New Users

If you're following along step-by-step, no one can access your website or the MyBB backend, but you should quickly head over to the Admin CP and check all users that joined around the time of the attack. It is possible that the hacker created a new admin account and set the display usergroup to a normal user (thus being hidden). To see all the users with admin permissions and manage them go to Admin CP > Users & Groups > Admin Permissions. It's also worth checking changes to admin permissions and other things.

### Check Templates for Malicious Code

Finally, you should quickly go through your templates, since they are a way to inject malicious JavaScript code into your forum. If possible, delete your current theme and install a fresh copy of it. If you hired a designer to create a custom theme and don't have a copy of it at the moment, contact them for one.

However, if you made a lot of modifications and don't have a backup, then you'll have to go through the templates and look for suspicious code. Common templates for malicious code insertion are the `header`, `footer`, and `headerinclude`, as they are loaded globally. It is also recommended to check the `index`, `forumdisplay`, and `showthread` templates. An easy way to do this is to click on the Options button next to a template name and select Diff Report. The code highlighted in red is what differs from the default template, and also what you should be looking at. Look specifically for code within a `<script>` tag. Not all of it is malicious, but this filters down the options. If you don't know what to look for, don't be afraid to [ask for help](https://community.mybb.com/forum-176.html).

## New Security Measures

### MyBB Updates

Your forum is safe, but you shouldn't stop here. You should take new security measures immediately to prevent this from happening again. One thing we cannot stress enough is to always have your MyBB installation up to date. If you are running an older version, you are open to security vulnerabilities that were already fixed. MyBB takes security very seriously. Whenever a security vulnerability is reported it is patched very quickly and a new release is sent out. You should never skip upgrading, as you will be opening yourself to a security risk that hackers can easily take advantage of.

### Protecting the Admin CP

The Admin CP is the most powerful tool in MyBB. If anyone gains access to it, they can easily deface your forum and get complete control over it. It is therefore important to guarantee that only you or your administrators can access it.

#### Renaming the Admin CP Directory

As a starting point, you should rename the Admin CP directory. To do this:

- Rename the `admin` directory from `admin` to something random, such as `d8e8fca2dc0f896` (pick your own random value!). Create a bookmark in your browser if it helps.
- Open `./inc/config.php` in a text editor
	+ Find:

        ```php
        $config['admin_dir'] = 'admin';
        ```

	+ Replace `admin` with the random value you just used (`d8e8fca2dc0f896` in this example).

Confirm that the rename was completed successfully by browsing to your Admin CP and logging in.

#### Hiding Admin CP Links

In addition to renaming the Admin CP directory, it may also be useful to disable links to the Admin CP on the frontend of your forum. While this isn't the greatest form of protection, it can be helpful if there's any risk of you or another administrator browsing the forum frontend on an untrusted internet connection. An attacker could theoretically find your Admin CP URL just by examining the link printed in the forum header and begin an attack.

To disable display of all Admin CP links on the frontend of your forum:

- Open `./inc/config.php` in a text editor
	+ Find:

        ```php
        $config['hide_admin_links'] = 0;
        ```

	+ Change the value from `0` to `1`.

#### Installing an Admin CP Honeypot

Once you have done that it is a good idea to install [Admin CP Honeypot](https://community.mybb.com/thread-94406.html). This will take your previous Admin CP location and install a fake Admin CP, which will record the IP of anyone who tries to login to it and email you a small report.

Now your real Admin CP directory should look something like `d8e8fca2dc0f896` (which you should bookmark or take note of) and the fake Admin CP will be located at `admin` (which will record the details of anyone who tries to access it).

#### Password-Protect the Admin Directory

An additional measure to protect the Admin CP from attackers is to enable HTTP Basic Authentication (also known as auth_basic or .htpasswd protection). The procedure for doing this varies, depending on the HTTP server being used to serve your forum.

##### For cPanel Users (Easy Version)

1. Log into your cPanel and click on the Password Protect Directories option found under Security.
2. Choose Web Root, if prompted (you may also need to select Show Hidden Files)
3. Click on the name of the directory that you wish to password protect.
4. Check the box for Password protect this directory.
5. Fill in Name the protected directory field. This will be the message shown to visitors when they try to login and can be anything you like.
6. Click on the Save button below.
7. Click Go Back.
8. Fill in a Username and Password at the bottom of the page, and click Add/modify authorized user.

##### For Apache Users (cPanel/VPS/Dedicated Server)

To enable HTTP Basic Authentication on a server running Apache 2.4:

- Install the `apache2-utils` (Debian/Ubuntu) or `httpd-tools` (RHEL/CentOS 7) package, which contains the `htpasswd` utility, to help generate the .htpasswd credentials file.
- Run the following shell command: `sudo htpasswd -c /path/to/htpasswd/file desired_username`
	- A sane place to put this file is somewhere like `/etc/apache2/.htpasswd`, but there is great flexibility in this. Just make sure to keep the file out of the web root, because improper server configuration could lead to an attacker being able to download the file.
	- You will be prompted for a password, which will be stored in hashed form in `/path/to/htpasswd/file`
	- **If adding another user to a previously-created file, do not include the `-c` flag**. Doing so will overwrite the file, removing the credentials already configured.
- Create or edit a `.htaccess` file in your Admin CP directory.
	- Add

      ```
      AuthType Basic
      AuthName "AUTHENTICATION_MESSAGE_BROWSERS_WILL_DISPLAY"
      AuthUserFile "/path/to/htpasswd/file"
      Require valid-user
      ```

Upon navigating to the Admin CP, your browser should prompt you for a username and password.

##### For Nginx Users (VPS/Dedicated Server)

To enable HTTP Basic Authentication on a server running Nginx:

- Install the `apache2-utils` (Debian/Ubuntu) or `httpd-tools` (RHEL/CentOS 7) package, which contains the `htpasswd` utility, to help generate the .htpasswd credentials file.
- Run the following shell command: `sudo htpasswd -c /path/to/htpasswd/file desired_username`
	- A sane place to put this file is somewhere like `/etc/nginx/.htpasswd`, but there is great flexibility in this. Just make sure to keep the file out of the web root, because improper server configuration could lead to an attacker being able to download the file.
	- You will be prompted for a password, which will be stored in hashed form in `/path/to/htpasswd/file`
	- **If adding another user to a previously-created file, do not include the `-c` flag**. Doing so will overwrite the file, removing the credentials already configured.
- Edit the Nginx configuration file that contains the server declaration for your forum. This varies depending on your server's configuration.
	- Inside the `server {` block add

      ```
      location /your/admin/directory {
      auth_basic "YOUR_AUTHENTICATION_MESSAGE";
      auth_basic_user_file /path/to/htpasswd/file;
      }
      ```

Upon navigating to the Admin CP, your browser should prompt you for a username and password.

#### Configuring a Two-Factor Authentication (2FA)

[*See more information here*](/1.8/administration/security/2fa)

### Administrator Accounts

No matter how hard you try to secure the Admin CP, if people other than yourself have access to it then it really is a risk. You should only allow Admin CP access to people you know well and trust. Do not randomly allow a user of your forum to access it, even if he promises you to install a bunch of cool plugins or themes. Administrators should be selected carefully and reviewed thoroughly. Be **very careful** in who you trust access to the Admin CP to. If you trust no one, then perhaps you're better off as an administrator. In fact, if you don't need help with webmaster or admin tasks it really is best to remain the only administrator.

However, if you need help as an administrator permissions should be limited as much as possible. Distribute tasks between all the accounts. Discuss this with your admins and decide who should take care of what. For example, one of your administrators may be an HTML & CSS guru and could be in charge of making changes to templates and keeping the code clean. The other administrators may not know HTML, so why should they have access to the Templates & Style module? Similarly, if the HTML-guy doesn't like managing users and group permissions, then he definitely doesn't need access to that module. You can configure all of this in Admin CP > Users & Groups > Admin Permissions. Your administrators will be listed there, and you can specify everything they can and cannot access. Be rigorous and only allow access to the parts your administrators really need. As an example, you should probably disable all administrators other than yourself from accessing the database backups section. A backup of your database essentially contains all the information in your forum, which can be quite dangerous in the wrong hands. Provided that you have a proper backup solution (covered later on) there is no need for them to be able to create backups.

### Protect the `inc` Directory

The `inc` directory in your MyBB installation contains sensitive information, such as database details, and plugin files. All files in this directory should have code that prevents them from being directly accessed. However, an attacker can still tell if the file exists and gain information based on that. To protect against this, you can deny all access by users to the directory, since they should never need it. This won't impact your forum's function at all because it accesses the files a different way.

##### For cPanel or Apache Users

Create a `.htaccess` file in the `inc` directory. Inside it, add:

```
# Only if using Apache 2.4
Require all denied

# Only if using Apache 2.2
Order deny,allow
Deny from all
```

##### For Nginx Users (VPS/Dedicated)

In the server block for your forum, add:
```
location /inc {
	deny all;
	return 404;
}
```

### Change the Default Table Prefix (MySQL)

Changing your table prefix can prove to be helpful in certain cases. If a hacker manages to run an SQL query, he can easily destroy your forum completely. But if for some reason he doesn't know what your table prefix is (and therefore doesn't have a table name to query) it would certainly slow him down. With that in mind, consider changing your database prefix, as explained below.

**REMEMBER:** Before making any changes to your database, [perform a database backup](/1.8/administration/backups) so that if something goes wrong, it will be trivial to recover your data.

#### phpMyAdmin

1. Select all of the MyBB tables (at the bottom), click the dropdown and select "Replace table prefix".
2. In the from box, type in mybb (or whatever your old prefix was, ignoring the underscore); in the to box, type in your new prefix.

#### Manual SQL

Using the MySQL command line, execute this script:

```sql
SET @database   = "mybb";
SET @old_prefix = "mybb";
SET @new_prefix = "mybb123232"; -- Example new prefix

SELECT concat("RENAME TABLE ",TABLE_NAME," TO ",replace(TABLE_NAME, @old_prefix, @new_prefix),';') AS "SQL"
FROM information_schema.TABLES WHERE TABLE_SCHEMA = @database;
```

The output will be a list of SQL statements that can be run from the command line or using any other database management program, such as phpMyAdmin.

### Disallow HTML in Posts

Allowing HTML to be used in posts is a terrible, terrible idea. That is why MyBB does not allow it by default. Unless you are absolutely certain that you want to use it (in which case you should install [HTML Purifier](https://mods.mybb.com/view/htmlpurifier)) it should be disabled on all forums. To do this quickly, run the following SQL query.

```sql
UPDATE `mybb_forums` SET `allowhtml` = '0';
```

Afterwards you should go to Admin CP > Tools & Maintenance > Cache Manager > forums > Rebuild Cache to make sure this change is cached and is applied immediately.

### Hide the Version Number

Displaying which MyBB version you're running is essentially the same as yelling "Hey, I'm running this specific version, which contains these specific vulnerabilities, hack me!". It's an open invitation to hackers. If you're running on the latest version, it's probably nothing to worry about, but there is simply no point in displaying it. To hide it go to Admin CP > Configuration > Settings > General Configuration > Show Version Numbers > Off.

### Keep Plugins to a Minimum

The more plugins you have installed, the more code hackers can exploit. Most plugins are fairly secure, but if one of them has a vulnerability, hackers can take advantage of it to get access to your forum. And for that simple reason it is highly recommended to keep the number of plugins to a minimum and only install those that you really need. It's also worth considering the popularity and the author of the plugin. Having that said, to improve your forum's security, we still recommend having a look at our list of [security plugins](https://community.mybb.com/thread-109872.html).

### Secure Other Software

Similarly, if you have other software like WordPress or Drupal installed on your server then you are facing a potential security risk because hackers have even more code to exploit. If they manage to hack your blog or image gallery, it's very possible that they get access to MyBB as well. This doesn't mean you should refrain from installing other software or that WordPress and the like are bad, you simply need to invest a little extra time securing them. Obviously, we can't help you with that, but things like updating the software and using strong passwords are a few key aspects you should keep in mind. For more information you should look up articles on securing the other software you have installed.

### Backup Regularly

None of this stuff matters if a hacker gets access to your database and drops all tables. He probably shouldn't have gotten that far provided that you have secure passwords and all, but if he did and you don't have a backup, you are essentially screwed. You will have to start over. That is why making backups of all your files and your database is **extremely important**. If the task is enabled in Admin CP > Tools & Maintenance > Task Manager, MyBB will backup your forum's database to the `backups` directory. In most cases this is not ideal, as hackers can easily destroy the backups. For a more sophisticated and complete backup solution, refer to the backup section in our list of [security tutorials](https://community.mybb.com/thread-109872.html).

## Final Words

Even if you had the world's most advanced security system, if the person in control of it does something wrong, then all work is in vain. Always keep an eye on what you install and run on your computer, make sure your passwords are safe, ensure your forum is properly patched, and never try to do anything that would expose any "flaws" to others. If you and your fellow administrators do your job properly, your website will certainly be much safer. And to be prepared at all times, make backups frequently, and you will thank yourself in the long run.

We hope you never have to go through the "recovery" steps in this guide. What you should follow are the preparation steps - if you are prepared, it makes you a much less viable target.

## Future Security Measures

Your forum is safe, but you shouldn't stop here. You should take new security measures immediately to prevent this from happening again. See [Protecting Your MyBB Forum](/1.8/administration/security/protection).
