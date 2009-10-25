---
layout: post
title: Odpowiedzi do laboratorium 2
---

W katalogu c utwórz plik program.c zawierający co najmniej 10 linii kodu napisanego w języku C.
<pre>
[mszygenda@sigma wazne-sprawy]$ 
[mszygenda@sigma wazne-sprawy]$ cd ..
[mszygenda@sigma dom]$ cd ..
[mszygenda@sigma temp]$ cd nauka/c
[mszygenda@sigma c]$ ls
[mszygenda@sigma c]$ vim program.c
</pre>
#Zadanie 1
Wyświetl na ekran 2 pierwsze wiersze pliku program.c
<pre>
[mszygenda@sigma c]$ cat program.c | grep . -m 2
\#include <stdio.h>
\#int main()
</pre>

#Zadanie 2
Wyświetl na ekran4  ostatnie wiersze pliku program.c
<pre>
[mszygenda@sigma c]$ tail program.c -n -4
}
int wynik = n * 2;
return 0;
}
[mszygenda@sigma c]$ 
</pre>

#Zadanie 3
Wyświetl na ekran całą zawartość pliku program.c
<pre>
[mszygenda@sigma c]$ cat program.c
\#include <stdio.h>

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
#Zadanie 4
W pliku program.c znajdź wszystkie wiersze z wystąpieniem słowa "main"
<pre>
[mszygenda@sigma c]$ cat program.c | grep '\bmain\b'
int main()
</pre>

#Zadanie 5
Plikowi program.c nadaj następujące uprawnienia 
właściciel - czytanie,pisanie
grupa - czytanie
pozostali - brak uprawnień
<pre>
[mszygenda@sigma c]$ chmod o+rw program.c
[mszygenda@sigma c]$ chmod g+r program.c
[mszygenda@sigma c]$ chmod o-rwx program.c
</pre>

#Zadanie 6
Będąc w katalogu temp przenieś katalog wazne-sprawy do katalogu praca

<pre>
[mszygenda@sigma temp]$ mv dom/wazne-sprawy/ praca/
</pre>

#Zadanie 7

Zarchiwizuj cały katalog temp
<pre>
[mszygenda@sigma srod_program]$ zip -r temp.zip temp
  adding: temp/ (stored 0%)
  adding: temp/praca/ (stored 0%)
  adding: temp/praca/dokumenty/ (stored 0%)
  adding: temp/praca/dokumenty/xab (stored 0%)
  adding: temp/praca/dokumenty/xaa (stored 0%)
  adding: temp/praca/dokumenty/xac (stored 0%)
  adding: temp/praca/dokumenty/odtworzono.txt (stored 0%)
  adding: temp/praca/zlecenia/ (stored 0%)
  adding: temp/praca/zlecenia/niezrealizowane/ (stored 0%)
  adding: temp/praca/zlecenia/zrealizowane/ (stored 0%)
  adding: temp/praca/zlecenia/zrealizowane/xab (stored 0%)
  adding: temp/praca/zlecenia/zrealizowane/wykonano.txt (stored 0%)
  adding: temp/praca/zlecenia/zrealizowane/xaa (stored 0%)
  adding: temp/praca/zlecenia/zrealizowane/xac (stored 0%)
  adding: temp/praca/wazne-sprawy/ (stored 0%)
  adding: temp/praca/wazne-sprawy/rachunki.txt (stored 0%)
  adding: temp/praca/wazne-sprawy/odtworzono.txt (stored 0%)
  adding: temp/nauka/ (stored 0%)
  adding: temp/nauka/logo/ (stored 0%)
  adding: temp/nauka/c/ (stored 0%)
  adding: temp/nauka/c/program.c (deflated 13%)
  adding: temp/nauka/pascal/ (stored 0%)
  adding: temp/dom/ (stored 0%)
[mszygenda@sigma srod_program]$ ls
temp  temp.tar  temp.zip
[mszygenda@sigma srod_program]$ tar -cf temp.tar temp

</pre>

#Zadanie 8
Usuń katalog temp
<pre>
[mszygenda@sigma srod_program]$ rm -R temp
</pre>

#Zadanie 9
Odtwórz archiwum
<pre>
[mszygenda@sigma srod_program]$ tar xf temp.tar
[mszygenda@sigma srod_program]$ ls
temp  temp.tar  temp.zip
[mszygenda@sigma srod_program]$ rm -R temp
[mszygenda@sigma srod_program]$ unzip temp.zip
Archive:  temp.zip
   creating: temp/
   creating: temp/praca/
   creating: temp/praca/dokumenty/
 extracting: temp/praca/dokumenty/xab  
 extracting: temp/praca/dokumenty/xaa  
 extracting: temp/praca/dokumenty/xac  
 extracting: temp/praca/dokumenty/odtworzono.txt  
   creating: temp/praca/zlecenia/
   creating: temp/praca/zlecenia/niezrealizowane/
   creating: temp/praca/zlecenia/zrealizowane/
 extracting: temp/praca/zlecenia/zrealizowane/xab  
 extracting: temp/praca/zlecenia/zrealizowane/wykonano.txt  
 extracting: temp/praca/zlecenia/zrealizowane/xaa  
 extracting: temp/praca/zlecenia/zrealizowane/xac  
   creating: temp/praca/wazne-sprawy/
 extracting: temp/praca/wazne-sprawy/rachunki.txt  
 extracting: temp/praca/wazne-sprawy/odtworzono.txt  
   creating: temp/nauka/
   creating: temp/nauka/logo/
   creating: temp/nauka/c/
  inflating: temp/nauka/c/program.c  
   creating: temp/nauka/pascal/
   creating: temp/dom/
[mszygenda@sigma srod_program]$ tree
.
|-- temp
|   |-- dom
|   |-- nauka
|   |   |-- c
|   |   |   `-- program.c
|   |   |-- logo
|   |   `-- pascal
|   `-- praca
|       |-- dokumenty
|       |   |-- odtworzono.txt
|       |   |-- xaa
|       |   |-- xab
|       |   `-- xac
|       |-- wazne-sprawy
|       |   |-- odtworzono.txt
|       |   `-- rachunki.txt
|       `-- zlecenia
|           |-- niezrealizowane
|           `-- zrealizowane
|               |-- wykonano.txt
|               |-- xaa
|               |-- xab
|               `-- xac
|-- temp.tar
`-- temp.zip

12 directories, 13 files
[mszygenda@sigma srod_program]$
</pre>