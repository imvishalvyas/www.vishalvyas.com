MySQL is the most popular open-source and widely used relational database management system, MySQL is a free and open-source database service. It's easy to set up and run the database on local or cloud servers. In this post, I will explain to you some MySql useful commands to create MySQL database, backup MySQL database, and restore MySQL database.


### How to create MySQL database using CLI

Login to MySQL as the root  user
```
mysql -u root -p
```

### Create a database name mydb
```
create database mydb;
```
We have created our first MySQL database. Let's create a MySQL user to access the database.


### How to create a MySQL user
We will create a user name vishal with the password vishal#123. Execute the below command to create a MySQL user
```
CREATE USER 'vishal@localhost' IDENTIFIED BY 'vishal#123';
```
**Note**: If you are connecting the database using an IP address then use a username like 'vishal'@'server-ip' and Use 'vishal'@'%' to access from any machine.


### How to grant permission in MySQL
We have successfully created the database and user yet, Now it's time to grant privileges to the MySQL user to access the database. Currently, we will grant all permission to the database for users.
```
GRANT ALL PRIVILEGES ON * . * TO 'vishal'@'localhost';
```
```
There are several more grant options available that you can use.
CREATE: The user can create a database and tables
SELECT: The user can retrieve the data
DELETE: The user can erase the table entries
INSERT: The user can add new entries to the tables
DROP: The user can drop entire tables and databases
UPDATE: The user can modify existing entries in tables
```

### How to backup MySQL database
Run the below command to dump the MySQL database
```
mysqldump -u [username] -p [password] [database_name] > [backup_file.sql]
```
This command will create a backup for the database and save it to the backup_file.sql


### How to restore MySQL database
Apply below command to restore a database using backup file.
```
mysql -u [username] -p [password] [database_name] < [backup_file.sql]
```
This command will import the backup in the database using backup file.

Hope you like the article, Like share, and comment on the post if you have any suggestions. 
