---
layout: page
title:  "Running the Merge System"
categories: [merge]
---

**The latest publicly released version of the MyBB Merge System only imports to MyBB 1.8.**

# Requirements
**You must already have a copy of MyBB 1.8 installed in order to run the MyBB Merge System.** More information on installing MyBB can be found at [Installing]({{ site.baseurl }}/1.8/install/).

# Initial Preparation
## Downloading the Merge System Package
First, you need to download the Merge System package from the [MyBB website]({{ site.mainsiteurl }}/download/merge-system/). After downloading the zip file, you need to unzip the file. If you right click on the file, there should be an option similar that inludes the words "Unzip," referring to the file (if you have WinZIP, WinRAR, or a similar program installed, do as instructed by the creators of the software). Unzip the contents of the file to a folder within the same folder that the zip is in, such as a folder called "mybb" or "merge"

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

-- To Be Added --

# After running
After you used the Merge System you should run all "Recount and Rebuild" tools, which are located under "Tools and Maintenance" in your Admin-CP. After that you should also rebuild the caches.
As last thing you need to recheck all permission (forum and group).