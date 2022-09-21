# DCAT-AP.de SHACL-Validation

|  :warning: Hinweis zur aktuellen Entwicklung :warning:  |
|:--------------------------------------------------------|
| Die [DCAT-AP.de SHACL-Validation](https://www.itb.ec.europa.eu/shacl/dcat-ap.de/upload) wurde mit Blick auf die [DCAT-AP.de 2.0 Spezifikation](https://www.dcat-ap.de/def/dcatde/2.0/spec/) neu erstellt. <br> Wenn Sie Fehler entdecken, dann freuen wir uns über Ihr Feedback! |

## DCAT-AP.de 2.0 - Spezifikation
Die SEMIC stellt ihren eigenen [DCAT-AP-Validator](https://www.itb.ec.europa.eu/shacl/dcat-ap/upload) zur Verfügung, der zuverlässig funktioniert.

Der deutsche Validator verwendet die verpflichtenden Regeln der SEMIC und reichert sie mit deutschen Fehlernachrichten an. Dazu werden folgende Dateien verwendet:  
- https://github.com/init-dcat-ap-de/DCAT-AP/blob/2.1.1-draft/releases/2.1.1/dcat-ap_2.1.1_shacl_shapes.ttl  
- https://github.com/GovDataOfficial/DCAT-AP.de-SHACL-Validation/blob/master/validator/resources/v2.0/shapes/dcat-ap-spec-german-messages.ttl

Die folgende Datei fügt zu den DCAT-AP-SHACL-Shapes deutsche Regeln hinzu, so dass DCAT-AP.de 2.0 geprüft wird. Dafür werden zum Teil auch widersprüchliche DCAT-AP-SHACL-Shapes deaktiviert:  
- https://github.com/GovDataOfficial/DCAT-AP.de-SHACL-Validation/blob/master/validator/resources/v2.0/shapes/dcat-ap-spec-german-additions.ttl

Weitere externe Quellen, wie Ontologien, deren Kontext relevant sind oder kontrollierte Vokabulare, werden durch diese Datei importiert:
- https://github.com/GovDataOfficial/DCAT-AP.de-SHACL-Validation/blob/master/validator/resources/v2.0/shapes/dcat-ap-de-imports.ttl

### Prüfungen
 - Verwendung aller Pflichteigenschaften
 - Min- und Max-Kardinalitäten
 - Verwendung (getypter) Literals, wenn zutreffend
 - Verwendung von URIs, wenn als Ziel eine Klasse erwartet wird
 - Verwendung von URIs, wenn als Ziel eine beliebige Webadresse erwartet wird
 - Verwendung der korrekten kontrollierten Vokabulare
 - Warnung bei der Verwendung von `deprecated`-Eigenschaften

Ob das Objekt einer Eigenschaft die von DCAT-AP(.de) vorgegebene Klasse hat, wird geprüft, wenn der Aufbau des Objekts für den Anwendungsfall "Anlieferung an ein Metadatenportal" entscheidend ist.
Dies betrifft die DCAT-AP-Kernklassen und Eigenschaften `dcat:catalog`, `dcat:dataset`, `dcat:service`, `dcat:record` und `dcat:distribution` sowie die Eigenschaften, die auf z.B. `foaf:Agent`, `dct:PeriodOfTime` oder `dct:Location` verweisen.

Für die Eigenschaften `adms:sample`, `dct:source`, `dct:hasVersion`, `dct:isVersionOf`, `dct:hasPart` und `dct:isPartOf` wird davon ausgegangen, dass deren Objekte nicht im Kern der Validierung stehen. Daher wird lediglich gewarnt, wenn sie nicht die korrekte Klasse haben.


### Keine Prüfungen
 - Kategorie (da kontrolliertes Vokabular genutzt werden muss)
 - Kategorienschema (da kontrolliertes Vokabular genutzt werden muss)
 - Lizenzdokument (da kontrolliertes Vokabular genutzt werden muss)


* * *


## DCAT-AP.de 2.0 - Spezifikation & Konventionen

Dieses Profil prüft alles, was DCAT-AP.de SHACL-Validation prüft. Zusätzlich:

### Prüfung von Konventionen
 - `K01: dcat:contactPoint`: Kontaktinformationen MÜSSEN mindestens Angaben zur Email (vcard:hasEmail) oder einen Link zum Kontaktformular oder Chatbot (vcard:hasURL) enthalten.
 - `K12&13: dcat:Dataset`: `dcatde:contributorID` MUSS verwendet werden und DARF nur genau einmal eine IRI aus http://dcat-ap.de/def/contributors/ verwenden.
 - `K36: dcat:Dataset`: `dct:publisher` MUSS verwendet werden.
 - `K30: dcat:Dataset`: `dcat:theme`: Zur Steigerung der Metadatenqualität wird die Angabe von Kategorien empfohlen.
 - `K31: dcat:Distribution`: `dct:license` MUSS eine IRI aus http://dcat-ap.de/def/licenses/ verwenden.
 - `K32: dcat:Distribution`: `dct:format` MUSS eine IRI aus dem  EU Vokabular 'File Type' verwenden.

### Prüfung besonders empfohlener Eigenschaften
 - `dcat:Dataset`: `dcat:distribution`: Es wird empfohlen, dass jedes Dataset über eine Distribution verfügt.
 - `dcat:Dataset`: `dcat:keyword`: Zur Steigerung der Metadatenqualität wird die Angabe von Schlagworten empfohlen.
 - `dcat:Dataset`: `dcat:landingPage`: Zur Steigerung der Metadatenqualität wird die Angabe der ursprünglichen Webseite empfohlen.
 - `dcat:Dataset`: `dct:issued`: Zur Steigerung der Metadatenqualität wird die Angabe des Veröffentlichungsdatums empfohlen.
 - `dcat:Distribution`: `dct:title`: Es wird empfohlen, dass jede Distribution über einen dct:title verfügt.

### Prüfung im Rahmen der Dublettenprüfung
 - `dcat:Dataset`: Ggf. MUSS `dct:identifier` zur Dublettenprüfung verwendet werden.
 - `dcat:Dataset`: Ggf. MUSS `dct:modified` zur Dublettenprüfung verwendet werden.

### Prüfung auf (ausgewählte) sinnvolle Ranges
Die Auswahl erfolgte mit Blick auf die Verarbeitung im GovData-Frontend.
 - `dcat:Dataset`: **IRIorLiteral**: `dct:conformsTo`, `dct:accessRights`, `dct:provenance`
 - `dcat:Dataset`: **IRI**: `prov:wasGeneratedBy`, `dcat:landingPage`, `foaf:page`
 - `dcat:Catalog`: **IRIorLiteral**: `dct:rights`
 - `dcat:Catalog`: **IRI**: `foaf:homepage`
 - `dcat:DataService`: **IRIorLiteral**: `dct:accessRights`
 - `dcat:Distribution`: **IRIorLiteral**: `dct:conformsTo`, `dct:rights`
 - `dcat:Distribution`: **IRI**: `foaf:page`, `odrl:hasPolicy`
 - `dcat:CatalogRecord`: **IRIorLiteral**: `dct:conformsTo`

* * *

## GovData MQA/Dashboard

Diese Profile prüfen Eigenschaften, die auch im GovData-Dashboard zur Metadatenqualität angezeigt werden.

* * *


## Weitere Informationen
Feedback gerne als GitHub Issue oder per E-Mail an info@govdata.de.  

Bisherige Inhalte wurden in die Datei [README_v1X.md](README_v1X.md) verschoben.

© CC BY 4.0 ']init[ AG für GovData'  
