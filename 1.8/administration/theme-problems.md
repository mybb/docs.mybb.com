# Broken themes
If your theme doesn't look right or is completely broken you can try the following things to help you fix it.

## Check your Board URL
If your board URL is not set correctly then the paths to the resources in your theme will be broken. To check your board URL go to *ACP > Configuration > General Configuration* > edit the *Board URL* field. Make sure you include **http://** in your URL and don't put a trailing slash.

## Deleted cache file
The CSS of your theme is cached in the cache directory and if this is modified or deleted (for example by accident during an upgrade) you can regenerate it by saving your theme again in the theme editor. To do this go to *ACP > Templates & Styles > Select theme > global.css > Save changes*.

## Incorrect theme image directory
If images are not showing in your theme it is possible that your image directory is not correctly set in your theme properties. Go to *ACP > Templates & Styles > Select theme* > Edit the image directory field. The path here is relative to your root forum directory so for example if your images are located at *http://www.yoursite.com/forum/images/yourtheme* you would enter *images/yourtheme* and remember not to include a trailing slash.

## Incorrect CHMOD settings
Your theme cache files need to both readable and writable so make sure that your *./cache/* and *./cache/themes/* folders are set to **777**.
