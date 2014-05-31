---
layout: page
title:  "How to CHMOD Files"
---

# How To CHMOD Files

CHMODing a file changes its permissions. This controls who can and can not have access to the file. There are three user permission groups used when CHMODing a file and every user belongs to one of these permission groups.

**Owner** - The owner of the file is the person who created it. Depending on how your system is setup, the user might be called 'root' or the username you use to login to the system.

**Group** - Users can belong to a group. Being in a group allows an admin to put users who need the same level of access together in one group, and then set permissions for that group here.

**Others** - If you are the user or do not belong to the group, you are treated as an 'other'.

Each permission group has three values associated with it. One for reading access, another for writing access and the last one is for execute access. With CHMOD, reading access is denoted by r, writing by w and execute by x. These are placed in one string with each permission groups' parameters tagged onto the end.

A string that looks like `rwx rw- r--`, defines who can access this file. The first three characters (rwx) represent the **owners** permissions. The second set of three characers (`rw-`) are for the **group** permissions, and the last three characters (`r--`) represent the **other** permissions. rwx means that user has the power to read, write and execute the file. `rw-` means the user has the power to read and write the file, but not execute it. `r--` means the user can only read the file.

When using FTP programs, permissions can sometime be given as numbers.

    0 (or blank) = No permissions 1 = Execute 2 = Write 3 = Execute + Write 4 = Read 5 = Read + Execute 6 = Read + Write 7 = Read + Write + Execute 

A permission string of *764* means the **owner** of the file can read, write and execute, the **group** can read and write and the **others** can only read.

The easiest way to change permissions in Unix via the command line is to use the command

    chmod ABC file_name
    
where *ABC* are the number representations of the permissions you wish to set. With *A* being the permissions for **owner**, *B* permissions for **group** and *C* permissions for **other**. `file_name` is the name of the file you wish to set permissions for.

**Example:**

    chmod 666 inc/config.php chmod 777 uploads
    
Most GUI applications have a box that allows you to check/uncheck permissions per permission group. This will save you time working out which numbers you require. Where this command/tool is located depends on the program, but in Smart FTP, it is located under the Commands menu. Most programs should also allow you to change your file permissions by right clicking on the file you require.

See [Using FTP](ftp) for a list of programs that you can use and how to use them. Tutorials on CHMODing on specific programs can be found here.

CHMOD is a Linux/Unix file property. In Windows the property is slightly different (read-only), but most of the time you will not need to modify the permissions of the files listed above on a Windows system.
