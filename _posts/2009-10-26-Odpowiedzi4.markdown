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
[mszygenda@sigma jblog]$ ls --format=long --human-readable
</pre>

#Zadanie 3
Wyświetl listę plików w aktualnym katalogu, posortowaną według rozmiaru pliku.
<pre>
[mszygenda@sigma jblog]$ ls --sort=size -l
</pre>