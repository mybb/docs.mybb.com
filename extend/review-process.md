---
layout: page
title:  "Review Process"
categories: [extend]
---

The *Extend* platform provides an official, central directory of plugins, themes and other resources for MyBB. The Team assesses submissions in order to prevent issues related to:

- licensing,
- low quality,
- security,
- privacy,
- unclear code,
- incompatibility,
- undesirable effects on the Community or the Web.

Major problems related to new submissions, when spotted, can prevent it from appearing on the platform. Extension maintainers can additionally request technical reviews of specific builds (versions) to make it possible for other users to easily find safe extensions.

## Project Approval

Submissions of new projects, along with the initial build, must reviewed by the MyBB staff in order to appear on the platform. Projects submitted by *Approved Developers* are added immediately.

The Project Approval process involves basic checks performed to reduce duplicate submissions and prevent potential abuse of the *Extend* platform.

## Build Review

Selected builds can be submitted for review by project authors. Build-level reviews are more intensive and  can be interpreted as limited security audits (especially in plugin submissions). If the review passes successfully, the build is visually marked as reviewed and safe for use.

While the licensing and overall quality are being checked for submissions of all types, the principles of technical assessment differ and are explained below.

- ### Plugins
  
  Plugin packages' structure and types of files and operations can vary depending on intended purpose, however the package and its code should:
  
  - not overwrite MyBB's core files &mdash; [hooks](https://docs.mybb.com/1.8/development/plugins/hooks/) should be used instead,
  - not cause negative, unexpected or undocumented effects,
  - be free of vulnerabilities and security issues,
  - be easy to read and understand, which includes proper indenting, self-descriptive naming of variables, functions, classes, namespaces and files, consistency across the codebase and following a common style guide (like [PSR-2](http://www.php-fig.org/psr/psr-2/)),
  - be optimized to reduce unnecessary resource usage,
  - be compatible with latest versions of the web stack (PHP, MyBB-supported databases and HTTP servers).
  
- ### Themes
  
  Theme packages should be limited to:
  
  - XML files containing the theme data intended to be processed by MyBB,
  - default package's `index.html` files,
  - front-end design & UI functionality files (like JavaScript files, images in common graphic extensions),
  - metadata files (like licenses or  *README* files).
  
  Loading of resources from external locations, excluding common CDN sites, is not allowed.
  
- ### Translations
  
  Translation packages should be limited to:
  
  - PHP files that begin with the `<?php` tag and contain either:
    - string values assigned to the `$langinfo` variable language in manifest files and the `$l` variable in standard language files, which should not contain or cause output of any additional executable code (CSS, HTML, PHP, etc.) when compared with the default language package,
    - PHP comments,
    - empty lines.
  - default package's `index.html` files,
  - images with texts in the translated language,
  - metadata files.

- ### Graphics

  Graphics-related submissions should only contain files in common raster or vector graphic formats. Optional metadata files are also allowed.



## Hosting code in *git* repositories

We encourage authors to host and maintain their extensions with the  *git* version control system, which is also used for MyBB core development.

Platforms like [GitHub](https://github.com/), [GitLab](https://about.gitlab.com/) or [Bitbucket](https://www.atlassian.com/software/bitbucket) provide free hosting of *git* repositories which allow easier contribution, management and code inspection.

Using code repositories can often speed up the approval and review process of *Extend* submissions.