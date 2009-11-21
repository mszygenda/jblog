---
layout: post
title: Odpowiedzi do laboratorium 5
---

#Zadanie 1
Znajdź w swoim katalogu domowym (bez podkatalogów) wszystkie pliki, które zostały zmodyfikowane w ciągu ostatnich dziesięciu dni i wyświetl ich nazwy.
<pre>
[mszygenda@sigma ~]$ find ~/ -mtime -10 -maxdepth 1
</pre>

#Zadanie 2
Znajdź wszystkie pliki zwykłe w systemie, które mają w nazwie ciąg znaków „conf” i wyświetl ich nazwy na ekranie.
<pre>
[mszygenda@sigma ~]$ find / -name \*conf\* -type f 2> /dev/null
</pre>

#Zadanie 3
Znajdź w swoim katalogu domowym wszystkie pliki, które nie były używane w ciągu ostatnich 20 dni.
<pre>
[mszygenda@sigma ~]$ find ~ -mtime -20 -type f
</pre>

#Zadanie 4
Znajdź w katalogu /etc wszystkie niepuste podkatalogi i pliki o nazwach zaczynających się na literę „a”.
<pre>
find /etc \( -type f -and -name a* \) -or \( -type d -and ! -empty \) 2> /dev/null
</pre>

#Zadanie 5
Z bieżącego katalogu usuń pliki, których nazwa zaczyna się na literę „x” i zawiera dokładnie trzy znaki.
<pre>
[mszygenda@sigma ~]$ touch xaa xab xac
[mszygenda@sigma ~]$ ls x\*
xaa  xab  xac
[mszygenda@sigma ~]$ rm x??
[mszygenda@sigma ~]$ ls x\*
ls: nie ma dostępu do x\*: Nie ma takiego pliku ani katalogu
[mszygenda@sigma ~]$
</pre>

#Zadanie 6
Skonstruuj polecenie tworzące katalog, którego nazwą będzie aktualna (w momencie wywołania) systemowa data w formacie
<pre>
[mszygenda@sigma tmp]$ mkdir \`date +%Y-%m-%d\`
</pre>

#Zadanie 7
Wyeksportowanie manuala do postscripta.
<pre>
[mszygenda@sigma tmp]$ man find -t > wynik.ps && ps2pdf wynik.ps druk.pdf
</pre>