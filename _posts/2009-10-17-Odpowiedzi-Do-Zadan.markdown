---
layout: post
title: Odpowiedzi do laboratorium
---
# {{ page.title }}

# Zadanie 1
<pre>
[mszygenda@sigma temp]$ cal -m
  październik 2009
po wt śr cz pi so ni
          1  2  3  4
 5  6  7  8  9 10 11
12 13 14 15 16 17 18
19 20 21 22 23 24 25
26 27 28 29 30 31

</pre>


# Zadanie 2
<pre>
[mszygenda@sigma temp]$ date -d 1975-05-25 +%A
niedziela
</pre>


# Zadanie 3.

<pre>
[mszygenda@sigma srod_program]$ mkdir temp
[mszygenda@sigma srod_program]$ cd temp
[mszygenda@sigma temp]$ mkdir dom
[mszygenda@sigma temp]$ mkdir -p nauka/c
[mszygenda@sigma temp]$ mkdir -p nauka/logo
[mszygenda@sigma temp]$ mkdir -p nauka/pascal
[mszygenda@sigma temp]$ mkdir -p praca/dokumenty
[mszygenda@sigma temp]$ mkdir -p praca/zlecenia/niezrealizowane
[mszygenda@sigma temp]$ mkdir -p praca/zlecenia/zrealizowane
[mszygenda@sigma temp]$ tree
.
|-- dom
|-- nauka
|   |-- c
|   |-- logo
|   `-- pascal
`-- praca
    |-- dokumenty
    `-- zlecenia
        |-- niezrealizowane
        `-- zrealizowane

10 directories, 0 files

</pre>
# Zadanie 4

<pre>
[mszygenda@sigma temp]$ cd dom
[mszygenda@sigma dom]$ mkdir wazne-sprawy
</pre>

# Zadanie 5
<pre>
[mszygenda@sigma dom]$ cd wazne-sprawy
[mszygenda@sigma wazne-sprawy]$ echo 12345678911 > rachunki.txt
[mszygenda@sigma wazne-sprawy]$ ls
rachunki.txt
</pre>
# Zadanie 6
<pre>
[mszygenda@sigma wazne-sprawy]$ cp rachunki.txt ../../praca/zlecenia/zrealizowane
[mszygenda@sigma wazne-sprawy]$ cd ..
[mszygenda@sigma dom]$ ls
wazne-sprawy
</pre>
#Zadanie 7
<pre>
[mszygenda@sigma dom]$ cd ..
[mszygenda@sigma temp]$ ls
dom  nauka  praca
[mszygenda@sigma temp]$ cd praca
[mszygenda@sigma praca]$ ls
dokumenty  zlecenia
[mszygenda@sigma praca]$ cd zlecenia
[mszygenda@sigma zlecenia]$ ls
niezrealizowane  zrealizowane
[mszygenda@sigma zlecenia]$ cd zrealizowane
[mszygenda@sigma zrealizowane]$ ls
rachunki.txt
[mszygenda@sigma zrealizowane]$ mv rachunki.txt wykonano.txt
</pre>
#Zadanie 8
<pre>
[mszygenda@sigma zrealizowane]$ split wykonano.txt --bytes=5
[mszygenda@sigma zrealizowane]$ ls
wykonano.txt  xaa  xab  xac
[mszygenda@sigma zrealizowane]$ cat xaa
12345
[mszygenda@sigma zrealizowane]$ cat xab
67891
[mszygenda@sigma zrealizowane]$ cat xac
1
</pre>
#Zadanie 9
#
<pre>
[mszygenda@sigma zrealizowane]$ cd ..
[mszygenda@sigma zlecenia]$ cd ..
[mszygenda@sigma praca]$ ls
dokumenty  zlecenia
[mszygenda@sigma praca]$ cd dokumenty
[mszygenda@sigma dokumenty]$ ls
[mszygenda@sigma dokumenty]$ cd ..
[mszygenda@sigma praca]$ ls
dokumenty  zlecenia
[mszygenda@sigma praca]$ cd ..
[mszygenda@sigma temp]$ ls
dom  nauka  praca
[mszygenda@sigma temp]$ cd nauka/logo
[mszygenda@sigma logo]$ cp ../../praca/zlecenia/zrealizowane/x* ../../praca/dokumenty
</pre>

#Zadanie 10
<pre>
[mszygenda@sigma logo]$ cd ../../praca/dokumenty
[mszygenda@sigma dokumenty]$ ls
xaa  xab  xac
[mszygenda@sigma dokumenty]$ cat xaa > odtworzono.txt
[mszygenda@sigma dokumenty]$ cat xab >> odtworzono.txt
[mszygenda@sigma dokumenty]$ cat xac >> odtworzono.txt
[mszygenda@sigma dokumenty]$ cat odt*
12345678911
[mszygenda@sigma dokumenty]$ ls
odtworzono.txt  xaa  xab  xac
[mszygenda@sigma dokumenty]$ cp odtworzono.txt ../../dom/wazne-sprawy
</pre>
#Zadanie 11
<pre>
[mszygenda@sigma dokumenty]$ cd ../../dom/wazne-sprawy
[mszygenda@sigma wazne-sprawy]$ ls
odtworzono.txt  rachunki.txt
[mszygenda@sigma wazne-sprawy]$ diff ./odtworzono.txt ../../praca/zlecenia/zrealizowane/wykonano.txt
</pre>

#Zadanie 12
<pre>
[mszygenda@sigma wazne-sprawy]$ 
[mszygenda@sigma wazne-sprawy]$ cd ..
[mszygenda@sigma dom]$ cd ..
[mszygenda@sigma temp]$ cd nauka/c
[mszygenda@sigma c]$ ls
[mszygenda@sigma c]$ vim program.c
</pre>
#Zadanie 13
<pre>
[mszygenda@sigma c]$ cat program.c | grep . -m 2
#include <stdio.h>
#int main()
</pre>

#Zadanie 14
<pre>
[mszygenda@sigma c]$ cat program.c
#include <stdio.h>

int main()
{
	int n;
	for(n = 0; n < 100; n++)
	{
		printf("Witaj po raz %i", n);
	}
	int wynik = n * 2;
	return 0;
}
</pre>
#Zadanie 15
<pre>
[mszygenda@sigma c]$ cat program.c | grep main
int main()
</pre>

#Zadanie 16
<pre>
[mszygenda@sigma c]$ chmod o+rw program.c
[mszygenda@sigma c]$ chmod g+r program.c
[mszygenda@sigma c]$ chmod o-rwx program.c
[mszygenda@sigma c]$ ls -l
total 4
-rw-r----- 1 mszygenda studinf 138 10-12 12:58 program.c
[mszygenda@sigma c]$ cd ..
[mszygenda@sigma nauka]$ cd ..
[mszygenda@sigma temp]$ ls
dom  nauka  praca
[mszygenda@sigma temp]$ tree
.
|-- dom
|   `-- wazne-sprawy
|       |-- odtworzono.txt
|       `-- rachunki.txt
|-- nauka
|   |-- c
|   |   `-- program.c
|   |-- logo
|   `-- pascal
`-- praca
    |-- dokumenty
    |   |-- odtworzono.txt
    |   |-- xaa
    |   |-- xab
    |   `-- xac
    `-- zlecenia
        |-- niezrealizowane
        `-- zrealizowane
            |-- wykonano.txt
            |-- xaa
            |-- xab
            `-- xac

11 directories, 11 files
[mszygenda@sigma temp]$ ls
dom  nauka  praca
</pre>
