---
layout: page
title: "Task Manager"
categories: [administration]
---

The task manager section in the Admin CP allows you to manage the scheduled tasks that are run on your forum. Scheduled tasks are run at the specified time(s), on the specified day(s), in the specified month(s) that you choose. Tasks run specified PHP files located in the inc/tasks directory.

The task listing page displays the name of the task, its description, the time of the next run, and whether or not it is enabled. From the task listing page, you can choose to edit the task, enable/disable the task, delete the task, or run the task. 

## Add New Task

<dl>
  <dt>Title</dt> 
  <dd>Name for the task.</dd>
  
  <dt>Short Description</dt> 
  <dd>A short description explaining the purpose of this task.</dd> 
  
  <dt>Task File</dt> 
  <dd>The file located in the inc/tasks directory that will be run when this task is run. You are provided a select list of the tasks located in the directory.</dd> 
  
  <dt>Time: Minutes</dt> 
  <dd>The minutes of the hour (between 0 and 59) this task should be run. Use an asterisk (*) to have the task run every minute.</dd> 

  <dt>Time: Hours</dt> 
  <dd>The hours of the day (between 0 and 23) this task should be run. Use an asterisk (*) to have the task run every hour.</dd> 

  <dt>Time: Days of Month</dt> 
  <dd>The days of the month (between 1 and 31) this task should be run. Use an asterisk (*) to have the task run every day, or if you wish to specify weekdays for this task to be run.</dd> 

  <dt>Time: Weekdays</dt> 
  <dd>The days of the week this task should be run. Select "Every Weekday" to have it run every day of the week (this will override any other selections for this setting). Hold down CTRL to select multiple days.</dd> 

  <dt>Time: Months</dt> 
  <dd>The months this task should be run. Select "Every Month" to have this task run every month (this will override any other selections for this setting). Hold down CTRL to select multiple months.</dd> 

  <dt>Enable Logging?</dt> 
  <dd>Should logging be enabled for this task?</dd> 

  <dt>Task enabled?</dt> 
  <dd>Should this task be enabled (be run at the times specified)?</dd>
</dl>

## View Task Logs

The task logs allow you to see all tasks that have been run in the past thirty days that have logging enabled. You are shown the task name, the day and time it was run, and additional data that relates to the task.

Logs older than 30 days are automatically deleted.
