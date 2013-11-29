---
layout: page
title:  "Translations"
---

Translations, also known as **language packs** or **languages** are available to translate the MyBB interface into another language. All of the text that MyBB generates (besides user-inputted messages), are translatable. The ability to do this lies in the various `.lang.php` files found in the folders within `inc/languages/` folders.

Each MyBB file has its own `.lang.php` file. For example, the language phrases used in `member.php` would be stored in `inc/languages/<language name>/member.lang.php`.

There are also some **global** language files that are used in all of MyBB. These include `global.lang.php` and `messages.lang.php`.

Each board comes with the English language pack by default. It is recommended that you do **not** delete this language pack.

### Finding Translations

The complete translations that have been submitted to the MyBB Group are listed on the [MyBB Mods website](http://mods.mybb.com) and can also be found in the [Translation Releases](http://community.mybb.com/forum-169.html) forum.

More discussions about translations (in development, or other), may be found in the [Translation Discussion and Development](http://community.mybb.com/forum-21.html) forum.

### Installing Translations

There are usually two main components of installing a language. Firstly, the language files need to be uploaded. Secondly, the translated image files (should they exist) need to be uploaded.

#### Uploading the Language Files

The language files should be uploaded to the `inc/languages/<language name>/` folder. The translation author should give you instructions via his or her `readme` on details including what the `<language name>` folder name should be.

#### Uploading the Image Files

If these exist, they should be uploaded to `images/<language name>/` and `groupimages/<language name>/`. Again, the translation author should have given you more detailed instructions in his or her `readme` file.

#### Finishing Touches

Go to **User CP > Edit Options**. You should see the translation in the **Other Options** menu. Try out the new translation and make sure that everything works.