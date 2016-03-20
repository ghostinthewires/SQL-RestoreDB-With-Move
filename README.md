# Restore SQL Server database to different filenames and locations #

The RESTORE WITH MOVE option allows you to restore your database, but also specify the new location for the database files (mdf and ldf).  If you are restoring an existing database from a backup of that database then this is not required, but if you are restoring a database from a different instance with different file locations then you may need to use this option.

## Determine contents of the backup ##

So the first thing you need to do is determine the logical names and the physical location of the files.  This can be done by using the RESTORE FILELISTONLY command at the top of the **RestoreDBWithMove.sql** script.  This will give you the logical and physical names.

Note the logical names of the .mdf & .ldf from the results

## Restore full backup WITH MOVE ##

This part of the **RestoreDBWithMove.sql** script will restore the database & log to the location of your choice. Here is an example from the script:

** RESTORE DATABASE MYDATABASE
FROM DISK = 'C:\TORESTORE\MYDATABASE.bak'
WITH MOVE 'MYDATABASE' TO 'E:\DATA\MYDATABASE.mdf',
MOVE 'MYDATABASE_log' TO 'L:\Logs\MYDATABASE.ldf' **
