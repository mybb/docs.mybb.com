---
layout: page
title: "Task Manager"
categories: [administration]
---

The task manager section in the Admin CP allows you to manage the scheduled tasks that are run on your forum. Scheduled tasks are run at the specified time(s), on the specified day(s), in the specified month(s). Tasks run specified PHP files located in the inc/tasks directory.

The task listing page displays the name of the task, its description, the time of the next run, and whether or not it is enabled. From the task listing page, you can choose to edit the task, enable/disable the task, delete the task, or run the task. 

## Tools & Maintenance: Add Task

 Title 
    Name for the task.
    
 Short Description 
    A short description explaining the purpose of this task. 
    
Task File 
    The file located in the inc/tasks directory that will be run when this task is run. You are provided a select list of the tasks located in the directory. 
    
Time: Minutes 
    The minutes of the hour (between 0 and 59) this task should be run. Use an asterisk (*) to have the task run every minute. 

Time: Hours 
    The hours of the day (between 0 and 23) this task should be run. Use an asterisk (*) to have the task run every hour. 

Time: Days of Month 
    The days of the month (between 1 and 31) this task should be run. Use an asterisk (*) to have the task run every day, or if you wish to specify weekdays for this task to be run. 

Time: Weekdays 
    The days of the week this task should be run. Select "Every Weekday" to have it run every day of the week (this will override any other selections for this setting). Hold down CTRL to select multiple days. 

Time: Months 
    The months this task should be run. Select "Every Month" to have this task run every month (this will override any other selections for this setting). Hold down CTRL to select multiple months. 

Enable Logging? 
    Should logging be enabled for this task? 

Task enabled? 
    Should this task be enabled (be run at the times specified)? 

The "Weekly Backup" task can be used to periodically back up your MyBB database, but its use is recommended only for small boards, because it might slow down the board when it takes its time to complete. If you have it running as a task but notice the board is slow when the backup task is running, then use a cron job instead. Below is an example for MySQL. 
