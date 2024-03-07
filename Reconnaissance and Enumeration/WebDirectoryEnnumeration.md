# Web Directory Enumeration

### Explanation
Directory scanning, also known as web directory enumeration or web directory brute-forcing, is a technique used to discover and enumerate directories and files on a web server. It is a crucial step in web application testing, penetration testing, and security auditing as it helps identify potential entry points, sensitive files, and misconfigurations that could be exploited by attackers.

### Prerequisite
Local machine must have:
- ***Python 3 installed***
- **[dirsearch](https://github.com/maurosoria/dirsearch) installed**

### Usage
First of all we need to be inside the repo folder. Then to execute the script we use:

```python3 dirsearch.py -u https://targetwebsite.com```

- **-u https://targetwebsite.com**: Specifies the target URL (https://targetwebsite.com) to be scanned for directories and files.

#### Output

```
[+] URL: https://targetwebsite.com/
[+] Threads: 10
[+] Wordlist: /path/to/dirsearch/common.txt
[+] Status codes: 200,204,301,302,307,401,403
[+] User Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3

[14:30:20] Starting: 
[14:30:21] 200 -    1KB - /admin/
[14:30:21] 301 -  317B - /cgi-bin/  ->  http://targetwebsite.com/cgi-bin/
[14:30:21] 200 -    1KB - /index.html
[14:30:21] 200 -    1KB - /robots.txt
[14:30:22] 301 -  316B - /test/  ->  https://targetwebsite.com/test/
[14:30:22] 301 -  317B - /temp/  ->  http://targetwebsite.com/temp/
[14:30:23] 403 -  289B - /cgi-bin/.htaccess
```