1. Verify PostgreSQL Installation
First, make sure PostgreSQL is installed on your system. You should have a directory where PostgreSQL is installed. By default, this is usually under C:\Program Files\PostgreSQL\XX\, where XX represents the version number.

2. Locate the psql Executable
Find the path to the psql executable. It is typically located in the bin directory of your PostgreSQL installation. For example:

C:\Program Files\PostgreSQL\XX\bin\psql.exe
3. Add PostgreSQL to the System PATH
To run psql from any command prompt, you need to add the PostgreSQL bin directory to your system’s PATH environment variable. Here’s how you can do this:

Add to PATH via System Properties
Open System Properties:

Press Win + R, type sysdm.cpl, and press Enter. This will open the System Properties window.
Open Environment Variables:

Go to the Advanced tab.
Click on Environment Variables.
Edit the PATH Variable:

In the Environment Variables window, locate the System variables section.
Scroll down and find the Path variable, then select it and click Edit.
Add New Path:

Click New and add the path to the bin directory where psql.exe is located. For example:
makefile
Copy code
C:\Program Files\PostgreSQL\XX\bin
Save Changes:

Click OK to close all dialog boxes and save the changes.
Restart Command Prompt:

Close the Command Prompt window and open a new one to apply the changes.
Verify PATH Update
Open a new Command Prompt and type:

bash
Copy code
psql --version
This should display the version of psql if the PATH is set correctly.

4. Running psql
Once the PATH is updated, you should be able to run psql commands from any directory. For example:

bash
Copy code
psql -h 127.0.0.1 -U postgres -d firozdb < D:\sqlex\sqlexbackup.sql
Troubleshooting
Reinstall PostgreSQL: If psql is still not recognized, consider reinstalling PostgreSQL and ensuring that the option to add PostgreSQL to the PATH is selected during installation.


1.Install postgresql
refer: http://w3resource.com/PostgreSQL/install-postgresql-on-linux-and-windows.php
2.In postgresql prompt
create database "dbname"
3.\q
4.psql -h ip -U postgres dbname < sqlexbackup.sql (sqlexbackup.sql is for sqlex database, empexbackup.sql is for employee database
  and northwindexbackup.sql is for northwind database)
sqlex_backup.pgsql must be with proper path. For local machine ip is 127.0.0.1
5.psql -h ip -U postgres dbname
6.CREATE ROLE username WITH LOGIN ENCRYPTED PASSWORD 'password';
7.GRANT CONNECT ON DATABASE dbname TO username;
8.GRANT USAGE ON SCHEMA public TO datasoft1;
9.GRANT SELECT ON ALL TABLES IN SCHEMA public TO username;
10.\q
11.psql -h ip -U username dbname
supply password for username
11.Start executing SQL commands now

psql -h 127.0.0.1 -U postgres -d firozdb < D:\sqlex\sqlexbackup.sql
psql -h 127.0.0.1 -U postgres firozdb< D:\sqlex\empexbackup.sql
psql -h 127.0.0.1 -U postgres firozdb < D:\sqlex\northwindexbackup.sql


Check Permissions: Ensure you have the necessary permissions to access and modify environment variables.

https://www.w3resource.com/sql-exercises/
