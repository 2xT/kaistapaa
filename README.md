Kaistapää - TVkaista downloader
===============================

Kaistapää on komentoriviohjelma, mikä mahdollistaa avainsanojen perusteella tapahtuvan mediatiedostojen lataamisen [TVkaista](http://tvkaista.fi/) -palvelusta.

Kaistapää on toteutettu [Ruby](https://www.ruby-lang.org/en/downloads/) -ohjelmointikielellä ja toimii kaikilla yleisimmillä käyttöjärjestelmillä.

Kaistapään toimivuus on testattu Rubyn versiolla 2.0. Ohjelma saattaa toimia vanhemmillakin Rubyn versioilla, mutta niiden toimivuutta ei ole kokeiltu.

Ohjelma tarvitsee [TVkaista](http://tvkaista.fi/) -palvelun tunnukset toimiakseen.

Käyttöönotto
------------

1. [Asenna Ruby](https://www.ruby-lang.org/en/downloads/)
2. [Asenna Git](http://git-scm.com/downloads)
3. Hae [Kaistapää](https://github.com/2xT/kaistapaa)
	
        git clone https://github.com/2xT/kaistapaa

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

* ... kokeilla avainsana-asetuksia, mutta en vielä ladata ohjelmia?

		ruby ./kaistapaa -t

* ... ladata rinnakkain eikä peräkkäin?

		ruby ./kaistapaa -c

	(Omalla vastuulla, yhtäaikainen lataus ei ole tällä hetkellä kovin vakaa ...)

* ... etsiä löytyykö TVkaistalta "Pulp Fiction" -elokuvaa?

		ruby ./kaistapaa -s "pulp fiction" -t

* ... ladata "Pulp Fiction" -elokuvan?

		ruby ./kaistapaa -s "pulp fiction"

* ... ettei ohjelma tulosta ruudulle mitään vaan hakee pelkästään avainsanat.yml -tiedostossa asetetut ohjelmat?

		ruby ./kaistapaa -v

* ... poistaa lukkotiedoston?

		ruby ./kaistapaa -f

* ... siirtää lataushakemisto toiseen paikkaan?

	Kopioi lataushakemisto haluttuun paikkaan ja aseta uusi polku asetukset.yml -tiedostoon.

* ... siirtää tilahakemisto toiseen paikkaan?

	Kopioi tilahakemisto haluttuun paikkaan ja aseta uusi polku asetukset.yml -tiedostoon.

* ... suorittaa ohjelman automaattisesti 15 minuutin välein?

	[Apple OSX](http://en.wikipedia.org/wiki/OS_X) ja [Linux](http://en.wikipedia.org/wiki/Linux) -pohjaisissa käyttöjärjestelmissä voit hyödyntää cron -palvelua.
	
	Muokkaa crontab -tiedostoa
	
		crontab -e

	Lisää tiedoston loppuun uusi rivi
	
		*/15 * * * * /polku/minne/laitoit/ohjelman/nimelta/kaistapaa

	Ohjelma luo käynnistyessään lukkotiedoston, mikä varmistaa, että vain yksi kaistapaa on kerrallaan ajossa.

Ohjelma on ihan kuraa - yritin ...
----------------------------------

* ... suorittaa ohjelman ja tuloksena oli virheilmoitus:

	```
	[!] Could not parse ./avainsanat.yml: syntax error on line 61, col 1: `}'
	[!] Could not parse ./asetukset.yml: syntax error on line 5, col 1: `} '
	kaistapaa.rb:266: undefined method `[]' for nil:NilClass (NoMethodError)
	```

	Vastaus: Ruby -versiosi on liian vanha, ole ystävällinen ja päivitä uudempaan.

Lisenssi
--------

[DBAD](http://www.dbad-license.org/)

Palaute
-------

Rakentavaa palautetta voi laittaa osoitteeseen 2xT@iki.fi

