# H5 Binääri tässä, missä koodit?  

## Lab 0  

Aloitetaan purkamalla lab0.zip komennolla "unzip lab0". Siirrytään tiedostoon ja paljastetaan sisältö tutuilla komennoilla.  

---  

<img width="663" height="417" alt="Näyttökuva 2026-08-27 153110" src="https://github.com/user-attachments/assets/6aed170c-82b6-4d8f-ae96-9fabd66a61dc" />  

---  

Käännetään koodi komennolla "g++ buggy_program.c -g -Wall -Werror -o buggy_program-dbg". 
Tämän jälkeen siirrytään debuggeriin komennolla "gdb ./buggy_program-dgb".  

--- 

<img width="1874" height="564" alt="image" src="https://github.com/user-attachments/assets/f3d29c34-204c-4e7a-8e65-6962ab74f0bc" />  

---  

Seuraavaksi olisi tarkoitus etsiä koodista virhe, joa korjata se parhaamme mukaan.  
Komento "list" paljastaa meille luettavaa koodia seuraavasti:  

---  

<img width="1878" height="487" alt="image" src="https://github.com/user-attachments/assets/f1cb35a4-350b-4e0a-916e-3136fbf9d315" />  

---  

Koodia tarkastelemalla huomaamme virheen silmukassa verrattuna taulukon kokoon. Taulukossa on viisi numeroa (1-5), mutta taulukon ensimmäisen numeron yksi (1) arvo on nolla (0). Tällöin silmukan pyöritys alkaa "liian aikaisin", jos vertaamme sitä yhtäsuuresti taulukon kokoon alkaen nollasta. Tulostuksessa numero viisi (5) jää ulkopuolelle, ja printti laittaa kuudennen rivin, vaikka niitä kuuluisi olla vain halutut viisi.  

Muutetaan koodissa "i <= size", niin että poistetaan yhtäsuurikuin merkki. Lopullinen koodi näyttäisi tältä.  

---  

<img width="931" height="480" alt="image" src="https://github.com/user-attachments/assets/17b78210-da85-4735-b828-a2fcf5c468a9" />  

---  


Lähdekoodin korjauksen jälkeen ihmettelin miksi muutosta ei tapahtunut, kunnes kysyin luottokaverilta (chatgpt) promptilla "Miksi ohjelmassani ei tapahtunut muutosta vaikka muutin koodia?" Kaveri tiesi kertoa että koodi täytyy kääntää uudestaan komennolla "g++ buggy_program.c -o testikaannos". 
Saimme uuden ajettavan tiedoston korjatulla lähdekoodilla, jonka nimi on nyt testikaannos.  

---  

<img width="893" height="98" alt="image" src="https://github.com/user-attachments/assets/d1bb8d95-3c2a-48b6-9e20-d37fb5dfd006" />  

---  

Tämän jälkeen voidaan koeajaa molemmat tiedostot vertailun vuoksi ja lopputuloksen näemme välittömästi edessämme.  

---  

<img width="891" height="582" alt="image" src="https://github.com/user-attachments/assets/87d23dde-62ee-46c8-84d2-d59bfe9fb62b" />  

## Lab 1

Tehtävän tarkoituksena on selvittää miksi ohjelma kaatuu ja onko se korjattavissa. Ajamalla ohjelman saamme seuraavan virheilmoituksen.  

---  

<img width="577" height="208" alt="image" src="https://github.com/user-attachments/assets/25d562d7-bcc6-453a-810b-44206f460ee1" />  

---  

Käännetään koodi samalla komennnolla kuin aikaisemmin, ainoana erona että vaihdetaan komennon alusta "g++ -> gcc", koska koodissa on C kieltä, jotai c++ kääntäjä ei tue. Tässä virhekoodi g++ kääntämisestä, sekä lopullinen oikea käännös.  

---  

<img width="946" height="475" alt="image" src="https://github.com/user-attachments/assets/78d9c594-e3de-47a0-b664-e5bd1580e450" />  

---  

Käyttämällä debuggerissa "continue" huomaamme että virhe tulee tässä vaiheessa koodia.  

---  

<img width="867" height="242" alt="image" src="https://github.com/user-attachments/assets/ce8c08d3-42fe-4bf5-88ba-c5c627796433" />  

---  

Printtaamalla messagea debuggerin sisällä saamme seuraavan lausekkeen. Lähdekoodia tarkastellessa huomataan että tämä varmaan tarkoittaa printissä kohtaa "NULL", eikä saada haluttua "Hello World".  

---  

<img width="285" height="108" alt="image" src="https://github.com/user-attachments/assets/9c29e691-4b49-49d4-96a8-b37a343d0baa" />  

---  

Itse en ole kauhean etevä C kielissä, enkä kauhean fiksu edes pythonilla, mutta virhe mielestäni johtuu hassun näköisestä messagen kutsumisen rakenteesta, tai i = 3 kohdasta. Koodi olisi varmasti korjattavissa, jos C kieltä osaisin.  

---  

## Lab 2  

---  

Tehtävässä on tarkoituksena löytää salasana, joka vaaditaan ohjelman ajamiseen.  

---  

<img width="602" height="375" alt="image" src="https://github.com/user-attachments/assets/a53b08c9-f224-4730-86af-d3d9d2141572" />  

---  

Avasin debuggerilla "passtr", jossai list komennolla näimme password kohdan, ajamalla ohjelmaa pääsimme salasanan syöttämisen vaiheeseen, ja annoin salasanaksi "sala-hakkeri-321", jonka ohjelma sanoi olevan oikea ja saimme tulostuksen. En tiedä oliko ohjelman tarkoitus olla näin helppo, vai ymmmärsinkö jotain väärin.  

---  

<img width="947" height="843" alt="image" src="https://github.com/user-attachments/assets/18942666-897b-48e0-b667-d7d907d0e832" />  

---  

Ehkä ohjelma kuitenkin oli tarkoituksella noin helppo, sillä "passtr2o" sisältä ei löytynyt mitään ja salasanakin oli eri.  

---  

<img width="915" height="496" alt="image" src="https://github.com/user-attachments/assets/ad9e5842-9e2d-4e89-bfc8-427517c5781c" />  

---  

Koska debuggerissa listaus ei anna mitään, ajattelin lähteä työstämään tätä main funktion kohdalla laittamalla siihen pysäytyspisteen. Tunnilla käytettiin myös debuggerissa komentoa "disassemble" joten hyödynsin sitä tässä vaiheessa. Tämä ei kerro itselleni vielä mitään.  

---  

<img width="908" height="803" alt="image" src="https://github.com/user-attachments/assets/6a55fdd4-af7c-45a2-8008-e37b7b053dd6" />  

---  

Tässä vaiheessa sormi oli jo suussa, joten päädyin kysymään tekoälyltä (Gemini, promptilla "Tässä debuggerin sisällä disassembloitu main funktio, ja tarvitsen salasanan, mistä voisin alkaa etsimään").  
Tekoäly pyysi kiinnittämään huomiota funktioon "mAsdf3a" joka löytyy mainista hieman alempaa "call" rivillä +123. joten päädyin disassembloimaan sen komennolla "disassemble mAsdf3a".  

---  

<img width="832" height="859" alt="Näyttökuva 2026-08-28 185550" src="https://github.com/user-attachments/assets/e10822fa-baea-4391-9edc-c2982e85ded8" />  

---  

Tekoäly bongasi hajotuksesta kohdat "rdi" ja "rsi", joihin merkkijonoja tallennetaan. Syöttämällä salasanan pyyntökohdassa tekaistun "testi123" salasanan, tallentuu se jompaan kumpaan noista. Komennolla "x/s $rdi" ja vastaava rsi:lle, saamme printtinä kaksi merkkijonoa joista toinen on antamamme salasana ja toinen on tehtävän oikea salasana, ainakin melkein.  

---  

<img width="370" height="182" alt="image" src="https://github.com/user-attachments/assets/fbc2cb51-923a-4b43-88e2-a49638ebad73" />  
<img width="606" height="169" alt="image" src="https://github.com/user-attachments/assets/3c92b8c0-7474-4688-9c4d-ce4c001c7beb" />  

---  

Edelleen olen täysin hukassa tämän tulkitsemisen kanssa, enkä tajunnut muutakuin kaksi kutsuvaa funktiota riveilä +10 sekä +21. Näiden tulkitsemiseen käytin tekoälyä, joka sanoi että funktiolle annetaan kaksi merkkijonoa jota vertaillaan. Tämän jälkeen tulee rivit +34 sekä +37 joissa on cmp ja jne, jotka antavat epäonnistumisen jos merkkijonojen pituudet eivät ole samat. 

Sen jälkeen siirrytään riveille +45 sekä +50, joissa on "movsbl". Nämä hakevat merkit merkkijonoista. Tekoäly tiesi myös kertoa, että koodissa on merkkijonoa käsittelevä kohta "rax", joka lisää merkin arvoa +3, jos se on parillinen, ja laskee merkin arvoa -7, jos se on pariton.  Tämän jälkeen alunperin löytämämme "oikea" salasana muunnetaan ja salasanaksi tulee "dgOMm-x1".  

---  

<img width="879" height="344" alt="image" src="https://github.com/user-attachments/assets/f1ca4571-2624-4055-928f-a72193493435" />  

---  

Debuggerista opin hieman lisää disassemblen jälkeisestä tulkinnasta ilman lähdekoodia. Tätä auttoi hieman tunnilla näytetty disassemblen purku, mutta tehtävä vaati huomattavasti syvempää analyysia. En ole varma, olisiko syvempi tietämys C kielestä ollut eduksi tässä, mutta ilman tekoälyä en olisi tästä tehtävästä selvinnyt mitenkään päin. Tehtävä tuntui huomattavasti haastavemmalta aikaisempiin verrattuna, ja hyppy viimetehtävästä oli mielestäni liian suuri. Ei se mitään, haasteet on kivoja vaikka hieman turhautti. Aijon ehdottomasti tulevaisuudssa palata tähän raporttiin katsomaan miten hajotettua koodia pystyy tulkitsemaan.  

---  

## Lab 3  

---  

Tehtävän tarkoituksena on selvittää salasana Nora Crackme haasteissa. Valitsin itselleni crackme01.64 haasteen.  
Tiedostoa ajaessa saamme seuraavan varoituksen.  

---  

<img width="905" height="391" alt="image" src="https://github.com/user-attachments/assets/9f1f18d9-a503-4bfd-b4a2-758d8693cde5" />  

---  

Lähdekoodi näyttää tältä.  

---  

<img width="922" height="756" alt="image" src="https://github.com/user-attachments/assets/561c09b1-46a1-44f0-939e-9cc56fa250db" />  

---  

En ole varma oliko tarkoituksella näin helppo, mutta salasanahan lukee suoraa lähdekoodissa.  

---  

<img width="792" height="202" alt="image" src="https://github.com/user-attachments/assets/b9325343-2096-4b3e-8f16-9d8f235a12e6" />  

---  

Aijon ehdottomasti tulevaisudeessa ratkoa lisää Nora Crackme haasteita, mutta jätän ne kuitenkin tästä dokumentoinnista pois pituuden takia. 
Pahoittelen jos raportti on aika-ajoin hieman epäselvää luettavaa, otetaan vinkkejä vastaan siistin markdownin kirjoittamiseen, kiitos!!  

---  

## Lähteet

1. terokarvinen.com
2. Chatgpt
3. Gemini
