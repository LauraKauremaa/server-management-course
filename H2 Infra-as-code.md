# X)
## Karvinen 2021: 
Debian 11 ja Vagrantin avulla luodaan kahden koneen virtuaaliverkko. 
## Karvinen 2018: 
Salt Stackin pikaopas Ubuntu Linuxille. Nykyään Saltin asennusta edeltää pakettivaraston lisääminen.
## Karvinen 2014: 
Salt-moduulien järjestelyvinkki: jokainen moduli omaan kansioon (esim. /srv/salt/hello/init.sls).
## Karvinen 2023: 
Salt Vagrant -ympäristön provisiointi yhdelle master- ja kahdelle slave-koneelle. Tärkeät aiheet:
Infra as Code - toiveet tekstimuotoon.
top.sls - määrittää, mitkä tilat slave-koneet suorittavat.
## Salt Contributors - Salt Overview:
Rules of YAML: YAML noudattaa selkeitä sääntöjä, kuten sisennystä ja avain-arvo -pareja, jotka helpottavat luettavuutta.
YAML Simple Structure: YAML yksinkertainen rakenne tekee tiedostojen lukemisesta ja kirjoittamisesta helppoa.
Lists and Dictionaries - YAML Block Structures: YAML käyttää listoja ja sanakirjoja lohkorakenteina, jotka auttavat järjestämään tietoja hierarkkisesti ja selkeästi.

# a) Hello vagrant!
Olen asentanut vagrantin ja virtualboxin.

![image](https://github.com/user-attachments/assets/ffc25cdb-f184-48a3-a6c6-8ebd44bf7e82)


![image](https://github.com/user-attachments/assets/e700bbe7-ca05-43f6-9f0e-3a2d896dff3c)


# b) Linux vagrant
Tein vagrantilla uuden Linux virtuaalikoneen. Loin ensiksi oman hakemiston ja siirryin sinne. Sen jälkeen suoritin komennon alustamaan vagrant ympäristöä:
vagrant init ubuntu/bookworm64
Sitten lähdin muokkaamaan vagrantfile tiedostoani ja muutin sinne enemmän muistia ja prosessoritehoa. 
Sen jälkeen suoritin komennon vagrant up käynnistääkseni virtuaalikoneen ja se onnistui hienosti. Vähän oli ongelmia kun latasi todella hitaasti, mutta lopulta sain sen käynnistettyä vagrant ssh komennolla.

![image](https://github.com/user-attachments/assets/daca7a44-e8a6-4e1a-b79a-2868fa985e4c)


![image](https://github.com/user-attachments/assets/ed6c71c3-26cc-4087-9adb-7a52a498b7b9)


![image](https://github.com/user-attachments/assets/efb02e96-6514-44a8-a1da-bb394ffe0f8a)


# c) Kahden Linux-tietokoneen verkko Vagrantilla
Loin aluksi kaksi debian palvelinta.

![image](https://github.com/user-attachments/assets/7010462d-98bb-4bee-8cbc-57bd324d2364)


Alla olevassa kuvassa on luomani kahden palvelimen tiedot missä näkyy myös ip osoitteet.

![image](https://github.com/user-attachments/assets/c0e8ee3b-0cc9-4fb2-9e29-060e0bd91169)


Otin ssh yhteyden toiseen servereistä ja pingasin sitten toiseen serveriin.

![image](https://github.com/user-attachments/assets/9c943969-5fc1-4f8f-9ee4-1f70192d98d0)

Ja sain tehtyä tehtävän ilman mutkia.


# d)  Herra-orja verkossa
Aloitin niin, että asensin ensin Curl toiminnon sudo apt install curl ja sen jälkeen asensin palvelimille saltin komennoilla:

Sen jälkeen päivitin paketit:

sudo apt update
sudo apt upgrade

ja sitten asensin server 1 salt masterin ja server 2 salt minionin:

sudo apt-get install salt-master
sudo apt-get install salt-minion

Salt minionilla vaihoin vähän tietoja:

/etc/hosts
192.168.56.110 salt
sudo service salt-minion stop
sudo service salt-minion start

Salt masterillakin vaihoin tietoja:

sudo salt-key
sudo systemctl status salt-minion
sudo systemctl status salt-master

Seuraavaksi pitää asentaa avaimet jotta herra voi komentaa orjaa.

![image](https://github.com/user-attachments/assets/0b7eed44-25de-4591-bf5b-458d4dfb037b)

ja sain yhteyden:

![image](https://github.com/user-attachments/assets/e79d56e5-9c00-455e-9025-9a47c4e45e4f)


# e) Hei infrakoodi!  &  f) sls-tiedosto verkon yli orjalla 

Kirjoitin sls-tiedosto, joka tekee esimerkkitiedoston /tmp/ -kansioon.

Lisäsin nämä tiedot: 

![image](https://github.com/user-attachments/assets/88c50ba3-69e3-4e16-a2dc-bf1d7e13302d)

ja sain luotua tiedoston:

![image](https://github.com/user-attachments/assets/719d4bbb-9a4a-498c-9e81-567574305606)

ja se näkyy minionilla

![image](https://github.com/user-attachments/assets/80cd4e9b-d0e1-476e-8fa1-7ad4a59b99e8)


# g) sls-tiedosto
Tein sls-tiedoston ja se ajoi kaikki 4 pakettia.

![image](https://github.com/user-attachments/assets/33ab6b67-c238-4b90-ad9f-4b8fd30ce915)


# h) Top file


apache.sls ja hello.sls sain toimimaan:

![image](https://github.com/user-attachments/assets/826e409c-c4ef-4d91-8000-ca1f702e06d8)


apache.sls tiedoston sisälle loin nämä:

![image](https://github.com/user-attachments/assets/de8c5c82-7391-4f6d-85d7-1e1398dbe87a)


hello.sls tiedoston sisälle puolestaan loin nämä:

![image](https://github.com/user-attachments/assets/d2879989-41c5-431d-baf5-393748e2d657)



# Lähteet:
* Karvinen, Tero. Two Machine Virtual Network With Debian 11 Bullseye and Vagrant, 2021. https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/ -luettu 12.11.2024

* Karvinen, Tero. Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux, 2018. https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux - luettu 12.11.2024

* Karvinen, Tero. Hello Salt Infra-as-Code, 2014. https://terokarvinen.com/palvelinten-hallinta/#h2-infra-as-code - luettu 12.11.2024

* Karvinen, Tero. Salt Vagrant - automatically provision one master and two slaves, kohdat "Infra as Code" ja "top.sls", 2023. https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file - luettu 12.11.2024

* Salt conributors. Luettu 13.11.2024

