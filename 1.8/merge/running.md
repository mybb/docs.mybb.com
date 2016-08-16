---
layout: page
title:  "Running the Merge System"
categories: [merge]
order: 1
---

**The latest publicly released version of the MyBB Merge System only imports to MyBB 1.8.**

# Requirements
**You must already have a copy of MyBB 1.8 installed in order to run the MyBB Merge System.** More information on installing MyBB can be found at [Installing]({{ site.baseurl }}/1.8/install/).

# Initial Preparation
## Downloading the Merge System Package
First, you need to download the Merge System package from the [MyBB website](https://www.mybb.com/download/merge-system/). After downloading the zip file, you need to unzip the file. If you right click on the file, there should be an option similar that inludes the words "Unzip," referring to the file (if you have WinZIP, WinRAR, or a similar program installed, do as instructed by the creators of the software). Unzip the contents of the file to a folder within the same folder that the zip is in, such as a folder called "mybb" or "merge"

## Uploading the Files
With the files extracted from the MyBB package, upload the 'merge' directory from the package to your existing installation of MyBB's folder. **You must keep the files inside the 'merge' directory.**

Things to keep in mind:

- Make sure that the directory structure is kept. (ie. the files in the admin directory should be uploaded to a directory called admin, the files in the archive directory should be uploaded to a directory called archive, etc)
- Make sure that you upload the .php, .html, .css and any other text file in ASCII mode, and that you upload the .gif, .jpg, .png, and any other binary file in Binary mode (see your FTP software documentation)

## "Dry Run" Testing
Backup your MyBB database now, before you do anything else. Then run the merge system once as a "dry run" to make sure everything works. If it doesn't, restore the MyBB backup and report the errors on the MyBB forums.

## Pre-Run Board Configuration
Before you run the merge system, please close/lock both forums. This is to prevent content and users from being added or removed while you're running the system. This is for your own safety. Once again, please backup the MyBB database before beginning as well. Just in case.

# Running the Merge System Wizard
If you're experiencing any problems you can reference the [Troubleshooting Page]({{ site.baseurl }}/1.8/merge/troubleshooting).

After uploading the files to your existing MyBB install, visit your forum's URL, appending /merge/ to the end. So, if your forum is at http://www.yourforum.com/forums/ you would visit http://www.yourforum.com/forums/merge/

## Welcome
The first page you see is the Welcome page. From this page, you must choose the forum software and the version of the forum you will be converting into MyBB. Select the appropriate software, and then click "Next"

## Module Selection (Initial)
This page lets you pick and choose what you want imported, and what you don't want imported. As you can see, many modules have "dependencies," which requires you to run another module first before running that one. After you run all of the "dependencies," you will be able to run that module.

The first module that you must run in order to perform the merge process is the "Database Configuration" module, which is where you enter the database details for your existing install of another forum software.

## Database Configuration
On this page, you must enter the database details for your existing forum software - not the MyBB forum you are merging into.

**Database Engine**

This is the engine that the forum software is running on.

### Database Host
This is the server where the database is. Unless told otherwise by your host, this should be localhost.
### Database Username
This is the username used to access the forum database for the forum software you are converting from.
### Database Password
This is the corresponding password for the database username you entered.
### Database Name
This is the name of the database that the forum software is installed to.
### Table Prefix
This is the prefix to all of the database fields for the forum software you are converting from.

## Module Selection (After Database Configuration)
After entering in the Database Configuration details, you will see that several other modules are now able to be run. The modules that you have already run are marked as completed, and if another module is dependent on a module that has already been run, the module will be crossed out in the "dependencies" section.

## Importing Data (Running an Import Module)
When you choose to run a module, you will then see a screen that lets you decide how many items to import at a time, and you also have the ability to automatically continue to the next page until the merge system is finished importing the data for that module.

If you wish to go back to the module selection screen before running the module, all you need to do is click on "Back"

## Module Selection (After more modules have been run)
Once you have run a few more modules, you will see that more and more modules are available to be run. As you can see, import modules cannot be run again, due to the risk of accidentally importing the same data twice, which could leave you with duplicate information.

## Cleanup
This is the final step, and the conversion process will be finished after running this step. This step automatically removes any temporary data that may have been created during the process.

In addition, you can download a text or HTML file that allows you to view the statistics of your merge.

## loginconvert.php plugin
You may receive a message like the following during the merge system conversion for some forum softwares: "Warning: You should upload loginconvert.php to inc/plugins if you wish to convert passwords." This means the merge system was not able to automatically move the plugin for you. It's not imperative for you to upload it right then and there. You can upload it after the merge system is run, but you'll have to activate it yourself. If you upload it while the merge system is being ran, it will automatically activate it for you. Note: Your converted members will not be able to log in until you upload and activate the plugin.

## Anonymous Statistics
The MyBB Merge System (RC4 and later) now allows you to send anonymous statistical data about your merge to the MyBB Group. This information allows us to better improve our products in the future.

What information is Sent?

### Converters Ran
These are the modules that you ran during the merge (Users, Threads, Posts, etc).
### Counter Information
These are the amount of users, threads, posts, etc that were converted to your new forum.
### Board Title
This is simply the title of the forum you're importing from. This helps us weed out duplicates.
### IP Address
This is the IP Address of your computer which also helps us weed out duplicates.

If any of this information you don't want sent, simply un-tick the "Send anonymous statistics about my merge to the MyBB Group" on the first page, and that's it. Absolutely no information will be sent to the MyBB Group should you choose not to.

# After running
After you used the Merge System you should run all "Recount and Rebuild" tools, which are located under "Tools and Maintenance" in your Admin-CP. After that you should also rebuild the caches.
As last thing you need to recheck all permission (forum and group).
