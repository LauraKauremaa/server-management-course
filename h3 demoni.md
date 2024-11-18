# x) Lue ja tiivistä

## Karvinen 2018 - Pkg-File-Service - Change SSH Server Port:
* Artikkelissa esitellään, kuinka Linux-järjestelmän SSH-palvelimen portin vaihtaminen voidaan automatisoida Salt-työkalun avulla.
* Prosessi sisältää kolmen tärkeän tilafunktion käytön: pkg (pakettien hallinta), file (tiedostojen hallinta), ja service (palveluiden hallinta).
* Artikkeli korostaa oman järjestelmän asetustiedostojen käyttämistä esimerkkien sijaan.

## Saltin tilafunktiot:

* pkg: Käytetään pakettien asentamiseen ja poistamiseen.
  Komennot: pkg.installed, pkg.purged, pkgs.
* file: Tiedostojen hallinta, esimerkiksi luominen, poistaminen tai symbolisten linkkien hallinta.
  Komennot: file.managed, file.absent, file.symlink.
* service: Palveluiden hallinta, esimerkiksi käynnistys, pysäytys tai automaattinen käynnistys.
  Komennot: service.running, service.dead, enable.

# a) Apache easy mode

Aloitin apache2 asentamisen niin, että ensin katsoin päivitykset:

<code>sudo apt update</code> 

ja sitten latasin:

<code>sudo apt install apache2</code>


Asennuksen jälkeen loin uuden index.html kansion ja katsoin apache2 statuksen.


loin kansion komennolla:

<code>echo "My Custom Apache Page" | sudo tee /var/www/html/index.html</code>

ja katsoin statuksen komennolla:

<code>sudo systemctl start apache2</code>

<code>sudo systemctl status apache2</code>


![image](https://github.com/user-attachments/assets/79e913ea-9f48-4648-be2e-8059e61b27e4)



Sitten aloitin automatisoinnin ja lisäsin install.sls tiedostoon nämä tiedot:



![image](https://github.com/user-attachments/assets/ae3e3987-a787-413e-a0a0-3e1b3c172419)


muokkasin /srv/salt hakemistossa olevaa top.sls tiedostoa.


![image](https://github.com/user-attachments/assets/92637aae-a845-48fc-8bd9-36571e1c9a8e)



ja sen jälkeen kokeilin ja kaikki toimi miten piti.


![image](https://github.com/user-attachments/assets/992e7b0c-82b2-4a3e-bddf-f156a9c2fde0)


server2 (minion) tarkistin että indexi tiedoston sisältö on muuttunut.


![image](https://github.com/user-attachments/assets/440a73b5-8bc1-40e3-bff4-523d393308cc)




# b) SSHouto

Avasin tiedoston:

<code>sudo nano /etc/ssh/sshd_config</code>

lisäsin sinne rivit:

<code>Port 22</code>
<code>Port 2222</code>

Sitten käynnistin SSH-palvelun uudelleen:

<code>sudo systemctl restart sshd</code>


Sitten varmistin, että palvelu kuuntelee uusissa porteissa:

<code>sudo ssh -tuln</code>

![image](https://github.com/user-attachments/assets/063d90b4-9a5d-41b9-8a7a-973ab56bf873) 


Loin <code>/srv/salt/ssh</code> hakemistoon <code>openssh.sls</code> tiedoston ja kopioin <code>/etc/ssh/sshd_config</code> tiedoston tuohon samaan hakemistoon:

![image](https://github.com/user-attachments/assets/08507773-8b09-42ca-8860-6f5dc189188e)


Sitten muokkasin <code>top.sls</code> tiedostoa:

![image](https://github.com/user-attachments/assets/219bf2aa-6b3e-4377-8f3e-cb79c513bb83)


Ja suoritin komennon <code>sudo salt '*' status.apply</code>

![image](https://github.com/user-attachments/assets/eb2086fd-9abe-41a9-9bdb-dc3d4113dd16)


Server2 (minion) varmistin että palvelin kuntelee portteja 22 ja 2222

![image](https://github.com/user-attachments/assets/5b176b07-58fa-4fee-83a0-0eb6b88c0ae6)



# c) Oma moduuli

vielä mietinnässä.....





# d) VirtualHost













  # Lähteet:

* Karvinen 2018: Pkg-File-Service – Control Daemons with Salt – Change SSH Server Port Luettu 18.1.2024.
