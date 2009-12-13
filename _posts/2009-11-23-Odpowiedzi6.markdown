---
layout: post
title: Odpowiedzi do laboratorium 6
---

#Zadanie 1
W pliku „plik.txt” znajdź wiersze zawierające co najmniej jeden znak.
<pre>
[mszygenda@sigma lab6]$ egrep "[:alnum:]{1,}" plik.txt
</pre>

#Zadanie 2
Znajdź w plikach „pl*” wiersze rozpoczynające się od cyfry.
<pre>
[mszygenda@sigma tmp]$ egrep ^[0-9] pl*
</pre>

#Zadanie 3
Znajdź pliki, w których na 9 pozycji występuje litera „r”.
<pre>
[mszygenda@sigma tmp]$ find . 2> /dev/null | xargs egrep ^.{8}r -l 2> /dev/null
</pre>

#Zadanie 4
Policz, ilu użytkowników systemu używa powłoki bash (zgodnie z zapisami w pliku /etc/passwd).
<pre>
[mszygenda@sigma tmp]$ egrep /bin/bash$ /etc/passwd | wc -l
</pre>

#Zadanie 5
Znajdź wiersze zawierające liczby rzymskie w pliku „plik.txt”.
<pre>
[mszygenda@sigma tmp]$ egrep "(X|D|C|M|V|L|I){1,}" plik.txt
</pre>
