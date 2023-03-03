#####Level 0

$ssh bandit0@bandit.labs.overthewire.org -p 2220 
#da bismo pristupili serveru koristimo alat (komandu) SSH, gdje preko porta 2220 pristupamo
#hostu bandit.labs.overthewire.org

#ispis na ekranu, gdje nam trazi sifru:
#bandit0@bandit.labs.overthewire.org's password:
$bandit0


#####Level 0 -> Level 1

$ls #komanda ls ispisuje listu svih file-ova koji se nalaze

$cat readme #komadom cat ispisujemo sve sto se nalazi u file-u "readme"
#tj konkretno u njemu se nalazi pass za pristup bandit1
#isti trebamo kopirati i iskoristiti za sljedeci korak

$exit #da bismo se mogli spojiti na bandit1, moramo se odjaviti sa bandit0 i to radi komanda exit - vraca se na prethodnog korisnika ili logout

$ssh bandit1@bandit.labs.overthewire.org -p 2220 #komadom ssh se spajamo na bandit1, preko porta 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit1@bandit.labs.overthewire.org's password:
$NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL


#####Level 1 -> Level 2

$ls

$cat < - #dodajemo znak manje "<" kako bismo otvorili file "-"
#da ne bismo dobili otvoreni terminal prilikom poziva "cat -"
#kopiramo sadrzaj file-a "-"

$exit

$ssh bandit2@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit2@bandit.labs.overthewire.org's password:
$rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

#####Level 2 -> Level 3

$ls

$cat spaces\ in\ this\ filename #posto naziv file-a ima razmake, iza svakog zadnjeg slova
#rijeci stavljamo znak "\", kako bi se isti ucitao
#kopiramo sadrzaj file-a "spaces in this filename"

$exit

$ssh bandit3@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit3@bandit.labs.overthewire.org's password:
$aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

#####Level 3 -> Level 4

$ls

$cd inhere #posto se radi o folderu prvo moramo uci u taj folder pa u neki od file-ova

$ls -la #komanda ls koja ispisuje sve file-ove ne bi nista uradila
#potrebna nam komanda -la koja ispisuje i skrivene file-ove

$cat .hidden
#kopiramo sadrzaj skrivenom file-a ".hidden"

$exit

$ssh bandit4@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit4@bandit.labs.overthewire.org's password:
$2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe


#####Level 4 -> Level 5

$ls

$cd inhere #posto se radi o folderu prvo moramo uci u taj folder pa u neki od file-ova

$ls -la 

$cat <-file07 #
#kopiramo sadrzaj file-a "-file07"

$exit

$ssh bandit5@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit5@bandit.labs.overthewire.org's password:
$lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

#####Level 5 -> Level 6

$ls

$cd inhere #posto se radi o folderu prvo moramo uci u taj folder pa u neki od foldera

$find . -type f -size 1033c -name "[[:print:]]*" ! -executable 
#pretrazivanje file-a uz pomoc karakteristika: 
#. type f - pokreni svaku datoteku prilikom potrage za file-om
#velicina 1033c(gdje je c oznaka za bytes)
#not executable - znak "!" je sinonim za negaciju
#nakon poziva komande file, u terminalu nam izlazi direktorij do trazenog file-a
#./maybehere07/.file2


$cd maybehere07 #ulazimo prvo u ovaj folder

$cat .file2
#kopiramo sadrzaj file-a ".file2"

$exit

$ssh bandit6@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit6@bandit.labs.overthewire.org's password:
$P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU


#####Level 6 -> Level 7


$ find / -user bandit7 -group bandit6 -size 33c -type f 2>/dev/n
ull 
#pretrazivanje file-a uz pomoc karakteristika: 
#. type f - pokreni svaku datoteku prilikom potrage za file-om
#velicina 33c(gdje je c oznaka za bytes)
#da je u vlasnistvu user-a bandit7
#da je u vlasnistvu grupe bandit6
#nakon poziva komande file, u terminalu nam izlazi direktorij do trazenog file-a
#/var/lib/dpkg/info/bandit7.password


$cat /var/lib/dpkg/info/bandit7.password
#kopiramo sadrzaj file-a "bandit7.password"

$exit

$ssh bandit7@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit7@bandit.labs.overthewire.org's password:
&z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S



#####Level 7 -> Level 8

$ls -la

$grep millionth data.txt #posto je data.txt prevelika datoteka
#pomocu komande grep pranadimo sve dijelove tog file-a koji sadrze "millionth"
#kopiramo sadrzaj iza rijeci "millionth"

$exit

$ssh bandit8@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit8@bandit.labs.overthewire.org's password:
&TESKZC0XvTetK0S9xNwm25STk5iWrBvP


#####Level 8 -> Level 9

$sort data.txt | uniq -c | grep '^ *1 '
#pomocu komande sort, sortiramo file data.txt tako da se pojavljuje u jednoj liniji i jednom
#kopiramo sadrzaj iza broja "1"

$exit

$ssh bandit9@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit9@bandit.labs.overthewire.org's password:
&EN632PlfYiZbn3PhVK3XOGSlNInNE00t

#####Level 9 -> Level 10

$strings data.txt | grep -E "=+"
#trazimo stringove u file-u data.txt ispred koji se nalazi jedan ili vise znakova "="
#kopiramo sadrzaj passworda iza nekoliko znakova "="

$exit

$ssh bandit10@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit10@bandit.labs.overthewire.org's password:
$G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s


#####Level 10 -> Level 11

$cat data.txt | base64 -d
#pretrazi file data.txt i pronaci base64 kodirane podatke
#kopiraj password

$exit

$ssh bandit11@bandit.labs.overthewire.org -p 2220

#ispis na ekranu, gdje nam trazi sifru:
#bandit10@bandit.labs.overthewire.org's password:
$6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
