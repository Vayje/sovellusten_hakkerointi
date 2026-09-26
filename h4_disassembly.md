# Some disassembly required

## x) Lue (katso) ja tiivistä

### Ghidra for Reverse Engineering, https://www.youtube.com/watch?v=oTD_ki86c9I

## a) Install Ghidra 

Tehtävän tarkoituksena on asentaa ghidra ja dokumentoida se. Käytän tässä koko raportissa Debian distroa VirtualBoxin kautta.
Asensin ensiksi snapd paketin, jota ei varsinaiseti ole pakko asentaa mutta se auttaa pitämään ghidran käyttöä tulevaisuudessa 
helpompana. Kun asennetaan ghidra snappina, saamme mukaan eristetyn ympäristön joka ei ole riippuvainen tulevista java päivityksistä 
ja yhteensopivuusongelmia ei pitäisi tulla. Ghidra on siis java pohjainen paketti. (Varoituksena että tässä saattaa kestää hetki). 

Komennot asennukseen suoritetaan tässä järjestyksessä: 
- sudo apt install snapd
- sudo snap install snapd
- sudo snap install ghidra 

Lopputuloksena saamme ghidralle kansion, ja sovelluksen suoritus tapahtuu komennolla ./ghidraRun.  

<img width="951" height="753" alt="kuva" src="https://github.com/user-attachments/assets/a4f9fb5d-8a64-41ba-a7cc-8590fca5d514" />  

---  

## b) rever-C 

Tehtävän tarkoituksena on käänteismallintaa Tero Karvisen tarjoama ezbin haaste ja analysoida sitä Ghidran avulla niin, 
että osaat kertoa ohjelman tarkoituksen ilman lähdekoodia. 












  
## Lähteet
- www.youtube.com/watch?v=oTD_ki86c9I (x osio, katsottu 25.9.2026)
- https://snapcraft.io/install/ghidra/debian (a osio)
