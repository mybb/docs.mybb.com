---
layout: page
title:  "Themes"
categories: [administration]
---

### About Themes / Skins

Themes, also known as **skins**, **forum designs**, or **styles**  improve the style and design of your board. They stylize the layout of your forum (it can be front-end design and back-end design). Themes use stylesheets (CSS files) and HTML-based templates.

Each board comes with a default MyBB theme. It is recommended to **not** delete or rewrite this theme.

## Finding Themes

Themes can be found at the MyBB Extend site (Extend) - [MyBB Mods - Themes](https://community.mybb.com/mods.php?action=browse&category=themes).

Themes discussion, relases, requests and support can be found at [MyBB Community Forums - Themes](https://community.mybb.com/forum-103.html).

You can also find MyBB themes at lot of other sites on the internet, but be sure that that themes are 1.8.x version compatible.
For 1.6 Themes check [MyBB 1.6 Documentation]({{ site.baseurl }}/1.6/), or directly [MyBB 1.6 Themes]({{ site.baseurl }}/1.6/Admin-CP-Themes/).

## Installing themes

Firstly, after you download (usually a ZIP file), extract it somewhere and find in the resulting folder a file named  `<theme name>.xml` or similar..
Also, many authors provide a README file in there, which will help you install it correctly. Sometimes there is more complexity than a basic installation as described here.

## Uploading Images

In the folder, you will probably see either a folder of images named similar to the theme, or an images folder with a subfolder (usually named the same as the theme, or similar) of images. Upload the entire folder that contains the images to `images/<theme-images-folder-name>`, unless the documentation provided with your theme requests otherwise.

## Uploading the XML File

An XML file is bundled with a theme download. This XML file contains all the templates the theme uses, as well as some other default settings and details about the theme.

The XML file should be uploaded through the Admin Control Panel. So go to **Admin Control Panel -> Templates & Style -> Import a theme**.
Under `Import from` choose `Local file` -> Search and upload your `.xml` file (file named `<theme name>.xml`).

You may need to check the `Ignore version compatiblity` option so you can upload it. And click **Import theme** to finish.

A tutorial with images can be found here: [Theme installation](https://community.mybb.com/thread-163256.html).
