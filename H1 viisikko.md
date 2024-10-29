# x)
# Karvinen 2023: Run Salt Command Locally
Käsittelee, miten Salt-komentoja ajetaan paikallisesti ilman master-palvelinta.
Korostaa 'salt-call --local' -komennon käyttöä, jolla voidaan testata komentoja suoraan minion-koneella.

# Karvinen 2018: Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux
Johdatus Salt Stackin käyttöönottoon master-slave (herra-orja) -mallissa.
Selittää master- ja minion-palveluiden asennusprosessin sekä niiden konfiguroinnin.

# Karvinen 2006: Raportin kirjoittaminen
Ohjeistaa raportoin

# a) 
Asensin debian 12-bookwormin linux virtualkoneelleni ilman ongelmia.
# b)
Asensin Salt minion ja käytin ohjetta salt instal quide https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/debian.html#install-salt-on-debian-12-bookworm-amd64 Luettu 29.10.2024.
Asenus sujui hyvin ja ilman mitään mutkia. Ohjeessa oli paljon hyötyä ja asennus alkoi pitkällä komennolla: mkdir /etc/apt/keyrings
sudo curl -fsSL -o /etc/apt/keyrings/salt-archive-keyring-2023.gpg https://repo.saltproject.io/salt/py3/debian/12/amd64/SALT-PROJECT-GPG-PUBKEY-2023.gpg
echo "deb [signed-by=/etc/apt/keyrings/salt-archive-keyring-2023.gpg arch=amd64] https://repo.saltproject.io/salt/py3/debian/12/amd64/latest bookworm main" | sudo tee /etc/apt/sources.list.d/salt.list jonka jälkeen komennoilla:
sudo apt-get install salt-master
sudo apt-get install salt-minion
sudo apt-get install salt-ssh
sudo apt-get install salt-syndic
sudo apt-get install salt-cloud
sudo apt-get install salt-api
Sain asennuksen tehtyä onnistuneesti. 
# c) Viisi tärkeintä Saltin tilafunktiota: pkg, file, service, user, cmd
Aloitin kokeilun pkg tilafunktiosta. Käytin apunani Tero Karvisen nettisivua mistä löysin ohjeita. Karvinen 2023 Run Salt command Locally https://terokarvinen.com/2021/salt-run-command-locally/ Luettu 29.10.2024
Kokeilin pkg.installed mikä asentaa määritellyn paketin. Kokeilin komentoa sudo salt-call --local pkg.install name=htop ja sain ilmoituksen, että paketti on jo olemassa eli nähtävästi olin sen asentanut jo joskus aikaisemmin.
Seuraavaksi kokeilin file.management tilafunktiota ja kyseinen komento joko hallitsee tiedostoa tai luo sellaisen jos sitä ei ole olemassa. Kokeilin koodia sudo salt-call --local file.managed name=/tmp/testfile.txt contents="Hello SaltStack"
ja sain tulokseksi että tiedosto luotu ja salt vahvisti että tiedostossa on oikeat asetukset. 
Kokeilin sitten service.running ja se varmistaa että tietty palvelu on käynnissä. kokeilin komentoa sudo salt-call --local service.running name=apache2 ja sain tulokseksi, että palvelu käynnistetty sillä olen asentanut Apache2.
Sitten kokeilin user.present tilafunktiota ja se lisää käyttäjän palvelimeeni. kokeilin komentoa sudo salt-call --local user.present name=testuser jolloin Slat ilmoitti että käyttäjä lisätty. 
Viimeisenä kokeilin komentoa cmd.run joka suorittaa komennon minkä itse määritän komentoriville. Esimerkiksi komennolla sudo salt-call --local cmd.run "echo 'Hello SaltStack'" jolloin Slat tulostaa komennon ' Hello SaltStack'

# d)  Idempotentti
Ajoin komennon sudo salt-call --local pkg.install name=htop ja ensimmäisellä ajolla Salt asensi sen ja palautti tiedon onnistuneesta asennuksesta.
Toisella ajolla koska htop on jo asennettu, Salt ei tee mitään, ja tuloksena on ilmoitus, että paketti on jo olemassa.
Salt-tilafunktio on idempotentti, koska sen suorittaminen ei muuta järjestelmää, jos määritelty tila on jo saavutettu. Tämä takaa, ettei pakettia asenneta uudelleen, jos se on jo asennettu.
Ominaisuus tekee Saltin käytöstä luotettavaa, koska voidaan varmistaa, että tila pysyy haluttuna, vaikka komentoja ajettaisiin useita kertoja.

# Lähteet 
salt instal quide https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/debian.html#install-salt-on-debian-12-bookworm-amd64 Luettu 29.10.2024.

Karvinen 2023 Run Salt command Locally https://terokarvinen.com/2021/salt-run-command-locally/ Luettu 29.10.2024

Karvinen 2023 Salt Quickstart https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/ Luettu 29.10.2024

Karvinen 2023 Raportin kirjoittaminen https://terokarvinen.com/2006/06/04/raportin-kirjoittaminen-4/ Luettu 29.20.2024
