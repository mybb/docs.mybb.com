---
layout: page
title:  "Translations Development"
categories: [translations]
---

This document contains instructions on how to translate MyBB into another language and serves as a guide for new translators.

# Introduction

Thanks to the hard work of many volunteers who have translated MyBB in the past it is now available in a great number of languages other than English. If you see that a language pack for a language you speak fluently (very preferably your native language) is not available yet, then you can become one of those volunteers yourself by translating MyBB.

Translating is a simple task: you have to translate all English text into your language. It is not difficult, but it is time-consuming. You could try to find someone else that can help you translate and split the work in two. You could also do all the work yourself, if you wish. This thread should contain all the information you need.

# Getting Started

In the MyBB download package you will find the folder inc/languages/. In it you will find a file named english.php and a folder named english. You should copy those to another location and change the names to the language you will translate into. You should try to use lowercase letters from a to z without any special diacritics. Using the English name for your language is probably best. For example, if you were to translate into German you could use the name german. However, if you think it is better to use another name, for example german96 to indicate you are using the new German spelling (spelling reform or Rechtschreibereform 1996), feel free to do so. After renaming the file and folder move them back to the folder inc/languages/.

Say you have chosen the name newlang for your translation. Open the file newlang.php with a text editor of your choice (such as Notepad++). You will see the following (or very similar) lines:

```php
// The friendly name of the language
$langinfo['name'] = "English (American)";

// The author of the language
$langinfo['author'] = "MyBulletinBoard";

// The language authors website
$langinfo['website'] = "http://www.mybboard.net/";

// Compatible version of MyBB
$langinfo['version'] = "1400";

// Sets if the translation includes the Admin CP (1 = yes, 0 = no)
$langinfo['admin'] = 1;

// Sets if the language is RTL (Right to Left) (1 = yes, 0 = no)
$langinfo['rtl'] = 0;

// Sets the lang in the <html> on all pages
$langinfo['htmllang'] = "en";

// Sets the character set, blank uses the default.
$langinfo['charset'] = "UTF-8";
```

You need to change these values for your language pack.

Change the friendly name of your language to the name you wish the users to see. For German you could use Deutsch, for French you could use Français, for Spanish you could use Español, and so on. If you are using special non-alphabetical characters or diacritics, such as the ~ above the n in ñ, you should make sure these will display properly. You can use HTML entities (such as &ntilde;) or save the file UTF-8 encoded. You might need to play with it a bit to see what works for your language. For more information on character encoding see Wikipedia.

You can put your name (or nickname) as the author of the language pack. This will be displayed in the Admin CP.

You can also enter a website address if you have your own website. Otherwise, you could, for example, put the link to your profile on these Community Forums there.

The compatible version should be set to the same value that is being used in english.php. It indicates for which version of MyBB the translation is meant.

If you have also translated (or are going to translate) the Admin CP into your language you need to set the next value to 1. If you set it to 0 the English language files will be used for the Admin CP.

If your language is read from right-to-left set the next value to 1 as well, otherwise leave it 0.

Change the "en" to the 2-letter code for your language. You can find this code at this page.

Change the character set to the set for your language if your language requires a different character set. You can find such codes at pages like this page. You should certainly try and see if UTF-8 works for you before changing this value.

After this has been done you can start the real work.

# Translating Text Strings

In inc/languages/newlang/ you will find the language files for MyBB, ending in .lang.php. You can open these with a text editor. Every language file looks the same way and very similar to the following snippet from akismet.lang.php:

```php
<?php
/**
 * MyBB 1.4 English Language Pack
 * Copyright © 2008 MyBB Group, All Rights Reserved
 *
 * $Id: akismet.lang.php 3790 2008-04-23 22:50:33Z Tikitiki $
 */

$l['spam'] = "Spam";

$l['post_spam_success'] = "The post(s) has been marked as spam successfully.";
$l['thread_spam_success'] = "The thread has been marked as spam successfully.";

$l['akismet_error'] = "Akismet Error";
?>
```

It starts with `<?php` and ends with `?>`. At the beginning you will find a comment block that is not used and can be removed if you wish. You can also leave it there or change the comments to something useful for you, for example when you last modified the file. After the comment block you will find the text strings. They all have the form

```php
$l['variable'] = "Text string";
```

You should translate the text between double quotes from English to your language for all text strings. Do not change the text between single quotes (i.e. `$l['variable']`). Make sure every such line ends with a semicolon. The job is simple: translate all such strings, in all language files.

The strings for the Board Settings page in the Admin CP are not found in the language files. You can translate them, though. Simply copy the strings in the next post and paste them in inc/languages/newlang/admin/config_settings.lang.php after the last string and before the ?>.

To check your translations you can set up a copy of MyBB and set it to use your language. Go to the User CP and select the language you are translating into on the Edit Options page. The friendly name you have given your language will be used in the list there. Note that you will need to re-upload every file to the server if you make any changes to it if you are not directly altering the files on your server. You can change the language to be used in the Admin CP from the Board Settings page.

# Translating Other Items

The image files for the group images can be found in `images/groupimages/english/`. You can create a new folder `images/groupimages/newlang/`, copy all images from `images/groupimages/english/` to `images/groupimages/newlang/` and replace them by buttons with text in your language. As you see the buttons are still using the old style. For those a PSD file also exists, made by madmax:

.psd  groupimages_eng.psd (Size: 221.55 KB / Downloads: 565)

Apart from the images there is also a language file for the installer (install/resources/language.lang.php), however, it does not contain all text for the installer and you might therefore consider not translating it but simply creating a document in your language with instructions on how to install MyBB. In addition, most people will be knowledgeable enough to install MyBB with English instructions so this doesn't have a high priority.

# Proofreading

After all the translating has been done be sure to check your translation extensively. Have other native speakers check it, point out mistakes and make suggestions. Check, double check and triple check everything to make sure your translation is of a very high quality. You could post a thread in the Internationalization forum to recruit proofreaders.

# Finishing Steps

After you have completed the five steps above you are ready to offer your language pack for public download. A language pack is a zip archive with the translated files in it. It should at least contain

- all the files in `inc/languages/newlang/`
- all the files in `images/newlang/`
- all the files in `images/groupimages/newlang/`
- an English readme file
- a localised readme file

The English readme file is so that administrators who do not speak the language can install it nonetheless. You can find a template for an English readme file here:

.html  readme.html (Size: 11 KB / Downloads: 1414)

You can edit it to include the English name of your language. Make sure the folder structure mentioned in the readme file matches the folder structure in your archive. Please also ensure that your readme mentions whether or not you have translated the Admin CP as well and adjust the readme file accordingly.

After that you can translate the English readme file into your language. That way users who don't speak English well but do speak your language can install the language pack easily. Name the translated file logically, e.g. "lesemich" in German or "lisezmoi" in French.

You should translate the sample English text into your language, an English translation is not required. You may add or omit paragraphs if you wish. Please note carefully that you should try not to post the language pack itself in your discussion thread: after each update you need to notify Tochjo so he can upload the new version for download from the main page.
