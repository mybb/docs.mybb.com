---
layout: page
title:  "Creating and Modifying Templates"
categories: [plugins]
---

## Creating Your Own Templates

If you want to insert a whole block of HTML rather than a simple value, it's generally better to create your own template.

Templates are usually created in the `_install()` function. They can be created like this:

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

Once your plugin has been installed, you should now be able to see the template you created in your Admin CP under `Templates & Style > Templates > Global Templates`.

To replace a variable inserted into another template with your custom template you must do the following from your hook function:

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

## Editing Templates

Most plugins require some changes to the front end of the site, typically to display some extra information.

### Modifying Templates to Add a Variable

A variable can easily be inserted into a template using the `find_replace_templatesets()` function, which looks for a string and replaces it in a given template.

For this purpose, you usually replace the string with itself plus your variable, for example:

```php
require_once MYBB_ROOT."/inc/adminfunctions_templates.php";

find_replace_templatesets(
    "index",
    "#" . preg_quote('<body>') . "#i",
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
