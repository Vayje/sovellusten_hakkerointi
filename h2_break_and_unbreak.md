# Break & Unbreak

## x) Lue ja tiivistä  

---  

Tässä osiossa on tarkoitus tiivistää seuraavat artikkelit:
1. https://top10.owasp.org/2025/A01_2025-Broken_Access_Control/
2. https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/
3. https://portswigger.net/web-security/access-control
4. https://terokarvinen.com/2006/raportin-kirjoittaminen-4/

Ensimmäisessä artikkelissa kerrotaan rikkinäisen pääsynhallinnan vaaroista, joka on pitää ensimmäistä sijaa OWASPIN top 10 uhkalistauksessa. 100% testatuista sovelluksista omisti jonkun asteen haavoittuvuuden pääsynhallinnassa. 
Pääsynhallinnan tarkoitus olisi suojata arkaluontoista dataa niiltä silmäpareilta, joille se ei kuulu. Tässä epäonnistuessa dataa voidaan manipuloida, tuhota tai käyttää liiketoiminnallisesti väärin. 
Yksi rikkeistä on esimerkiksi "deny by default" -periaatteen laiminlyönti, jonka tarkoituksena olisi kieltää pääsy aluksi kaikilta jonka jälkeen lähdetään antamaan oikeuksia vain niitä oikeasti tarvitseville. 
Muita merkittäviä rikkeitä on tunnistatumisen ohitus, kirjautumisen ohitus, metadatan manipulointi ja URLien arvailu joka voi johtaa liiallisiin oikeuksiin. 
Haavoittuvuuksia on ainakin periaatteen tasolla "helppo" tehostaa. Deny by defaultista vankasti kiinnipitäminen ja kirjautumisvirheiden logaus ja ilmoitus tapauskohtaisesti kuulostavat ainakin omaan korvaan todella kustannustehokkailta ratkaisuilta. 
Artikkelissa on myös muutama käytännön esimerkki perinteisistä SQL injektoista.  

Toisessa artikkelissa avataan URL osotteiden fuzzausta ffufin avulla. SQL injektio metodi tämäkin. 
Ffuf on suomalaisten kehittämä opensource työkalu jolla voidaan fuzzata URLeista haluttuja kohteita nopeasti ja tehokkaasti tarkoituksenaan löytää haavoittuvuuksia. 
Esimerkiksi ffuffila voitaisiin kokeilla tuhansia ja jälleen tuhansia eri sanoja URLin perään, http://www.esimerkki.fi/*fuzzattavat_kohde*. 
Käymällä sanalistoja läpi voimme kokeilla urlin perään mitä tahansa, vaikkapa "admin" joka voisi antaa meille todella heikkolaatuisella sivulla täydet ylläpitäjän oikeudet. 
Ffuf on työkaluna tehokas, koska se automatisoi tehtävän työn täysin. 
Teron sivuilla on myös demonstraatio ja pieni haaste fuzzaamisesta, mutta en aijo dokumentoida niitä tähän.  

Kolmannessa artikkelissa kerrotaan lisää pääsynhallinnasta ja sen manipuloinnista. 
Ensimmäisenä uutena asiana verrattuna ensimmäiseen artikkeliin joka pisti silmään on, että pääsynhallinnan konfigurointi on oikean ihmisen, ei tietokoneen tehävä. Siksi virhemarginaali on korkeampi. 
Vertikaalisessa pääsynhallinnassa käyttöä rajataan käyttäjien/roolin perusteella, kun taas horisontaalisessa pääsynhallinnassa käyttöä rajataan resurssin/tuotteen perusteella. 
Konteksiriippuvaisessa pääsynhallinnassa rajataan käyttöä sovelluksen statuksen perusteella. Esimerkiksi käyttäjä ei voi muokata ostoskoria enää sen jälkeen, kun verkkokaupassa on ostotapahtuma jo suoritettu. 
Artikkelissa pureudutaan hieman tarkemmin SQL injektio haavoittuvuuksiin, ja kuinka paljon eri mahdollisuuksia sillä oikeasti on. 

Neljännessä artikkelissa on Tero Karvisen ohjeet raportin kirjoittamiseen. Näkökulmana tässä on painotettu IT-kursseihin liittyvien kokeilujen ja työtehtävien raportointi, eikä esseemäinen "virallinen" raportointi. 
Tarkoituksena on kirjoittaa raporttia ylös samalla kun tekee harjoituksia, tai mitä tahansa muuta troubleshoottausta. Tämä auttaa sinua itseäkin pysymään kartalla siitä mitä olet jo tehnyt etkä joudu looppiin toistamaan samoja virheitä uudestaan ja uudestaan. 
Raportissa painotetaan myös toistettavuutta. Jos annat raporttisi toiselle henkilölle, tulisi kaikki vaiheet olla toistettavissa ja lopputulos sama myös muilla. Tärkeää on myös kuvata työympäristö ja käytetyt laitteet/työkalut. 
Yksityiskohtainen raportointi on tärkeää. Mitä komentoja käytit ja missä järjestyksessä? Tuliko virheitä ja pääsitkö/miten pääsit yli? 
On myös tärkeää tehdä raportoinnista lukukelpoista väliotsikoiden, luettavan tekstin, kuvien ja kappaleiden avulla. 
Lähteiden merkitseminen auttaa tekemään tekstistä uskottavampaa, sillä se antaa kuvan että kirjoittava on oikeasti itse perehtynyt aiheeseen. 
Mokiin Tero on listannut plagioinnin ja sepittämisen. Sepittäminen on turhanpäiväistä, aikaa vievää ja usein myös todella läpinäkyvästi kertovaa siitä, että et ole oikeasti itse tehnyt mitään. Plagiointi mokana on mielestäni itsestäänselvyys. 
Koska artikkeli on vuodelta 2006, lisäisin mokiin ainakin tekoälyn generoimat tekstit, sillä ne ovat lukukelvotonta kuraa ja kielii laiskuudesta ja riman alituksesta.  

---  

## a) Break into 010-staff-only  





--- 
## Lähteet
1. https://top10.owasp.org/2025/A01_2025-Broken_Access_Control/ (Luettu 18.9.2026), x) Lue ja tiivistä
2. https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/ (Luettu 18.9.2026), x) Lue ja tiivistä
3. https://portswigger.net/web-security/access-control (Luettu 18.9.2026), x) Lue ja tiivistä
4. https://terokarvinen.com/2006/raportin-kirjoittaminen-4/ (Luettu 18.9.2026), x) Lue ja tiivistä
5. https://terokarvinen.com/hack-n-fix/ (Luettu 18.9.2026), a) Break into 010-staff-only
