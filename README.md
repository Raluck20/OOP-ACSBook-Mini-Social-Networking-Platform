# OOP-ACSBook-Mini-Social-Networking-Platform

I implemented a simplified social networking platform to simulate user interactions through classes and objects. Authenticated users in the system will be able to: create posts (which will contain text-only content), view posts from other users, like a post, leave comments on a post (which will also contain text-only content), like a comment, and follow other users.



Clasa User
-----------------------------------------------------------------------------------------------
Are 2 constructori: unul fara parametrii si unul cu parametrii username si password.

Metoda verif_login verifica daca lungimea lui args este fie 1, fie 2. In caz afirmativ,
afiseaza mesajul corespunzator de eroare si returneaza null. Apoi analizează argumentele
liniei de comanda pentru a extrage numele de utilizator și parola. Verifica daca primul
argument este "-u" (indicand prezenta unui nume de utilizator) si daca al doilea argument
este "-p" (indicand prezenta unei parole).
Dacă aceste condiții nu sunt îndeplinite, se afișează un mesaj de eroare corespunzator.

Metoda încearcă să citească datele utilizatorilor din users.csv.
Dacă fișierul este gol, se afișează un mesaj de eroare corepunzator.
Dacă fișierul nu este gol, se compară numele de utilizator și parola furnizate cu cele
stocate în fișier.
Dacă se găsește o potrivire, se returnează un nou obiect user cu numele de utilizator si
parola furnizate.

Metoda most_liked_users trateaza doar cazurile de UsersUsernameDoesNotExists, UsersNoUsername,
UsersNoPassword, UsersLoginCredentialsAreWrong.


Clasa Post
-----------------------------------------------------------------------------------------------
Metoda createpost:
  Se creează o instanță a clasei user și se apelează metoda verif_login pentru a verifica
autentificarea utilizatorului pe baza argumentelor primite. Dacă autentificarea eșuează, metoda
se încheie și se afiseaza mesajul de eroare corespunzator.
  Se verifică dacă numărul de argumente este exact 3 (adică, doar argumentele pentru comanda
createpost fără textul postului). Dacă da, se afișează un mesaj de eroare și se încheie metoda.
Altfel, daca numarul de argumente este mai mare decat 2, se obține textul postului și se
verifică dacă lungimea acestuia depășește 300 de caractere. Dacă da, se afișează un mesaj de
eroare corespunzator și se încheie metoda. Altfel, se delimitează textul postului, se verifică
dacă primul element al array-ului text este "-text".Dacă condiția este îndeplinită, se adăuga
textul postului in posts.csv si se adauga id-ul acestuia la final.

Metoda deletepost:
  Se creează o instanță a clasei user și se apelează metoda verif_login pentru a verifica
autentificarea utilizatorului pe baza argumentelor primite. Dacă autentificarea eșuează, metoda
se încheie și se afiseaza mesajul de eroare corespunzator.
  Se verifică dacă numărul de argumente este exact 3 (adică, doar argumentele pentru comanda
createpost fără textul postului). Dacă da, se afișează un mesaj de eroare și se încheie metoda.
Se obține identificatorul din al patrulea element al array-ului args (args[3]) și se verifică 
dacă primul element al array-ului arg3 este "-id". Dacă condiția este îndeplinită, se parcurge
fiecare linie a fișierului. Pentru fiecare linie, se desparte linia în componente folosind 
virgula ca separator și se obține identificatorul postului. Se compară identificatorul obținut
din linia curentă cu identificatorul furnizat prin linia de comandă (arg3[1]). Dacă există o
potrivire, se creează două obiecte de tip File pentru a reprezenta fișierul de intrare și fișierul
temporar.Se parcurge fiecare linie a fișierului de intrare, și se scrie în fișierul temporar toate
liniile care nu corespund identificatorului postului care trebuie șters.
Se afișează un mesaj de succes dacă ștergerea a fost realizată cu succes, altfel, se afișează un
mesaj de eroare.

Metoda like_post:
  Se creează o instanță a clasei user și se apelează metoda verif_login pentru a verifica
autentificarea utilizatorului pe baza argumentelor primite. Dacă autentificarea eșuează, metoda
se încheie și se afiseaza mesajul de eroare corespunzator.
  Se verifică dacă numărul de argumente este exact 3 (adică, doar argumentele pentru comanda
like_post fără identificatorul postului de apreciat). Dacă da, se afișează un mesaj de eroare
și se încheie metoda.
  Altfel, dacă numărul de argumente este mai mare decât 2, se obține identificatorul postului
din al patrulea element al array-ului args (args[3]) și se verifică dacă primul element al
array-ului argid este "-post-id". Dacă condiția este îndeplinită, se parcurge fiecare linie a
fișierului. Pentru fiecare linie, se desparte linia în componente folosind virgula ca separator
si se obține identificatorul postului. Se compară identificatorul obținut din linia curentă cu
identificatorul furnizat. Dacă există o potrivire, se incrementază numărul de like-uri, ok
devine 1 (adica postarea a fost apreciata) și se afișează un mesaj de succes.
Dacă nu există potrivire, se afișează un mesaj de eroare.

Metoda unlike_post:
  Am implementat aceasi idee ca la metoda like_post, doar ca de aceasta data numarul de like-uri
scade.

Metodele lista_postari_follow, lista_postari_user, details_post, most_liked_posts si
most_commented_posts trateaza doar cazurile de UsersUsernameDoesNotExists, UsersNoUsername,
UsersNoPassword, UsersLoginCredentialsAreWrong.


Clasa Follow
-----------------------------------------------------------------------------------------------
  Metoda follow_user am implementat-o dupa aceasi idee ca la metoda createpost, metoda
unfollow_user am implementat-o dupa aceasi idee ca la metoda detelepost.
  Metodele following_user, followers_user si most_followed_users trateaza doar cazurile de
UsersUsernameDoesNotExists, UsersNoUsername, UsersNoPassword, UsersLoginCredentialsAreWrong.


Clasa Comment
-----------------------------------------------------------------------------------------------
  Metoda createcomment am implementat-o dupa aceasi idee ca la metoda createpost, metoda
deletecomment am implementat-o dupa aceasi idee ca la metoda deletepost, metoda like_comment
am implementat-o dupa aceasi idee ca la metoda like_post iar metoda unlike_comment am
implementat-o dupa aceasi idee ca la metoda unlike_post.


Main
-----------------------------------------------------------------------------------------------
  Verific care este comanda.
  Daca este -cleanup-all, sterg continutul fisierelor create.
  Daca este -create-user, se verifică dacă există suficiente argumente pentru a crea un utilizator.
Dacă nu există suficiente argumente, se afișează un mesaj de eroare corespunzător. Se desparte
al doilea argument (strings[1]) în două componente folosind spațiul ca separator.
Se obține primul element (argument1) și al doilea element (username) din rezultatul splitării.
Se verifică dacă primul element (argument1) este "-u", indicând prezența unui nume de utilizator
în următorul argument. Dacă nu este prezent un nume de utilizator (argument1 nu este "-u"),
se afișează un mesaj de eroare corespunzator. Dacă este prezent un nume de utilizator, se
verifică dacă acesta există deja in users.csv. Dacă da, se afișează un mesaj de eroare
corespunzator.
Se desparte al treilea argument (strings[2]) în două componente folosind spațiul ca separator.
Se verifică dacă primul element (argument2[0]) este "-p", indicând prezența unei parole in
următorul argument.
Dacă nu este prezentă o parolă (argument2[0] nu este "-p"), se afișează un mesaj de eroare
corespunzator.Dacă este prezentă o parolă, se atribuie parola variabilei my_password.
Se afișează un mesaj de succes, indicând că utilizatorul a fost creat cu succes și se adaugă
numele de utilizator și parola într-o nouă linie a fișierului users.csv.
  Dacă prima comandă este "-create-post", se creează o instanță a clasei post și se apelează
metoda createpost cu argumentele primite.
  Dacă prima comandă este "-delete-post-by-id", se creează o instanță a clasei post și se
apelează metoda deletepost cu argumentele primite.
  Dacă prima comandă este "-follow-user-by-username", se creează o instanță a clasei follow
si se apelează metoda follow_user cu argumentele primite.
...si asa mai departe pentru fiecare comanda.
