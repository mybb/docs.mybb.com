---
layout: page
title:  "MyBB Security Guide"
categories: [security]
description: "Hardening & Best Practices for Securing Forums"
---

## General Advice
Forum users with elevated permissions should follow universal digital security recommendations, including the use [strong, unique passwords and password managers](https://ssd.eff.org/en/module/creating-strong-passwords) and _Two-Factor Authentication_ (2FA) for their forum accounts as well as any related personal accounts (e.g. used for password recovery). _Universal 2nd Factor_ (U2F) and on-device TOTP types are [preferred](https://www.eff.org/deeplinks/2017/09/guide-common-types-two-factor-authentication-web) to SMS-based codes.

Scanning devices with antivirus tools and installing security software is also a good idea. Consult reputed publications and organizations for recommendation appropriate for used platforms (e.g. [AV-Comparatives](https://www.av-comparatives.org/consumer/test-results/), [AV-TEST](https://www.av-test.org/en/antivirus/), [MRG Effitas](https://www.mrg-effitas.com/services/endpoint-protection-testing/360-protection-testing/), [SE Labs](https://www.selabs.uk/en/reports/consumers)).

## Software & Updates

### MyBB
MyBB, besides normal development, runs a [Security Research program](https://mybb.com/get-involved/security/) to prevent, and respond to, threats and vulnerabilities that may affect forums running MyBB. Solutions for discovered and reported issues are included in subsequent updates. Such security releases should be installed by board administrators as soon as possible to prevent exploitation.

We recommend subscribing to at least one of the [**several announcement channels**](https://mybb.com/download/verifying/) to follow notifications of new MyBB version releases.

By default, MyBB installations contact `mybb.com` to check for updates daily and display a warning in the Admin CP when new versions are found. This happens as long as the _Version Check_ task (**Tools & Maintenance &rarr; Task Manager**) is enabled. Administrators should confirm that no network problems occur by running **Home &rarr; Check for Updates**.

### Extensions
Similarly, installed MyBB extensions should be kept up to date, especially if new releases address security issues &mdash; we recommend subscribing to plugins and themes in use on the [Extend](https://community.mybb.com/mods.php) section (or other official sources) to get notified of extension updates.

It's recommended to keep the number of extensions to a minimum and only install those that are really needed, since the more plugins (and, to a lesser extent, themes) are installed, the more code can be potentially exploited. Extensions should only be downloaded from trusted sources and authors. Inspecting the code (including updates) by technical staff before installation may help prevent security issues and familiarize themselves with new functionality better.

#### Admin CP
Plugins and themes that affect the ACP should not use resources (like images, CSS, or JavaScript files) hosted on, or attempt to send or receive data from, external servers. Connections to third-party domains can be spotted using browsers' _Inspect_ feature by observing _Network_ requests during page load.

## Regular Backups
Making backups of all forum files and database is **extremely important**. The copies should be routinely verified to make sure the forum can be fully restored without any problems.

Forum administrators can enable and customize frequency of the included _Weekly Backup_ task (**Tools & Maintenance &rarr; Task Manager**) to let MyBB create copies of the database ready for download.

[**MyBB Documentation &rsaquo; Backups &rarr;**](/1.8/administration/backups/)

## MyBB &mdash; General Configuration

### Use HTTPS and Related Security Controls
The forum should only be available over the `https://` protocol with a valid certificate and safe configuration including secure redirects, no mixed content issues, suitable security headers and _Secure_ cookies.

We recommend to set up basic HTTPS support before installing MyBB to use it during the installation; passwords, tokens, and other sensitive values entered on the forum with no HTTPS should be changed.

[**MyBB Documentation &rsaquo; Setting up HTTPS &rarr;**](/1.8/administration/security/https/)

### Disable HTML Parsing
Parsing HTML in all user content (like posts and profile fields) is highly dangerous and should be kept disabled.

The following Settings should be set to **_No_**:
- _Posting &raquo; Allow HTML in Announcements_ (`announcementshtml`)
- _Private Messaging &raquo; Allow HTML_ (`pmsallowhtml`)
- _Profile Options &raquo; Allow HTML in Signatures_ (`sightml`)

To disable HTML in individual Calendars, Forums, and Profile Fields, you can execute the following SQL query:
```sql
UPDATE mybb_calendars SET allowhtml = 0;
UPDATE mybb_forums SET allowhtml = 0;
UPDATE mybb_profilefields SET allowhtml = 0;
```

Afterwards go to **Tools & Maintenance &rarr; Cache Manager** and Rebuild the `forums` and `profilefields` cache to make sure these changes are applied immediately.

### Enable _SameSite Cookie Flag_
Some web attacks can be prevented by having the _Site Details &raquo; SameSite Cookie Flag_ setting (**Configuration &rarr; Settings**) set to **Yes** (default).

### Apply Server-Specific Directives
The MyBB package contains `htaccess.txt` and `htaccess-nginx.txt` files in the MyBB root directory.

- #### Apache servers
  - `htaccess.txt` should be renamed to `.htaccess` and kept in the same directory,
  - the installation should contain a `.htaccess` file in the `admin/backups/` directory (already renamed in the package).

- #### nginx servers

  The directives included in the `htaccess-nginx.txt` file should be inserted into the [nginx configuration file](https://docs.nginx.com/nginx/admin-guide/basic-functionality/managing-configuration-files/) of your server.

### Limit Access to Private Hosts and IP Addresses
The MyBB [configuration file](/1.8/administration/configuration-file/) (`inc/config.php`) contains host names and IPv4 addresses the application should not be connecting to (e.g. while attempting to download remote avatars), mitigating a _Server Side Request Forgery_ (SSRF) vulnerability. Board administrators should update their configuration files by adjusting default values (or adding the fragment included below to the PHP code of the file for older installations).

If the forum's server infrastructure contains additional hostnames or IPv4 addresses that may point to private network servers, they should be appended to the arrays.

The  `$config['disallowed_remote_addresses']` array supports wildcards and address groups in CIDR notation.

```php
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

### Hide the Version Number
Displaying which MyBB version the forum is running may make it easier for potential attackers to establish whether it contains vulnerabilities related to older versions. The _Site Details &raquo; Show Version Numbers_ setting (**Configuration &rarr; Settings**) should be set to **_Off_**.

### Restrict Web Access to Internal Files
  Depending on installed extensions, you can disable access to [internal files and directories](/1.8/development/directory-structure/).

  - #### Apache servers

    Create a `.htaccess` file in chosen directory with the following content to deny access to it:

    - Apache 2.4
    ```apache
    Require all denied
    ```

    - Apache 2.2
    ```apache
    Order deny,allow
    Deny from all
    ```

  - #### Nginx servers

    In the server block for the forum, add to disable access to the `inc/` directory:

    ```nginx
    location ~ /inc {
      internal;
    }
    ```

### _Change the Default Table Prefix_
Changing the table prefix can prove to be helpful in certain cases. If an attacker manages to run an SQL query, they can easily damage the forum, but if they don't know what the table prefix is (and therefore don't have a table name to query) it would slow them down.

**Remember:** Before making any changes to the database, [perform a database backup](/1.8/administration/backups/) so that if something goes wrong, it will be trivial to recover your data.

- #### Using phpMyAdmin

  1. Select all of the MyBB tables (at the bottom), click the dropdown and select _Replace table prefix_.
  2. In the from box, type in `mybb` (or whatever the old prefix was, ignoring the underscore); in the to box, type in your new prefix.

- #### Manual SQL execution

  ```sql
  SET @database   = "mybb";
  SET @old_prefix = "mybb";
  SET @new_prefix = "mybb123232"; -- Example new prefix

  SELECT concat(
      "RENAME TABLE ",
      TABLE_NAME,
      " TO ",
      replace(TABLE_NAME, @old_prefix, @new_prefix),
      ';'
  ) AS "SQL"
  FROM information_schema.TABLES WHERE TABLE_SCHEMA = @database;
  ```

  The output will be a list of SQL statements that can be run to rename the tables.

After renaming the tables, adjust the value of `$config['database']['table_prefix']` in the [Configuration File](/1.8/administration/configuration-file/) accordingly.

## MyBB &mdash; Admin Control Panel
### Use Two-Factor Authentication (2FA)

All forum administrators should enable Two-Factor Authentication to protect against compromised passwords.

[**MyBB Documentation &rsaquo; Using Two-Factor Authentication with MyBB
 &rarr;**](/1.8/administration/security/2fa)

### Rename the Admin CP Directory
We recommend renaming the `admin/` Admin CP directory to a value known only to forum administrators, reducing the impact of potential password/2FA compromise and XSS attacks. To do this:

- rename the `admin` directory from `admin` to something random, such as `d8e8fca2dc0f896` (pick your own random value!),
- in the `inc/config.php` file:
  - modify the name of the directory in `$config['admin_dir']`:
    ```php
    $config['admin_dir'] = 'd8e8fca2dc0f896';
    ```
  - disable showing links to the ACP to make it undiscoverable even after logging in on the forum:
    ```php
    $config['hide_admin_links'] = 0;
    ```

Confirm that the rename was completed successfully by browsing to your Admin CP and logging in. The address can be securely distributed to other administrators and bookmarked locally for convenience.

**Note**: after this change, extension files intended for upload to the `admin/` directory will have to be uploaded to the renamed directory instead.

### Limit Administrative Access
The MyBB ACP can be used not only to cause damage using assigned permissions, but also to escalate them and inject malicious code executed by administrators with more permissions (which is mostly related to [HTML support in many fields editable through the ACP](https://github.com/mybb/mybb/issues/3126)).

You should only allow Admin CP access to people you know well and trust, and potential administrators should be carefully selected and thoroughly reviewed. It is a good idea to distribute tasks between accounts, removing all permissions not relevant to performed tasks.

User and Group Administrator permissions can be inspected and modified in **Users & Groups &rarr; Admin Permissions**.

Admin Permissions that may be dangerous include (but are not limited to):
- Configuration:
  - _Can manage settings?_ (unfiltered HTML, sensitive data, security configuration),
  - _Can manage custom profile fields?_ (unfiltered HTML),
  - _Can manage custom MyCode?_ (unfiltered HTML),
  - _Can manage language packs?_ (unfiltered HTML),
  - _Can manage help documents?_ (unfiltered HTML),
  - _Can manage calendars?_ (unfiltered HTML),
- Forums & Posts:
  - _Can manage forums?_ (unfiltered HTML),
- Users & Groups:
  - _Can manage users?_ (permission escalation),
  - _Can manage user groups?_ (permission escalation),
  - _Can manage admin permissions?_ (permission escalation),
  - _Can manage group promotions?_ (permission escalation),
- Templates & Style:
  - _Can manage themes?_ (unfiltered HTML),
  - _Can manage templates?_ (unfiltered HTML),
- Tools & Maintenance:
  - _Can manage cache?_ (sensitive data),
  - _Can manage backup database?_ (sensitive data).

MyBB extensions may introduce additional areas to be wary of.

### Configure Super Administrators
Super Administrator accounts cannot be deleted, banned, or otherwise altered by regular administrators in most sections of the Admin CP. During the MyBB installation process, the first user (with ID 1) is set as a Super Administrator.

The `$config['super_admins']` variable of the [MyBB configuration file](/1.8/administration/configuration-file/) (`inc/config.php`) defines a comma-separated list of user IDs.

E.g. to set users with ID `1` and ID `2002` as Super Administrators, the variable would be saved as:
```php
$config['super_admins'] = '1,2002';
```

### Use Private Browsing
It is recommended that forum administrators use separate browsers for public pages of the forum and the Admin CP or, preferably, use [private browsing](https://en.wikipedia.org/wiki/Private_browsing) for ACP activities, limiting potential impact of vulnerabilities affecting the forum front-end and those originating from external sites. In this approach:
- a new browser session with no saved data should be opened before logging into the ACP,
- the ACP URL should be entered directly,
- no external pages, including the forum front-end, should be visited within the browser session involving interaction with the ACP.

### _Protect the Admin CP with HTTP Basic Auth_
Also known as _htpasswd protection_, adding HTTP Basic Auth protection to the Admin Control Panel directory is one of many ways to put sensitive settings behind another layer of security, independent from MyBB authentication mechanisms.

- #### cPanel
  1. Search for the _Directory Privacy_ menu item (icon: blue folder with lock),
  1. select the directory you wish to protect (the Admin CP directory),
  1. check the _Password protect this directory_ checkbox,
  1. fill out the given form with a username and strong password,
  1. click _Save_.

- #### DirectAdmin
  1. Search for the _Password Protected Directories_ menu item,
  1. click _Find a Directory to Password Protect_,
  1. find the directory you wish to protect (the Admin CP directory) and click the _Protect_ Action,
  1. fill out the given form with a username and strong password,
  1. check the _Protection Enabled_ checkbox,
  1. click _Save_.

- #### SSH &mdash; Apache Servers
  This method requires Apache to be configured to allow `.htaccess` files to override configuration values.

  1. Create a new `.htaccess` file in the Admin CP directory (Apache will interpret the file as a local configuration file in the directory and any subdirectories inside of it),
  1. Insert the HTTP Auth configuration into it:
     ```apache
     AuthUserFile /PATH/TO/.htpasswd
     AuthGroupFile /dev/null
     AuthName Restricted
     AuthType Basic
     require valid-user
     ```
  1. Run the following shell command:
     ```bash
     htpasswd -c -b /PATH/TO/.htpasswd DESIRED-USERNAME DESIRED-SECURE-PASSWORD
     ```

  **Note:** replace `/PATH/TO/.htpasswd` in both places with the respective file location.

- #### SSH &mdash; Nginx Servers
  1. Open the [nginx configuration file](https://docs.nginx.com/nginx/admin-guide/basic-functionality/managing-configuration-files/),
  1. within the `server` block, add the HTTP Auth configuration:
     ```nginx
     location /admin {
       auth_basic           "Restricted";
       auth_basic_user_file /PATH/TO/.htpasswd;
     }
     ```
  1. Run the following shell command:
     ```bash
     htpasswd -c -b /PATH/TO/.htpasswd DESIRED-USERNAME DESIRED-SECURE-PASSWORD
     ```
  	 If the command is not found, install the `apache2-utils`, `httpd-utils`, or similar package for your Linux distribution.

  **Note:** replace `/PATH/TO/.htpasswd` in both places with the respective file location.


When finished, browse to the Admin CP again, and you should receive an additional username/password prompt before seeing the Admin CP login or interface.

### _Admin CP PIN_
The Admin Control Panel login, besides passwords and 2FA tokens, can include a _Secret PIN_ that serves as an additional, global password required to access the ACP. To set it up, edit the `$config['secret_pin']` variable in the [configuration file](/1.8/administration/configuration-file/) (`inc/config.php`):
```php
$config['secret_pin'] = 'RANDOM-VALUE-HERE';
```
The _Secret PIN_ can be securely distributed to other administrators to save in a safe place.

## Inadvertent Data Disclosures
MyBB uses tokens which confidentiality allows security mechanisms to work properly. Those codes usually contain random, alphanumeric characters and may be appear in:

- details of MyBB's internal operations:

  - database exports, query results, and manual lookups (e.g. using _phpMyAdmin_),
  - Database Queries listed in MyBB Debug Information,
  - configuration (`inc/config.php`) and cached settings (`inc/settings.php`) files,
  - MyBB settings (usually secret API keys for external services),
  - Cache content (usually in the ACP's Cache Manager),
  - [Database Backup](/1.8/administration/backups/) file names,
  - error logs and access logs,
  - information displayed by additional debug code,


- normal MyBB usage artifacts:

  - cookie values in users' browsers,
  - page source (usually named `my_post_key`, `logoutkey`),
  - URL parameters (`...&my_post_key=...`),
  - error messages.

Administrators, users, and visitors should take caution when seeking [technical support](https://mybb.com/support/) and reporting problems to avoid including such data in code samples and diagnostic information (especially publicly), e.g. by limiting snippets to areas specific to the problem in question or replacing sensitive codes with `[REMOVED]`.

Examples of sensitive Values:
```js
var my_post_key = "0c153ee1b3a6f3847d98ab660fc0a64b";
```
```html
<input type="hidden" name="my_post_key" value="0c153ee1b3a6f3847d98ab660fc0a64b" />
```
```html
<a href="https://example.com/member.php?action=logout&amp;logoutkey=e77ed4a03c8ae73f3aada970f0230d3f" class="logout">
```
```sql
SELECT * FROM mybb_sessions WHERE sid='2ab3cb1c5142e42654cab26aa9fd0ee9' AND ip=X'4d794242'
```

### Password-related Fields
Likewise, the `password` and `salt` values in the `mybb_users` table should not be shared, regardless [password hashing](https://en.wikipedia.org/wiki/Cryptographic_hash_function#Password_verification), as such disclosures may make it easier to guess the original passwords and any tokens generated using such values.

## Monitoring
### Error Logs
PHP, SQL, or other errors that appear during normal MyBB usage may indicate incorrect behavior that may pose a security risk or result from malicious activity. To observe such events, you can take advantage of the server's error reporting features or use the _Server and Optimization Options &raquo; Use Error Handling_ setting (**Configuration &rarr; Settings**) with suitable _Error Logging Medium_.

### Activity Logs
We recommend to regularly review **Administrator Logs** (**Tools & Maintenance**) to look out for malicious activity. While MyBB does not record failed login attempts, the [Security Log](https://community.mybb.com/mods.php?action=view&pid=740) plugin can be used to add this functionality.

### Files and Database
The **File Verification** (**Tools & Maintenance**) can be used to check MyBB source files for modification. With the [DVZ Integrity Tools](https://community.mybb.com/mods.php?action=view&pid=980) plugin, forum Super Administrators will be also able to compare files showing specific changes and list changes applied to database table structure.

### _Admin CP Honeypot_
The [Admin CP Honeypot](https://community.mybb.com/thread-94406.html) installs a fake Admin CP that may be used together with a [renamed Admin CP directory](#rename-the-admin-cp-directory), recording the IP of anyone who tries to login to it and emailing you a small report.

### External Tools
Some search engine webmaster tools offer alerts upon discovery of problems affecting websites, including malicious activity (e.g. [Bing](https://www.bing.com/toolbox/webmaster), [Google](https://search.google.com/search-console/about), [Yandex](https://webmaster.yandex.com/welcome/)), which may also help identify the issue.

## Environment
We recommend choosing reputable and trusted providers for domain, hosting, and other infrastructure services.

Forum staff with access to such administrative accounts should have 2-Factor Authentication (2FA) enabled and make sure hidden features like _reset password_ cannot be used to easily bypass it. Server management tools and other installed web applications should only be used over a secure connection (HTTPS, SFTP, SSH).

### Domain
Domains associated with the board should have a [registrar lock](https://en.wikipedia.org/wiki/Registrar-Lock) and [DNSSEC](https://en.wikipedia.org/wiki/Domain_Name_System_Security_Extensions) enabled to limit attempts of domain and traffic hijacking.

### Server
- #### Shared Hosting and Managed Servers
  You should verify that server software and tools (underlying operating system, web hosting control panel &mdash; _cPanel_/_DirectAdmin_, HTTP server, database system, PHP, _phpMyAdmin_, etc.) are kept up to date and the organization is capable of quickly responding to security concerns.

- #### VPS and Dedicated Servers
  Virtual or dedicated servers should be maintained by experienced system administrators. For more information you should look up articles on maintaining and securing servers relevant to the operating system and software (HTTP server, PHP, database system, etc.).

If the forum traffic is cached by accelerators or caching servers (e.g. _Varnish_), you should make sure they are configured properly and never cache the HTML content of MyBB-generated pages, especially those intended for authenticated users, as it may leak secret security tokens intended for individual users or visitors.

### Third Party Software
Applications installed on the same server may affect each other's functionality directly &mdash; by accessing foreign files, database or executing foreign code &mdash; and indirectly &mdash; e.g. by accessing server software. Vulnerability in third party software may threaten the security of the forum, therefore all web applications should be kept up to date and secured, similar to MyBB. For more information you should look up articles on securing any other software you have installed.


## Response Readiness
Administrators running MyBB forums should be familiar with steps and tools involved in the response to potential security incidents and data breaches:

[**MyBB Documentation &rsaquo; Security Incident Response & Recovery &rarr;**](/1.8/administration/security/recovery/)

---
See also:
- [**Security Research at MyBB &rarr;**](https://mybb.com/get-involved/security/)
- [**Known Security Issues in MyBB 1.8 &rarr;**](https://github.com/mybb/mybb/blob/feature/.github/SECURITY.md#known-security-issues)
- [**MyBB Community &rsaquo; Security Management and Support &rarr;**](https://community.mybb.com/forum-179.html)
- [**Contact MyBB Team regarding security concerns &rarr;**](https://mybb.com/contact/)
