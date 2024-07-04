# 1. Einleitung

# 2. Ziele

## 2.1 Datengrundlage eingrenzen:
* Region: Ostmitteleuropa
  * Polen
  * Slowakei
  * Tschechische Republik
  * Ungarn
* Sprachen:
  * Polnisch
  * Slowakisch
  * Tschechisch
  * Ungarisch

## 2.2 Auswahl der Artefakte
### 2.2.1 Kriterien
* Problem: ungenaue Angaben. Was tun, wenn die Sprache des Magazins bekannt ist, aber die Herkunft nicht?
* Wie beweist man, dass das Magazin genau dem (Sprach-)Raum zugeordnet werden kann?
  * Stichprobenartige Überprüfung der Ausgaben anhand der Screenshots
  * Der Titel des Magazins in entsprechender Sprache (z.B. `Paczka Tynku`)
  * Andere Quellen (Foren, Wikipedia etc.)
### 2.2.2 Vorgehensweise
1. Subset aus dem Hauptdatensatz ableiten: Filtern nach Sprachen `Language` und Ländern `Origin`
2. Anhand dieses Datensatzes die Daten zu einzelnen Ausgaben in Quelldatensätzen finden

## 2.3 Aufbereitung
### 2.3.1 Struktur des Datensatzes:
* Nachvollziehbares Schema für die Benennung der Spalten definieren
* Intuitive Gruppierung einzelner Spalten

### 2.3.2 Umgang mit fehlenden Werten
* `missing` oder `no value found`

### 2.3.3 Angaben zur Sprache
* Überprüfen anhand der Informationen auf jeweiligen Ressourcen oder Screenshots von Inhalten

#### 2.3.4 Datumsangaben:
* **ISO 8601** als Standardformat
* Verdächtige Angaben überprüfen (z.B. `01.01.1998`, wenn nur das Jahr bekannt ist)

### 2.4 Bereitstellung der Datensätze
* `mw_import_east_middle_europe_magazines_issues.csv` - für den Diskmags-Katalog auf MediaWiki-Basis:
  * Benennung der Felder nach zuvor definiertem Schema
  * Zusammenführung der Duplikate
* `east_middle_europe_magazines_issues.csv` - für Publikation:
  * Benennung der Felder nach einem speziellen Schema
  * Entsprechende Behandlung fehlender Werte
  * wird aus vorigem Datensatz abgeleitet

# 3. Beschreibung der Datensätze

### 1. Quelldaten
* Datengrundlage: [CSDB](https://csdb.dk/), [Demozoo](https://demozoo.org/), [Pouet](https://www.pouet.net/), 
[Internet Archive](https://archive.org/), [ZXPress](https://zxpress.ru/).
* Hauptdatensatz: [`mw_import_magazines.csv`](../data/source_datasets/mw_import_magazines.csv):
  * `Title` Abgeleiteter Titel des Magazins
  * `Also known as` Mögliche Schreibweisen
  * `Language` Sprachen des Magazins (Angaben größtenteils nicht überprüft)
  * `Origin` Orte, wo das Magazin erschien
  * `Start date` Erscheinungsdatum der ersten Ausgabe
  * `End date` Erscheinungsdatum der letzten Ausgabe
  * `Systems` Heimcomputersysteme, auf denen das Magazin verfasst wurde
  * `Issues` Liste aller Ausgaben
  * `Issues cleaned` Bereinigte Liste aller Ausgaben (nach zuvor definiertem Schema)
  * `Source` Die Quellen, auf welchen das Magazin zu finden ist
* Einzelne Quellen:
  * Diese sind unter dem Titel `diskmags_source_name.csv` zu finden. Die Datensätze bilden die Grundlage des Hauptdatensatzes.
  Diese befinden sich im Ordner [`data/source_datasets`](../data/source_datasets)

# 3. Methodik

## 3.1 Zuordnung eines Magazins zu einer bestimmten Region

1. Orientierung erfolgt über die Angaben im Hauptdatensatz
2. Angaben validieren:
    * Recherche im Internet
    * Herkunftsland der Gruppe (=Verfasser)

## 3.2 Zuordnung der sprachlichen Merkmale
1. Orientierung erfolgt über die Angaben im Hauptdatensatz
2. Angaben validieren:
   * Zuordnung erfolgt auf der Ebene einzelner Ausgaben
   * Jede Ausgabe anhand der Screenshots oder anderer Metadaten überprüfen
3. Falls die Ausgaben desselben Magazins in unterschiedlichen Sprachen verfasst sind, so erbt das Magazin 
all diese Merkmale.

## 3.3 Umgang mit Metadaten
### 3.3.1 Für den Import ins Mediawiki:
| Feld                 | Bedeutung                            | Werte                           | Separator |
|----------------------|--------------------------------------|---------------------------------|-----------|
| `Title`              | Der "bereinigte" Titel einer Ausgabe | single `string`                 |           |
| `Spellings`          | Mögliche Schreibweisen               | multiple `string`               | `;`       |
| `Magazine`           | Der Titel des Magazins               | single `string`                 | `;`       |
| `Release date`       | Erscheinungsdatum                    | multiple `date` (`YYYY-MM-DD)`) | `;`       |
| `Language`           | Sprachen                             | multiple `string`               | `;`       |
| `Origin`             | Origin                               | multiple `string`               | `;`       |
| `Systems`            | Systeme                              | multiple `string`               | `;`       |
| `OriginalSystemName` | Originale Namen der Systeme          | multiple `string`               | `;`       |
| `Groups`             | Verfasser                            | multiple `string`               | `;`       |
| `Sources`            | Namen der Quellen                    | multiple `string`               | `;`       |
| `Links`              | Links                                | multiple `string`               | `;`       |
### 3.2 Für den Import in Bibliothekskataloge
Es handelt sich um eine vorläufige Architektur des Datensatzes. Im Gegensatz zum Datensatz für den Import in den
Diskmags Katalog findet hier keine Zusammenführung zusammengehöriger Ausgaben statt.
