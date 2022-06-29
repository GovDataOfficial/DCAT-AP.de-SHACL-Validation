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

### Was wird überprüft?
 - Min- und Max-Kardinalitäten, damit auch Pflichteigenschaften
 - Verwendung von Literals und ihren Typen
 - Verwendung von URIs, wenn als Ziel eine Klasse erwartet wird
 - Typen von Klassen, wenn Regeln existieren, wie die Klassen aufgebaut sein müssen
 - Verwendung der korrekten kontrollierten Vokabulare
 - Warnung bei der Verwendung von `deprecated`-Eigenschaften

### Welche Klassen werden nicht geprüft?
 - Kategorie
 - Kategorienschema
 - Lizenzdokument (da kontrolliertes Vokabular genutzt werden muss)

### Offene Punkte
 - ausführliches Testing
 - Typen-Prüfung (z.B. `xsd:date`) funktioniert nicht
 - Wechsel (für manche Eigenschaften) auf IRIorBlankNode?
 - wird eine IRI eines CV verlangt, kann man die Shapes "täuschen", in dem man eine BlankNode mit dem richtigen skos:inScheme-Attribut angibt.


* * *


## DCAT-AP.de 2.0 - GovData (TBD)
 - Verwendung von URIs, wenn als Ziel eine URI verlangt wird und sinnvoll ist (z.B. foaf:page)
 - Sinnvolle Erweiterung: Eigenschaften entweder ein Literal oder eine URL sein zu lassen, z.B.: dct:conformsTo, da nur diese im Portal angezeigt werden können
 - Konventionen
 - Besonders empfohlene Eigenschaften


* * *


## Weitere Informationen
Feedback gerne als GitHub Issue oder per E-Mail an info@govdata.de.  

Bisherige Inhalte wurden in die Datei [README_v1X.md](README_v1X.md) verschoben.

© CC BY 4.0 ']init[ AG für GovData'  
