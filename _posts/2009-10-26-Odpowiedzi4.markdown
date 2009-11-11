---
layout: post
title: Odpowiedzi do laboratorium 4
---

#Zadanie 1
Wyświetl listę plików z aktualnego katalogu, zamieniając wszystkie małe litery na duże.
<pre>
[mszygenda@sigma _posts]$ ls | tr [:lower:] [:upper:]
2009-06-12-JEKYLL-HOWTO.MARKDOWN
2009-10-17-ODPOWIEDZI-DO-ZADAN-LABORATORIUM-1.MARKDOWN
2009-10-19-ABOUT.MARKDOWN
2009-10-25-ODPOWIEDZI2.MARKDOWN
2009-10-25-ODPOWIEDZI3.MARKDOWN
2009-10-26-ODPOWIEDZI4.MARKDOWN
[mszygenda@sigma _posts]$ 
</pre>

#Zadanie 2
 Wyświetl listę praw dostępu do plików w aktualnym katalogu, ich rozmiar i nazwę.
<pre>
[mszygenda@sigma _posts]$ find . -printf "Plik: %f Rozmiar: %s Prawa: %M \n" -maxdepth 1
</pre>

#Zadanie 3
Wyświetl listę plików w aktualnym katalogu, posortowaną według rozmiaru pliku.

<pre>
[mszygenda@localhost srod_program]$ ls --sort=size -1
</pre>

#Zadanie 4
Wyświetl zawartość pliku /etc/passwd posortowaną według numerów UID w kolejności od największego do najmniejszego.

<pre>
cat /etc/passwd | sort --reverse --field-separator=":" --general-numeric-sort --key 3
</pre>

#Zadanie 5
Wyświetl zawartość pliku /etc/passwd posortowaną najpierw według numerów GID w kolejności od największego do najmniejszego, a następnie UID.
<pre>
cat /etc/passwd | sort --field-separator=":" --general-numeric-sort --key 4,3 --reverse
</pre>
#Zadanie 6
Podaj liczbę plików każdego użytkownika.
<pre>
[mszygenda@localhost srod_program]$ find / -printf "%u\n" 2> /dev/null | sort | uniq -c
</pre>

#Zadanie 7
Sporządź statystykę praw dostępu (dla każdego z praw dostępu podaj ile razy zostało ono przydzielone).
<pre>
[mszygenda@localhost srod_program]$ find -printf "%m\n" | sort | uniq -c
</pre>

#Zadanie 8

<pre>
//Do pliku lsout.txt wpisz szczegolowa liste plikow
ls -l > lsout.txt                          #  1
//Do pliku lsout.txt dopisz szczegolowa liste plikow z tego katalogu wraz z plikami ukrytymi(Zaczynajacymi sie od .)
ls -la >> lsout.txt                        #  2
//Do pliku psout.txt dopisz liste uruchomionych procesow
ps >> psout.txt                            #  3
//Do pliku znajdujacego sie w katalogu domowym dopisz ilosc wolnej pamieci
free -m >> ~/wynik                         #  4
//Zabij proces o identyfikatorz 1234 i bledy przekaz do pliku killerr.txt natomiast. Komunikaty informacyjne do pliku killout.txt
kill -1 1234 > killout.txt 2>killerr.txt   #  5
// - || - Przekaz bledy na standardowe wyjscie(Na ekran)
kill -1 1234 > killout.txt 2>&1            #  6
// Nie pokazuj komunikatow informacyjnych(Wywal do /dev/null, wyswietl natomiast bledy)
kill -1 1234 > /dev/null 2>&1              #  7
//Posortuj liste procesow w pliku psout.txt
sort psout.txt > pssort.txt                #  8
//pssort.txt nadpisz posortowanymi procesami(Nic sie nie zmieni)
ps | sort > pssort.txt                     #  9
//Posortuj liste plikow z pliku lsout.txt
cat lsout.txt | sort > lssort.txt          # 10
//Posortuj liste zalogowanych uzytkownikow i dodaj stronicowanie
who | sort | more                          # 11
who | sort | less                          # 12
</pre>