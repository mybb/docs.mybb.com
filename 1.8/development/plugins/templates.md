---
layout: page
title:  "Templates"
categories: [plugins]
---

## Editing Templates

Most plugins require some changes to the front end of the site, typically to display some extra information.

### Modifying templates to add a variable

A variable can easily be inserted into a template using the `find_replace_templatesets()` function, which looks for a string and replaces it in a given template.

Usually you'd replace the string with itself plus your variable, for example:

```php
require_once MYBB_ROOT."/inc/adminfunctions_templates.php";

find_replace_templatesets(
    "index",
    "#" . preg_quote('') . "#i",
    '<body>{$myVar}'
);
```

This would insert `{$myVar}` after `<body>` in the `index` template.

**It is important to make sure the string you search for is unlikely to change between templates**, otherwise users will have to manually edit their templates to insert the variable if the string doesn't exist in their template.

### Passing Simple Values to a Template

Global variables can be accessed from templates, so the easiest way to access a variable in your hook function from a template is to make it global:

```php
global $myVar;

$myVar = 'Hello World!';
```

This will insert **Hello World!** where the `{$myVar}` variable is in the template. `$myVar` can, of course, be any value, such as one dynamically generated or from a database query.

An alternative solution is to modify an existing global variable such as `$user`. For example, you could insert `{$user['favorite_colour']}` into a template, then do the following in your hook function:

```php
global $user;

$user['favorite_colour'] = 'Blue';
```

## Creating Your Own Templates

If you want to insert a whole block of HTML rather than a simple value then you probably want to create your own template.

Templates are usually created in your `_install()` function. They can be created like this:

```php
global $db;

$template = '<strong>{$hello_world}</strong>';

$insert_array = array(
    'title' => 'hello_world_template',
    'template' => $db->escape_string($template),
    'sid' => '-1',
    'version' => '',
    'dateline' => time()
);

$db->insert_query('templates', $insert_array);
```

The template can be deleted in your `_uninstall()` function using:

```php
$db->delete_query("templates", "title = 'hello_world_template'");
```

Once your plugin has been installed you should now be able to see the template you created under global templates.

To replace a variable you inserted into another template with your custom template you must do the following from your hook function:

```php
global $templates, $myVar;

$hello_world = 'foobar';
eval('$myVar  = "' . $templates->get('hello_world_template') . '";');
```

Note that `$hello_world` does not have to be global, yet it's passed to your custom template.

If all has worked correctly you should see the following at the top of your index page:

```html
<strong>Hello World</strong>
```

## Creating a New Page / Action

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

If your custom page has a lot of functionality you may prefer to use a separate file, such as `my_plugin.php` which would be placed in the root MyBB directory.

The process is basically the same except you'd put your functionality in the `my_plugin.php` file rather than in a hook function:

```php
<?php

define("IN_MYBB", 1);
define('THIS_SCRIPT', 'my_plugin.php');

require_once "./global.php";

// Only required because we're using misc_help for our page wrapper
$lang->load("misc");

// Add a breadcrumb
add_breadcrumb('My Page', "my_plugin.php");

$hello_world = 'This text will appear on the page';
eval('$sections  = "' . $templates->get('hello_world_template') . '";');

// Using the misc_help template for the page wrapper
eval("\$page = \"".$templates->get("misc_help")."\";");
output_page($page);

?>
```

You can access this by navigating to `my_plugin.php`, you can also run a switch statement on `$mybb->get_input('action')` to serve several actions from your custom page.
