# drop database
drop database dbname;

# create database
create database name;

# import single database
mysql -uroot -p dbname < db.sql

# import method 2
sql> use dbname;
sql> source db.sql;

# drop user
drop user name;

# create user
create user 'dumper'@'%' identified by 'password';

# grant privileges
GRANT ALL PRIVILEGES ON dbname.* To 'user'@'host';

# all privileges with grant on wildcard
GRANT ALL PRIVILEGES ON *.* To 'user'@'host' WITH GRANT OPTION;

# mysqldump single database remotely
mysqldump -h -u -p database_name > dump.sql 

# mysqldump skip comments
mysqldump -h -u -p database_name > dump.sql --skip-comments

# mysqldump --all-databases
mysqldump -uroot -p --all-databases > dump.sql

# mysqldump retain encoding?
mysqldump -uroot -p database -r dump.sql

# show databases
show databases;

# use database
use databasename;

# show tables
show tables;

# login
mysql -hIPaddress -uroot -p***

# list users
select user,host from mysql.user;

# replication users
GRANT REPLICATION SLAVE ON *.* TO replication_user;

# show grants for current user
show grants;

# check slave privileges
SELECT user, host FROM mysql.user WHERE Repl_slave_priv = 'Y';

# lock all databases
FLUSH TABLES WITH READ LOCK;

# unlock all databases
UNLOCK TABLES;

# timezone 
mysql> SELECT @@global.time_zone, @@session.time_zone;

# MD5
SELECT MD5('notsecret'); 

# Convert all tables to innodb
Copy the output and run as a new SQL query

https://stackoverflow.com/a/30648414/1331456

```
SELECT CONCAT('ALTER TABLE ',TABLE_NAME,' ENGINE=InnoDB;') 
FROM INFORMATION_SCHEMA.TABLES
WHERE ENGINE='MyISAM'
AND table_schema = 'mydatabase';
```

# Out of sync
Is your local and staging NOW() returning different time?

Ideally we want to use the global time_zone +00:00 but if you want to localise then do the following.

## MYSQL
Check MYSQL time_zone

`SELECT @@global.time_zone;`

To set a value for it use either one:

`SET GLOBAL time_zone = '+8:00';`

`SET @@global.time_zone='+00:00';`

[Reference](https://stackoverflow.com/questions/19023978/should-mysql-have-its-timezone-set-to-utc)

## Amazon RDS

[Change](https://aws.amazon.com/premiumsupport/knowledge-center/rds-change-time-zone/) RDS time_zone.
