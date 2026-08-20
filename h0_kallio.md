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





