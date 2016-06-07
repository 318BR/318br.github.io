---
layout: post
title: CTF-H4K - Fuck You (1stplace)
address: "0x0004"
tags:
 - shc
 - writeups
---

Nossa primeira vitória com o novo nome, não poderia ser em melhor estilo, a CTF-H4K promoveu no sábado passado (04/06) um novo CTF, desta vez apenas reverse, foram 5 desafios, compostos em sua maioria por binários windows, e nós vencemos! gostaria de parabenizar o *Boot Santos* por trazer mais uma vez bons desafios como este.

<hr class="codebreak">
# Obfusfail
*  Wine tá bugado!? eu avisei que um windows ia te ajudar!
<br/><br/>

Esse não teve jeito, tive que usar o Ruindows, logo quando se tentava rodar o binário, fosse no wine ou mesmo no windows ele abria uma dialog informando o bloqueio de disassemble por uma ferramenta chamada Eziriz .NET Reactor, foi bem simples. realizado o download da ferramenta, foi só abrir o binário nela e a flag logo de cara aparecia.
![Obfusfail]({{ site.url }}/assets/img/obfusfail.png)

<hr class="codebreak">
# ELF
* Eu sei de suas skill então pega essa!
<br/><br/>

A flag exigia apenas o basico do gdb

```bash
fatlips//deadcow ~/shc % gdb ./crackme
GNU gdb (GDB) 7.10.1
Copyright (C) 2015 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-unknown-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from ./crackme...(no debugging symbols found)...done.
(gdb) disas main
Dump of assembler code for function main:
   0x000000000040074d <+0>:	push   %rbp
   0x000000000040074e <+1>:	mov    %rsp,%rbp
   0x0000000000400751 <+4>:	push   %rbx
   0x0000000000400752 <+5>:	sub    $0x2a8,%rsp
   0x0000000000400759 <+12>:	mov    %edi,-0x2a4(%rbp)
   0x000000000040075f <+18>:	mov    %rsi,-0x2b0(%rbp)
   0x0000000000400766 <+25>:	mov    %fs:0x28,%rax
   0x000000000040076f <+34>:	mov    %rax,-0x18(%rbp)
   0x0000000000400773 <+38>:	xor    %eax,%eax
   0x0000000000400775 <+40>:	movb   $0x53,-0x290(%rbp)
   0x000000000040077c <+47>:	movb   $0x48,-0x28f(%rbp)
   0x0000000000400783 <+54>:	movb   $0x43,-0x28e(%rbp)
   0x000000000040078a <+61>:	movb   $0x7b,-0x28d(%rbp)
   0x0000000000400791 <+68>:	movb   $0x50,-0x28c(%rbp)
   0x0000000000400798 <+75>:	movb   $0x65,-0x28b(%rbp)
   0x000000000040079f <+82>:	movb   $0x67,-0x28a(%rbp)
   0x00000000004007a6 <+89>:	movb   $0x75,-0x289(%rbp)
   0x00000000004007ad <+96>:	movb   $0x65,-0x288(%rbp)
   0x00000000004007b4 <+103>:	movb   $0x5f,-0x287(%rbp)
   0x00000000004007bb <+110>:	movb   $0x53,-0x286(%rbp)
   0x00000000004007c2 <+117>:	movb   $0x65,-0x285(%rbp)
   0x00000000004007c9 <+124>:	movb   $0x75,-0x284(%rbp)
   0x00000000004007d0 <+131>:	movb   $0x73,-0x283(%rbp)
   0x00000000004007d7 <+138>:	movb   $0x5f,-0x282(%rbp)
   0x00000000004007de <+145>:	movb   $0x50,-0x281(%rbp)
   0x00000000004007e5 <+152>:	movb   $0x6f,-0x280(%rbp)
   0x00000000004007ec <+159>:	movb   $0x6e,-0x27f(%rbp)
   0x00000000004007f3 <+166>:	movb   $0x74,-0x27e(%rbp)
   0x00000000004007fa <+173>:	movb   $0x6f,-0x27d(%rbp)
   0x0000000000400801 <+180>:	movb   $0x73,-0x27c(%rbp)
   0x0000000000400808 <+187>:	movb   $0x5f,-0x27b(%rbp)
   0x000000000040080f <+194>:	movb   $0x65,-0x27a(%rbp)
   0x0000000000400816 <+201>:	movb   $0x5f,-0x279(%rbp)
   0x000000000040081d <+208>:	movb   $0x53,-0x278(%rbp)
   0x0000000000400824 <+215>:	movb   $0x61,-0x277(%rbp)
   0x000000000040082b <+222>:	movb   $0x69,-0x276(%rbp)
   0x0000000000400832 <+229>:	movb   $0x61,-0x275(%rbp)
   0x0000000000400839 <+236>:	movb   $0x5f,-0x274(%rbp)
   0x0000000000400840 <+243>:	movb   $0x43,-0x273(%rbp)
   0x0000000000400847 <+250>:	movb   $0x6f,-0x272(%rbp)
   0x000000000040084e <+257>:	movb   $0x72,-0x271(%rbp)
   0x0000000000400855 <+264>:	movb   $0x72,-0x270(%rbp)
   0x000000000040085c <+271>:	movb   $0x65,-0x26f(%rbp)
   0x0000000000400863 <+278>:	movb   $0x6e,-0x26e(%rbp)
   0x000000000040086a <+285>:	movb   $0x64,-0x26d(%rbp)
   0x0000000000400871 <+292>:	movb   $0x6f,-0x26c(%rbp)
   0x0000000000400878 <+299>:	movb   $0x7d,-0x26b(%rbp)
   0x000000000040087f <+306>:	lea    -0x220(%rbp),%rax
   0x0000000000400886 <+313>:	add    $0x1,%rax
   ...
End of assembler dump.
(gdb)
```

de cara já da pra notar que a flag está ai, faltando apenas formatar e printar, durante o desafio pela agilidade acabei editando no vim mesmo e fazendo o parse no python

```bash
fatlips//deadcow ~/shc % python
Python 3.5.1 (default, Dec  7 2015, 12:58:09) 
[GCC 5.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> flag = "\x53\x48\x43\x7b\x50\x65\x67\x75\x65\x5f\x53\x65\x75"+ \
"\x73\x5f\x50\x6f\x6e\x74\x6f\x73\x5f\x65\x5f\x53\x61\x69\x61\x5f"+ \
"\x43\x6f\x72\x72\x65\x6e\x64\x6f\x7d"
>>> flag
'SHC{Pegue_Seus_Pontos_e_Saia_Correndo}'
>>> 
```

e ai era só pontuar :D
<br/><br/>
<hr class="codebreak">
# See
* Ghost
<br/><br/>

Bem facil essa, apesar do executavel apresentar dialog solicitando username e password, pelo descritivo já dava pra imaginar o que era.

```bash
fatlips//deadcow ~/shc % foremost veja.exe
Processing: veja.exe
|*|
fatlips//deadcow ~/shc % feh output/jpg/00000935.jpg
```
e voilá

![flag_see]({{ site.url }}/assets/img/flag_see.jpg)

<hr class="codebreak">
# Patch
* Hue Designer
<br/><br/>

Quando se tentava rodar o binário pelo wine, era apresentado uma dialog toda preta, com apenas um botão com "Ver Flag", quando se clicava, era apresentado uma nova dialog escrito "Péssimo Designer" com um botão de OK, e em seguida uma nova dialog com apenas um botão de OK. 

Da forma que foi apresentado o problema, das duas uma, ou tinha a ver com o fundo preto da dialog ou era necessário um debugging mais a fundo pois provavelmente voce teria que criar algum jump para obter a flag, mas na verdade era bem mais simples do que isso

```bash
fatlips//deadcow ~/shc % strings patch.exe|less
...
TForm1
TForm1
arquivo
ssimo Designer
S01ZREtSU1NLVlJURVRMTUlaSEZFMlNLSkJKSFV...
ZYYd
ZYYd
Error
Runtime error     at 00000000
0123456789ABCDEF
...
fatlips//deadcow ~/shc % echo S01ZREtSU1NLVlJURVRMTUlaSEZFMlNLSkJKSFVT... \
base64 -d | base32 | base64 -d | base32
SHC{Patch_1s_L1f3}
fatlips//deadcow ~/shc %
```
**ps:** o hash foi omitido pelo bem da formatação HUE!
<br/><br/>
<hr class="codebreak">
# Kathy
* O Que achou desses Pés?
<br/><br/>


Esse de longe foi o mais dificil, o problema consistia em 2 etapas distintas até que fosse encontrada a flag, na primeira analise do binário acabei encontrando um decimal que convertido apresentava uma dica.

```bash
fatlips//deadcow ~/shc % python2
Python 2.7.11 (default, Dec  6 2015, 15:43:46) 
[GCC 5.2.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> senha = [ 77,85,73,84,79,76,73,71,69,73,82,79,77,65,83,86,79,76,84,65,81,...
>>> ''.join(chr(c) for c in senha)
'MUITOLIGEIROMASVOLTAQUEASENHA\x14\x01DECIMAL'
>>>
```

Bom, pela informação do decimal, ele é uma senha, mas senha do que? nós tinhamos um executavel que exibia apenas uma imagem, e o steghide exige uma senha para extrair arquivos, entao temos que ter essa imagem para tentar alguma coisa mas usar o foremost foi em vão, então tivemos que descompactar o executavel para tentar achar a imagem.

```bash
fatlips//deadcow ~/shc % 7z x kathy.exe

7-Zip [64] 9.38 beta  Copyright (c) 1999-2014 Igor Pavlov  2015-01-03
p7zip Version 9.38.1 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs,ASM)

Processing archive: kathy.exe

Extracting  CODE
Extracting  DATA
Extracting  BSS
Extracting  .idata
Extracting  .tls
Extracting  .rdata
Extracting  .reloc
Extracting  .rsrc/0/CURSOR/1
Extracting  .rsrc/0/CURSOR/2
Extracting  .rsrc/0/CURSOR/3
Extracting  .rsrc/0/CURSOR/4
Extracting  .rsrc/0/CURSOR/5
Extracting  .rsrc/0/CURSOR/6
Extracting  .rsrc/0/CURSOR/7
Extracting  .rsrc/0/BITMAP/BBABORT.bmp
Extracting  .rsrc/0/BITMAP/BBALL.bmp
Extracting  .rsrc/0/BITMAP/BBCANCEL.bmp
Extracting  .rsrc/0/BITMAP/BBCLOSE.bmp
Extracting  .rsrc/0/BITMAP/BBHELP.bmp
Extracting  .rsrc/0/BITMAP/BBIGNORE.bmp
Extracting  .rsrc/0/BITMAP/BBNO.bmp
Extracting  .rsrc/0/BITMAP/BBOK.bmp
Extracting  .rsrc/0/BITMAP/BBRETRY.bmp
Extracting  .rsrc/0/BITMAP/BBYES.bmp
Extracting  .rsrc/0/BITMAP/PREVIEWGLYPH.bmp
Extracting  .rsrc/1046/ICON/1.ico
Extracting  .rsrc/0/DIALOG/DLGTEMPLATE
Extracting  .rsrc/0/STRING/4080
Extracting  .rsrc/0/STRING/4081
Extracting  .rsrc/0/STRING/4082
Extracting  .rsrc/0/STRING/4083
Extracting  .rsrc/0/STRING/4084
Extracting  .rsrc/0/STRING/4085
Extracting  .rsrc/0/STRING/4086
Extracting  .rsrc/0/STRING/4087
Extracting  .rsrc/0/STRING/4088
Extracting  .rsrc/0/STRING/4089
Extracting  .rsrc/0/STRING/4090
Extracting  .rsrc/0/STRING/4091
Extracting  .rsrc/0/STRING/4092
Extracting  .rsrc/0/STRING/4093
Extracting  .rsrc/0/STRING/4094
Extracting  .rsrc/0/STRING/4095
Extracting  .rsrc/0/STRING/4096
Extracting  .rsrc/0/RCDATA/DVCLAL
Extracting  .rsrc/0/RCDATA/PACKAGEINFO
Extracting  .rsrc/0/RCDATA/TFORM1
Extracting  .rsrc/0/GROUP_CURSOR/32761
Extracting  .rsrc/0/GROUP_CURSOR/32762
Extracting  .rsrc/0/GROUP_CURSOR/32763
Extracting  .rsrc/0/GROUP_CURSOR/32764
Extracting  .rsrc/0/GROUP_CURSOR/32765
Extracting  .rsrc/0/GROUP_CURSOR/32766
Extracting  .rsrc/0/GROUP_CURSOR/32767
Extracting  .rsrc/1046/GROUP_ICON/MAINICON

Everything is Ok

Files: 55
Size:       532936
Compressed: 536576
fatlips//deadcow ~/shc %
```

Com o executavel descompactado, foi necessário achar a imagem que o binário exibia e então usar o steghide com a senha que strings no executavel mostrava.

```bash
fatlips//deadcow ~/shc/.rsrc/0/RCDATA % xxd -p TFORM1 | tr -d '\n' | \
grep -Eo "ffd8.*ffd9" | xxd -r -p > flag.jpg
fatlips//deadcow ~/shc/.rsrc/0/RCDATA % file flag.jpg
flag.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), densit..
fatlips//deadcow ~/shc/.rsrc/0/RCDATA % cp -fr flag.png ~/shc/foot.jpg 
fatlips//deadcow ~/shc/.rsrc/0/RCDATA % cd ~/shc 
fatlips//deadcow ~/shc % steghide --extract -sf foot.jpg
Enter passphrase: 
Corrupt JPEG data: 75 extraneous bytes before marker 0xdb
wrote extracted data to "flag.txt".
fatlips//deadcow ~/shc % cat flag.txt
http://ctf.sucurihc.org/flag/fuck/p.rar
fatlips//deadcow ~/shc % wget http://ctf.sucurihc.org/flag/fuck/p.rar
--2016-06-07 01:08:28--  http://ctf.sucurihc.org/flag/fuck/p.rar
Resolving ctf.sucurihc.org (ctf.sucurihc.org)... 104.28.16.81, 104.28.17.81
Connecting to ctf.sucurihc.org (ctf.sucurihc.org)|104.28.16.81|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 54963 (54K) [application/x-rar-compressed]
Saving to: ‘p.rar’

p.rar                100%[=====================>]  53.67K   153KB/s   in 0.4s 

2016-06-07 01:08:29 (153 KB/s) - ‘p.rar’ saved [54963/54963]

fatlips//deadcow ~/shc % unrar x p.rar

UNRAR 5.30 beta 4 freeware      Copyright (c) 1993-2015 Alexander Roshal


Extracting from p.rar

Extracting  flag.jpg                                                  OK 
All OK
fatlips//deadcow ~/shc % feh flag.jpg   # O tal pé bonito!
fatlips//deadcow ~/shc % strings flag.jpg
...
["GL
kgbs
<'i|
L<}t
]x3D
@>`;W
([K"
SHC{Kathy_Quer0_ver_S3u_pe!lol!slc}
fatlips//deadcow ~/shc %
```

Bang! a flag na mão heh :D
<br/><br/>
