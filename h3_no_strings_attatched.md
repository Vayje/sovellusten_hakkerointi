# No Strings Attached

## a) Strings

Tehtävässä on tarkoituksena ladata Tero Karvisen tarjoama "ezbin" haaste ja selvittää sen sisällä olevan "passtr" filun salasana stringeistä katsomatta lähdekoodia.  

<img width="606" height="145" alt="kuva" src="https://github.com/user-attachments/assets/4f5a529f-6761-40b4-8bc5-57dbf0a6f66b" />  

---  

Strings komento paljasti liudan kaikennäköistä, ja siellä on selkeästi jotain silmäänpistävää.  

<img width="718" height="433" alt="kuva" src="https://github.com/user-attachments/assets/b7e4e539-c349-4213-a13f-4ff26428a692" />  

---  

Ja näin on salasana sekä lippu löydetty!  

<img width="710" height="124" alt="kuva" src="https://github.com/user-attachments/assets/fcc15c98-c80d-403e-9729-f7d6af23217a" />  

---  

## b) Modify passtr  

Seuraavaksi on tarkoitus muokata tai luoda uusi versio passtr.c ohjelmasta jossa salasana ei ole niin näkyvissä binäärissä. 
Päätin käyttää salasanan obfuskoinnissa metodina opettajan vinkkaamaa caesar salausta, jossa jokaista salasanan merkin arvoa kasvatetaan yhdellä. 
Tällöin stringsin pitäisi näyttää salasanan kohdalla "sotkua". Ajaessa salasanan arvoja pudotetaan yhdellä, ja vertailtava salasana on taas sala-hakkeri-321. 
Koska C kieli on itselleni täysin vieras, pyysin tässä kohtaa apua tekoälyltä (Claude).  

Loin "uusipsstr.c" tiedoston johon loin uuden koodinpätkän. Toiminnaltaan tämä koodi on samanlainen kuin Teron luoma, ja salasanakin on sama. 
Tässä salasana on vain hieman paremmin piilotettu. 

<img width="606" height="470" alt="kuva" src="https://github.com/user-attachments/assets/c56fbc0d-1c90-4b3b-89a1-90ba821c5105" />  

---   

Käydään koodin toiminta pala palalta läpi. 
- Aluksi lisätään stdio.h sekä string.h jotka sisältävät printf, scanf, strcmp ja strlen funktiot
- Luodaan main funktio ja varataan siinä 20 tavun muistialue käyttäjän syöttämälle salasanalle
- char enc_pw[] rivi sisältää "sala-hakkeri-321" salasanan jossa kaikkien merkkien arvoa on nostettu yhdellä
- real_pw[20] riville puretaan oikea salasana ajon aikana
- int len = strlen(enc_pw) laskee koodatun salasanan pituuden jotta se tietää monta merkkiä täytyy purkaa
- for silmukka koodissa ottaa jokaisen merkin koodatusta salasanasta ja tiputtaa arvoa yhdellä. Tämän jälkeen merkki merkin jälkeen ne tallennetaan real_pw taulukkoon.
- '\0' kertoo että merkkijono on päättynyt. Tämä on lisättävä koska rakensimme merkkijonon itse silmukassa.
- printf kysyy käyttäjältä salasanaa, ja scanf tarkistaa ettei siinä ole enemmän kuin 19 merkkiä (+'0' NULL terminaattori)
- if vertailee käyttäjän syöttämää salasanaa ja koodattua salasanaa keskenään. Jos ne ovat identtiset, koodi palauttaa 0 ja ajo suoritetaan onnistuneesti.

Seuraavaksi käänsin lähdekoodin ajettavaan muotoon komennolla "gcc uusipasstr.c". 
Ajaessa ohjelma kysyy salasanaa. Siihen syötetään "sala-hakkeri-321" niinkuin aiemminkin, ja saadaan onnistunut tulos.
"Strings uusipasstgr.c" komennolla voidaan tarkastella miltä salasana nyt näyttää edes hieman paremmin suojattuna. 
Salasana on pilkottu kahtia stringsissä, koska salasanassa muutettu "-" ei ole enää tulostuskelpoinen. Syytä tähän en tiedä.  

<img width="629" height="168" alt="kuva" src="https://github.com/user-attachments/assets/8fcfffca-20ad-42c1-ac64-3fadae15fd7c" />  

<img width="695" height="459" alt="kuva" src="https://github.com/user-attachments/assets/0bb6a98d-00a8-4543-8680-6300812f3455" />  

---  

## c) Packd

Tehtävän tarkoituksena on selvittää "packd" tiedoston salasana ja paljastaa flagi. 
Kokeillaan ensiksi aikaisempaa "sala-hakkeri-321" salasanaa for funsies, mutta myös siksi että näemme millaisen virheilmoituksen saamme (ehkä)väärästä salasanasta.  

<img width="671" height="165" alt="kuva" src="https://github.com/user-attachments/assets/1ff19dc8-9a5e-4af5-8ace-4429b146c9df" />  

---  

Stringseillä paljastui seuraava "salasana", joka se ei kuitenkaan ollut kokeiltuani sitä.  

<img width="798" height="707" alt="kuva" src="https://github.com/user-attachments/assets/88387336-6990-4681-a0bc-04289c14c799" />  

---  

Hieman alempana kuitenkin lukee "This file is packed with the UPX executable packer". Tämä herätti mielenkiintoni joten lähdin tutkimaan sitä tarkemmin. 
Nopealla googlauksella selvisi, että UPX on avoimen lähdekoodin paketti, joka kompressoi tiedostoja jopa 50-70% pienemmäksi. 
Kokeilin kääntää tiedoston takaisin originaaliin muotoon komennolla "upx -d packd.exe". (Ensin oli asennettava paketti itselleni komennolla "sudo apt install upx-ucl".  

<img width="791" height="213" alt="kuva" src="https://github.com/user-attachments/assets/899a73bc-ba1d-4408-84a0-84323ebdc224" />  

---  

Tässä nähdäänkin kuinka tiedoston koko muuttuu huomattavasti suuremmaksi. Seuraavaksi kokeilin strings komentoa uudestaan. 
Sieltä paljastui aikaisemmin löytämämme "salasana" mutta hieman pidempänä. Nyt siinä lukee "piilos-AnAnAs". 
Se osoittautui oikeaksi salasanaksi.  

<img width="709" height="106" alt="kuva" src="https://github.com/user-attachments/assets/2eec6d60-6014-44a7-9bf3-4ba5d851a377" />  

---  

## Yhteenveto
A tehtävä oli ainakin itselleni yksinkertainen ja helppo. Voisi ehkä ajatella sen olevan eräänlainen johdanto strings komentoon ja tuleviin tehtäviin. 
Täsä ei jäänyt sen enempää analysoitavaa.  

B tehtävä olikin jo hieman haastavampi c kielen taidon puutteista johtuen. Mielenkiintoinen tehtävä johon oli useampi eri tyyli toteuttaa. 
Näin sitä onneksi oppii, ja tästäkin jäi taas jotain uutta käteen, lähinnä c kielen syntaksia ja caesar metodi. 
Tekoäly antoi myös muita vaihtoehtoja salasanan obfuskointiin, mutta jostain syystä valitsemani metodi oli mielenkiintoisimman kuulonen. Liekkö johtuu nimestä.  

C tehtävä oli mielestäni hauskin, ja siinä tuli eniten onnistumisen tunnetta. Tuntui hyvältä huomata heti jotain poikkeavaa strings komennon tulosteesta, 
jota pääsi heti googlaamaan ja etsimään miten kääntää tiedosto takaisin. Tämä tuntui itseasiassa todella helpolta, ehkä liian helpolta, 
joten päädyin kysymään tekoälyltä (Claude) mitä muita lähestymistapoja tähän olisi ollut jos upx -d takaisinkäännös ei olisikaan toiminut. 
Claude tiesi vinkata debuggeria ja ghidraa, joten päädyin vielä tarkastamaan olisiko debuggerilla löytynyt salasana myöskin. 
Purkamalla main funktiota löysin kutsun jota tutkimalla saimme salasanan.  

<img width="814" height="649" alt="kuva" src="https://github.com/user-attachments/assets/c9882d8a-9221-4bd1-8477-533a80d39815" />  


## Lähteet
1. https://upx.github.io/
2. https://www.reverseengineering.app/en/techniques/upx-packing
3. Tekoälyä (Claude) käytetty apuna c kielen koodin kirjoituksessa
