---
layout: page
title:  "Directory Structure"
categories: [development]
---

# Directory Structure

Locations marked as "_internal_" contain source code or other files that don't need to be accessible through the web, and remote access can be safely restricted. Installed extensions may need relaxing such restrictions to work properly.

### MyBB's Root Directory
- **admin/** &mdash; files related to the Admin Control Panel; name may be safely changed in the configuration file to improve security
  - **backups/** &mdash; default location for database backups _(internal)_; should not be accessible remotely
  - **inc/** &mdash; source code _(internal)_
  - **jscripts/** &mdash; user interface scripts accessed by the browser
  - **modules/** &mdash; source code for specific ACP pages _(internal)_
  - **styles/** &mdash; user interface scripts accessed by the browser

- **archive/** &mdash; archive mode-related files
  - **index.php** &mdash; interface
  - **global.php** &mdash; source code _(internal)_
  - **print.css**, **screen.css** &mdash; interface-related files

- **cache/** &mdash; pre-generated source code and interface files
- **images/** &mdash; static interface files (usually images)
- **inc/** &mdash; source code files _(internal)_
  - **3rdparty/** &mdash; external software included in MyBB _(internal)_
  - **languages/** &mdash; language pack directories _(internal)_
    - `LANGUAGE-NAME/` &mdash; phrase files of a language pack
    - `LANGUAGE-NAME.php` &mdash; metadata file for a language pack
  - **plugins/** &mdash; plugin source code files _(internal)_

  - **config.default.php** &mdash; renamed to _config.php_ after installation
  - [**config.php** &mdash; the MyBB configuration file]({{ site.baseurl }}/1.8/administration/configuration-file/) (database connection details and security options)
  - **settings.php** &mdash; compiled contents of the board's Settings

- **install/** &mdash; files related to the MyBB installer and upgrade script; should be removed after use
- **jscripts/** &mdash; static JavaScript and related files
- **uploads/** &mdash; user-supplied content;
  - **avatars/** &mdash; uploaded avatar images (in the `avatar_USER-ID.EXTENSION` format)
  - **`YYYYMM`/** year & month number pattern &mdash; directories generated for storing raw attachment files; should not be accessible remotely _(internal)_
    - `*.attach` files &mdash; raw attachment files, usually in the `post_USER-ID_UNIX-TIMESTAMP_RANDOM-STRING.attach` format
    - `*_thumb.EXTENSION` &mdash; image preview files for attachments

- **global.php** &mdash; source code _(internal)_  
- other **\*.php** files in the root directory &mdash; HTTP-accessible MyBB interface

### Additional Files

- **index.html** &mdash; files placed in directories to prevent web servers from listing all files within them when accessed through web
- **.htaccess** &mdash; server rules related to redirections and security features (Apache servers only)
- **error.log** &mdash; default name of log files containing information about encountered errors for developers; usually found in the root directory and `admin/`; should not be accessible remotely _(internal)_
