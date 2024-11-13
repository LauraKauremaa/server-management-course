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
Tässä tehtävässä minulla oli vähän vaikeuksia saada yhdistettyä kaksi verkkoa, koska vagranttini jäi jumiin ja ei suosunut käynnistyä. Aloitin kuitenkin niin, että loin taas uuden hakemiston mdir vagrant_kaksiverkkoa. Sen jälkeen alustin vagrantfilen vagrant init komennolla. 

















# Lähteet:
* Karvinen, Tero. Two Machine Virtual Network With Debian 11 Bullseye and Vagrant, 2021. https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/ -luettu 12.11.2024

* Karvinen, Tero. Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux, 2018. https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux - luettu 12.11.2024

* Karvinen, Tero. Hello Salt Infra-as-Code, 2014. https://terokarvinen.com/palvelinten-hallinta/#h2-infra-as-code - luettu 12.11.2024

* Karvinen, Tero. Salt Vagrant - automatically provision one master and two slaves, kohdat "Infra as Code" ja "top.sls", 2023. https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file - luettu 12.11.2024

* Salt conributors. Luettu 13.11.2024

