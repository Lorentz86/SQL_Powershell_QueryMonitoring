# SQL_Powershell_QueryMonitoring

This script is for monitoring active queries on MSSQL. 
Tested in Powershell 5.1 and MSSQL 2014
This script needs PS module SqlServer
Database should have WhoisActive installed. See http://whoisactive.com/ or install DBAtools and Install-DbaWhoIsActive -sqlinstance sqlserver -database databasename. See https://dbatools.io/. 

# Permissions
Make sure the user that the script wil run under has permissions to do queries on the database. 

# Trigger explanation
I don't work continuously with the actual software that uses the SQL server. So to only get logs when users experience 'lag' in the software. There needs to be a user based triger. 
I don't want to give users permission to run this / a script themselves on te SQLserver for multiple reasons.

# Scheduled Task
The script should run as a task. I run this scipt every 1 minute. Task Scheduler only has a minimum of 5 minutes. You can make a scheduled task using powershell. 
TIP: https://stackoverflow.com/questions/20108886/powershell-scheduled-task-with-daily-trigger-and-repetition-interval

If you need help contact me. 

Here is a solution I used:
Make a batch script thats creates a file in a folder. The Powershell script detects if there is a file inside the folder. 
If there is a file, the script runs. If not, nothing happens. 

# Example of a batch script
Open Notepad and save the following as a .bat file. Or download trigger.bat and make the changes. Make sure to have the same location in the powershell script. 

@echo off
whoami >> \\\Examplesrv\Exampleloc\Trigger.txt
hostname >> \\\Examplesrv\Exampleloc\Trigger.txt
date /t >> \\\Examplesrv\Exampleloc\Trigger.txt


# Bat file
I made a shortcut from the bat file. You can assign an icon to the shortcut so it acually looks like a program and you can always make changes to the actual bat file. 
Share the shortcut with some or all of the users. 

#T
