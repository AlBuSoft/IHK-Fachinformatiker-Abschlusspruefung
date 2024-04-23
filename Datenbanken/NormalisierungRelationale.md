# Normalisieren von Relationalen Datenbanken
- [Kurzerklärung](#kurzerklärung)
- [Beispielaufgabe](#beispiel-aufgabentabelle)
- [Normalform 1 (1NF)](#normalform-1)
    - [Erklärung](#erklärung)
    - [Beispiel](#beispiel)
- [Normalform 2 (2NF)](#normalform-2)
    - [Erklärung](#erklc3a4rung-1)
    - [Beispiel](#beispiel-1)
- [Normalform 3 (3NF)](#normalform-3)
    - [Erklärung](#erklc3a4rung-2)
    - [Beispiel](#beispiel-2)

## Kurzerklärung
Die Normalformen der Datenbankmodellierung dienen dazu, Redundanzen zu vermeiden und die Datenintegrität zu verbessern. Die Normalisierung hilft dabei, Datenanomalien zu vermeiden, die Datenkonsistenz zu verbessern und die Effizienz bei Abfragen und Aktuallisierungen zu erhöhen.

## Beispiel (Aufgabentabelle)
Hier wird eine Beispielaufgabentabelle gezeigt, die in den folgenden erklärungen der drei Normalformen aufgelöst und verwendet wird.

|KundenNr|Name|Adresse|BestellNr|Bestelldatum|ArtikelNr|Artikelbezeichnung|Menge|Preis|Artikelgruppe|Rabatt
|-|-|-|-|-|-|-|-|-|-|-
|1|Klaus Huber|Berlinerstr. 1, 49377 Vechta|23|06.09.2024|1|Fernseher|1|799|Elektronik|10%
|2|Hans Meier|Goethestr. 32, 54434 Köln|42|07.09.2024|2<br>3<br>1|Monitor<br>Tastertur<br>Fernseher|2<br>1<br>1|199<br>39<br>799|Elektronik<br>Peripherie<br>Elektronik|10%
1|Klaus Huber|Berlinerstr. 1, 49377 Vechta|78|08.09.2024|4|Maus|1|19|Tiernahrung|10%
|3|Jens König|Eichenweg 43, 12433 Berlin|99|09.09.2024|5|Hundefutter|1|49|Tiernahrung|0%

## Normalform 1
### Erklärung
Elimierung von Duplikaten und Gewährleistung, dass jede Spalte nur atomare (nicht teilbare) Werte enthält. Jede Spalte sollte nur einen Wert enthalten (keine Mengen oder Listen von Werten).

### Beispiel
|KundenNr|Name|Straße|PLZ|Ort|BestellNr|Bestelldatum|ArtikelNr|Artikelbezeichnung|Menge|Preis|Artikelgruppe|Rabatt
|-|-|-|-|-|-|-|-|-|-|-|-|-
|1|Klaus Huber|Berlinerstr. 1|49377|Vechta|23|06.09.2024|1|Fernseher|1|799|Elektronik|10%
|2|Hans Meier|Goethestr. 32|54434|Köln|42|07.09.2024|2|Monitor|2|199|Elektronik|10%
|2|Hans Meier|Goethestr. 32|54434|Köln|42|07.09.2024|3|Tastertur|1|39|Peripherie|10%
|2|Hans Meier|Goethestr. 32|54434|Köln|42|07.09.2024|1|Fernseher|1|799|Elektronik|10%
1|Klaus Huber|Berlinerstr. 1|49377|Vechta|78|08.09.2024|4|Maus|1|19|Tiernahrung|10%
|3|Jens König|Eichenweg 43|12433|Berlin|99|09.09.2024|5|Hundefutter|1|49|Tiernahrung|0%

## Normalform 2
### Erklärung
Eliminierung von Redundanzen, die durch funktionale Abhängigkeit von einem Teil eines zusammengesetzten Primärschlüssels entstehen. Die Tabelle muss 1NF sein, und jedes Nicht-Schlüsselattribut muss voll funktional abhängig von jedem Primärschlüssel der Tabelle sein. Das bedeutet, Nicht-Schlüsselattribute dürfen nur von dem gesamten Primärschlüssel abhängen und nicht von Teilen davon.

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
### Erklärung
Beseitigung von Abhängigkeiten zwischen Nicht-Schlüsselattributen. Die Tabelle muss in 2NF sein, und alle Nicht-Schlüsselattribute müssen direkt von den Primärschlüsseln abhängen, nicht von anderen Nicht-Schlüsselattributen (keine transitiven Abhängigkeiten).

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


