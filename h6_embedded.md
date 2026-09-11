# Tapo C200 kameran turvallisuus

---  

Tehtävän tarkoituksena on löytää root salasana TAPO C200 kameralle. 
Aloitin lataamalla kolme softaa/dumppia: 
1. tp-link-decrypt softa githubista
2. TapoV3 firmware binary
3. Tapo C200 v3 dump file  

<img width="567" height="868" alt="image" src="https://github.com/user-attachments/assets/3ba092aa-9669-44ab-8e12-790df1a243ae" />  

---  
Tiedosto sisältää dataa, lähdetään purkamaan.
Hexdump ei paljasta meille varsinaisesti mitään.  

<img width="842" height="226" alt="image" src="https://github.com/user-attachments/assets/bfd13c1e-26d9-4bc3-a22e-feea470c515a" />  

<img width="946" height="710" alt="image" src="https://github.com/user-attachments/assets/d05e5bbf-04e1-4a5a-9ca1-35d423f18b96" />  

---  


Tekoälyn (ChatGPT) avustukella laskin tiedoston entropian. Jos laskelma on tasaisesti lähellä 1.0 akselia, on tiedosto kryptattu tai vahvasti pakattu.
Myöskään stringsit ei paljastanut mitään uutta.  

<img width="788" height="954" alt="image" src="https://github.com/user-attachments/assets/46eff93d-ece2-40a2-83be-a8a462bc15f2" />  

<img width="939" height="704" alt="image" src="https://github.com/user-attachments/assets/ca0a2cb5-848a-4972-9575-8733ef57546b" />  

---  

Tarkastellaan tiedoston kokoa sekä headeria.  

<img width="922" height="498" alt="image" src="https://github.com/user-attachments/assets/88084660-e8a3-4858-a7d9-18dac6816b91" />  

---  

Tässä vaiheessa chatGPT meni mankeliin, joten vaihdoin Geminiin. Gemini tiesi kertoa että kyseinen kamera on kryptattu RSA/AES mentelmällä.
Ajoin ensin komennon >./extract_keys.sh Tapo_C200v4_en_1.4.2.bin<. Tämän jälkeen vaadittu >make< komento ei vieläkään toiminut.  

<img width="956" height="504" alt="Näyttökuva 2026-09-10 153038" src="https://github.com/user-attachments/assets/ca6251b6-8873-44e1-91db-71b84c88381b" />  

---  

Ongelmaan ei löytynyt ratkaisua koko ryhmässä, joten opettaja antoi valmiiksi käännetyn tiedoston jonka jälkeen pääsin purkamaan Tapon firmwaren.
Nyt voin lähteä etsimään root salasanaa. 
"binwalk -e Tapo_C200v4_en_1.4.2.bin.dec" komento loi meille uuden kansion josta löydämme kameran tiedostojärjestelmän.

<img width="924" height="716" alt="Näyttökuva 2026-09-10 163009" src="https://github.com/user-attachments/assets/e3411653-9b7f-422f-b43d-9c9726a37c16" />  

---  

Tarkoituksenamme olisi nyt extractata tästä ja dump tiedostoista rootfs osiot.
Siirryin puretussa kansiossa squashfs-root kansioon josta löytyy taas bin, config, etc, lib ja usr kansiot. 
Tarkastellaan mitä löytyykö tämän sisältä mitään ohjelmaa komennolla >find . -type f -executable | sort<.  

<img width="955" height="872" alt="Näyttökuva 2026-09-10 182145" src="https://github.com/user-attachments/assets/457edc4a-207e-4cc7-bec2-fb62e6020038" />  

---  

Täältä löysimme >root/bin/main<, joka on ohjelman "pääydin". Kiinnostavaa on myös kirjasto >lib/libcrypt-0.0.33.2.0.so< jossa on crypt() funktio salasanojen hashaukseen.
Jatketaan tutkimalla mainia. Tämän tein komennolla >grep -iE "passwd|shadow|root:|admin|crypt|/etc/|default*pass" /tmp/main_strings.txt<. 
Tällä löysimme mielenkiintoisen kohdan, joka generoi salasanan.  

<img width="825" height="276" alt="Näyttökuva 2026-09-11 115637" src="https://github.com/user-attachments/assets/188f62d8-94f5-4d46-b6d6-bc0e74212df5" />  

---  

Seuraavaksi avasin /mainin ghidralla analysoitavaksi, ja ikkuna on jokseenkin sekavan näköinen näin alkuun. 
Pienen (ison) vääntämisen jälkeen ghidrassa clauden avustuksella löysimme compileriin funktion joka liittyy salasanan tarkistukseen. Myönnettäköön että tässä vaiheessa meinasi päästä itku.  


<img width="959" height="965" alt="Näyttökuva 2026-09-11 121133" src="https://github.com/user-attachments/assets/22377495-ca04-471e-a627-fee29dc90408" />  

<img width="1674" height="950" alt="image" src="https://github.com/user-attachments/assets/6b6a53f7-7528-4a97-b3c5-34ebc8815593" />  

---  

Tässä vaiheessa tekoäly (claude) tiesi kertoa että firmware dumpissa ei varsinaisesti ole mitään kiinnostavaa tällä hetkellä, vaan olisi viisaampaa siirtyä purkamaan opettajan toimittamaa dumppi fileä. 
Aloitetaan ajamalla binwalk toiselle dumpille.  

<img width="1909" height="636" alt="image" src="https://github.com/user-attachments/assets/236cf89a-9108-4922-b4a0-e73121e8e929" />  

---  


Löysimme binwalkilla kohdan "4456448   0x440000   Squashfs filesystem, little endian, version 4.0, compression:xz, size: 3032084 bytes, 96 inodes", jota lähdemme nyt purkamaan. 
Täten päädyimme toisen dumppi filun squashfs-root hakemistoon.  

<img width="940" height="235" alt="image" src="https://github.com/user-attachments/assets/2ce0f976-667b-4ef2-b851-2c92fd831685" />  

---  

Toistin samoja vaiheita kuin aikaisemmassa dumpissa, ja claude tuli siihen tulokseen että salasanaa ei voi kummastkaan dumpista löytää. Veikkaan virheen johtuvan eri firmware versioista. Jokseenkin hieman kyllä silti epäilyttää, sillä opettaja näytti löydetyn salasanan. 
En kuitenkaan suostunut tähän lopputulokseen ja jatkoin etsintää ghidralla. Etsin aikaisemmasta dumpista nyt >factory_passwd< kohtaa.  

<img width="718" height="815" alt="image" src="https://github.com/user-attachments/assets/8348e195-73ac-4efc-8a3c-a16a50528415" />  

---  

Löysimme ghidralla funktion joka sisältää >digest_password< sisennyksen. Decompilerissa löysimme koodista rivit 42-44, jotka autentikoi salasanan ja palauttaa nollaa jos salasana on virheellinen.  

<img width="721" height="792" alt="image" src="https://github.com/user-attachments/assets/d5dad423-7ccd-4cdb-95b2-826a563cc306" />  

<img width="567" height="121" alt="image" src="https://github.com/user-attachments/assets/c7f4fa4d-a4cb-4d33-be4f-b9ac62805cd3" />  

---  

# Yhteenveto  

Tässä vaiheessa tekoälykin "luovutti" ja kehotti kirjoittamaan tämän raportiksi. Emme löytäneet salasanaa, ja claude oli sitä mieltä että sitä ei edes näillä kahdella dumpilla voi löytää. 
Clauden mielestä salasanaa EI ole kovakoodattu firmwareen eikä sitä löydy kummastakaan annetusta dumpista. Looginen polku salasanaan löytyy, mutta salasanaa ei sinne ole tallennettu.
Löysimme kuitenkin selkeän haavoittuvuuden salasanan autentikoinissa, jos laite on tehdastilassa, se ei kysy salasanaa ollenkaan jolloin meillä olisi täysi pääsy laitteelle.  

---  
# Lähteet

1. Opettajan moodle materiaalit
2. https://quentinkaiser.be/security/2025/07/25/rooting-tapo-c200/
3. Käytetyt tekoälyt: chatGPT, Gemini, Claude



