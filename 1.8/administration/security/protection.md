---
layout: page
title:  "Protecting Your MyBB Forum"
categories: [security]
---

## MyBB Updates

One thing we cannot stress enough is to always have your MyBB installation up to date. If you are running an older version, you are open to security vulnerabilities that were already fixed. MyBB takes security very seriously. Whenever a security vulnerability is reported it is patched very quickly and a new release is sent out. You should never skip upgrading, as you will be opening yourself to a security risk that hackers can easily take advantage of.

## Fine Tuning the Admin CP

The Admin CP is the most powerful tool in MyBB. If anyone gains access to it, they can easily deface your forum and get complete control over it. It is therefore important to guarantee that only you or your administrators can access it. For starters you should rename your Admin CP directory and hide all links to it. Once you have done that it is a good idea to install [Admin CP Honeypot](https://community.mybb.com/thread-94406.html). This will take your previous Admin CP location and install a fake Admin CP, which will record the IP of anyone who tries to login to it and email you a small report.

Now your real Admin CP directory should look something like `Svt06wbowXgMVvFmkFaz` (which you should bookmark or take note of) and the fake Admin CP will be located at `admin` (which will record the details of anyone who tries to access it). To finalize, [you should password protect your real Admin CP with HTTP Basic Auth](#Protect_the_Admin_CP_with_HTTP_Basic_Auth). Additionally you can enable the Admin CP PIN, which was added in 1.8, but having to go through all of these steps might be a little troublesome if you just want to do some quick edits.

**Note**: If you change the Admin CP directory and add any plugins that use it after, you will have to rename the directory in the plugin before uploading it.

## Protect the Admin CP with HTTP Basic Auth

Also known as "htpasswd protection," adding HTTP Basic Auth protection to your Admin Control Panel directory is one of many ways to put sensitive settings behind another layer of security, and thus making it theoretically harder for hackers to take advantage of. The procedures differ between web servers, but specific instructions for cPanel, Apache, and Nginx (all on a Linux system) are provided below.

When finished with one of the instruction sets below, browse to your Admin CP again, and you should receive an additional username/password prompt before seeing the Admin CP login or interface.

## cPanel Basic Auth Configuration (without SSH)

Similar to Apache, but with the cPanel UI on shared hosts.

- Search for the `Directory Privacy` menu item (icon: blue folder with lock)
- Select the directory you wish to protect (your Admin CP directory)
- **Check** the `Password protect this directory.` checkbox.
- Fill out the given form with a username and strong password (>85 score)
- Click `Save`.

## Apache Basic Auth Configuration (with or without SSH)

Requirements:
- SSH access to site
    - If not available, use [DynamicDrive's generator tool](http://www.tools.dynamicdrive.com/password/) and upload the files, as if you followed the directions below to create them.
- Apache configured to allow .htaccess files to override configuration values

First, create a new file in the Admin CP directory named .htaccess. Apache will interpret the file as a local configuration file in the directory and any subdirectories inside of it.

- Open the `.htaccess` file
- **ADD**:
```
AuthUserFile /path/to/.htpasswd
AuthGroupFile /dev/null
AuthName Restricted
AuthType Basic
require valid-user
```
- Run shell command: `htpasswd -c -b /path/to/.htpasswd desired_username desired_secure_password`
    - **NOTE:** Replace `/path/to/.htpasswd` in both places with the respective file location.

## Nginx Basic Auth Configuration (with SSH)

Requirements:

- SSH access to site configuration file

Let's begin:

- Open your nginx site configuration file.
- Within the `server` block, **ADD**
```
location /path/to/ACP {
auth_basic           "Restricted";
auth_basic_user_file /path/to/.htpasswd;
}
```
- Run shell command: `htpasswd -c -b /path/to/.htpasswd desired_username desired_secure_password`
	- If the command is not found, install the `apache2-utils`, `httpd-utils`, or similar package for your Linux distribution.  
	- **NOTE:** Replace `/path/to/.htpasswd` in both places with the respective file location.

## Configuring an Admin CP PIN

With MyBB 1.8, an Admin Control Panel "Secret PIN" setting was added to the core, inspired by a popular community tutorial. To enable the PIN:

- Open `inc/config.php`
- **FIND** or **ADD**:

	```php
	$config['secret_pin']
	```
- Set the variable to a value, such as `'S0me p1n'`.
- **DONE**

**Example:**

```php
$config['secret_pin'] = 'S0me p1n';
```

## Administrator Accounts

### More Admins = Less Security
No matter how hard you try to secure the Admin CP, if people other than yourself have access to it then it really is a risk. You should only allow Admin CP access to people you know well and trust. Do not randomly allow a user of your forum to access it, even if they promise to install a bunch of cool plugins or themes. Administrators should be selected carefully and reviewed thoroughly. Be **very careful** in who you trust access to the Admin CP to. If you trust no one, then perhaps you're better off as an administrator. In fact, if you don't need help with webmaster or admin tasks, it really is best to remain the only administrator.

### Give Each Administrator Minimal Permissions

Permissions for each Administrator can be configured at `Admin CP > Users & Groups > Admin Permissions`.

If you have multiple administrators, assign specific roles to apply a "divide and conquer" strategy across your administrators.

Examples:

- If one is strong in design, give them access to Templates and Style ACP features, but not settings, users, or system tools. They shouldn't need them for design tasks, and if they do, they can ask someone else to perform those actions.
- Perhaps another admin is great with managing community members. Give them access to Users and Groups, but nothing more.

The more features you give to each administrator, the more power you grant to each of them over your community and its security.

## Protect the `inc` Directory

The `inc` directory in your MyBB installation should not be accessible to the end user at all. It contains sensitive information such as your database details (`inc/config.php`). Even though it is almost impossible for hackers to access that data, it's always a good idea to have an extra layer of protection. The `inc` directory doesn't need to be publicly available, so protect it completely by disallowing access to the `inc` directory.

## Change the Default Table Prefix

Changing your table prefix can prove to be helpful in certain cases. If a hacker manages to run an SQL query, he can easily destroy your forum completely. But if they don't know what your table prefix is (and therefore don't have a table name to query) it would slow them down.

## Disallow HTML in Posts

Allowing HTML to be used in posts is a terrible, terrible idea. That is why MyBB does not allow it by default. Unless you are absolutely certain that you want to use it, it should be disabled on all forums. To do this quickly, run the following SQL query.

```sql
UPDATE `mybb_forums` SET `allowhtml` = '0';
```

Afterwards you should go to Admin CP > Tools & Maintenance > Cache Manager > forums > Rebuild Cache to make sure this change is cached and is applied immediately.

## Configure access to private hosts and IP addresses

MyBB 1.8.8 introduced two new values to the `inc/config.php` file containing respecively host names and IPv4 addresses the script should not be connecting to (e.g. while attempting to check remote avatars), mitigating a Server Side Request Forgery (SSRF) vulnerability.

While MyBB will continue to work when these values are not present, it is highly recommended that board administrators update their configuration files by appending the default fragment included below to the PHP code. Additionally, if other hostnames or IPv4 addresses that may point to private network servers are present, they should be appended to these arrays. `$config['disallowed_remote_addresses']` supports wildcards and address groups in CIDR notation.

```
/**
 * Disallowed Remote Hosts
 *  List of hosts the fetch_remote_file() function will not
 *  perform requests to.
 *  It is recommended that you enter hosts resolving to the
 *  forum server here to prevent Server Side Request
 *  Forgery attacks.
 */

$config['disallowed_remote_hosts'] = array(
	'localhost',
);

/**
 * Disallowed Remote Addresses
 *  List of IPv4 addresses the fetch_remote_file() function
 *  will not perform requests to.
 *  It is recommended that you enter addresses resolving to
 *  the forum server here to prevent Server Side Request
 *  Forgery attacks.
 *  Removing all values disables resolving hosts in that
 *  function.
 */

$config['disallowed_remote_addresses'] = array(
	'127.0.0.1',
	'10.0.0.0/8',
	'172.16.0.0/12',
	'192.168.0.0/16',
);
```

## Hide the Version Number

Displaying which MyBB version you're running is essentially the same as yelling "hey, I'm running this specific version, which contains these specific vulnerabilities". It's an open invitation to hackers. If you're running on the latest version, it's probably nothing to worry about, but there is simply no point in displaying it. To hide it go to Admin CP > Configuration > Settings > Site Details > Show Version Numbers > Off.

## Minimize Installed Plugins

The more plugins you have installed, the more code can hackers exploit. Most plugins are fairly secure, but if one of them has a vulnerability, hackers can take advantage of it to get access to your forum. And for that simple reason it is highly recommended to keep the number of plugins to a minimum and only install those that you really need. It's also worth considering the popularity and the author of the plugin. Having that said, to improve your forum's security, we still recommend having a look at our list of [security plugins](https://community.mybb.com/thread-109872.html).

## Secure Other Software

Similarly, if you have other software like WordPress or Drupal installed on your server then you are facing a potential security risk because hackers have even more code to exploit. If they manage to hack your blog or image gallery, it's very possible that they get access to MyBB as well. This doesn't mean you should refrain from installing other software or that WordPress and the like are bad, you simply need to invest a little extra time securing them. Obviously, we can't help you with that, but things like updating the software and using strong passwords are a few key aspects you should keep in mind. For more information you should look up articles on securing the other software you have installed.

## Backup Regularly

None of this stuff matters if a hacker gets access to your database and drops all tables. He probably shouldn't have gotten that far provided that you have secure passwords and all, but if he did and you don't have a backup, you are essentially screwed. You will have to start over. That is why making backups of all your files and your database is **extremely important**. If the task is enabled in Admin CP > Tools & Maintenance > Task Manager, MyBB will backup your forum's database to the `backups` directory. In most cases this is not ideal, as hackers can easily destroy the backups. For a more sophisticated and complete backup solution, refer to the backup section in our list of [security tutorials](https://community.mybb.com/thread-109872.html).
