---
layout: page
title:  "Datacache"
categories: [development]
---

# Datacache

Besides dedicated database table structures, MyBB utilizes a data cache system. Cache entries are saved in the `mybb_datacache` table and propagated to [configured](/1.8/administration/configuration-file/) cache store.

The following table lists default content of the Admin CP's **Tools & Maintenance &rarr; Cache Manager**. Entries with  _Redundancy_ are usually created for performance improvements and can be rebuilt automatically using the database.

Name | Storage | Redundancy
-|-|-
`adminnotes` | Datacache system | No (cache-only)
`internal_settings` | Datacache system | No (cache-only)
`modnotes` | Datacache system | No (cache-only)
`mostonline` | Datacache system | No (cache-only)
`plugins` | Datacache system | No (cache-only)
`update_check` | Datacache system | No (cache-only)
`version` | Datacache system | No (cache-only)
`version_history` | Datacache system | No (cache-only)
`attachtypes` | Datacache system | Yes
`awaitingactivation` | Datacache system | Yes
`badwords` | Datacache system | Yes
`banned` | Datacache system | Yes
`bannedemails` | Datacache system | Yes
`bannedips` | Datacache system | Yes
`birthdays` | Datacache system | Yes
`default_theme` | Datacache system | Yes
`forumpermissions` | Datacache system | Yes
`forums` | Datacache system | Yes
`forumsdisplay` | Datacache system | Yes
`groupleaders` | Datacache system | Yes
`mailqueue` | Datacache system | Yes
`moderators` | Datacache system | Yes
`most_replied_threads` | Datacache system | Yes
`most_viewed_threads` | Datacache system | Yes
`mycode` | Datacache system | Yes
`posticons` | Datacache system | Yes
`profilefields` | Datacache system | Yes
`reportedcontent` | Datacache system | Yes
`reportreasons` | Datacache system | Yes
`smilies` | Datacache system | Yes
`spiders` | Datacache system | Yes
`statistics` | Datacache system | Yes
`stats` | Datacache system | Yes
`tasks` | Datacache system | Yes
`threadprefixes` | Datacache system | Yes
`usergroups` | Datacache system | Yes
`usertitles` | Datacache system | Yes
`settings` | PHP file (`inc/settings.php`) | Yes
