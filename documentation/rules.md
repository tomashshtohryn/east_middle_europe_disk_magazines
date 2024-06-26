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
### 3.1 Für den Import ins Mediawiki:
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