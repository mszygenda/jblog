---
layout: post
title: Odpowiedzi do laboratorium 1
---
# {{ page.title }}


# Zadanie 1.
Używając linii poleceń stwórz strukturę katalogów

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
# Zadanie 2
Przejdź do katalogu dom i utwórz katalog wazne-sprawy

<pre>
[mszygenda@sigma temp]$ cd dom
[mszygenda@sigma dom]$ mkdir wazne-sprawy
</pre>

# Zadanie 3
Przejdz do katalogu wazne-sprawy i utworz tam pusty plik rachunki.txt

<pre>
[mszygenda@sigma dom]$ cd wazne-sprawy
[mszygenda@sigma wazne-sprawy]$ echo -n 12345678911 > rachunki.txt
[mszygenda@sigma wazne-sprawy]$ ls
rachunki.txt
</pre>
# Zadanie 4
Będąc w katalogu wazne-sprawy skopiuj plik rachunki.txt do katalogu zrealizowane
<pre>
[mszygenda@sigma wazne-sprawy]$ cp rachunki.txt ../../praca/zlecenia/zrealizowane
[mszygenda@sigma wazne-sprawy]$ cd ..
[mszygenda@sigma dom]$ ls
wazne-sprawy
</pre>
#Zadanie 5
Przejdź do katalogu zrealizowane i zmień nazwę pliku rachunki.txt na wykonano.txt
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
#Zadanie 6
Utwórz plik wykonano.txt wielkości 11 bajtów, następnie podziel go na pliki wielkości 5 bajtów.
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
#Zadanie 7

Będąc w katalogu logo skopiuj otrzymane 3 pliki do katalogu dokumenty.
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

#Zadanie 8
Będąc w katalogu dokumenty połącz skopiowane 3 pliki w odtworzono.txt tak aby otrzymać identyczną zawartość jak wykonano.txt nastepnie skopiuj odtworzono.txt do katalogu wazne-sprawy
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
#Zadanie 9
Będąc w katalogu wazne-sprawy sprawdź czy sa jakies roznice w zawartosci wykonano.txt i odtworzono.txt
<pre>
[mszygenda@sigma dokumenty]$ cd ../../dom/wazne-sprawy
[mszygenda@sigma wazne-sprawy]$ ls
odtworzono.txt  rachunki.txt
[mszygenda@sigma wazne-sprawy]$ diff ./odtworzono.txt ../../praca/zlecenia/zrealizowane/wykonano.txt
</pre>

#Zadanie 10
Wyświetl kalendarz na październik

<pre>
[mszygenda@sigma temp]$ cal -m 10 2009
  październik 2009
po wt śr cz pi so ni
          1  2  3  4
 5  6  7  8  9 10 11
12 13 14 15 16 17 18
19 20 21 22 23 24 25
26 27 28 29 30 31

</pre>

#Zadanie 11
Jaki był dzień tygodnia 25 maja 1975.
<pre>
[mszygenda@sigma temp]$ date -d 1975-05-25 +%A
niedziela
</pre>

