## Vorhaben

### 1. Datengrundlage eingrenzen:
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

### 2. Auswahl der Artefakte
#### 2.1 Kriterien
* Problem: ungenaue Angaben. Was tun, wenn die Sprache des Magazins bekannt ist, aber die Herkunft nicht?
* Wie beweist man, dass das Magazin genau dem (Sprach-)Raum zugeordnet werden kann?
  * Stichprobenartige Überprüfung der Ausgaben anhand der Screenshots
  * Der Titel des Magazins in entsprechender Sprache (z.B. `Paczka Tynku`)
  * Andere Quellen (Foren, Wikipedia etc.)
#### 2.2 Vorgehensweise
1. Subset aus dem Hauptdatensatz ableiten: Filtern nach Sprachen `Language` und Ländern `Origin`
2. Anhand dieses Datensatzes die Daten zu einzelnen Ausgaben in Quelldatensätzen finden

### 3. Aufbereitung
#### 3.1 Struktur des Datensatzes:
* Nachvollziehbares Schema für die Benennung der Spalten definieren
* Intuitive Gruppierung einzelner Spalten

#### 3.2 Umgang mit fehlenden Werten
*

#### 3.3 Datumsangaben:
* **ISO 8601** als Standardformat
* Verdächtige Angaben überprüfen (z.B. `01.01.1998`, wenn nur das Jahr bekannt ist)
