# Vaatimusmäärittely
Opinto-ohjelma: Tietojenkäsittelytieteen kandidaatti (TKT) 

Projekti toteutetaan Pythonilla ja dokumentoidaan suomeksi (pystyn vertaisarvioimaan Pythonilla toteutettuja projekteja).

[Gomoku](https://en.wikipedia.org/wiki/Gomoku) on kahden pelattava strategiapeli 15x15-kokoisella pelilaudalla. Pelin tavoitteena on muodostaa jatkuva rivi viidestä saman tyyppisestä nappulasta – vaaka-, pysty- tai vinottain. Ensimmäinen pelaaja, joka tässä onnistuu, voittaa pelin.

Tässä projektissa käyttäjä voi pelata tekoälyä vastaan, joka toteutetaan alpha-beta-karsinnalla tehostetulla minimax-algoritmilla. Käyttöliittymä toteutetaan `pygame`-kirjaston avulla.

Algoritmi laskee siirtoja pelitilanteesta eteenpäin ja valitsee siirron, joka tuottaa käytetyllä laskentasyvyydellä parhaan tuloksen olettaen, että sekä tekoäly että vastapelaaja tekevät joka tilanteessa itsensä kannalta parhaan mahdollisen siirron:

- Tutkitaan vain vapaat ruudut, jotka ovat korkeintaan kahden ruudun päässä aiemmin tehdyistä siirroista, tai muu tätä tehokkaampi mielekäs kokeiltavien siirtojen karsinta.
- Tutkittavia siirtoja ei selvitetä erikseen joka pelitilanteessa, vaan pidetään yllä listaa tällaisista ruuduista, ja päivitetään sitä tehtyjen / minimaxissa kokeiltujen siirtojen myötä.
- Siirtojen mukaan päivitetty lista annetaan parametrina eteenpäin minimaxissa.
- Voiton tarkistus tehdään tutkimalla vain rivit, jotka sisältävät edellisen siirron.
- Jos viiden rivi on syntynyt, voittaja on edellisen siirron tehnyt pelaaja, ja edellinen siirto on osa voittoriviä.

Tavoitteena oleva aikavaatimus on [Wikipedian](https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning) mukaisesti $O(\sqrt{b^d})$, jossa b on haarautumiskerroin (keskimääräinen tai vakio) ja d etsintäsyvyyden taso. 

Riippuvuuksien hallintaan käytetään Poetryä. Algoritmin oikea toiminta varmistetaan kattavalla yksikkötestauksella Unittest-kehystä hyödyntäen.
