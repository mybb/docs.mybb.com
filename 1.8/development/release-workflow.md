---
layout: page
title:  "Release Workflow"
categories: [development]
---

1. ### Source Code
   These changes can be applies during normal development in the public repository, or as patches stored in the data repository and applied to final packages by the build script.

   - #### Version Metadata
   MyBB's version and the corresponding version code (digit-only format) is hardcoded in multiple locations:
     - `MyBB::$version`, `MyBB::$version_code` (_inc/class_core.php_)

       Indicates the current version. As a result, a modified `inc/class_core.php` file is always included in the update package.
     - `$langinfo['version']` in the English language manifest (_inc/languages/english.php_)

       Indicates the latest version in which changes to language phrases occurred. If no phrases were modified, this values is left unchanged.
     - `version` attributes of `<theme>`, `<stylesheet>`, `<template>` (_install/resources/mybb_theme.xml_)

       Indicates the latest version in which changes to the default theme occurred, and in specific stylesheets and templates. If the theme was not modified, these values are left unchanged.
   - #### Update File
     Modified templates and settings should result in a `install/resources/upgrade*.php` file created for the upgrade process (no custom code is needed for synchronization of templates and settings). See [examples](https://github.com/mybb/mybb/tree/feature/install/resources).

     The file's comment is [parsed](https://github.com/mybb/mybb/blob/cfe8257da0b017001a0f1af16f7d20f461b889ba/install/upgrade.php#L318) by the upgrade script, and should indicate which previous versions the script applies to.

1. ### Repository Maintenance
   - #### Public Repositories
     Issue and Pull Requests are reviewed to ensure that:
     - the version [Milestone](https://github.com/mybb/mybb/milestones) doesn't contain unresolved entries,
     - all Issues resolved after the previous version are assigned to the new version's Milestone,
     - correct metadata is attached to Milestone entries (i.a. closed; `s:resolved` label).

     The final public commit for the version is marked with a signed `mybb_*_build` git tag.

   - #### Internal Repositories

     Final security patches (if any) are added to the data repository on the `mybb_*_build` branch.

1. ### Pre-Release Public Testing
   The `mybb_*_build` git tag is used to provide downloadable packages of the final codebase that excludes non-public patches.

   1. A pinned [announcement thread](https://community.mybb.com/thread-219265.html) is created in the [Development forum](https://community.mybb.com/forum-165.html).

      Values copied from the internal _Getting * Ready_ thread:
      - _Comment_, basing on the `comment` value in _Additional values for version .md_ (if present; converted from Markdown to MyCode)
      - _Testing focus_ list, basing on _Public QA focus_ (if present)

   1. The link is shared and pinned in the public Discord `#18-development` channel.

   Codebase changes applied after the announcement are noted in the thread.

   The recommended minimum waiting period between the announcement and the version's final release is 7 days.

1. ### Package Building and Testing
   The [`mybb/mybb-build`](https://github.com/mybb/mybb-build) build script is used to perform tasks related to preparing releasable packages and associated information.

   1. The [`mybb/mybb-build`](https://github.com/mybb/mybb-build) repository is downloaded.
   1. Previous content of `input/patches/` is deleted (if any).
   1. The build properties in the `input/build.properties` file are configured:
     - `targetVersion`: the version number
     - `sourceRepositoryBranch`: the tag/branch in the [`mybb/mybb`](https://github.com/mybb/mybb) repository; usually `mybb_*_build`, or `mybb_*` pointing to a previous MyBB version for a security-only release
     - `inputFilesRepositoryBranch`: the branch in the data repository; usually `mybb_*_build`, or `master` if no patches are necessary
     - `includeInstallInUpdateSet`: `true` if running the upgrade script is required, `false` otherwise
     - `packageDate`: the build date (GMT+0)
   1. The build process is [run](https://github.com/mybb/mybb-build#readme).
   1. The build log is verified.
   1. The `input/` and `output/` directories are added to a `build_*_rc*.zip` archive (indicating the version code and the Release Candidate number).
   1. The created archive is signed with the Team member's public key.
   1. A post is added to the _Getting * Ready_ thread, including:
      - tags and commit hashes of repositories used during the build process:
        - [`mybb/mybb`](https://github.com/mybb/mybb)
        - the data repository
        - [`mybb/mybb-build`](https://github.com/mybb/mybb-build)
      - downloadable package and the Team member's signature
      - Release Candidate (RC) number
   1. A link to the package post is added to the _Packages_ list in the first post:
      ```
      https://... RC1 (YYYY-MM-DD 00:00)
      ```

      Links to posts with previous packages are crossed out (`[s]...[/s]`).

   1. The link to the package post is posted in the internal Discord `#staff-18-organization` channel, indicating the RC number.
   1. The packages are tested by Team members according to the _Internal QA focus_ list in the _Getting * Ready_ thread.

   The recommended minimum waiting period between the last Release Candidate is added and the version's final release is 3 days.

1. ### Announcements Preparation

   The package- and version-related information is completed and verified internally:
   - Updates to the MyBB.com website ([`mybb/mybb.com`](https://github.com/mybb/mybb.com)):
     - `_versions/*.md` [version metadata](https://github.com/mybb/mybb.com/tree/gh-pages/_versions/#versioning-metadata) for Release Notes, combined from:
       - the partial `*.md` file generated by the build script
       -  _Additional values for version .md_ from the _Getting * Ready_ thread
     - [`checksums/release_mybb_*.txt`](https://github.com/mybb/mybb.com/tree/gh-pages/checksums) checksums file, fully generated by the build script.
   - Release [Blog](https://blog.mybb.com/) Post, with:
      - the title and content generated by Jekyll basing on the version metadata at `/versions/release-blog-post/` (locally), separated by a `---` line,
      - the author set to _MyBB Team_,
      - tags _Release_, _Updates_, and _Security_ if the release addresses security-related issues.
   - Updates to the Docs.MyBB.com website ([`mybb/docs.mybb.com`](https://github.com/mybb/docs.mybb.com)):
     - [`_data/mybb18_plugin_hooks.yml`](https://github.com/mybb/docs.mybb.com/blob/gh-pages/_data/mybb18_plugin_hooks.yml) plugin hook data, fully generated by the build script.

1. ### Publication

   The packages and associated information are published. These tasks should be executed without unnecessary delay.

   1. **The packages are uploaded** to `resources.mybb.com` and verified.
   1. **The MyBB.com website is updated** by pushing new files to the [`mybb/mybb.com`](https://github.com/mybb/mybb.com) repository:
      - `_versions/*.md` [version metadata](https://github.com/mybb/mybb.com/tree/gh-pages/_versions/) (producing Release Notes and updating MyBB.com latest version information),
      - `checksums/release_mybb_*.txt` checksums.

      The new [mybb.com/download](https://mybb.com/download/) page and the version's Release Notes are verified.

      The download links for packages on the Release Notes page are verified.
   1. **The Release Blog Post is published**.
   1. A link to the Release Blog Post is posted in:
      - [@mybb](https://twitter.com/mybb) on Twitter (automated by _WordPress.com_),
      - [@mybbsecurity](https://twitter.com/mybbsecurity) on Twitter (security releases only), indicating the number of addressed vulnerabilities per severity:
        ```
        MyBB 1.8.x addressing (...) high, (...) medium, (...) low risk vulnerabilities has been released. https://blog.mybb.com/...
        ```
      - public Discord `#18-support` channel (pinned message; links related to previous versions are unpinned).

1. ### Repository Updates

   1. Synchronization commits, based on individual non-public patches are pushed to the public repository (if any).
   1. The resulting `mybb/mybb` repository state is tagged (signed `mybb_18xx` git tag indicating the version code).
   1. A [Release](https://github.com/mybb/mybb/releases) is created and all packages are attached (`mybb_*.zip`, `changed_files_*.zip`, and `build_*.zip`, containing the input and output of the build script).
   1. GitHub is added to the list of package locations in the [version metadata](https://github.com/mybb/mybb.com/tree/gh-pages/_versions/) file:

      ```yaml
        locations:
          - name: github.com/mybb/mybb/releases/
      ```

1. ### Advisory Publication
   1. Security Advisories for addressed vulnerabilities are published.
   1. Links to published Security Advisories are added to:
      - the Release Blog Post:

        ```html
        Medium risk: Example vulnerability (<a href="...">advisory</a>) — reported by ...
        ```

      - the Release Notes:

        ```yaml
        references:
          - url: ...
            title: "Advisory: ..."
            type: advisory
        ```

   1. Titles and links to published Security Advisories are added as replies to the [@mybbsecurity](https://twitter.com/mybbsecurity) version announcement tweet:

      ```
      Advisory: ... https://...
      ```

1. ### Archiving
   The Release Notes and Release Blog Post pages are archived using [web.archive.org](https://web.archive.org/save).

1. ### Documentation & Forum Updates
   1. #### Documentation
      - The plugin hooks data (`_data/mybb18_plugin_hooks.yml`) is pushed to the Docs repository.
      - The version [Milestone](https://github.com/mybb/mybb/milestones) is closed.
      - A new [Milestone](https://github.com/mybb/mybb/milestones) is created for the next version.

   1. #### Community Forums & Discord
      - ##### Public
        - The Pre-Release thread is unpinned and locked.
        - The link to the Pre-Release thread in the public Discord `#18-development` channel is unpinned.

   1. #### Third Parties
      - ##### [Security Workflow](/1.8/development/security-workflow/#final-feedback)
        - Reporters of addressed security issues are contacted.
        - CVE update requests are submitted to relevant CNAs.

   1. #### Internal
      - The _Post-release tasks_ list is checked.
      - A link to the Release Blog Post is posted in the _Getting * Ready_ thread.
      - The _Getting * Ready_ thread is unpinned.
      - A new _Getting * Ready_ thread is created and pinned.
