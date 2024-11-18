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

<code>sudo apt update></code> 

ja sitten latasin:

sudo apt install apache2


Asennuksen jälkeen loin uuden index.html kansion ja katsoin apache2 statuksen.


loin kansion komennolla:

echo "My Custom Apache Page" | sudo tee /var/www/html/index.html

ja katsoin statuksen komennolla:

sudo systemctl start apache2

sudo systemctl status apache2


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















# c) Oma moduuli

vielä mietinnässä.....





# d) VirtualHost













  # Lähteet:

* Karvinen 2018: Pkg-File-Service – Control Daemons with Salt – Change SSH Server Port Luettu 18.1.2024.
