# Break & Unbreak

## x) Lue ja tiivistä

Tässä osiossa on tarkoitus tiivistää neljä artikkelia.

---

### 1. Broken Access Control

[OWASP Top 10 2025 — A01](https://top10.owasp.org/2025/A01_2025-Broken_Access_Control/)

Ensimmäisessä artikkelissa kerrotaan rikkinäisen pääsynhallinnan vaaroista,
joka pitää ensimmäistä sijaa OWASPIN top 10 uhkalistauksessa.
100% testatuista sovelluksista omisti jonkun asteen haavoittuvuuden pääsynhallinnassa.

Pääsynhallinnan tarkoitus olisi suojata arkaluontoista dataa niiltä silmäpareilta,
joille se ei kuulu.
Tässä epäonnistuessa dataa voidaan manipuloida, tuhota tai käyttää liiketoiminnallisesti väärin.

Yksi rikkeistä on esimerkiksi **"deny by default"** -periaatteen laiminlyönti,
jonka tarkoituksena olisi kieltää pääsy aluksi kaikilta jonka jälkeen lähdetään
antamaan oikeuksia vain niitä oikeasti tarvitseville.

Muita merkittäviä rikkeitä on:

- tunnistatumisen ohitus
- kirjautumisen ohitus
- metadatan manipulointi
- URLien arvailu joka voi johtaa liiallisiin oikeuksiin

Haavoittuvuuksia on ainakin periaatteen tasolla "helppo" tehostaa.

> Deny by defaultista vankasti kiinnipitäminen ja kirjautumisvirheiden logaus ja
> ilmoitus tapauskohtaisesti kuulostavat ainakin omaan korvaan todella
> kustannustehokkailta ratkaisuilta.

Artikkelissa on myös muutama käytännön esimerkki perinteisistä SQL injektoista.

---

### 2. Fuzz URLs, Find Hidden Directories

[Tero Karvinen, 2023](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/)

Toisessa artikkelissa avataan URL osotteiden fuzzausta **ffufin** avulla.

Ffuf on suomalaisten kehittämä opensource työkalu jolla voidaan fuzzata URLeista
haluttuja kohteita nopeasti ja tehokkaasti tarkoituksenaan löytää haavoittuvuuksia.
Esimerkiksi ffuffila voitaisiin kokeilla tuhansia ja jälleen tuhansia eri sanoja
URLin perään:

http://www.esimerkki.fi/*fuzzattavat_kohde*


Käymällä sanalistoja läpi voimme kokeilla urlin perään mitä tahansa, vaikkapa
`admin` joka voisi antaa meille todella heikkolaatuisella sivulla täydet
ylläpitäjän oikeudet.

Ffuf on työkaluna tehokas, koska se automatisoi tehtävän työn täysin.

Teron sivuilla on myös demonstraatio ja pieni haaste fuzzaamisesta,
mutta en aio dokumentoida niitä tähän.

---

### 3. Access Control Vulnerabilities

[PortSwigger Web Security Academy](https://portswigger.net/web-security/access-control)

Kolmannessa artikkelissa kerrotaan lisää pääsynhallinnasta ja sen manipuloinnista.

Ensimmäisenä uutena asiana verrattuna ensimmäiseen artikkeliin joka pisti silmään on,
että pääsynhallinnan konfigurointi on oikean ihmisen, ei tietokoneen tehävä.
Siksi virhemarginaali on korkeampi.

| Pääsynhallinnan tyyppi | Käyttöä rajataan |
| --- | --- |
| **Vertikaalinen** | käyttäjien/roolin perusteella |
| **Horisontaalinen** | resurssin/tuotteen perusteella |
| **Konteksiriippuvainen** | sovelluksen statuksen perusteella |

Konteksiriippuvaisella tarkoitetaan sitä, että esimerkiksi käyttäjä ei voi muokata ostoskoria enää sen jälkeen,
kun verkkokaupassa on ostotapahtuma jo suoritettu.

Artikkelissa pureudutaan hieman tarkemmin SQL injektio haavoittuvuuksiin,
ja kuinka paljon eri mahdollisuuksia sillä oikeasti on.

---

### 4. Raportin kirjoittaminen

[Tero Karvinen, 2006](https://terokarvinen.com/2006/raportin-kirjoittaminen-4/)

Neljännessä artikkelissa on Tero Karvisen ohjeet raportin kirjoittamiseen.
Näkökulmana tässä on painotettu IT-kursseihin liittyvien kokeilujen ja
työtehtävien raportointi, eikä esseemäinen "virallinen" raportointi.

Tarkoituksena on kirjoittaa raporttia ylös samalla kun tekee harjoituksia,
tai mitä tahansa muuta troubleshoottausta.
Tämä auttaa sinua itseäkin pysymään kartalla siitä mitä olet jo tehnyt
etkä joudu looppiin toistamaan samoja virheitä uudestaan ja uudestaan.

**Toistettavuus.**
Jos annat raporttisi toiselle henkilölle, tulisi kaikki vaiheet olla
toistettavissa ja lopputulos sama myös muilla.
Tärkeää on myös kuvata työympäristö ja käytetyt laitteet/työkalut.

**Yksityiskohtaisuus.**
Yksityiskohtainen raportointi on tärkeää.

- Mitä komentoja käytit ja missä järjestyksessä?
- Tuliko virheitä ja pääsitkö/miten pääsit yli?

**Luettavuus.**
On myös tärkeää tehdä raportoinnista lukukelpoista väliotsikoiden,
luettavan tekstin, kuvien ja kappaleiden avulla.
Lähteiden merkitseminen auttaa tekemään tekstistä uskottavampaa,
sillä se antaa kuvan että kirjoittava on oikeasti itse perehtynyt aiheeseen.

**Mokat.**
Mokiin Tero on listannut plagioinnin ja sepittämisen.
Sepittäminen on turhanpäiväistä, aikaa vievää ja usein myös todella
läpinäkyvästi kertovaa siitä, että et ole oikeasti itse tehnyt mitään.
Plagiointi mokana on mielestäni itsestäänselvyys.

> Koska artikkeli on vuodelta 2006, lisäisin mokiin ainakin tekoälyn generoimat
> tekstit, sillä ne ovat lukukelvotonta kuraa ja kielii laiskuudesta ja
> riman alituksesta.

---

## a+b) Break into 010-staff-only  

Tehtävän tarkoituksena on paljastaa tehtävämateriaalista salasana, joka sisältää stringin "SUPERADMIN". 
Tehtävää varten lataan materiaalin Teron sivuilta, ja alustana minulla on virtuaaliympäristössä toimiva Debian käyttöjärjestelmä. 
Tehtävän ohjeet löytyy Teron sivuilta jonka linkitän tähän lähteeksi, joten en aijo dokumentoida "tuplana" tehtävämateriaalien latausvaiheita. 

Tältä sivulta olisi tarkoitus löytää admin käyttäjän salasana käyttäen pelkkää web interfacea, ja sen jälkeen korjata haavoittuvuus lähdekoodissa.    

<img width="956" height="801" alt="Näyttökuva 2026-09-18 144511" src="https://github.com/user-attachments/assets/e30d2c06-2abd-4792-9367-7417a6e45c5a" />  

---  
Lähdin tehtävään kokeilemalla yksinkertaista heittomerkkiä (') PIN kenttään, jos se olisi rikkonut jotain. Kenttä antoi vain varoituksen "Please enter a number". Saman varoituksen sain, kun kokeilin syöttää erilaisia syntakseja tekstistä 123'OR 1=1'. 
Tämän jälkeen siirryin selaimen debuggeriin, jossa huomasin syöttökentän vaadittuna parametrina "numberin", kokeilin vaihtaa tämän tekstimuotoon. 

<img width="955" height="952" alt="Näyttökuva 2026-09-18 145824" src="https://github.com/user-attachments/assets/c81650be-813a-4586-9c1f-666aa1947eed" />  

---  

Tämä ei kuitenkaan vienyt meitä eteenpäin, joten siirrytään uuteen lähestymistapaan. 
Debuggerissa avasin network osion, josta löysin yhden POST pyynnön, klikkasin sitä oikealla ja valitsin "Edit and Resend". 
Tämän jälkeen vasemmassa alakulmassa on kenttä jossa lukee "pin=123", lisäsin sen perään heittomerkin "'", ja sendasin. Saimme network osioon uuden POST pyynnön. Uusi POST pyyntö 500 oli server error, mikä on oikeastaan hyvä merkki. Se tarkoittaa, että lisäämällä syöttökenttään heittomerkin saamme kaadettua serverin. Nyt oikeisiin töihin.  

Muokkasin uusiksi vasemassa alakulmassa nähtyä kenttää, ja muutin tekstiä seuraavasti "pin=123'OR 1=1--", tämä antoi meille uuden POST 200 pyynnön. Sen avattuamme voimmme surffata oikeassa reunassa sijaitsevaan Response ikkunaan jossa meitä odottaa uusi salasana "foo".  

<img width="1919" height="419" alt="kuva" src="https://github.com/user-attachments/assets/0c5418e0-4242-4922-8082-c85012aaa0df" />  

---  

Seuraavaksi tarkoituksenamme olisi korjata tämä haavoittuvuus lähdekoodista. Saatavillamme on opettajan antama python tiedosto, index.html sekä joitain css tiedostoja. Python skripti näyttää tällä hetkellä tältä, ja hakemisto on seuraavanlainen. Emme tee HTML tai css tiedostoilla mitään, joten siirrytään pythonin pariin.   

<img width="1034" height="886" alt="kuva" src="https://github.com/user-attachments/assets/fb10e0e1-99d0-4099-a767-2614a47cf0fc" />  

<img width="731" height="314" alt="kuva" src="https://github.com/user-attachments/assets/da314195-1e43-4286-a537-aaebe72497e6" />  

---  

Koska SQL syntaksi on minulle vielä täysin uutta enkä tajunnut mistä haavoittuvuus johtui, turvauduin korjaamaan koodin pätkää tekoälyn (clauden) avulla. Virhe sijaitsee tässä lohkossa: 
>sql = "SELECT password FROM pins WHERE pin='"+pin+"';"
        row = ""
        with app.app_context():
                res=db.session.execute(text(sql))
                db.session.commit()
                row = res.fetchone()<

Korjaus tapahtuu niin, että erotamme tuon ensimmäisen rivin kahteen eri koodiriviin, jolloin tietokanta saa erikseen kyselyn sekä syöttökentän arvon. Tällöin tietokanta ei mene rikki, vaan se osaa lukea arvon sellaisena kun se on, eikä antamaamme 'OR 1=1-- salasanaa löydy tietokannasta. Tässä korjattu koodi sekä testaus toimivuudesta.  

<img width="634" height="159" alt="kuva" src="https://github.com/user-attachments/assets/80188864-d9bb-4d15-b75c-4bb4983008be" />  

<img width="1918" height="880" alt="kuva" src="https://github.com/user-attachments/assets/e3a83e82-0551-4291-9f8d-991f1648887e" />  

---  

## c) Solve dirfuzt-1  

Tehtävän tarkoituksena on selvittää "dirfuzt-1" binääristä admin page sekä version control related page. 
Aloitin tehtävän lisäämällä dirfuztiin ajo-oikeudet komennolla "chmod +x dirfuzt-1". 
Ajettua dirfuztin saimme ip-osoitteen joka vei seuraavanlaiselle sivulle.  

<img width="606" height="263" alt="kuva" src="https://github.com/user-attachments/assets/9fb720fa-b051-455a-a38d-cc5b754c083d" />  

---  

Lisäämällä osoitteen perään /admin, emme saaneet mitään uutta irti. Kannatti kuitenkin yrittää. 
Lähdin kokeilemaan fuzzausta ffufilla ja common.txt sanalistan avulla. Käytin komentoa "ffuf -w ~/common.txt -u http://127.0.0.2:800/FUZZ. Komento kokeilee common.txt listan sanoja tässä osoitteen perään, jossa nyt lukee FUZZ. 
Tuloksia on todella paljon, seuraavaksi filtteröidään 154 kokoiset tulokset pois jos löytäisimmekin jotain poikkeavaa. Tämä tapahtuu lisäämällä komennon perään "-fs 154".  

<img width="960" height="625" alt="kuva" src="https://github.com/user-attachments/assets/d5d2f84f-716d-4b08-808d-bc7be24f310a" />  

<img width="929" height="631" alt="kuva" src="https://github.com/user-attachments/assets/57dbd855-cfae-4123-8e90-828f74fb304e" />  

---  

Nyt vain kokeilemaan löydettyjä ip päätteitä selaimeen. /.git/logs/ löysi "versionhallinta" sivun, ja /wp-admin vei "admin" sivulle.  

<img width="548" height="352" alt="kuva" src="https://github.com/user-attachments/assets/f2ceb028-6cb2-40ee-9adf-cb6af785f884" />  

<img width="493" height="308" alt="kuva" src="https://github.com/user-attachments/assets/3c7992e6-7dee-4644-bbe6-740f6a1dc421" />  

---  

## d & e) Break into & fix 020-your-eyes-only

Tehtävän tarkoituksena on murtautua Teron luomaan 020 harjoitukseen ja korjata haavoittuvuus. 
Tehtävää varten kansiossa on README.txt tiedosto joka sisältää ohjeet vaadittavien pakettien asennukseen, en aijo niitä sen tarkemmin dokumentoida tähän sillä en koe niiden osoittavan teknistä osaamistani. 
Saatuani paketit asennettua saimme tehtävän etusivun auki, sisällä ollaan.  

<img width="827" height="612" alt="kuva" src="https://github.com/user-attachments/assets/d7f201e9-dadb-4991-b646-d0fb5a71639f" />  

---  

Kun painamme "Show my personal data" nappia, saamme esiin kirjautumissivun joka vaatii käyttäjätunnusta ja salasanaa. Kumpaakaan meillä ei vielä ole. Samat kentät saamme painamalla "admin dashboard" nappia. Siirtymällä kirjautumissivuille, osoite muuttuu seuraavasti: 
Show my personal data = http://127.0.0.1:8000/accounts/login/?next=/my-data/
Admin dashboard = http://127.0.0.1:8000/accounts/login/?next=/admin-dashboard/
Login = http://127.0.0.1:8000/accounts/login/
Register = http://127.0.0.1:8000/accounts/register/. 

Luodaan ensiksi käyttäjätunnus register näppäimestä ja siirrytään my personal data välilehdelle.  

<img width="952" height="997" alt="kuva" src="https://github.com/user-attachments/assets/e4cc8754-db01-43fe-95f5-4154a267e4fc" />  

---  

Menemällä oman datan sivuilleni ja muokkaamalla osoitekenttää näin "http://127.0.0.1:8000/my-data/1/" saamme hieman erilaisen Page not found sivun joka saattaa paljastaa meille lisää vihjeitä.  

<img width="958" height="417" alt="kuva" src="https://github.com/user-attachments/assets/d6e5d617-95e0-475e-817c-bd270a5a4222" />  

---  

Muokkaamalla taas osoitekenttää niin, että loppuun tulee /admin-console/ pääsemme salattuun sivuun ilman minkäänlaista käyttäjän oikeuksian tarkastusta.  

<img width="658" height="393" alt="kuva" src="https://github.com/user-attachments/assets/d2f277ab-26a9-4e92-9d5b-986dd8d4401c" />  

---  

Seuraavaksi olisi tarkoitus korjata tämä pääsynhallinnan haavoittuvuus lähdekoodista. Koska djangon rakenne on minulle täysin tuntematon, luin Teron antamista vinkeistä että pääsynhallinnan oikeuksia jaetaan views.py tiedostossa joten avasin sen nanolla.  

<img width="939" height="596" alt="kuva" src="https://github.com/user-attachments/assets/6bd857df-fe98-4591-b843-b11fd36f3fbc" />  

---  

Kun vertaillaan kahta adminview kohtaa, huomataan että alemmasta puuttuu toinen käyttäjäntarkistus kokonaan. Lisätään "AdminShowAllView" classin returnin perään "and self.request.user.is_staff". Tallennettua muutokset toistin aikaisemmat vaiheet uudestaan, ja nyt lisättyäni osoitekenttään /admin-console/ saamme seuraavan näkymän.  

<img width="558" height="254" alt="kuva" src="https://github.com/user-attachments/assets/6f8b35ed-3e30-4092-a4cd-11277254d3b9" />  

Tehtävä suoritettu onnistuneesti! Tämän olisi varmasti voinut suorittaa myös eritavalla, sillä ratkaisussani en edes käyttänyt ffuffia vaikka Teron ohjeistuksen mukaaan siitä olisi ollut apua.  


--- 
## Lähteet
1. https://top10.owasp.org/2025/A01_2025-Broken_Access_Control/ (Luettu 18.9.2026), x) Lue ja tiivistä
2. https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/ (Luettu 18.9.2026), x) Lue ja tiivistä
3. https://portswigger.net/web-security/access-control (Luettu 18.9.2026), x) Lue ja tiivistä
4. https://terokarvinen.com/2006/raportin-kirjoittaminen-4/ (Luettu 18.9.2026), x) Lue ja tiivistä
5. https://terokarvinen.com/hack-n-fix/ (Luettu 18.9.2026), a+b) Break into 010-staff-only
6. Tekoälyä käytetty komentojen selventämiseen sekä x) osion siistimiseen/luettavuuden parantamiseen (Claude)
