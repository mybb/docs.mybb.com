---
layout: page
title:  "Plugins"
---

Plugins allow you to easily extend or modify MyBB in a modular way, such that changes can easily be activated, deactivated, installed or uninstalled.
You can also safely replace the core MyBB files  during upgrades without fear of losing your modifications, therefore it is strongly recommended that any changed to the default MyBB functionality be done via the plugin system rather than modifying files.

Developing plugins requires a sound knowledge of PHP, SQL and enough knowledge of MyBB to navigate the core files so that you can find answers in the source code.
If you require help please don't hesitate to post in the [plugin development section](http://community.mybb.com/forum-68.html) of the community forums.

## Plugin basics

Firstly, you must pick a short lowercase string to name your plugin file and use in some of your plugin function names.
This string should be unique and relevant to your plugin, for the sake of this example we'll use "myplugin".

Create a PHP file for your plugin at `inc/plugins` and name it according to the above, for example `inc/plugins/myplugin.php`.

Start by putting the following code into your plugin file:

```php
<?php

// Disallow direct access to this file for security reasons
if(!defined("IN_MYBB"))
{
	die("Direct initialization of this file is not allowed.");
}


function myplugin_info()
{
	return array(
		"name"			=> "",
		"description"	=> "",
		"website"		=> "",
		"author"		=> "",
		"authorsite"	=> "",
		"version"		=> "1.0",
		"guid" 			=> "",
		"compatibility" => "*"
	);
}

function myplugin_install()
{

}

function myplugin_is_installed()
{

}

function myplugin_uninstall()
{

}

function myplugin_activate()
{

}

function myplugin_deactivate()
{

}

```

**The functions listed above _must_ be prefixed with the name of the plugin file.** Therefore you should replace `myplugin` with the name of your plugin file, for example `myplugin_info` should be called `foobar_info` if your plugin file was named `foobar.php`.

The `_info()` function is the only required function, however you should ensure any changes made by install or activate are undone in uninstall or deactivate respectively. For example if you create a table in _install() you should remove that table in _uninstall().

Complete the body of the functions in your plugin file as required:

### `_info()`

Returns an array of information about the plugin:

 * name: The name of the plugin
 * description: Description of what the plugin does
 * website: The website the plugin is maintained at (Optional)
 * author: The name of the author of the plugin
 * authorsite: The URL to the website of the author (Optional)
 * version: The version number of the plugin
 * guid: Unique ID issued by the MyBB Mods site for version checking
 * compatibility: A CSV list of MyBB versions supported. Ex, "121,123", "12*". Wildcards supported.

### `_install()`

Called whenever a plugin is installed by clicking the "Install" button in the plugin manager.

If no install routine exists, the install button is not shown and it assumed any work will be performed in the _activate() routine.

It is common to create required tables, fields and settings in this function.

### `_is_installed()`

Called on the plugin management page to establish if a plugin is already installed or not.

This should return TRUE if the plugin is installed (by checking tables, fields etc) or FALSE if the plugin is not installed.

It is common to use the existence of a table or setting created in the `_install()` function to determine whether the plugin is installed or not, for example this is a common implementation assuming a table called `my_plugin` is created:

```php
function myplugin_is_installed()
{
    global $db;
    if($db->table_exists("my_plugin"))
    {
        return true;
    }
    return false;
}
```

### `_uninstall()`

Called whenever a plugin is to be uninstalled. This should remove ALL traces of the plugin from the installation (tables etc). If it does not exist, uninstall button is not shown.

### `_activate()`

Called whenever a plugin is activated via the Admin CP. This should essentially make a plugin "visible" by adding templates/template changes, language changes etc.

### `_deactivate`

Called whenever a plugin is deactivated. This should essentially "hide" the plugin from view by removing templates/template changes etc.
It should not, however, remove any information such as tables, fields etc - that should be handled by an _uninstall routine.
When a plugin is uninstalled, this routine will also be called before _uninstall() if the plugin is active.

## Plugin hooks

For your plugin to actually work, you need to "hook" your code into MyBB. This can be done in many places throughout MyBB code.

You can find a list of hooks [here](hooks), alternatively you can run the following command on a *nix system in a MyBB directory:

`grep -inr '$plugins->run_hooks' ./`

### Hook usage

