---
layout: page
title:  "Creating a New Page"
categories: [plugins]
---

## Creating a New Page / Action

Sometimes it is useful to create a new, dedicated page for your plugin. Perhaps there would otherwise be too many links needed to get to different controls/settings for your plugin, or maybe more freedom in customizing the design of a UI for your plugin would be helpful. In this case, creating a dedicated page would be a viable solution. There are two ways to do this.

Using misc.php allows you to add custom "pages" without creating a new PHP file yourself, and lets you deal with just the standard core files and a plugin file. However, if you need even more flexibility, you can use a separate file to achieve your goal.

### Using `misc.php`

An easy way to add a custom page via a plugin is to use the `misc_start` hook.

```php
$plugins->add_hook('misc_start', 'my_action');

// In the body of your plugin
function my_action()
{
    global $mybb, $templates, $lang, $header, $headerinclude, $footer;

    if($mybb->get_input('action') == 'myaction')
    {
        // Do something, for example I'll create a page using the hello_world_template

        // Add a breadcrumb
        add_breadcrumb('My Action', "misc.php?action=myaction");

        $hello_world = 'This text will appear on the page';
        eval('$sections  = "' . $templates->get('hello_world_template') . '";');

        // Using the misc_help template for the page wrapper
        eval("\$page = \"".$templates->get("misc_help")."\";");
        output_page($page);
    }
}
```

This should create a page nicely wrapped in the template header and footer, accessible by navigating to `misc.php?action=myaction`.

You can of course add your own page template instead of using `misc_help`.

### Using a Separate File

If your custom page has a lot of functionality, you may prefer to use a separate file, such as `my_plugin.php`, placed in the root MyBB directory.

The process is almost the same, except you put your functionality in the `my_plugin.php` file rather than in a hook function:

```php
<?php

// Set some useful constants that the core may require or use
define("IN_MYBB", 1);
define('THIS_SCRIPT', 'my_plugin.php');

// Including global.php gives us access to a bunch of MyBB functions and variables
require_once "./global.php";

// Only required because we're using misc_help for our page wrapper
$lang->load("misc");

// Add a breadcrumb
add_breadcrumb('My Page', "my_plugin.php");

$hello_world = 'This text will appear on the page';
eval('$sections  = "' . $templates->get('hello_world_template') . '";');

// Using the misc_help template for the page wrapper
eval("\$page = \"".$templates->get("misc_help")."\";");

// Spit out the page to the user once we've put all the templates and vars together
output_page($page);

?>
```

You can access this by navigating to `my_plugin.php`. You can also run a switch statement on `$mybb->get_input('action')` to serve several actions from your custom page.
