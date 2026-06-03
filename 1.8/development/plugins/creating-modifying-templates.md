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

## Working with a Template Group

It is easier to scale when implementing many templates by creating a template group for all relevant templates.

A template group can be created like this:

```php
$template_group = array(
    'prefix' => $db->escape_string("hello_world"),
    'title' => $db->escape_string("Hello World"),
    'isdefault' => 0
);

$db->insert_query('templategroups', $template_group);
```

The above code example will create a template group titled 'Hello World' and will include all templates that use the unique prefix of 'hello_world'.

An example of creating one template group and two templates:

```php
global $db;

$template_group = array(
    'prefix' => $db->escape_string("hello_world"),
    'title' => $db->escape_string("Hello World"),
    'isdefault' => 0
);

$db->insert_query('templategroups', $template_group);

$insert_array_first = array(
    'title' => 'hello_world_first',
    'template' => $db->escape_string($template_first),
    'sid' => '-2',
    'version' => '',
    'dateline' => time()
);

$db->insert_query('templates', $insert_array_first);

$insert_array_second = array(
    'title' => 'hello_world_second',
    'template' => $db->escape_string($template_second),
    'sid' => '-2',
    'version' => '',
    'dateline' => time()
);

$db->insert_query('templates', $insert_array_second);

```

Deletion of a template group is done separately from templates. If there is a need to delete a template group but not its matching templates, change the sid on the templates, or else they will not show up in the Admin CP.

Example of deleting a template group and changing sid for relevant templates:

```php
global $db;

$db->delete_query("templategroups", "prefix = 'hello_world'");

$update_array = array(
    'sid' => '-1'
);

$db->update_query("templates", $update_array, "title like '%hello_world_%'");
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

## Caching Templates
Don't forget to cache the template. This is important for pages with big load and prevent the database server from extra queries.

### Caching a template
A simple way to cache an template only at the place where it's needed is to use the `THIS_SCRIPT` definition.
For example, the template is needed in the postbit. Then we can load it in the showthreads.php.
```php
if(THIS_SCRIPT == 'showthread.php')
{
    global $templatelist;
    if(isset($templatelist))
    {
        $templatelist .= ',';
    }
    $templatelist .= 'hello_world_template';
}
```
Another example, here are some more templates needed on the member page. Then we can load it in the member.php.
```php
if(THIS_SCRIPT == 'member.php')
{
    global $templatelist;
    if(isset($templatelist))
    {
        $templatelist .= ',';
    }
    $templatelist .= ',hello_world_template_second';
    $templatelist .= ',hello_world_template_third';
}
```

### Testing if the template gets cached
You can simply test if the templates get cached correctly or not. Open the page where they should get cached and add a `?debug&debug=1` or `&debug&debug=1` to the url into the browser.
Now you see the `MyBB Debug Information` page. The first table called `Page Generation Statistics` contains a row with the template cache information. 

#### If a template does not get cached
`No. Templates Used: 90 (89 Cached / 1 Manually Loaded)`
This means there is 1 template that needs an extra select query to the database to get loaded. At the botton you see the `Template Statistics` and now can control which templates don't get cached. All template names in `Templates Requiring Additional Calls (Not Cached at Startup) - 1 Total` are not cached, so you should correct your code.

#### How to determine if templates are being cached correctly
`No. Templates Used: 90 (90 Cached / 0 Manually Loaded)`
Your template is now listed in the correct `Template Statistics` table.
