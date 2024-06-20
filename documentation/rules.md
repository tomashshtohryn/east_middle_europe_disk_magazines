# Regeln

## 1. Zuordnung eines Magazins zu einer bestimmten Region

1. Orientierung erfolgt über die Angaben im Hauptdatensatz
2. Angaben validieren:
    * Recherche im Internet
    * Herkunftsland der Gruppe (=Verfasser)

## 2. Zuordnung der sprachlichen Merkmale
1. Orientierung erfolgt über die Angaben im Hauptdatensatz
2. Angaben validieren:
   * Zuordnung erfolgt auf der Ebene einzelner Ausgaben
   * Jede Ausgabe anhand der Screenshots oder anderer Metadaten überprüfen
3. Falls die Ausgaben desselben Magazins in unterschiedlichen Sprachen verfasst sind, so erbt das Magazin 
all diese Merkmale.

## 3. Umgang mit Metadaten
* Die Metadaten zu ausgewählten Ausgaben werden in einer separaten CSV-Tabelle gespeichert. Bei multiplen Werten ist
ein Semikolon zu setzen:

| Feld                 | Bedeutung                            | Werte             |
|----------------------|--------------------------------------|-------------------|
| `Title`              | Der "bereinigte" Titel einer Ausgabe | single `string`   |
| `Spellings`          | Mögliche Schreibweisen               | multiple `string` |
| `Magazine`           | Der Titel des Magazins               | single `string`   |
| `Release date`       | Erscheinungsdatum                    | multiple `date`   |
| `Source`             | Quellen                              | multiple `string` |
| `Language`           | Sprachen                             | multiple `string` |
| `Origin`             | Origin                               | multiple `string` |
| `Systems`            | Systeme                              | multiple `string` |
| `OriginalSystemName` | Originale Namen der Systeme          | multiple `string` |
| `Groups`             | Verfasser                            | multiple `string` |
| `Links`              | Links                                | multiple `string` |


* Die Benennung der Ausgaben:
  * Das Feld `Title` enthält den Titel des Magazins und den Zusatz mit deren Nummer (`No.` oder `number-year`)
  * Die Originalen Titel einer Ausgabe werden im Feld `issue_orig` gespeichert