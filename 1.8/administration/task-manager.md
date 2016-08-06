---
layout: page
title: "Task Manager"
categories: [administration]
---

The task manager section in the Admin CP allows you to manage the scheduled tasks that are run on your forum. Scheduled tasks are run at the specified time(s), on the specified day(s), in the specified month(s) that you choose. Tasks run specified PHP files located in the inc/tasks directory.

The task listing page displays the name of the task, its description, the time of the next run, and whether or not it is enabled. From the task listing page, you can choose to edit the task, enable/disable the task, delete the task, or run the task. 

## Add New Task

<dl>
  <dt><b>Title</b></dt> 
  <dd>Name for the task.</dd>
  
  <dt><b>Short Description</b></dt> 
  <dd>A short description explaining the purpose of this task.</dd> 
  
  <dt><b>Task File</b></dt> 
  <dd>The file located in the inc/tasks directory that will be run when this task is run. You are provided a select list of the tasks located in the directory.</dd> 
  
  <dt><b>Time: Minutes</b></dt> 
  <dd>The minutes of the hour (between 0 and 59) this task should be run. Use an asterisk (*) to have the task run every minute.</dd> 

  <dt><b>Time: Hours</b></dt> 
  <dd>The hours of the day (between 0 and 23) this task should be run. Use an asterisk (*) to have the task run every hour.</dd> 

  <dt><b>Time: Days of Month</b></dt> 
  <dd>The days of the month (between 1 and 31) this task should be run. Use an asterisk (*) to have the task run every day, or if you wish to specify weekdays for this task to be run.</dd> 

  <dt><b>Time: Weekdays</b></dt> 
  <dd>The days of the week this task should be run. Select "Every Weekday" to have it run every day of the week (this will override any other selections for this setting). Hold down CTRL to select multiple days.</dd> 

  <dt><b>Time: Months</b></dt> 
  <dd>The months this task should be run. Select "Every Month" to have this task run every month (this will override any other selections for this setting). Hold down CTRL to select multiple months.</dd> 

  <dt><b>Enable Logging?</b></dt> 
  <dd>Should logging be enabled for this task?</dd> 

  <dt><b>Task enabled?</b></dt> 
  <dd>Should this task be enabled (be run at the times specified)?</dd>
</dl>

## View Task Logs

The task logs allow you to see all tasks that have been run in the past thirty days that have logging enabled. You are shown the task name, the day and time it was run, and additional data that relates to the task.

Logs older than 30 days are automatically deleted.

## Weekly Backups

The "Weekly Backup" task can be used to periodically back up your MyBB database, but its use is recommended only for small boards, because [it might slow down the board](https://community.mybb.com/thread-98163.html) when it takes its time to complete. If you have it running as a task but notice the board is slow when the backup task is running, then use a cron job instead. Below is an example for MySQL. 

Create a shell script named, for example, `~/forum_backup.sh`:

```
now=`date +%Y-%m-%dT%H-%M` ; mysqldump -u <MYBB_USER> --password=<MYBB_PASSWORD> --skip-opt --add-drop-table --complete-insert --create-options --disable-keys=FALSE --extended-insert=FALSE --lock-tables --skip-set-charset --skip-comments --dump-date <MYBB_DBNAME> > $now.sql ; zip -m $now.zip $now.sql
```

These parameters configure the mysqldump to be very close to the format of the [backups generated via Admin CP](https://docs.mybb.com/1.8/administration/backups/). In particular, one INSERT per line vs. multi-value INSERTs allow for easier visual comparison of dumps using [visual diff tools](https://en.wikipedia.org/wiki/Diff_utility). 

To create a cron job for automatically executing that backup, run: 

``` 
chmod +x ~/forum_backup.sh
crontab -e
# in the crontab editor, enter a CRON expression like:
0 4 * * * ~/forum_backup.sh  # run the backup every day at 4am
```

Note that having backups on the server won't protect you from a server failure, or losing access to the server. Make sure you transfer the backups from the server to an off-site location.
 
