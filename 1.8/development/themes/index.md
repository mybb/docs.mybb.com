---
layout: page
title:  "Themes"
categories: []
---

Authoring themes is similar to creating websites. It will require knowledge of HTML and CSS, as well as an understanding of MyBB's internal variables.

# Templates

MyBB stores its templates in the database, not in the filesystem. To edit the templates go to **Admin CP > Templates & Style > Templates > Your Theme**.

Once there click **Expand** to view the various template groups.

To edit a template, click its name. Templates you have edited will appear in a different color. You can restore the original version of a template by clicking **Revert To Original**.

[More information on template development &rarr;]({{ site.baseurl }}/1.8/development/themes/templates/)

# Structure

The MyBB template system doesn't have a simple hierarchical structure; templates can't include other templates. This makes following the structure of a page somewhat difficult. For example, if you start from the index page (the index template), you'll see that it uses a few variables:

```html
{$headerinclude}
{$header}
{$forums}
{$boardstats}
{$footer}
```

`{$header}` and `{$footer}` are easy enough to locate, in the Header Templates and Footer Templates groups. `{$headerinclude}` is somewhat counter-intuitively in the Ungrouped Templates group.

But where is `{$forums}`? It's not in Forum Bit Templates or Forum Display Templates. In fact, there's no `{$forums}` template. `{$forums}` is a variable, and so were `{$header}` and `{$footer}`. It was an intended coincidence that there are templates with the same name.

To correctly identify how a variable like `{$forums}` is set, you must search in the MyBB PHP files for the following MyBB idiom:

```php
eval("\$forums
```
Turns out `{$forums}` is defined in forumdisplay.php:

```php
eval("\$forums = \"".$templates->get("forumdisplay")."\";");
```

# Variables

Variables are used to define MyBB-specific functions inside the templates.

There are various variables that can be used throughout the templates but most of them are template specific.

To determine which variable to use for which template just view the template you're trying to edit and uses of it are guaranteed to be there.

Here's a list of a few variables used:

<dl>
    <dt>`$mybb->user`</dt>
    <dd>Contains the data of the user currently viewing the page. e.g. $mybb->user['postnum'] shows the user his post count.</dd>

    <dt>`$post`</dt>
    <dd>Same functionality as $mybb->user, however, it's only used in the postbit templates. It shows the user who authored the post info, and also contains the post subject and message.</dd>

    <dt>`$users`</dt>
    <dd>Again, same as $mybb->user but used in many other template to show the users info who's in that row.</dd>

    <dt>`$user`</dt>
    <dd>Same as $users except more page specific, rather than row specific</dd>

    <dt>`$theme`</dt>
    <dd>This variable is used inside HTML (such as table, tr, and td tags) to define theme specific attributes related to the current users theme of choice.</dd>
</dl>

There are many more variables but it would be a huge long list. Also, not all variables work on all templates.

If you plan on making and releasing template modifications be sure to use `$theme` variables instead of regular HTML because of the differences in different administrators themes.

# HTML

MyBB 1.8 uses XHTML 1.0 Transitional as the coding standard. It is important to code in this standard so that all browsers will view the same way.

# CSS

MyBB uses CSS to define most of its theme attributes. You can change these by going to **Admin CP > Themes > Modify / Delete**. Once there select **Edit Theme Style** and hit go.

Here you will view various different attributes related to the theme you are editing.

You can change various things like:

- Which templates set to use
- Image directory location
- Logo image location
- Table spacing
- Content table width
- Inner border width
- And various colors and font and additional CSS styles.

The Theme Editor also includes an Additional CSS field, where you can add your own custom CSS.

## Table Classes

Tables are used extensively in MyBB 1.x (MyBB was designed back in the day, before CSS-based layouts became the norm). There are many CSS classes that are used to style different parts of these tables.

<dl>
    <dt>`.thead`</dt>
    <dd>This is used for Table Headers, to display them properly using CSS.</dd>

    <dt>`.tcat`</dt>
    <dd>Used to properly display Table Sub Headers using CSS.</dd>

    <dt>`.trow1`</dt>
    <dd>This uses the first Alternating Table Row used by pages that show rows of information.</dd>

    <dt>`.trow2`</dt>
    <dd>This is the same as trow1 except it uses the second Alternating Table Row.</dd>

    <dt>`.tfoot`</dt>
    <dd>Same as thead, but for Table Footers</dd>

    <dt>`.tborder`</dt>
    <dd>This uses CSS to properly display Table Borders.</dd>

    <dt>`.trow_shaded`</dt>
    <dd>This is used to shade a row in a table (for example moderated threads and posts) and uses the Shaded Table Row CSS in the Theme Editor</dd>

    <dt>`.trow_sep`</dt>
    <dd>This uses the Table Row Separator CSS in the Theme Editor.</dd>
</dl>

For example, a sample table may look like this:

```html
<table border="0" cellspacing="{$theme[borderwidth]}" cellpadding="{$theme[tablespace]}" width="100%">
    <tr>
        <td class="thead" colspan="2">
            <strong>Title of My Table</strong>
        </td>
    </tr>
    <tr>
        <td class="tcat" colspan="2">
            <strong>Sub-category</strong>
        </td>
    </tr>
    <tr>
        <td class="trow1">What: </td>
        <td class="trow1">My Content</td>
    </tr>
    <tr>
        <td class="trow2">Where: </td>
        <td class="trow2">At MyBB Wiki</td>
    </tr>
</table>
```

See [MyBB 1.4 CSS Guide](https://community.mybb.com/thread-33809.html) for a visual diagram of CSS classes and ids for the main MyBB pages.
