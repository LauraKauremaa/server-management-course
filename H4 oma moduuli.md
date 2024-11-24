# Space Invaders minionilla

Loin alussa top.sls tiedostoon käynnistys rutiinin, joka käynnistää apache kansiosta install.sls tiedoston.


![image](https://github.com/user-attachments/assets/7df56ed0-0e5e-4e5f-92bd-fbd5576fbf9a)


## Install.sls tiedosto sisältää:

* Ensiksi asensin Apache2
  
* Varmistin, että Apache-palvelu on käynnissä

* Loin vagrant käyttäjän kotihakemistoon public niminen kansio ( mode: 755 )   

* Kopioin <code>000-default.conf</code> tiedosto Salt masterin Apache-kansiosta Salt-minionin <code>Apache2/sites-available/</code> kansioon
  ( 000-default.conf on Apache-palvelimen virtual host määrittely)

* Enabloin Apachessa virtualhost käyttöön komennolla <code>a2ensite</code>

* Käynnistin Apachen uudelleen

* Asensin palvelimelle Space Invaders pelin:
  - Hain githubista javascript space invanders pelin zip-tiedoston minion-palvelimen kotihakemistoon.
  - Asensin unzip ohjelman
  - Purin haetun tiedoston minionin kotihakemistoon
  - Siirsin kaikki puretut tiedostot public kansioon
  - Poistin puretun hakemiston
  - Poistin haetun zip-tiedoston
  - Käynnistin Apachen uudelleen
  

![image](https://github.com/user-attachments/assets/f3ab25cd-7dbd-4542-907d-c0ccdd434f9b)


![image](https://github.com/user-attachments/assets/2fe296b4-917f-4b24-a2e5-a9d0dc6c2b7f)


Install.sls tiedostossa oleva tehtävä kopioi Salt Masterin apache kansiosta <code>000-default.conf</code> tiedoston minions palvelimen apache kansioon, jonka sisältö on tässä alla:


![image](https://github.com/user-attachments/assets/8c0e8a85-ef6a-444f-907f-78339ec7bd0e)


Sitten ajoin <code>salt '*' state.apply</code> ja kaikki 7 install.sls tiedostossa olevaa tehtävää meni läpi.


![image](https://github.com/user-attachments/assets/6d633617-2e53-477f-bd9f-eae6fe766d3f)


Kaiken tämän jälkeen minion-palvelimen apache-palvelin tarjoaa space invaders peliä minion palvelimen IP osoitteesta <code>192.168.56.120</code>


Avasin selaimen ja kirjoitin hakukenttään kyseisen IP osoitteen ja peli avautui.


![image](https://github.com/user-attachments/assets/97f45670-a417-4c58-b09b-758beae80cb8)


## Lähteet:

Saltproject.io https://docs.saltproject.io/salt/user-guide/en/latest/index.html  Luettu 24.11.2024




