---
layout: post
title: Odpowiedzi do laboratorium 7 ( Skrypty ) 
---

#Zadanie 1
W bie��cym katalogu zamieni� rozszerzenia wszystkich plik�w z rozszerzeniem htm na html. Je�eli w nazwie pliku istnieje spacja, to nale�y zamieni� j� na znak podkre�lenia.
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
Napisa� skrypt zawieraj�cy funkcj� obliczaj�c� silni�. Nast�pnie nale�y obliczy� silni� z liczby, kt�ra jest argumentem skryptu. W przypadku niepoprawnego argumentu nale�y wypisa� odpowiedni komunikat.
<br />
silnia.sh
<pre>
#!/bin/bash
# Mateusz Szygenda
# Uzycie:
# silnia.sh Argument1 Argument2 Argument3 ... ArgumentN
# Gdzie Argument1,Argument2,Argument3 to liczby naturalne dla kt�rych skrypt powinien policzy� silnie
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
Napisa� skrypt zbieraj�cy jak najwi�cej informacji o u�ytkowniku, kt�rego login jest argumentem skryptu. Je�eli skrypt nie ma argumentu, to nale�y u�y� login osoby uruchamiaj�cej skrypt.
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
Napisz skrypt usuwaj�cy z katalogu domowego i jego podkatalog�w wszystkie pliki zwyk�e o nazwie 'core' starsze ni� 3 dni.
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
