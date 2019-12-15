---
layout: page
title:  "Security Incident Response & Recovery"
categories: [security]
description: "Recovering a Hacked or Compromised Forum"
---

Numerous actions and conditions can leave web applications open to exploitation. These can be related to administrator errors (like misconfiguration and social engineering) or factors out of their control (like software vulnerabilities and external data breaches), and can occur even after following [**best security practices and recommendations**](/1.8/administration/security/protection/).

Discover which components may be abused by attackers to run malicious code after gaining access, review common recovery steps, and learn how to respond to security incidents to protect your forum and users.

_This article provides advice for most common setups, focusing on MyBB, and is intended for administrators with technical experience. Specific steps and their order may depend on configuration, incident circumstances and discovered evidence. It is generally recommended to contact a security professional familiar with modern web stack technology and refer them to this page to recover and secure impacted installations._

## Overview
**Unverified code and data should be considered quarantined** and no interaction with them should take place. This establishes the following order of verification and recovery actions:
1. administrators' devices and personal accounts,
1. domains, hosting accounts, reverse proxies, origin servers and additional infrastructure, TLS certificates,
1. other installed applications/scripts,
1. MyBB source code,
1. MyBB stored data,
1. MyBB upgrades,
1. MyBB Admin CP's internal verification tools,
1. MyBB Settings and configuration,
1. MyBB front-end templates,
1. MyBB Extensions,

followed by remaining recovery operations. Elements and sections should not be used or accessed by anyone before they are
verified as safe (e.g. forum pages should not be visited until MyBB code & data is reviewed and the board is upgraded).

All steps taken during the recovery process should be documented, including timestamps and signs & effects of suspicious activity. This information may be useful during investigation, consultation and help composing an incident report.

Whenever an SQL query is provided, we assume your table prefix is `mybb_` &mdash; if you have a different table prefix, remember to replace it.

## Containment

### Restrict Access to the Forum
Access to a compromised forum should be disabled as soon as possible to reduce potential damage. This can be achieved by modifying the server configuration:

- #### Apache 2.4 servers
  Add the following code in the `.htaccess` file in the MyBB root directory:
   ```apache
   Require all denied
   Require ip 127.0.0.1
   ```

- #### Apache 2.2 servers
  Add the following code in the `.htaccess` file in the MyBB root directory
   ```apache
   Order deny,allow
   Deny from all
   Allow from 127.0.0.1
   ```

- #### Nginx servers
   Add the following code to server block configuration for the forum:
   ```nginx
   location / {
     allow 127.0.0.1;
     deny all;
   }
   ```

Replace `127.0.0.1` with [your IP address](https://icanhazip.com/); if you find yourself unable to access your website during this process, it is possible that you have a dynamic IP, in which case you will have to repeat the above procedure whenever your IP changes.

You can also close the forum using the _Board Closed_ setting. To avoid using the Admin CP:
- execute the following SQL commands:
```sql
UPDATE mybb_settings SET value = '1' WHERE name = 'boardclosed'; -- Close the board
UPDATE mybb_settings SET value = '' WHERE name = 'boardclosed_reason'; -- Remove malicious "reason" content
```
and delete the `inc/settings.php` file, **or**

- in `inc/settings.php`, change the value of `$settings['boardclosed']` to `1` (it will be reset if settings are rebuilt, e.g. by saving any setting in the ACP).


## Analysis

### Create Copies
To help investigate the cause of the incident, create a backup of files, database, and servers (if feasible), and save any related logs (access log, error log, FTP log, etc.).

### Identify Causes
To have a better understanding of what happened and what actions were performed, take time to review gathered logs to help establish a timeline of the attack and weaknesses leading to it, as well as attack artifacts, such as malicious data and file modifications. While the causes may be unrelated to the state of your MyBB installation, we recommend keeping affected websites offline until all potential problems are eliminated.

## Mitigation & Recovery

### Staff Devices and Accounts
It is possible that an administrator has downloaded something that infected their device(s) allowing the forum to be hacked, which makes it not safe to do anything else until it is 100% clean.

[**MyBB Documentation &rsaquo; MyBB Security Guide: General Advice &rarr;**](/1.8/development/directory-structure/)

### Infrastructure & Environment
Before recovering your MyBB installation, you should secure access to domains, hosting accounts, reverse proxy, server and additional infrastructure, TLS certificates, as well as other installed applications/scripts.

### MyBB Files
To ensure that your MyBB installation is clean and no extra files have been added, delete all hosted files and upload a  fresh copy of the [latest version of MyBB](https://mybb.com/download/) (after [verifying the downloaded package](https://mybb.com/download/verifying/)).

Manually rebuild the [configuration file](/1.8/administration/configuration-file/), entering database connection details and other necessary values.

### MyBB Database
Due to lack of HTML filtering in some portions of the Admin CP and the front-end, malicious code can continue to be executed whenever MyBB is used, and will need to be removed first.

The following actions may be recommended in the table below:
- **Delete & Import**

  For tables with content difficult to review manually:
  1. completely delete (`DROP`) the table,
  2. use structure and default content imported from a new MyBB installation (with the same version as the affected installation).

  Custom content may also need to be reviewed manually and restored after recovery.

- **Clear**

  For tables storing temporary or easily replaceable data: delete all content by executing a `DELETE` SQL command:
  ```sql
  DELETE FROM mybb_example;
  ```

- **Review**

  For tables storing data that may need to be preserved: use an external tool to list raw values of stored rows and search for suspicious content (usually containing `'`, `"`, `<` characters, intended to break existing HTML tags or insert new ones).

#### Recommended Actions for MyBB Database Table Content

Table Name | Content | Default Content | Recommended Action | Alternative Action (if not used/customized)
-|-|-|-|-
`mybb_adminoptions` | ACP preferences, notes, permissions (other than _Home_ section) | Yes | Clear
`mybb_adminsessions` | ACP login sessions | No | Clear
`mybb_adminviews` | ACP View filters for user listing | Yes | Delete & Import
`mybb_delayedmoderation` | Delayed Moderation | No | Clear
`mybb_helpdocs` | Help Documents | Yes | Delete & Import
`mybb_helpsections` | Help Documents sections | Yes | Delete & Import
`mybb_mailqueue` | Mass Mail Queue | No | Clear
`mybb_calendars` | Calendars | Yes | Review | Delete & Import
`mybb_datacache` | [**Datacache**](/1.8/development/datacache/) | Yes | Delete [_Redundant_ entries](/1.8/development/datacache/); Review remaining entries
`mybb_forums` | List of Forums and Categories | Yes | Review
`mybb_threadprefixes` | Thread Prefixes | No | Review | Clear
`mybb_usergroups` | User Groups | Yes | Review
`mybb_profilefields` | Custom Profile Fields | Yes | Review | Delete & Import
`mybb_mycode` | Custom MyCode | No | Review | Clear
`mybb_settings` | Settings metadata and values | Yes | Delete & Import
`mybb_spiders` | Spiders / Bots | Yes | Review | Clear
`mybb_templates` | Templates | Yes | Delete & Import
`mybb_templatesets` | Template Sets | Yes | Delete & Import
`mybb_themes` | Themes | Yes | Delete & Import
`mybb_themestylesheets` | Theme Stylesheets | Yes | Delete & Import
`mybb_usertitles` | User Titles | Yes | Review | Clear

#### Selective Modifications
Execute the following SQL query to mitigate dangerous values in other tables:
```sql
UPDATE mybb_banned SET oldgroup = '2', oldadditionalgroups = '', olddisplaygroup = ''; -- Prevent ban expirations from upgrading users to groups other than "Registered"
```

MyBB Extensions may use additional tables that will need to be reviewed.

#### General SQL Errors
You may during this process run into some common SQL Errors, we recommend to first search these on the [Error Messages](/1.8/faq/errors/) document as a solution should be there. If not you can open a support thread on our forums &mdash; [MyBB Forums](https://community.mybb.com/).

### Locally Stored Data
Malicious code served by compromised websites may be saved locally in the browser (e.g. cookies, cache, workers). This can be mitigated by [instructing browsers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Clear-Site-Data) to clear all data.

Copy the following code, replacing `RANDOM_VALUE` with a [random value](https://www.random.org/strings/?num=1&len=20&digits=on&upperalpha=on&loweralpha=on&unique=on&format=plain&rnd=new), and add it to the end of the `inc/init.php` file:

```php
// https://docs.mybb.com/1.8/administration/security/recovery/
$clearDataToken = 'RANDOM_VALUE';

if (!isset($mybb->cookies['clear_data_token']) || $mybb->cookies['clear_data_token'] !== $clearDataToken) {
    header('Clear-Site-Data: "cookies", "cache", "storage", "executionContexts"');
    header('Refresh: 0');

    my_setcookie('clear_data_token', $clearDataToken);

    exit;
}
```

The code should be active for at least 24 hours (the maximum lifetime of installed [service workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)) after removing server-side infections.

Forum users with elevated privileges should, in addition, manually clear cookies and other site data stored in their browsers.

## Mitigate Impact of Stolen Data

### Invalidate Tokens
The database may contain sensitive tokens that can be used on the restored forum, and should be removed &mdash; execute the following SQL query:
```sql
DELETE FROM mybb_adminsessions; -- Purge ACP login state
DELETE FROM mybb_awaitingactivation WHERE type == 'p'; -- Purge password reset requests
UPDATE mybb_datacache SET cache = 'a:1:{s:14:"encryption_key";s:0:"";}' WHERE title = 'internal_settings'; -- Reset encryption_key used with anti-SCRF tokens
UPDATE mybb_users SET loginkey = ''; -- Purge front-end login state and anti-CSRF tokens
```

### Change API Keys
Secret API keys that may have been compromised should be re-generated (or deactivated and re-created) at their providers (e.g. the _Stop Forum Spam API Key_) and replaced in MyBB Settings later on. Extensions may maintain additional values that will need to be changed.

### Remove Online Database Backups
Database backups previously [generated by MyBB](/1.8/administration/backups/) that are still stored within the directory structure (by default: `admin/backups/`) should be moved or deleted, as the disclosure of filenames may make it easier to obtain them by an attacker.

### Reset Passwords
User passwords should be reset (regardless of hashing algorithms used) &mdash; execute the following SQL query:
```sql
UPDATE mybb_users SET password = '';
```

First login attempts will be rejected by MyBB, forcing users to reset their passwords by e-mail.

## Using MyBB Again

### Restore Your Admin Account
Admin Control Panel access can be restored easily by configuring [super administrators](/1.8/administration/security/protection/#configure-super-administrators). If you are having trouble signing in, follow the article on login problems to fix cookie issues or reset your password with an SQL query:

[**MyBB Documentation &rsaquo; Login Problems &rarr;**](/1.8/faq/login-problems/)

### Perform MyBB Upgrades
If you were running an older version of MyBB, [upgrade the board](/1.8/install/upgrade/) first, as old versions may contain vulnerabilities addressed in more recent releases.

### Run Integrity Checks
- Use the **Tools & Maintenance &rarr; File Verification** tool to verify file integrity. You can also use the [DVZ Integrity Tools](https://community.mybb.com/mods.php?action=view&pid=980) plugin to verify the structure integrity of MyBB database tables.
- Validate templates using **Tools & Maintenance &rarr; System Health &rarr; Check Templates**.
- Go to **Home &rarr; Dashboard &rarr; Check for Updates** and make sure the board's version is identical to latest MyBB
version.

### Review Settings and Forum Behavior
Re-adjust MyBB Settings (**Configuration &rarr; Settings**) that have been reverted to default values in previous steps and review all other options, especially:
- Moderator Tools (**Configuration**),
- forum moderators (**Forums & Posts &rarr; Forum Management**),
- Admin Permissions (**Users & Groups**),
- _Moderation/Administration Options_ and _Group Leaders_ of all User Groups (**Users & Groups &rarr; Groups**),
- Group Promotions (**Users & Groups**).

## Review MyBB Logs
In addition to access logs generated by the server, you should review MyBB's own logs that may contain information related to the security breach and actions executed automatically after the forum was restored:
- **Tools & Maintenance &rarr; Logs**,
- **Users & Groups &rarr; Mass Mail &rarr; Mass Mailing Archive**,
- **Users & Groups &rarr; Group Promotions &rarr; View Promotion Logs**,
- **Tools & Maintenance &rarr; Task Manager &rarr; View Task Logs**.

### Review & Restore Customizations
If you have customized your board using plugins, themes, images, language packs and other custom modifications, you can use one of the previous backups to review and restore them (note it is possible that a vulnerability lies within such customizations).

[**MyBB Documentation &rsaquo; Directory Structure &rarr;**](/1.8/development/directory-structure/)

## General Security Measures
**Continue with the general MyBB Security Guide** to finish securing your board: existing measures may have not been implemented correctly, or may have been compromised.

[**MyBB Documentation &rsaquo; Security Guide &rarr;**](/1.8/administration/security/protection)

## Notification

### Affected Users
It is considered industry practice (and may be required by law) to make affected users aware of a potential data breach, usually by e-mail. This notification should be easy to understand for non-technical users and include:
 - a description of what happened and when,
 - what information was, or may have been, affected,
 - potential consequences for people whose data was involved,
 - what measures you have taken, are taking, or will take to mitigate the problem,
 - steps people should take to reduce potential impact of the event (like changing passwords on your forums and any other websites/applications where the password was re-used),
 - contact details.

It is also a good idea to add an easily discoverable announcement thread with same details.

### Local Authorities
Depending on the country of operation, supervisory authorities may need to be notified about data breaches.
Additionally, administrators may be required, or choose, to report malicious activity to law enforcement organizations.

Selected data breach regulations:
- [GDPR &mdash; Communication of a personal data breach to the data subject](https://gdpr.algolia.com/gdpr-article-34) (European Union)
- [GDPR &mdash; Notification of a personal data breach to the supervisory authority](https://gdpr.algolia.com/gdpr-article-33) (European Union)
- [Information Commissioner's Office &mdash; Personal data breaches](https://ico.org.uk/for-organisations/guide-to-data-protection/guide-to-the-general-data-protection-regulation-gdpr/personal-data-breaches/) (United Kingdom)
- [NCSL &mdash; Security Breach Notification Laws](http://www.ncsl.org/research/telecommunications-and-information-technology/security-breach-notification-laws.aspx) (United States)

### Hosting Company
We recommend contacting your hosting company if you have difficulty identifying attackers' entry points (especially if using shared hosting). There is a possibility that the attackers used host servers outside of your control first, or found a way to access it through your web account. The web host may also be able to provide additional information like logs and backups that may help with the recovery process.

### MyBB Team
You can [contact the MyBB Team](https://mybb.com/contact/) to share details related to the incident, especially if you suspect the breach to be related to vulnerabilities in MyBB or extensions. This information will also help track exploitation attempts of active MyBB boards.

---
See also:
- [**Security Research at MyBB &rarr;**](https://mybb.com/get-involved/security/)
- [**MyBB Community &rsaquo; Security Management and Support &rarr;**](https://community.mybb.com/forum-179.html)
