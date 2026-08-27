## H5 Binääri tässä, missä koodit?  

# Lab0  

Aloitetaan purkamalla lab0.zip komennolla "unzip lab0". Siirrytään tiedostoon ja paljastetaan sisältö tutuilla komennoilla.  

<img width="663" height="417" alt="Näyttökuva 2026-08-27 153110" src="https://github.com/user-attachments/assets/6aed170c-82b6-4d8f-ae96-9fabd66a61dc" />  

Käännetään koodi komennolla "g++ buggy_program.c -g -Wall -Werror -o buggy_program-dbg". 
Tämän jälkeen siirrytään debuggeriin komennolla "gdb ./buggy_program-dgb".  

<img width="1874" height="564" alt="image" src="https://github.com/user-attachments/assets/f3d29c34-204c-4e7a-8e65-6962ab74f0bc" />  

Seuraavaksi olisi tarkoitus etsiä koodista virhe, joa korjata se parhaamme mukaan.  
Komento "list" paljastaa meille luettavaa koodia seuraavasti:  

<img width="1878" height="487" alt="image" src="https://github.com/user-attachments/assets/f1cb35a4-350b-4e0a-916e-3136fbf9d315" />.  

Koodia tarkastelemalla huomaamme virheen silmukassa verrattuna taulukon kokoon. Taulukossa on viisi numeroa (1-5), mutta taulukon ensimmäisen numeron yksi (1) arvo on nolla (0). Tällöin silmukan pyöritys alkaa "liian aikaisin", jos vertaamme sitä yhtäsuuresti taulukon kokoon alkaen nollasta. Tulostuksessa numero viisi (5) jää ulkopuolelle, ja printti laittaa kuudennen rivin, vaikka niitä kuuluisi olla vain halutut viisi.  

Muutetaan koodissa "i <= size", niin että poistetaan yhtäsuurikuin merkki. Lopullinen koodi näyttäisi tältä.  

<img width="931" height="480" alt="image" src="https://github.com/user-attachments/assets/17b78210-da85-4735-b828-a2fcf5c468a9" /> 
Lähdekoodin korjauksen jälkeen ihmettelin miksi muutosta ei tapahtunut, kunnes kysyin luottokaverilta (chatgpt) promptilla "Miksi ohjelmassani ei tapahtunut muutosta vaikka muutin koodia?" Kaveri tiesi kertoa että koodi täytyy kääntää uudestaan komennolla "g++ buggy_program.c -o testikaannos". 
Saimme uuden ajettavan tiedoston korjatulla lähdekoodilla, jonka nimi on nyt testikaannos. 


<img width="893" height="98" alt="image" src="https://github.com/user-attachments/assets/d1bb8d95-3c2a-48b6-9e20-d37fb5dfd006" />  

Tämän jälkeen voidaan koeajaa molemmat tiedostot vertailun vuoksi ja lopputuloksen näemme välittömästi edessämme.  

<img width="891" height="582" alt="image" src="https://github.com/user-attachments/assets/87d23dde-62ee-46c8-84d2-d59bfe9fb62b" />
