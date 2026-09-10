# Tapo C200 kameran turvallisuus

---  

Tehtävän tarkoituksena on löytää root salasana TAPO C200 kameralle. 
Aloitin lataamalla kolme softaa/dumppia: 
1. tp-link-decrypt softa githubista
2. TapoV3 firmware binary
3. Tapo C200 v3 dump file  

<img width="567" height="868" alt="image" src="https://github.com/user-attachments/assets/3ba092aa-9669-44ab-8e12-790df1a243ae" />  

---  

<img width="842" height="226" alt="image" src="https://github.com/user-attachments/assets/bfd13c1e-26d9-4bc3-a22e-feea470c515a" />  

Tiedosto sisältää dataa, lähdetään purkamaan.
Hexdump ei paljasta meille varsinaisesti mitään.  

<img width="946" height="710" alt="image" src="https://github.com/user-attachments/assets/d05e5bbf-04e1-4a5a-9ca1-35d423f18b96" />  

Tekoälyn (ChatGPT) avustukella laskin tiedoston entropian. Jos laskelma on tasaisesti lähellä 1.0 akselia, on tiedosto kryptattu tai vahvasti pakattu.
Myöskään stringsit ei paljastanut mitään uutta.  

<img width="788" height="954" alt="image" src="https://github.com/user-attachments/assets/46eff93d-ece2-40a2-83be-a8a462bc15f2" />  

<img width="939" height="704" alt="image" src="https://github.com/user-attachments/assets/ca0a2cb5-848a-4972-9575-8733ef57546b" />  

Tarkastellaan tiedoston kokoa sekä headeria.  

<img width="922" height="498" alt="image" src="https://github.com/user-attachments/assets/88084660-e8a3-4858-a7d9-18dac6816b91" />  

Tässä vaiheessa chatGPT meni mankeliin, joten vaihdoin Geminiin. Gemini tiesi kertoa että kyseinen kamera on kryptattu RSA/AES mentelmällä.
Ajoin ensin komennon >./extract_keys.sh Tapo_C200v4_en_1.4.2.bin<. Tämän jälkeen vaadittu >make< komento ei vieläkään toiminut.  

<img width="956" height="504" alt="Näyttökuva 2026-09-10 153038" src="https://github.com/user-attachments/assets/ca6251b6-8873-44e1-91db-71b84c88381b" />  

Ongelmaan ei löytynyt ratkaisua koko ryhmässä, joten opettaja antoi valmiiksi käännetyn tiedoston jonka jälkeen pääsin purkamaan Tapon firmwaren.
Nyt voin lähteä etsimään root salasanaa. 
>binwalk -e Tapo_C200v4_en_1.4.2.bin.dec< komento loi meille uuden kansion josta löydämme kameran tiedostojärjestelmän.

<img width="924" height="716" alt="Näyttökuva 2026-09-10 163009" src="https://github.com/user-attachments/assets/e3411653-9b7f-422f-b43d-9c9726a37c16" />  


















