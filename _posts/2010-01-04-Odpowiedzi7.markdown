---
layout: post
title: Odpowiedzi do laboratorium 7 ( Skrypty ) 
---

#Zadanie 1
W bieżącym katalogu zamienić rozszerzenia wszystkich plików z rozszerzeniem htm na html. Jeżeli w nazwie pliku istnieje spacja, to należy zamienić ją na znak podkreślenia.
<br />
tohtml.sh
<pre>
#!/bin/bash
IFS='
'
files=(`find \`pwd\` -maxdepth 1 -iname "*.htm" `)
for file in ${files[*]}
do
    fileNew=`echo $file | tr " " "_"`l
    mv "$file"  "$fileNew"
done
</pre>

#Zadanie 2
Napisać skrypt zawierający funkcję obliczającą silnię. Następnie należy obliczyć silnię z liczby, która jest argumentem skryptu. W przypadku niepoprawnego argumentu należy wypisać odpowiedni komunikat.
<br />
silnia.sh
<pre>
#!/bin/bash
# Mateusz Szygenda
# Uzycie:
# silnia.sh Argument1 Argument2 Argument3 ... ArgumentN
# Gdzie Argument1,Argument2,Argument3 to liczby naturalne dla których skrypt powinien policzyć silnie
# Wynik:
# Silnia dla Argument1 = Argument1! ...
# lub Argument nie jest poprawny
for arg in $@
do
    result=1
    i=1
    if [ $arg -ge 0 ];
    then
	while [ $i -le $arg ]; 
	do
	    result=$[ $result * $i ]
	    i=$[ $i + 1]
	done
	echo "Silnia dla $arg = $result"
    else
	echo "$arg nie jest poprawnym argumentem"
    fi

done
</pre>


#Zadanie 3
Napisać skrypt zbierający jak najwięcej informacji o użytkowniku, którego login jest argumentem skryptu. Jeżeli skrypt nie ma argumentu, to należy użyć login osoby uruchamiającej skrypt.
<br />
userinfo.sh
<pre>
#!/bin/bash
# Mateusz Szygenda
# Uzycie
# userinfo.sh NAZWA_UZYTKOWNIKA

if [ $# -ge 1 ];
then
    user=$1
else
    user=`whoami`
fi
id $user 2> /dev/null > /dev/null
if [ $? -eq 0 ];
then
    echo "Uzytkownik nazywa sie $user"
    users | grep -w "$user" > /dev/null 2> /dev/null
    if [ $? -eq 0 ];
    then
	echo "Jest aktualnie zalogowany"
    else
	echo "Nie jest aktualnie zalogowany"
    fi
    echo "Nalezy do grup: "`id $user -gn`
    user_passwd=`cat /etc/passwd | grep -w $user`
    if [ $? -eq 0 ];
    then
	home_dir=`echo $user_passwd | cut -d ":" -f 6`
	shell=`echo $user_passwd | cut -d ":" -f 7`
	echo "Katalog domowy to $home_dir a powloka jakiej uzywa to $shell"
    else
	echo "W pliku /etc/passwd nie ma informacji o tym uzytkowniku"
    fi
else
    echo "Uzytkownik $user nie istnieje"
fi

</pre>
#Zadanie 4
Napisz skrypt usuwający z katalogu domowego i jego podkatalogów wszystkie pliki zwykłe o nazwie 'core' starsze niż 3 dni.
<br />
cleaner.sh
<pre>
#!/bin/bash
# Mateusz Szygenda
IFS='
'
files=`find ~ -name "core" -ctime +3  -type f | xargs -I file rm "$file" `
echo "Milego dnia! :)"
</pre>
