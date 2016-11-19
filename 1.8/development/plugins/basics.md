---
layout: page
title:  "Plugin Basics"
categories: [plugins]
---

Plugins allow you to easily extend or modify MyBB in a modular way, so that changes can easily be activated, deactivated, installed, or uninstalled.
You can also safely replace the core MyBB files during upgrades without fear of losing your modifications. Therefore, it is strongly recommended that any changes to the default MyBB functionality are made via the plugin system, rather than modifying files.

Developing plugins requires a sound knowledge of PHP, SQL and enough knowledge of MyBB to navigate the core files so that you can find answers in the source code.
If you need help, post in the [Plugin Development section](https://community.mybb.com/forum-68.html) of the MyBB Community Forums for assistance from the community.

## Plugin Basics

First, you must pick a short lowercase string to name your plugin file and use in some of your plugin function names.
This string should be unique and relevant to your plugin. In this example we'll use "myplugin".

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
		"codename"		=> "",
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

The `_info()` function is the only required function. However, you should ensure any changes made by install or activate are reversed in uninstall or deactivate, respectively. For example, if you create a table in \_install() you should remove that table in \_uninstall().

Complete the body of the functions in your plugin file as required:

### `_info()`

Returns an array of information about the plugin:

 * name: The name of the plugin
 * description: Description of what the plugin does
 * website: The website the plugin is maintained at (Optional)
 * author: The name of the author of the plugin
 * authorsite: The URL to the website of the author (Optional)
 * version: The version number of the plugin
 * guid: Unique ID issued by the MyBB Extend site for version checking (Obsolete, prefer codename)
 * codename: Unique codename of the plugin in the mods section
 * compatibility: A CSV list of MyBB versions supported. Ex, "121,123", "12*". Wildcards supported.

#### N.B.
The _codename_ is the same as the plugin name used to prefix the functions. A good way to have it is to use the following code:

```php
$codename = str_replace('.php', '', basename(__FILE__));
```

### `_install()`

Called whenever a plugin is installed by clicking the "Install" button in the plugin manager.

If no install routine exists, the install button is not shown in the Admin CP and it is assumed that any work will be performed in the \_activate() routine.

It is common to create required tables, fields and settings in this function.

### `_is_installed()`

Called on the plugin management page to establish if a plugin is already installed or not.

This should return TRUE if the plugin is installed (by checking tables, fields etc) or FALSE if the plugin is not installed.

It is common to use the existence of a table or setting created in the `_install()` function to determine whether the plugin is installed or not. Below is a common implementation, assuming a table called `my_plugin` is created:

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

Called whenever a plugin is to be uninstalled. This should remove ALL traces of the plugin from the installation (tables etc). If it does not exist, the uninstall button is not shown in the Admin CP.

### `_activate()`

Called whenever a plugin is activated via the Admin CP. This should essentially make a plugin "visible" by adding/modifying templates, language changes, etc.

### `_deactivate`

Called whenever a plugin is deactivated. This should essentially "hide" the plugin from view by removing templates/template changes etc.
It should not, however, remove any information such as tables, fields etc.; that should be handled by an \_uninstall routine.
When a plugin is uninstalled, this routine will also be called before \_uninstall() if the plugin is active.

## Plugin Hooks

For your plugin to actually work, you need to "hook" your code into MyBB. This can be done in many places throughout MyBB code.

You can find a list of hooks [here](https://docs.mybb.com/1.8/development/plugins/hooks/). Alternatively you can run the following command on a \*nix system in a MyBB directory:

`grep -inr '$plugins->run_hooks' ./`

### Basic Usage

First add the hook by putting the following code above the `_info()` function near the top of your plugin file:

```php
$plugins->add_hook('<hook name>', '<function name>');
```

Where `<hook name>` is the name of the hook you wish to use, and `<function name>` is the name of a function in your plugin that will be run every time this hook is called.

**Note, it must be a function *name*, you shouldn't actually call the function here.**

Here is an example which used the `index_start` hook and calls the `do_something()` function:

```php
$plugins->add_hook('index_start', 'do_something');
```

Now you can implement the function you specified. This function must be either in your plugin file or included by your plugin.

For example, if you defined the following function in this plugin file it would be called every time `index_start` is called:

```php
function do_something()
{
    // Do whatever you want here
}
```

To achieve most things, you'll need to interact with the MyBB global variables such as `$mybb`, `$user`, `$db`, etc.

For example, this would test if the current user is an Admin:

```php
function do_something()
{
    global $mybb;
    if($mybb->usergroup['cancp'] == 1)
    {
        // Admin only
    }
    else
    {
        // Everyone else
    }
}
```

### Hooks with Arguments

Some hooks also pass a value relevant to the location where it's called. These hooks are added the same way, except you must add an argument to your plugin function.
In some cases, you must also return that value (which your plugin may have modified).

Here is an example of two hooks:

```php
$plugins->add_hook("pre_output_page", "hello_world");
$plugins->add_hook("postbit", "hello_world_postbit");
```

And two associated plugin functions, the first modifies the content of `$content` and returns it, the second modifies a value passed by reference.

```php
function hello_world($page)
{
	// This will add Hello World to the top of pages
	$page = str_replace(
        '<div id="content">',
        '<div id="content"><p>Hello World!</p>',
        $page
	);
	return $page;
}

function hello_world_postbit(&$post)
{
	// This will add Hello World to the top of all posts
	$post['message'] = '<strong>Hello world!</strong><br />' . $post['message'];
}
```

You'll need to check the context where the hook is called to determine whether it is necessary to return the argument back, or whether it should be modified by reference.

### Other Hook Options

There are two other optional arguments which can be passed to `$plugins->add_hook()`: priority and file.

For example:

```php
$plugins->add_hook('<hook name>', '<function name>', '<priority>', '<file>');

// With values
$plugins->add_hook('index_start', 'do_something', 5, 'anotherfile.php');
```

The `<priority>` takes into account if there are two or more functions that are associated with a hook. A lesser value in the priority parameter will mean the function will be executed before the other function(s) with a higher value priority (for example, a priority `0` will execute before `10`). The default priority is `10`. Usually you will not need to use this parameter unless you have two plugins that conflict with each other on one hook.

The file name in the `<file>` parameter will be "included-once" when the hook is run, before the function is executed.

## Plugin Settings

Plugins can create settings which integrate with the "Configuration" tab of the ACP.
General plugin options should be implemented using this method to ensure consistency between plugins.

Settings are usually added and removed in the `_install()` and `_uninstall()` methods, respectively, so that the plugin can be deactivated without losing the settings.

### Adding Settings

To create settings you must first create a setting group and get its ID:

```php
global $db, $mybb;

$setting_group = array(
    'name' => 'mysettinggroup',
    'title' => 'My Plugin Settings',
    'description' => 'This is my plugin and it does some things',
    'disporder' => 5, // The order your setting group will display
    'isdefault' => 0
);

$gid = $db->insert_query("settinggroups", $setting_group);
```

Now you can add some settings to the group:

```php
$setting_array = array(
    // A text setting
    'fav_colour' => array(
        'title' => 'Favorite Colour',
        'description' => 'Enter your favorite colour:',
        'optionscode' => 'text',
        'value' => 'Blue', // Default
        'disporder' => 1
    ),
    // A select box
    'green_good' => array(
        'title' => 'Is green good?',
        'description' => 'Select your opinion on whether green is good:',
        'optionscode' => "select\n0=Yes\n1=Maybe\n2=No",
        'value' => 2,
        'disporder' => 2
    ),
    // A yes/no boolean box
    'enable_lasers' => array(
        'title' => 'Enable lasers?',
        'description' => 'Do you want the lasers turned on?',
        'optionscode' => 'yesno',
        'value' => 1,
        'disporder' => 3
    ),
);

foreach($setting_array as $name => $setting)
{
    $setting['name'] = $name;
    $setting['gid'] = $gid;

    $db->insert_query('settings', $setting);
}

// Don't forget this!
rebuild_settings();
```

The following setting field type (aka. optionscode) values are supported:

* text : A regular text box
* numeric : A numeric field
* textarea : A larger text box
* yesno : A boolean yes/no control
* onoff : A boolean on/off control
* select : A select box (in the format select followed by <key>=<value> with one per newline)
* forumselect : A built-in radio + select box to select forums
* forumselectsingle : A built-in select box to select only one forum
* groupselect : A built-in radio + select box to select groups
* groupselectsingle : A built-in select box to to select only one user group
* radio : A set of radio buttons (in the format select followed by <key>=<value> with one per newline)
* checkbox : A boolean checkbox field
* language : A language selection box
* adminlanguage : An ACP language select
* cpstyle : A theme selector
* php : A php code

If you were to install the plugin, you'd now see your new setting group and its settings in the "Configuration" tab of the ACP.

You can access these values via `$mybb->settings['<setting name>']`, for example `$mybb->settings['enable_lasers']`.

### Removing settings

If you add settings in your `_install()` function you must also remove them in your `_uninstall()` function.

Here is an example of removing the above settings:

```php
global $db;

$db->delete_query('settings', "name IN ('fav_colour','green_good','enable_lasers')");
$db->delete_query('settinggroups', "name = 'mysettinggroup'");

// Don't forget this
rebuild_settings();
```

### Using Settings for `_is_installed()`

You may wish to use one of your settings to implement the `_is_installed()` function; here is an example:

```php

global $mybb;
if(isset($mybb->settings['green_good']))
{
    return true;
}

return false;
```
