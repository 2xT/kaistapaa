Kaistapää - TVkaista downloader
===============================

Kaistapää on komentoriviohjelma, mikä mahdollistaa avainsanoihin perusteella tapahtuvan mediatiedostojen lataamisen [TVkaista](http://tvkaista.fi/) -palvelusta.

Kaistapää on toteutettu [Ruby](https://www.ruby-lang.org/en/downloads/) -ohjelmointikielellä ja toimii näin ollen kaikilla yleisimmillä käyttöjärjestelmillä.

Kaistapään toimivuus on testattu Rubyn versiolla 2.0. Ohjelma saattaa toimia vanhemmillakin Rubyn versioilla, mutta niiden toimivuutta ei ole kokeiltu.

Käyttöönotto
------------

1. [Asenna Ruby](https://www.ruby-lang.org/en/downloads/)
2. [Asenna Git](http://git-scm.com/downloads)
3. Hae [Kaistapää](polku)
	
        git clone <polku>

4. Muokkaa asetuksia

	Kopioi esimerkki asetusten pohjaksi

        cp asetukset.yml.esim asetukset.yml

	Avaa asetustiedosto haluamallasi tekstieditorilla

		nano -w asetukset.yml

	Aseta TVkaista -palvelun tunnus- ja salasanatiedot sekä tiedostopolut paikalleen.

5. Muokkaa avainsanoja

	Kopioi esimerkki avainsanojen pohjaksi

		cp avainsanat.yml.esim avainsanat.yml

	Avaa avainsanatiedosto haluamallasi tekstieditorilla

		nano -w avainsanat.yml

	Aseta haluamasi avainsanat - esimerkkitiedosto on varsin hyvin dokumentoitu.

6. Tarkista, että laittamasi asetukset toimivat suorittamalla testiajo (tiedostoja ei vielä ladata)

        ruby ./kaistapaa -t

6. Suorita tuotantoajo (tiedostot ladataan)

        ruby ./kaistapaa

Miten toimia kun haluan ...
---------------------------

* ... nähdä kaikki ohjelmiston komentorivivivut?

		ruby ./kaistapaa -h

* ... testata avainsanojen muutoksia?

		ruby ./kaistapaa -t

* ... ladata ohjelmat peräkkäin eikä samaan aikaan?

		ruby ./kaistapaa -c

* ... etsiä löytyykö TVkaistalta "Pulp Fiction" -elokuvaa?

		ruby ./kaistapaa -s "pulp fiction" -t

* ... ladata "Pulp Fiction" -elokuvan?

		ruby ./kaistapaa -s "pulp fiction"

* ... ettei ohjelma tulosta ruudulle mitään vaan hakee pelkästään avainsanat.yml -tiedostossa asetetut ohjelmat?

		ruby ./kaistapaa -v

* ... poistaa lukkotiedoston?

		ruby ./kaistapaa -f

* ... siirtää lataushakemiston toiseen paikkaan?

	Kopioi lataushakemisto haluttuun paikkaan ja aseta uusi polku asetukset.yml -tiedostoon.

* ... siirtää tilahakemiston toiseen paikkaan?

	Kopioi tilahakemisto haluttuun paikkaan ja aseta uusi polku asetukset.yml -tiedostoon.

* ... suorittaa ohjelman automaattisesti 15 minuutin välein?

	[Apple OSX](http://en.wikipedia.org/wiki/OS_X) ja [Linux](http://en.wikipedia.org/wiki/Linux) -pohjaisissa käyttöjärjestelmissä voit hyödyntää cron -palvelua
	
	Muokkaa crontab -tiedostoa
	
		crontab -e

	Lisää tiedoston loppuun uusi rivi
	
		*/15 * * * * /polku/minne/laitoit/ohjelman/nimelta/kaistapaa

	Ohjelma luo käynnistyessään lukkotiedoston, mikä varmistaa, että vain yksi kaistapaa on kerrallaan ajossa.

Palaute
-------

Rakentavaa palautetta voi laittaa osoitteeseen 2xT@iki.fi

