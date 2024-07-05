# 1. Einleitung
<!-- hier wäre es vielleicht hilfreich, noch einmal grundlegend das Projekt zu erläutern,  also was ist der Gegenstand (was sind Diskmags, was zeichnet sie aus)? Warum sind sie interessant? Was für Daten haben wir? Woher kommen diese? Was soll damit im Rahmen des Projekts passieren (Aufbereitung, Bereinigung etc, also welche Schritte und welche Zielformate: - Einpflegen in Euren Katalog, - Publikation als Forschundatensatz,  - Ausloten, ob die Daten in Bibliothekskataloge aufgenommen werden können bzw. Mapping der bestehenden Metadaten auf die Anforderungen von Bibliotheken bzw. von RDA). Die Informationen müssen nicht alle hier in die Einleitung, aber einen Überblick als Einstieg bräuchte es, denke ich. Vielleicht macht es auch mehr Sinn, die project_card.txt in die project_documentation.md zu integrieren? Sonst wird es möglicherweise redundante Informationen geben.-->
# 2. Ziele

## 2.1 Datengrundlage eingrenzen:  <!-- von was? Also was ist die Grundgesamtheit? und warum, also warum muss sie die Datengrundlage eingegrenzt werden und warum die Beschränkung auf diese Regionen und Sprachen?
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
* <!-- Wie gehst Du mit unvollständigen Angaben um, etwa, wenn nur das Jahr oder Jahr und Monat bekannt sind?-->

### 2.4 Bereitstellung der Datensätze
* `mw_import_east_middle_europe_magazines_issues.csv` - für den Diskmags-Katalog auf MediaWiki-Basis:
  * Benennung der Felder nach zuvor definiertem Schema  <!-- Schema beschreiben? Ist ja immerhin die Dokumentation hier ;-) -->
  * Zusammenführung der Duplikate <!-- wie geschieht das, nach welchem Schema? Wie wird entscheiden, welche Daten bei widersprüchlichen Angaben übernommen werden? -->
* `east_middle_europe_magazines_issues.csv` - für Publikation:
  * Benennung der Felder nach einem speziellen Schema <!-- siehe oben, wie sieht da Schema aus? -->
  * Entsprechende Behandlung fehlender Werte <!-- die da wäre? -->
  * wird aus vorigem Datensatz abgeleitet <!-- was wird daraus abgeleitet? welche Datenfelder? Unter welcher Bedingung? -->

# 3. Beschreibung der Datensätze

### 1. Quelldaten
* Datengrundlage: [CSDB](https://csdb.dk/), [Demozoo](https://demozoo.org/), [Pouet](https://www.pouet.net/), 
[Internet Archive](https://archive.org/), [ZXPress](https://zxpress.ru/).
* Hauptdatensatz: [`mw_import_magazines.csv`](../data/source_datasets/mw_import_magazines.csv):
* Datenfelder Hauptdatensatz: 
  * `Title` Abgeleiteter Titel des Magazins <!-- hier und für die anderen Datenfelder: Datentypen angeben (String, Integer, etc.); falls Standards wie ISO z. B. für Datums- oder Sprachangaben verwendet werden, ebenfalls nennen; dto. für Normvokabulare (falls zutreffend) -->
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
  Diese befinden sich im Ordner [`data/source_datasets`](../data/source_datasets)  <!-- hier ist mir der ZUsammenhang zwischen den einzelnen Dateien nicht klar. Oben wird für die Datengrundlage auf die externen Websites vewiesen, danach wir der Hauptdatensatz erwähnt. Was ist denn hier noch mit einzelnen Quellen gemeint? Ist das mglw. redundant an dieser Stelle? Der Link führt "nur" zu dem Ordner, in dem u.a. die oben genannte Datei des Hauptdatensatzes liegt -->

<!-- hier fehlt noch eine entsprechende Dokumentation der issues-Datensätze, oder? -->

# 3. Methodik

## 3.1 Zuordnung eines Magazins zu einer bestimmten Region

1. Orientierung erfolgt über die Angaben im Hauptdatensatz (Datenfeld "Origin")
2. Angaben validieren:
    * Recherche im Internet
    * Herkunftsland der Gruppe (=Verfasser) <!-- werden bislang nicht genannt, etwa bei den Datenfeldern des Hauptdatensatzes; daher wäre hier anzugeben, woher diese Informationen kommen -->

## 3.2 Zuordnung der sprachlichen Merkmale
1. Orientierung erfolgt über die Angaben im Hauptdatensatz (Datenfeld "Language")
2. Angaben validieren:
   * Zuordnung erfolgt auf der Ebene einzelner Ausgaben  
   * Jede Ausgabe anhand der Screenshots oder anderer Metadaten überprüfen
3. Falls die Ausgaben desselben Magazins in unterschiedlichen Sprachen verfasst sind, so erbt das Magazin 
all diese Merkmale.

## 3.3 Umgang mit Metadaten
### 3.3.1 Für den Import ins Mediawiki:  <!-- in der TAbelle hier stehen die Datenfelder des MediaWikis? Oder muss die TAbelle noch an die Datenfelder oben angeglichen werden? (etwa bei 'Spellings' = 'Also known as'? Was ist mit den Feldern, die oben keine Entsprechung haben, etwa 'OriginalSytemName'? -->
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
