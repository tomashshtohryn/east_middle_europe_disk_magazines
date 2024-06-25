## Beschreibung der Datensätze

### 1. Quelldaten
* Datengrundlage: [CSDB](https://csdb.dk/), [Demozoo](https://demozoo.org/), [Pouet](https://www.pouet.net/), 
[Internet Archive](https://archive.org/), [ZXPress](https://zxpress.ru/).
* Hauptdatensatz: [`mw_import_magazines.csv`](../data/mw_import_magazines.csv):
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
