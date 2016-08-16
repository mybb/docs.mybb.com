---
layout: page
title:  "Column Length Check"
categories: [merge]
order: 3
---

**Note:** If you haven't got a similar error after the database configuration module, you can safely ignore this page.
[![Error Page](/assets/images/merge/column_length_error.png)](/assets/images/merge/column_length_error.png)

# What's causing the error?

As the database schema is different for other forums, it may happen that it's not possible to save the old data in the MyBB database. However, the merge system detects those cases and warns you about that.

# What can I do?

You can either increase the column length (the merge system will detect those changes) or simply ignore it. You won't get any errors during the merge as the data will be shortened automatically to fit in the MyBB database.

# How to increment the column length?

Since the MyBB Group doesn't support custom database changes, you may get problems during MyBB upgrades in the future. Issues with plugins may be experienced as well. Therefore we don't include information about modifying the columns length here. If you don't know what you need to do to get it working, it's not recommended for you to try changing it.
