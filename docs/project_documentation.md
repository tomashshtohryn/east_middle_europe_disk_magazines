# 1. Einleitung

Diskettenmagazine, auch bekannt als *Diskmags*, sind elektronische Publikationen multimedialer Natur, deren primärer
Zweck in der Unterhaltung und Verbreitung des Wissens rund um die ersten Heimcomputersysteme bestand. Die ersten 
Diskmags erschienen in den frühen 1980er Jahren und waren bis hin zur ersten Dekade des 21. Jahrunderts als eine 
alternative Form der damals üblichen Periodika besonders beliebt.<br>
Aufgrund ihrer Bauweise waren die Disketten nicht besonders langlebig. Demzufolge griffen ihre Verfasser oder 
Enthusiasten oft auf Werkzeuge zur Übertragung der Inhalte von Diskmags in ein virtuelles Format zurück, um so die
Verfügbarkeit dieser Journale aufrechtzuerhalten. Derzeit sind die bekanntesten Reihen auf zahlreichen Ressourcen als
digitale Abbilder zu finden. Diese lassen sich innerhalb einer dafür geeigneten Softwareumgebung emulieren.<br>
Die Diskmags lassen sich zweifelsohne als Artefakte der damaligen digitalen Kultur betrachten. Deren Inhalte reichen von
Artikeln rund um das Programmieren und die kreative Tätigkeit der Demoszene bis hin zu Dienstprogrammen und zahlreichen
Spielen. Demzufolge ist ihre Erforschung ein wichtiger Schritt, um das kulturelle Erbe dieser Kultur und ihrer Medien erhalten 
zu können.<br>

# 2. Ziel des Projekts

Im Rahmen eines Forschungsprojekts zur Erhaltung der Diskmags als eine Ausprägung der frühen digitalen Kultur wurde
eine umfassende Katalogisierung aller frei verfügbaren Exemplare unternommen. Das Ergebnis ist ein wikibasierter
[Katalog](https://diskmags.de), in dem die Metadaten zu mehr als 2000 Zeitschriften zu unterschiedlicher Thematik und für
unterschiedliche Heimcomputersysteme zu finden sind.<br>
Im Laufe der Datenerfassung wurde auch eine Reihe von Magazinen aus dem ostmitteleuropäischen Raum
entdeckt. Die entsprechenden Metadaten fungieren als eine wichtige Quelle, um die Besonderheiten
der frühen digitalen Kultur dieser Region zu erforschen.<br>
Das Ziel dieses Projekts ist es, diese Informationen aufzubereiten und zwecks der Weiterverwendung 
durch interessierte Forschende zu veröffentlichen. Hierbei liegt der Fokus auf allen Ländern, die
zum ostmitteleuropäischen Raum gehören.<br>
Damit die Qualität dieser (Forschungs-)Daten sichergestellt wird, erfolgt die Bearbeitung des Datensatzes unter der Betreuung
von FDM-Expert:Innen vom Herder-Institut für historische Ostmitteleuropaforschung in Marburg.
Das Ergebnis des Vorhabens sind die Datensätze im CSV-Format, die nach der Aufbereitung 
folgendermaßen veröffentlicht wurden:
1. Publikation des Datensatzes im internationalen Katalog der Diskettenmagazine
2. Veröffentlichung in einem geeigneten Repositorium

# 3. Datengrundlage

## 3.1 Ausgaben
Die Grundlage für die Durchführung des Projekts bilden die Datensätze, die im Laufe
des bereits abgeschlossenen Diskmags-Projekts mittels der Web-Scraping-Bibliotheken 
`Selenium` und `Scrapy` erzeugt wurden. Diese sind im Ordner [`source_data`](../data/source_data) zu finden.<br>
Jeder darin enthaltene Datensatz repräsentiert eine der insgesamt 5 Quellen: [CSDB](https://csdb.dk/), [Demozoo](https://demozoo.org/), [Pouet](https://www.pouet.net/), 
[Internet Archive](https://archive.org/), [ZXPress](https://zxpress.ru/). Zur Vervollständigung
des Datenbestands wurde zudem die Enzyklopädie der Diskettenmagazine von Claus-Dieter Volko
(2012) berücksichtigt.
Die Datensätze sind im CSV-Format gespeichert und enthalten folgende Informationen
als Werte des Datentyps `string`:
* Titel der jeweiligen Ausgabe
* Titel des Magazins
* Das für das Auslesen oder Beschreiben der Diskette geeignetes Heimcomputersystem
* Die Namen der Verfasser:Innen
* Erscheinungsdatum nach deutscher Schreibweise (`TT.MM.JJJJ`)
* Der Link zur Ausgabe auf der jeweiligen Webressource
* Weiterführende URLs

> Sofern die jeweilige Ressource über unvollständige Informationen zu einer Diskmag-Ausgabe
verfügt, so wurde es durch einen fehlenden Wert gekennzeichnet, der bei der Betrachtung des
Datensatzes als eine leere Zelle zu sehen ist.

## 3.2 Magazine

Einen Überblick über alle Magazine bietet der Datensatz 
[`mw_import_magazines.csv`](../data/source_data/mw_import_magazines.csv). Dieser ist ebenfalls
im CSV-Format gespeichert und hat folgende Struktur:
* Titel des Magazins (abgeleitet aus den Titeln zugehöriger Ausgaben)
* Alternative Titel (*AKA*)
* Sprache des Magazins (ermittelt infolge stichprobenartiger Recherche)
* Land (ermittelt infolge stichprobenartiger Recherche)
* Datum der ersten Ausgabe
* Datum der letzten Ausgabe
* Kompatibles Heimcomputersystem
* Liste aller Ausgaben im Rohformat
* Bereinigte Liste aller Ausgaben ohne Duplikate
* Quelle, wo die Ausgaben dieses Magazins zu finden sind

> Zur Vermeidung der Probleme mit dem Auslesen und der Verarbeitung dieses Datensatzes wurde
im Falle multipler Werte das Semikolon-Zeichen (`;`) als Separator verwendet.
----
> Warnung: Manche Magazine, die in diesem Datensatz aufgeführt werden,
enthalten sensible Inhalte. Weiterführende Informationen zur Kennzeichnung
solcher Inhalte findet man im Abschnitt [Umgang mit sensiblen Inhalten](#433-kennzeichnung-der-ausgaben-mit-sensiblen-inhalten).

# 4. Methodik
## 4.1 Ableitung der Teilmenge aller Magazine aus ostmitteleuropäischem Raum
Mithilfe der Angaben, die der Datensatz [`mw_import_magazines.csv`](../data/source_data/mw_import_magazines.csv)
liefert, sollen alle Magazine ausgewählt werden, die sowohl aus dem Kerngebiet Osteuropas stammen
als auch aus den Ländern, die nur gelegentlich zu dieser Region zählen.
* **Schritt 1:** Auswahl der Magazine nach Land (Feld `Origin`)
* **Schritt 2:** Sofern es keine Angaben zum Herkunftsland der Zeitschrift gibt, erfolgt
die Auswahl nach der Sprache jedes ostmitteleuropäischen Landes. (Feld `Language`)<br>
> Es ist zu beachten, dass diese Magazine zum Teil mehrsprachig sind.

Es lässt sich feststellen, dass die Suche eine Liste mit folgenden Ländern ergibt: 
Polen, Tschechische Republik, Ungarn, Slowenien. Die Liste wird anschließend ergänzt,
indem man die entsprechenden Sprachen einschließlich englischsprachiger Reihen
hinzufügt. Das Ergebnis ist der Datensatz [`east_middle_europe_magazines.csv`](../data/target_data/east_middle_europe_magazines.csv),
 der die Teilmenge dieser Magazine darstellt.<br>

## 4.2 Erstellung des Datensatzes aller Ausgaben
Basierend auf der Liste aller Länder und Sprachen wird ein quellenübergreifender Datensatz erstellt,
indem alle 5 Datensätze mit Metadaten zu jeweiligen Ausgaben zusammengeführt werden. Dieser ist
unter dem Namen [`east_middle_europe_magazines_issues.csv`](../data/target_data/east_middle_europe_magazines_issues.csv)
zu finden und hat folgende Struktur:

| Feld                       | Beschreibung                                   | Datentyp |
|----------------------------|------------------------------------------------|----------|
| `issue_title`              | Der "vereinheitlichte Titel" der Ausgabe       | `str`    |
| `orig_issue_title`         | Der ursprüngliche Titel der Ausgabe            | `str`    |
| `magazine_title`           | Der Titel des Magazins                         | `str`    |
| `origin`                   | Das Land                                       | `str`    |
| `language`                 | Sprache(n)                                     | `str`    |
| `release_date`             | Erscheinungsdatum (`TT.MM.JJJJ`)               | `str`    |
| `system_name_standardized` | Standardisierter Name des Heimcomputersystems  | `str`    |
| `system_name`              | Ursprünglicher Name des Heimcomputersystems    | `str`    |
| `editor`                   | Der Name bzw. die Namen der Herausgebergruppen | `str`    |
| `source`                   | Die Quelle                                     | `str`    |
| `link`                     | Der Link zur Ausgabe                           | `str`    |
| `disclaimer`               | Anmerkung zum Inhalt des Magazins              | `str`    |


## 4.3 Aufbereitung
### 4.3.1 Zuteilung vereinheitlichten Titels einer Ausgabe
Damit die Ausgabe eindeutig identifizierbar wird, ist es erforderlich, eine eindeutige
Kennung im Feld `issue_title` zu erstellen. Dies erfolgt anhand des Titels des Magazins
einschließlich der Nummer der jeweiligen Ausgabe mit dem Präfix *No.*.
> Beispiel: Die erste Ausgabe des Magazins *AmigaCS*, die auf der Ressource *Pouet*
unter dem Titel *AmigaCS #1* zu finden ist, erhält folgende Kennung: `AmigaCS No.1`

> Wichtig: Es gibt auch Magazine, die zwar unterschiedlich sind, aber unter demselben
Titel erschienen. Zu diesem Zweck wurden ihre Titel durch eine entsprechende Nummer,
beginnend mit 1, ergänzt. In diesem Fall ist der "bereinigte" Titel der Ausgabe
durch diese Nummer in runden Klammern zu vervollständigen (z.B. `Always (2) No.19`).

### 4.3.2 Überprüfung der Angaben zum Herkunftsland und der Sprache des Magazins
Da die Informationen zur Herkunft und Sprache von dem in der Tabelle 
[`east_middle_europe_magazines.csv`](../data/target_data/east_middle_europe_magazines.csv)
aufgelisteten Magazin "geerbt" wurden, wird jede einzelne Ausgabe überprüft. Dies
wird ermittelt, in dem die Seite der Ausgabe auf der jeweiligen Ressource aufgerufen und
manuell untersucht wird. Behilflich sind in diesem Fall die hochgeladenen Screenshots der
Inhalte, die insbesondere die Informationen über die sprachlichen Besonderheiten der Ausgabe
liefern können. Für die Ermittlung der geografischen Merkmale werden die Informationen zur
Herkunft der jeweiligen Herausgebergruppe aufgerufen. Sollten die Angaben im Datensatz und 
im Internet nicht übereinstimmen, so wird es korrigiert, indem die 
richtigen Werte eingetragen werden.<br>
Die Sprachen und Länder werden als Kürzel eingetragen. Dabei orientiert man sich an den
Richtlinien des [ZDB-Formats](https://zeitschriftendatenbank.de/erschliessung/zdb-format). 
In diesem Sinne wird für eine Sprache ein Kürzel aus 3 Buchstaben
verwendet, während für ein Land die Kombination aus 3 Großbuchstaben eingetragen wird. Beispiel:
ein polnisches Magazin mit polnischsprachigen Inhalten erhält folgende Werte:
* `PL` für die Identifikation des Herkunftslandes
* `pol` für die Erfassung der sprachlichen Merkmale

> Bei mehrsprachigen Ausgaben werden alle Sprachen in alphabetischer Reihenfolge eingetragen.

> Sofern für die jeweilige Ausgabe keine Screenshots hochgeladen wurden, 
wird ein fehlender Wert eingetragen.

> Falls sich während der Überprüfung dieser Angaben herausstellt, dass der Link zur
Ausgabe nicht mehr aufgerufen werden kann, so ist es entsprechend zu kennzeichnen.

### 4.3.3 Kennzeichnung der Ausgaben mit sensiblen Inhalten
Im Hinblick auf die Tatsache, dass das Verfassen und Herausgeben der Diskmags von
Angehörigen der jeweiligen Communities kaum überprüft wurde, können manche Ausgaben
sexistische, rassistische und andere sensible Äußerungen oder Bilder enthalten. Für einen sicheren 
Umgang mit den im Rahmen dieses Projekts zu bearbeitenden Forschungsdaten müssen solche
Inhalte entsprechend gekennzeichnet werden.<br>
Als Grundlage für das Kennzeichnen solcher Inhalte eignet sich 
das  [*Handbuch zur Erstellung diskriminierungsfreier Metadaten für historische 
Quellen und Forschungsdaten* (2024[)]()](https://maehr.github.io/diskriminierungsfreie-metadaten/) von Moritz Mähr und Noëlle Schnegg. In Bezug auf die
Thematik solcher Inhalte lassen sich folgende Vermerke in Betracht ziehen:
* `Erotik`
* `Ideologie`
* `Körper`
* `Nationalsozialismus`
* `Sexismus`
* `Sucht`
* `Tier`
Andere Schlagwörter, die im Handbuch nicht aufgeführt sind:
* `Anarchismus`

> Es ist wichtig zu betonen, dass in diesem Datensatz keine vollumfängliche Kennzeichnung
unsicherer Inhalte garantiert werden kann. Vor allem liegt es daran, dass die vorhanden
Screenshots nur einen kleinen Anteil aller Inhalte repräsentieren, weshalb keine genaue
Einstufung erfolgen kann.

### 4.3.4 Datumsangaben
Ursprünglich wurden die Datumsangaben nach deutscher Schreibweise eingetragen. Ist das
Datum unvollständig, so wurde neben dem Jahr der erste Tag oder Monat als 
Erscheinungsdatum hinzugefügt.<br>
Zur Erhöhung der Plausibilität der Daten sollen alle Angaben zum Erscheinungsdatum
erneut überprüft und nach einem in der Forschung üblichen Standard gespeichert werden.
Hierfür eignet sich das Format *ISO 8601*. Demnach soll das Datum folgendermaßen
eingetragen werden: `JJJJ-MM-TT`.<br>
Falls das Datum unvollständig ist und nur aus dem Jahr oder dem Jahr und dem Monat
besteht, so werden nur die vorhandenen Informationen eingefügt.

> Beispiel: Es ist bekannt, dass die 25.Ausgabe des Magazins *Always* im September 1995
erschienen ist. Somit muss folgendes Datum eingetragen werden: `1995-09`.

### 4.3.5 Heimcomputersysteme und -familien
Die Ressourcen, die als Grundlage für die Zusammenstellung der Quelldatensätze dienen,
bieten teilweise unterschiedliche Angaben zur Plattform der jeweiligen Magazine.
Dabei handelt es sich of um dieselben Systeme, die allerdings je nach Ressource
unterschiedlich genannt werden. Zu diesem Zweck wird im Feld `system_name_standardized`
der standardisierte Name des Systems eingetragen. Dies erfolgt auf der Grundlage des
in dem Datensatz [`umbenennung-systeme.csv`](../data/source_data/umbenennung-systeme.csv)
aufgeführten Mappings.

### 4.3.6 Umgang mit fehlenden Werten
Alle Zellen, die keine Werte enthalten, sind als fehlende Werte zu bezeichnen. Um die
Nachvollziehbarkeit der Daten aufrechtzuerhalten, sollen diese durch einen Punkt (`.`)
gekennzeichnet werden.

# 5. Veröffentlichung des Datensatzes im Diskmags-Katalog
Die im Laufe des Projekts aufbereiteten Daten sollen zudem in den
internationalen Katalog der Diskettenmagazine eingespielt werden.
Hierfür steht die [Extension](https://www.mediawiki.org/wiki/Extension:Data_Transfer) zum Hochladen von
Datensätzen im CSV-Format zur Verfügung.

Dem Datenmodell des Diskmags-Katalogs liegen folgende Entitäten
zugrunde:
* Magazin (`Magazine`): enthält die Informationen über das Magazin
* Ausgabe (`Issue`): enthält die Informationen über eine konkrete Ausgabe

In dieser Hinsicht ist es erforderlich, die Datensätze der Magazine
und Ausgaben einem zusätzlichen Aufbereitungsschritt zu unterziehen:
1. Entsprechende Benennung der Spalten nach dem in der Wiki-Instanz definierten Schema
2. Zusammenführung der wiederholenden Zeilen im Datensatz `east_middle_europe_magazines_issues.csv`.
Dabei werden alle Zeilen überprüft, indem man die Einträge findet,
die zwar eine Ausgabe repräsentieren, aber aus unterschiedlichen Quellen
stammen und zum Teil unterschiedliche Angaben enthalten. Da das Mediawiki
die Erstellung der Seiten mit selben Titeln nicht zulässt, ist die Zusammenführung
dieser Einträge ein wichtiger Schritt.

Das Ergebnis dieses Schritts sind folgende Datensätze, die speziell
für das MediaWiki-Projekt aufbereitet wurden:
* [`mw_import_east_middle_europe_magazines.csv`](../data/target_data/mw_import_east_middle_europe_magazines.csv):
Für die Erstellung der Seiten von jeweiligen Magazinen
* [`mw_import_east_middle_europe_magazines_issues.csv`](../data/target_data/mw_import_east_middle_europe_magazines_issues.csv):
Für die Erstellung der Seiten einzelner Ausgaben

Diese sind nach UTF-16-Standard kodiert. Zunächst wird jeder Datensatz hochgeladen,
indem für jeden Eintrag eine separate Seite erzeugt wird. Sobald der Prozess abgeschlossen ist,
wird anhand einer speziellen Abfrage eine [Übersicht](https://diskmags.de/index.php?title=East-Central_Europe) erstellt, in der die Auflistung all dieser Magazine
samt einzelner Ausgaben aufgerufen werden kann.
