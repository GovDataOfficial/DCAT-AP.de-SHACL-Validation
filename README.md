# DCAT-AP.de SHACL-Validation (BETA)

|  :warning: Hinweis zur aktuellen Entwicklung :warning:  |
|:--------------------------------------------------------|
| Die DCAT-AP.de SHACL-Validation wurde mit Blick auf die [DCAT-AP.de 2.0 Spezifikation](https://www.dcat-ap.de/def/dcatde/2.0/spec/) neu erstellt. <br> Die vorliegende Version muss noch ausgiebig gestestet werden. Wenn Sie Fehler entdecken, dann freuen wir uns über Ihr Feedback! |

## DCAT-AP.de 2.0 - Spezifikation (BETA)
Die SEMIC stellt ihren eigenen [DCAT-AP-Validator](https://www.itb.ec.europa.eu/shacl/dcat-ap/upload) zur Verfügung, der zuverlässig funktioniert.

Der deutsche Validator verwendet die verpflichtenden Regeln der SEMIC und reichert sie mit deutschen Fehlernachrichten an. Dazu werden folgende Dateien verwendet:  
- https://github.com/init-dcat-ap-de/DCAT-AP/blob/2.1.1-draft/releases/2.1.1/dcat-ap_2.1.1_shacl_shapes.ttl  
- https://github.com/GovDataOfficial/DCAT-AP.de-SHACL-Validation/blob/master/validator/resources/v2.0/shapes/dcat-ap-spec-german-messages.ttl

Die folgende Datei fügt zu den DCAT-AP-SHACL-Shapes deutsche Regeln hinzu, so dass DCAT-AP.de 2.0 geprüft wird. Dafür werden zum Teil auch widersprüchliche DCAT-AP-SHACL-Shapes deaktiviert:  
- https://github.com/GovDataOfficial/DCAT-AP.de-SHACL-Validation/blob/master/validator/resources/v2.0/shapes/dcat-ap-spec-german-additions.ttl

Weitere externe Quellen, wie Ontologien, deren Kontext relevant sind oder kontrollierte Vokabulare, werden über hier importiert:
- https://github.com/GovDataOfficial/DCAT-AP.de-SHACL-Validation/blob/master/validator/resources/v2.0/shapes/dcat-ap-de-imports.ttl

### Prüfungen
 - Verwendung aller Pflichteigenschaften
 - Min- und Max-Kardinalitäten
 - Verwendung (getypter) Literals, wenn zutreffend
 - Verwendung von URIs, wenn als Ziel eine Klasse erwartet wird
 - Verwendung von URIs, wenn als Ziel eine beliebige Webadresse erwartet wird
 - Verwendung der korrekten kontrollierten Vokabulare
 - Typen von Klassen, wenn Regeln existieren, wie die Klassen aufgebaut sein müssen
 - Warnung bei der Verwendung von `deprecated`-Eigenschaften

### Keine Prüfungen
 - Kategorie
 - Kategorienschema
 - Lizenzdokument (da kontrolliertes Vokabular genutzt werden muss)


* * *


## DCAT-AP.de 2.0 - Spezifikation & Konventionen (BETA)

Dieses Profil prüft alles, was DCAT-AP.de SHACL-Validation (BETA) prüft. Zusätzlich:

### Prüfung von Konventionen
 - `K01:   ` `dcat:contactPoint`: Kontaktinformationen MÜSSEN mindestens Angaben zur Email (vcard:hasEmail) oder einen Link zum Kontaktformular oder Chatbot (vcard:hasURL) enthalten.
 - `K12&13:` `dcat:Dataset`: `dcatde:contributorID` MUSS verwendet werden und DARF nur genau einmal eine IRI aus http://dcat-ap.de/def/contributors/ verwenden.
 - `K36:   ` `dcat:Dataset`: `dct:publisher` MUSS verwendet werden.
 - `K30:   ` `dcat:Dataset`: `dcat:theme`: Zur Steigerung der Metadatenqualität wird die Angabe von Kategorien empfohlen.
 - `K31:   ` `dcat:Distribution`: `dct:license` MUSS eine IRI aus http://dcat-ap.de/def/licenses/ verwenden.
 - `K32:   ` `dcat:Distribution`: `dct:format` MUSS eine IRI aus dem  EU Vokabular 'File Type' verwenden.

### Prüfung besonders empfohlener Eigenschaften
 - `dcat:Dataset`: `dcat:distribution`: Es wird empfohlen, dass jedes Dataset über eine Distribution verfügt.
 - `dcat:Dataset`: `dcat:keyword`: Zur Steigerung der Metadatenqualität wird die Angabe von Schlagworten empfohlen.
 - `dcat:Dataset`: `dcat:landingPage`: Zur Steigerung der Metadatenqualität wird die Angabe der ursprünglichen Webseite empfohlen.
 - `dcat:Dataset`: `dct:issued`: Zur Steigerung der Metadatenqualität wird die Angabe des Veröffentlichungsdatums empfohlen.
 - `dcat:Distribution`: `dct:title`: Es wird empfohlen, dass jede Distribution über einen dct:title verfügt.


### Prüfung im Rahmen der Dublettenprüfung
 - `dcat:Dataset`: Ggf. MUSS `dct:identifier` zur Dublettenprüfung verwendet werden.
 - `dcat:Dataset`: Ggf. MUSS `dct:modified` zur Dublettenprüfung verwendet werden.


* * *

## GovData MQA/Dashboard

Diese Profile prüfen Eigenschaften, die auch im GovData-Dashboard zur Metadatenqualität angezeigt werden.

* * *


## Weitere Informationen
Feedback gerne als GitHub Issue oder per E-Mail an info@govdata.de.  

Bisherige Inhalte wurden in die Datei [README_v1X.md](README_v1X.md) verschoben.

© CC BY 4.0 ']init[ AG für GovData'  
