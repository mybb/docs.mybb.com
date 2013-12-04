---
layout: page
title:  "Common Tasks"
---

This section demonstrates how to imperilment several functions commonly required by plugins.

## Modifying templates and passing values to a template

Most plugins require some changes to the front end of the site, typically to display some extra information.

Implementing this in a plugin requires two steps, firstly a variable is inserted into a template during the plugin activation, then a value is passed to the template at runtime.

A variable can easily be inserted into a template using the `find_replace_templatesets()` function, which looks for a string and replaces it in a given template.
Usually you'd replace the string with itself plus your variable, for example:

```php
find_replace_templatesets(
    "postbit",
    "#" . preg_quote('{$post[\'user_details\']}') . "#i",
    '{$post[\'user_details\']}{$myVar}'
);
```
This would insert `{$myVar}` after `{$post['user_details']}` in the `postbit` template.
**It is important to make sure the string you search for is unlikely to change between templates**, otherwise users will have to manually edit their templates to insert the variable if the string doesn't exist in their template.

The second step is to pass a value to the template at runtime, this is done inside a hook function. Values must be passed via the `eval()` function, such as this:

```php
$myVal = 'Hello World!';
eval('$myVar  = "' . $myVal . '";');
```
This will insert "Hello World!" where the `{$myVar}` variable is in the template. `$myVal` could of course be any value, such as one dynamically generated or from a database query.
