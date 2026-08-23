# H1 High Standards  

## Sisällysluettelo  
1. Johdanto
2. Infrastruktuuri
3. Poisrajaukset, riskien kartoitus & hyväksyntä
4. Keskeiset rajapinnat
5. Topologia
6. Sidosryhmät
7. Lähteet

## Johdanto  

Tehtävänantona on kuvata oma työympäristö mahdollisimman tarkasti, jopa niin että se olisi auditoitavissa.  
Tässä raportissa avaan työympäristöäni enemmän esseemäisesti kuvaten mahdollisimman tarkasti käyttämiäni resursseja.  
Oma työympäristöni tässä vaiheeessa on oma kotiosoitteeni ja siihen sisältyvät (ja poisluettavat) laitteet, joita avaan syvemmin raportin edetessä.  
Pääasiassa raportissa käytän lähteenä löyhästi ISO27001 standardia vuodelta 2023. Löyhällä tarkoitan sitä, että en aijo sanasta sanaan kopioida koko auditointipohjaa, vaan enemmänkin käytän sitä apuna oman raporttini rakenteen laatimiseen.  
ISO27001 standardin tukena raportissa toimii Lari Iso-Mattilan luomat ohjeet tehtävästä (terokarvinen.com/application-hacking, h1 High Standards), 
joita yritän parhaani mukaan tuoda mukaan raporttiini ja soveltaa omaa tietämystäni laitteistostani sen kanssa.  

## Infrastruktuuri  

Punavuoressa sijaitsevaan työympäristööni kuuluu useita laitteita (joitain poissuljettavia) ja kaksi verkkoyhteyttä jotka toimii langallisena ja langattomana.  
Päälaitteena toimii kannettava tietokoneeni (Lenovo Ideapad 1), jolla teen kaiken opiskeluuni liittyvän ja joka myöskin kantautuu aina mukaan Pasilassa sijaitsevaan kampukseen.  
Kannettavani on yhdistettynä langattomasti omaan kotiverkkooni reitittimeni kautta. Reititin on taas yhdistettynä DNA:n tarjoamaan verkkoon.  
Reitittimen asetuksia ei ole sen enempää säädettynä, muutakun salasana langattomaan verkkoon vaihdettu, sekä reitittimen kirjautumistunnukset vaihdettu turvallisuussyistä. Reitittimen palomuuri on siis tehdasasetuksilla.  
Toinen koulutarpeisiini  liittyvä laite on mukana kulkeutuva puhelin (Nothing Phone 2a), jolla suoritan kaikki kaksivaiheiset kirjautumiset biometrisellä tunnistautumisella sekä vahvistuskoodeilla. 
Puhelin on yhteydessä MOI:n tarjoamaaan verkkoon.  

Kannettavassani on pohjalla Windows käyttöjärjestelmä, mutta pääosin kurssin tehtäviä varten käytän Virtualboxiin asennettua linux käyttöjärjestelmää. Nykyisin se on Debian 13.  
Puhelimessani on android pohjainen NothingOS käyttöjärjestelmä.  

Kurssin aikana käytän pääosin moodlesta sekä Tero Karvisen kotisivuilta löytyviä materiaaleja (terokarvinen.com). Raportit kirjoitan omaan githubiini, jonne julkaisen kaiken julkisesti.  

## Poisrajaukset, riskien kartoitus & hyväksyntä

Kotoani löytyy myös muita laitteita, jotka tarkoituksella poissuljen tästä kartoituksesta.  
Tässä ytimekäs lista, sekä poisrajauksen syyt:  
- Kotitietokoneeni. Vaikkakin päivittäisessä käytössä, ei kuitenkaan ikinä ole laite jolla suoritan raporteissa nähtyjä kokeiluja.  
- Kumppanin puhelin. Ei millään tavalla relevantti omiin projekteihini, sekä on kytkettynä omaan Elisan tarjoamaan mobiiliverkkoonsa. 
- Kumppanin kannettava tietokone. Ei ole relevantti (on myöskin macbook, hyi) ja on kytkettynä eri verkkoon.
- Äly tv (LG). Vaikka on kytkettynä samaan langattomaan verkkoon, en koe riskitekijäksi sillä siihen ei kytketä USB-laitteita taikka ladata verkosta mitään.
- Muut IoT laitteet. Taloudesta löytyy vielä joitain konsoleita (ps4, Nintendo switch) sekä langattomia kaijuttimia ja kuulokkeita. Nämä ei ole yhteydessä samaan käyttämääni verkkoon, ja harvoin ovat edes käytössä.  

Riskejä tällaisista useamman laitteen talouksista löytyy aina. Suurin mielestäni on kahden henkilön omistajuus, sekä eritasoinen tietoisuus verkkoturvallisuudesta.  
Neljä eri verkkoyhteyttä kolmen eri verkkopalvelun tarjoajan kautta antaa myös luonnollisesti enemmän hyökkäyspintaa.  
Nämä eri yhteydet ovat siis DNA:n tarjoama langaton sekä langallinen yhteys saman reitittimen kautta, MOI:n tarjoama mobiiliverkk sekä Elisan tarjoama mobiiliverkko.  
Kumppanin laitteita sekä verkkoa en kykene hallitsemaan, joten se on hyväksyttävä mutta todella pieni riski.  

## Keskeiset rajapinnat

Keskeisimpänä on kotiverkon ja internetin välissä sijaitseva reititin. Reitittimessä on vakioasetukset palomuurissa, mutta kaikki kirjautumistiedot ja salasanat ovat vaihdettu omiin alkuperäisiä vahvempiin. 
Tietokoneeni käyttöjärjestelmässä on myös Windowsin vakioasetuksilla porskuttava palomuuri. 
Käytössäni on SSH yhteys omaan githubiini, jolla joskus tallentelen Gitin kautta repojani. Joskus myös hyödynnän koulun tarjoamaa OneDrive palvelua, jonne tallennan hyödyllisiä kurssimateriaaleja.  

## Topologia 

<img width="935" height="772" alt="image" src="https://github.com/user-attachments/assets/cfff5cac-6c18-4853-a55e-feee2e88f6ba" />  


## Sidosryhmät  

Kaksi tärkeintä sidosryhmää työmpäristössäni on minä itse, sekä oppilaitos ja sen tarjoamat kurssimateriaalit, ohjeet ja kotisivut. 
Molemmat sidosryhmistä ovat välttämättömiä, sekä molemminpuolista luottamusta vaaditaan.

Minä itse ympäristön "johtajana" pidän huolen, että kaikki kurssiin liittyvä materiaali on eheä ja aina saatavilla kun sitä tarvitaan. 
Tämän toteutan tallentamalla materiaalit fyysisesti omalle laitteelleni, ja sen lisäksi myös koulun tarjoamaan OneDrive palveluun, josta löydän aina kopiot tarvittaessa. 
Ykistyisyydestä pidän huolen sulkemalla kaiken turvallisten salasanojen taakse, enkä jätä laitteitani auki.  Skannaan myös aktiivisesti virukset, sekä pidän laitteet ja tietoturvan päivitettyinä.  

Johtajana pidän huolen myös omalla kohdallani siitä, ettei kurssimateriaaleja päädy vääriin käsiin. Ohjeita noudatetaan vakavasti ja lain puitteissa etenkin kun on kyse hakkeroinnista.
Akateemisesta rehellisyydestä on pidettävä huoli merkitsemällä lähteet, ja mainitsemalla tekoälyn käytöstä jos siihen päädytään.  Kaikki teksti ja harjoitukset on omaa, eikä plagiointia sallita. 
Opittuja asioita käytetään vain silloin, kun siihen annetaan lupa, eikä sitä saa vapaasti soveltaa verkossa tehden haittaa.  

|  Sidosryhmä  |      Tarve        |         ISO Referenssi        |                  Todiste          |
--------------------------------------------------------------
| Minä/Johtaja | Vaadittu, ehdoton | 5.33 Tallenteiden suojaaminen | Kaikista materiaaleista on kopiot |
|   Kumppani   |    Väistämätön    |      6.7 Etätyöskentely       |  Kunnioitus työympäristöä kohtaan |

## Lähteet  
1. https://terokarvinen.com/application-hacking/#homework-tasks, H1 High Standards. (Luettu 21.8.2026)
2. ISO27001-2023 Standardi. (Luettu 21.8.2026)
3. Topologia luotu figmalla. Figma.com
