---
layout: post
title: Odpowiedzi do laboratorium 3
---
#Zadanie 1
Wyświetl plik /etc/passwd z podziałem na strony przyjmując ze strona ma 5 linii tekstu
<pre>
[mszygenda@sigma jblog]$ cat /etc/passwd | pg -5
</pre>

#Zadanie 2
Korzystając z polecenia cat utwórz plik tekst3.txt, który będzie składał się z zawartości pliku tekst1.txt, ciągu znaków podanego ze standardowego wejścia (klawiatury) i pliku tekst2.txt
<pre>
[mszygenda@sigma lab3]$ cat >  tekst1.txt
Plik tekst1.txt
[mszygenda@sigma lab3]$ ls
tekst1.txt
[mszygenda@sigma lab3]$ cat tekst1.txt 
Plik tekst1.txt
[mszygenda@sigma lab3]$ cat > tekst2.txt
Plik tekst2.txt
[mszygenda@sigma lab3]$ cat tekst1.txt > tekst3.txt
[mszygenda@sigma lab3]$ cat  >> tekst3.txt
Przykładowy tekst z klawiatury
[mszygenda@sigma lab3]$ cat tekst2.txt >> tekst3.txt
[mszygenda@sigma lab3]$ cat tekst3.txt
Plik tekst1.txt
Przykładowy tekst z klawiatury
Plik tekst2.txt
[mszygenda@sigma lab3]$ 
</pre>

#Zadanie 3
 Wyświetl po 5 pierwszych linii wszystkich plików w swoim katalogu domowym w taki sposób, aby nie były wyświetlane ich nazwy.
<pre>
[mszygenda@sigma ~]$ head -qn 5 *
</pre>

#Zadanie 4
Wyświetl linie o numerach 3, 4 i 5 z pliku /etc/passwd.
<pre>
[mszygenda@sigma ~]$ cat /etc/passwd | sed -n 3,5p
daemon:x:2:2:daemon:/sbin:/bin/false
adm:x:3:4:adm:/var/account:/bin/false
lp:x:4:7:lp:/var/spool/lpd:/bin/false
[mszygenda@sigma ~]
</pre>

#Zadanie 5
Wyświetl linie o numerach 7, 6 i 5 od końca pliku /etc/passwd.
<pre>
[mszygenda@sigma ~]$ tac /etc/passwd | sed -n 5,7p
polkituser:x:220:220:PolicyKit User:/usr/share/empty:/bin/false
messagebus:x:122:122:System message bus:/usr/share/empty:/bin/false
postgres:x:88:88:PostgreSQL Server:/home/services/postgres:/bin/sh
[mszygenda@sigma ~]$ 
</pre>

#Zadanie 6
Wyświetl zawartość pliku /etc/passwd w jednej linii.
<pre>
[mszygenda@sigma ~]$ cat /etc/passwd  | tr -d "\n"
</pre>

#Zadanie 7
Za pomocą filtru tr wykonaj modyfikację pliku plik.txt, polegającą na umieszczeniu każdego słowa w osobnej linii.
<pre>
[mszygenda@sigma ~]$ cat /etc/passwd  | tr " |:|/|." "\n"

</pre>
#Zadanie 8
Zlicz wszystkie pliki znajdujące się w katalogu /etc i jego podkatalogach.
<pre>
[mszygenda@sigma ~]$ find /etc/ -type f 2> errors | wc -l
829
[mszygenda@sigma ~]$ 

</pre>

#Zadanie 9
Napisać polecenie zliczające ilość znaków z pierwszych trzech linii pliku /etc/passwd.

<pre>
[mszygenda@sigma ~]$ head /etc/passwd -n 3 | wc -c
99
[mszygenda@sigma ~]$ 

</pre>