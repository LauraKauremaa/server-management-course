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
sudo apt update 

ja sitten latasin:
sudo apt install apache2

Asennuksen jälkeen loin uuden index.html kansion ja katsoin apache2 statuksen.

loin kansion komennolla:
echo "My Custom Apache Page" | sudo tee /var/www/html/index.html

ja katsoin statuksen komennolla:

sudo systemctl start apache2

sudo systemctl status apache2


![image](https://github.com/user-attachments/assets/48596853-b4fd-459d-9743-3e5cd351d9c8)












# b) SSHouto







# c) Oma moduuli







# d) VirtualHost













  # Lähteet:

* Karvinen 2018: Pkg-File-Service – Control Daemons with Salt – Change SSH Server Port Luettu 18.1.2024.
