# Normalisieren von Relationalen Datenbanken
- [Normalform 1](#normalform-1)
- [Normalform 2](#normalform-2)
- [Normalform 3](#normalform-3)

## Beispiel (Aufgabentabelle)
|KundenNr|Name|Adresse|BestellNr|Bestelldatum|ArtikelNr|Artikelbezeichnung|Menge|Preis|Artikelgruppe|Rabatt
|-|-|-|-|-|-|-|-|-|-|-
|1|Klaus Huber|Berlinerstr. 1, 49377 Vechta|23|06.09.2024|1|Fernseher|1|799|Elektronik|10%
|2|Hans Meier|Goethestr. 32, 54434 Köln|42|07.09.2024|2<br>3<br>1|Monitor<br>Tastertur<br>Fernseher|2<br>1<br>1|199<br>39<br>799|Elektronik<br>Peripherie<br>Elektronik|10%
1|Klaus Huber|Berlinerstr. 1, 49377 Vechta|78|08.09.2024|4|Maus|1|19|Tiernahrung|10%
|3|Jens König|Eichenweg 43, 12433 Berlin|99|09.09.2024|5|Hundefutter|1|49|Tiernahrung|0%

## Normalform 1
### Beispiel
<style>
.tableExampleRed {
    color: #f00;
}
</style>
Primärschlüssel <span class="tableExampleRed">rot</span> markiert

|KundenNr|Name|Straße|PLZ|Ort|BestellNr|Bestelldatum|ArtikelNr|Artikelbezeichnung|Menge|Preis|Artikelgruppe|Rabatt
|-|-|-|-|-|-|-|-|-|-|-|-|-
|<span class="tableExampleRed">1</span>|Klaus Huber|Berlinerstr. 1|49377|Vechta|<span class="tableExampleRed">23</span>|06.09.2024|<span class="tableExampleRed">1</span>|Fernseher|1|799|Elektronik|10%
|<span class="tableExampleRed">2</span>|Hans Meier|Goethestr. 32|54434|Köln|<span class="tableExampleRed">42</span>|07.09.2024|<span class="tableExampleRed">2</span>|Monitor|2|199|Elektronik|10%
|<span class="tableExampleRed">2</span>|Hans Meier|Goethestr. 32|54434|Köln|<span class="tableExampleRed">42</span>|07.09.2024|<span class="tableExampleRed">3</span>|Tastertur|1|39|Peripherie|10%
|<span class="tableExampleRed">2</span>|Hans Meier|Goethestr. 32|54434|Köln|<span class="tableExampleRed">42</span>|07.09.2024|<span class="tableExampleRed">1</span>|Fernseher|1|799|Elektronik|10%
<span class="tableExampleRed">1</span>|Klaus Huber|Berlinerstr. 1|49377|Vechta|<span class="tableExampleRed">78</span>|08.09.2024|<span class="tableExampleRed">4</span>|Maus|1|19|Tiernahrung|10%
|<span class="tableExampleRed">3</span>|Jens König|Eichenweg 43|12433|Berlin|<span class="tableExampleRed">99</span>|09.09.2024|<span class="tableExampleRed">5</span>|Hundefutter|1|49|Tiernahrung|0%

## Normalform 2
### Beispiel
#### Tabelle Kunde:
|KundenNr|Nachname|Vorname|Straße|PLZ|Ort
|-|-|-|-|-|-
|1|Huber|Klaus|Berlinerstr. 1|49377|Vechta
|2|Meier|Hans|Goethestr. 32|54434|Köln
|3|König|Jens|Eichenweg 43|12433|Berlin

#### Tabelle Bestellung:
|BestellNr|KundenNr|Bestelldatum
|-|-|-
|23|1|06.09.2024
|42|2|07.09.2024
|78|1|08.09.2024
|99|3|09.09.2024

#### Tabelle Position:
|BestellNr|ArtikelNr|Menge
|-|-|-
|23|1|1
|42|2|2
|42|3|1
|42|1|1
|78|4|1
|99|5|1

#### Tabelle Artikel:
|ArtikelNr|Bezeichnung|Preis|Artikelgruppe|Rabatt
|-|-|-|-|-
|1|Fernseher|799|Elektronik|10%
|2|Monitor|199|Elektronik|10%
|3|Tastertur|39|Peripherie|10%
|4|Maus|19|Peripherie|10%
|5|Hundefutter|49|Tiernahrung|0%

## Normalform 3
### Beispiel
#### Tabelle Artikelgruppe:
|ArtikelgruppeNr|Name|Rabatt
|-|-|-
|1|Elektronik|10%
|2|Peripherie|10%
|3|Tiernahrung|0%

#### Neue Tabelle Artikel:
|ArtikelNr|Bezeichnung|Preis|ArtikelgruppeNr
|-|-|-|-
|1|Fernseher|799|1
|2|Monitor|199|1
|3|Tastertur|39|2
|4|Maus|19|2
|5|Hundefutter|9|3

#### Kardinalitäten:
- [Artikel](#neue-tabelle-artikel) **n..1** [Artikelgruppe](#tabelle-artikelgruppe)
- [Bestellung](#tabelle-bestellung) **1..n** [Position](#tabelle-position)
- [Kunde](#tabelle-kunde) **1..n** [Bestellung](#tabelle-bestellung)


