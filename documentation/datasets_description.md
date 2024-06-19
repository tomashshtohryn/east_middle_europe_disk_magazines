## Beschreibung der Datensätze

### 1. Hauptdatensatz
* Die Quellen: CSDB, Demozoo, Pouet, Internet Archive, Volko Enzyklopädie.
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

### 2. Quelldatensätze
* Quelldatensätze: als `diskmags_source_name.csv` zu finden. Die Datensätze bilden die Grundlage des Hauptdatensatzes.
Diese befinden sich im Ordner [`data`](../data):
