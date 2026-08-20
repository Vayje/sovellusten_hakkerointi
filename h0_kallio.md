## H0 Compile and Analyze

Tehtävässä oli tarkoitus muuttaa koodi suorituskykyiseksi, eli binääriksi jota tietokone osaa lukea.  
Aloitin yksinkertaisella "Hello World" ohjelmalla, joka on kaiken perusta. Ohjeet tähän löysin nopealla googlauksella, ja koko tehtävä on suoritettu lähes kokonaan ohjeiden mukaan.  
Ainoa poikkeus on, että käytin koko harjoituksen ajan nanoa, enkä vimiä tekstieditorina.  

Ensimmäisessä vaiheessa loin testitiedoston komennolla "nano compiletest.c". Tiedoston sisään kirjoitin yksinkertaisen printin "Hello Worldista".  

<img width="441" height="119" alt="Näyttökuva 2026-08-20 144815" src="https://github.com/user-attachments/assets/bbe114a4-ca99-4749-9442-c0104e85ac63" />  
<img width="695" height="233" alt="Näyttökuva 2026-08-20 144802" src="https://github.com/user-attachments/assets/c719757d-b3fb-4197-a5a9-a91c3c4dcec8" />  

Ensimmäiseen virheeseen ajaudin jo heti alkumetreillä.  

<img width="1912" height="553" alt="Näyttökuva 2026-08-20 144930" src="https://github.com/user-attachments/assets/40ad54f0-9034-431e-b22e-f97cc1f7a722" />  

Tämän ratkaisusta saan kiittää vierustoveriani, joka huomautti että yläriviltä puuttui "#include <stdio.h>". Tässä lopullinen tiedoston sisältö:  

<img width="775" height="463" alt="Näyttökuva 2026-08-20 145126" src="https://github.com/user-attachments/assets/4940ddf6-a45e-4fda-a16b-83c9de25eac9" />  

Tämän jälkeen suoritettiin komento "gcc compiletest.c -o compiletest", joka kokoaa lähdekoodimme kasaan. "-o" kohta komennossa luo suoritettavan tiedoston, jonka nimeksi tulee alkuperäinen compiletest.  
Ilman "-o" kehotetta gcc käsky luo default nimisen tiedoston, esimkerkiksi a.out.  

Kokoamisen jälkeen kansiostamme löytyy muutama erilainen compiletest. tiedosto.  

<img width="241" height="155" alt="Näyttökuva 2026-08-20 145621" src="https://github.com/user-attachments/assets/65ab3d3d-0892-4918-bbfd-337e078ea2c8" />  

Compiletest.i tiedoston kun avaa nanolla, huomataan että "#include <stdio.h>" osio on muuttunut useaksi riviksi kaikennäköistä tavaraa.  

<img width="864" height="773" alt="Näyttökuva 2026-08-20 145720" src="https://github.com/user-attachments/assets/68b25fca-962b-4afe-9994-d93d85d0e3ce" />  

Lopusta kuitenkin löydämme alkuperäisen Hello World koodipätkän.  

<img width="940" height="859" alt="Näyttökuva 2026-08-20 145832" src="https://github.com/user-attachments/assets/686930f7-6a8a-47ad-a17b-06cbac3ce267" />  

Compiletest.s kun avataan, niin nähdään taas useampi rivi erinäköistä koodia, jossa näemme myös seassa luomamme Hello Worldin. .s tiedoston tarkoitus on antaa "kokoamisohjeet".  

Nanolla avattua compiletest.o tiedoston huomataan, että luomamme Hello World on muuttunut tietokoneeella luettavaksi kieleksi, jota emme pysty enää omin silmin tulkitsemaan.  

<img width="1886" height="336" alt="Näyttökuva 2026-08-20 150036" src="https://github.com/user-attachments/assets/c46b5e0c-5b76-44e1-b0dd-2ea8aa6b4107" />  

Tiedostoa suorittaessa kaikki compiletestist linkataan yhteen, ja compiler lisää siihen myös omaa koodia jota tarvitaan tiedoston suorittamiseen ja lopettamiseen.  
Tämä huomataan vertailemalla alkuperäisen (lähdekoodi) sekä ajettavan tiedoston kokoa.  

<img width="692" height="268" alt="Näyttökuva 2026-08-20 150210" src="https://github.com/user-attachments/assets/13a86990-fc94-410d-ae60-21a9542c2e14" />.

Lopullinen suoritus näyttää kaikessa yksinkertaisuudessaan tältä.  

<img width="495" height="116" alt="Näyttökuva 2026-08-20 145208" src="https://github.com/user-attachments/assets/385d6a7b-1630-4000-b75b-7859ccf0daa6" />  


# Lähteet
1) https://www.geeksforgeeks.org/c/compiling-a-c-program-behind-the-scenes/ (Luettu 20.8.2026)










