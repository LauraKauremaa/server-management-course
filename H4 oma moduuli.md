# Space Invanders minionilla

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

* Asensin palvelimelle Space Invanders pelin


![image](https://github.com/user-attachments/assets/f3ab25cd-7dbd-4542-907d-c0ccdd434f9b)


![image](https://github.com/user-attachments/assets/2fe296b4-917f-4b24-a2e5-a9d0dc6c2b7f)


Install.sls tiedostossa oleva tehtävä kopioi Salt Masterin apache kansiosta <code>000-default.conf</code> tiedoston minions palvelimen apache kansioon, jonka sisältö on tässä alla:

![image](https://github.com/user-attachments/assets/8c0e8a85-ef6a-444f-907f-78339ec7bd0e)


Sitten ajoin <code>salt '*' state.apply</code> ja kaikki 7 install.sls tiedostossa olevaa tehtävää meni läpi.

![image](https://github.com/user-attachments/assets/6d633617-2e53-477f-bd9f-eae6fe766d3f)
