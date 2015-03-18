---
layout: page
title:  "Themes"
categories: [administration]
---

### About Themes / Skins

Themes, also known as **skins**, **forum designs** or **styles**  up the style and design of your board. They stylize the layout of your forum (it can be front-end design and back-end design). Themes use styles (CSS files) and they can use templates (HTML files).

Each board comes with default MyBB design. It is recommended to **not** delete or rewrite this design.

## Finding Themes

Themes can be found at MyBB mods site (Extend) - [MyBB Mods - Themes](http://community.mybb.com/mods.php?action=browse&category=themes).

Themes discussion, relases, requests and support can be found at [MyBB Community Forums - Themes](http://community.mybb.com/forum-103.html).

You can also find MyBB themes at lot of other sites on the internet, but be sure that that themes are 1.8.x version compitable.
For 1.6 Themes check [MyBB 1.6 Documentation](http://docs.mybb.com/1.6/), or directly [MyBB 1.6 Themes](http://docs.mybb.com/1.6/Admin-CP-Themes/).

## Installing themes

Firstly, when you download (probably zipped (`.zip` file)), extract it somewhere and find in one folder document named `<theme name>.xml`.
Also, author should provide readme file inthere, wich will help you install it.

## Uploading images

Now you will find file named like theme ending with `.xml` and probably map in same folder. Upload that map to images map at your forum root, to be like `images/<theme name>/`.

## Uploading xml file

The xml file should be uploaded Throught admin panel. So go to **Admin panel -> Templates & Style -> Import a theme**.
Under `Import from` choose `Local file` -> Search and upload your `.xml` file (file named `<theme name>.xml`).

Probably you will need to check box `Ignore version compitablity` so you can upload it. And click **Import theme**

Tutorial with images can be found here: [Theme installation](http://community.mybb.com/thread-163256.html).