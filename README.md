# DCAT-AP.de SHACL-Validation (BETA)
*SHACL-Shapes für DCAT-AP.de*

## Inhalt
- [DCAT-AP.de SHACL-Validation (BETA)](#dcat-apde-shacl-validation-beta)
  - [Inhalt](#inhalt)
  - [Verfügbarkeit und Verwendung](#verfügbarkeit-und-verwendung)
  - [Überblick über die Test-Profile](#überblick-über-die-test-profile)
  - [Inhalt der Dateien](#inhalt-der-dateien)
    - [A - dcat-ap-de-imports.ttl](#a---dcat-ap-de-importsttl)
    - [B - dcat-ap-de-lists.ttl](#b---dcat-ap-de-liststtl)
    - [C - nal-lists.ttl](#c---nal-liststtl)
    - [D - dcat-ap-de-shapes-specification.ttl](#d---dcat-ap-de-shapes-specificationttl)
    - [E - dcat-ap-reasonable-ranges.ttl](#e---dcat-ap-reasonable-rangesttl)
    - [F - dcat-ap_2.1.0_shacl_shapes.ttl](#f---dcat-ap_210_shacl_shapesttl)
    - [G - dcat-ap_2.1.0_shacl_shapes_recommended.ttl](#g---dcat-ap_210_shacl_shapes_recommendedttl)
    - [H - dcat-ap-de-import-lists.ttl](#h---dcat-ap-de-import-liststtl)
    - [I - dcat-ap-de-shapes-impliedRules.ttl](#i---dcat-ap-de-shapes-impliedrulesttl)
  - [Bekannte Probleme / übergreifende ToDos](#bekannte-probleme--übergreifende-todos)
  - [Kontakt und Lizenz](#kontakt-und-lizenz)

## Verfügbarkeit und Verwendung
Wie der Validator verwendet werden kann, wird auf https://www.itb.ec.europa.eu/docs/guides/latest/validatingRDF/index.html#step-6-use-the-validator beschrieben.

**Webseite User-Interface:** https://www.itb.ec.europa.eu/shacl/dcat-ap.de/upload  
**Download Commandline-Tool:** https://www.itb.ec.europa.eu/shacl-offline/dcat-ap.de/validator.jar  
**Endpoint REST-API:** https://www.itb.ec.europa.eu/shacl/dcat-ap.de/api  
**Endpoint SOAP-API:** https://www.itb.ec.europa.eu/shacl/soap/dcat-ap.de/validation?wsdl  

* * *
:warning: :warning: :warning: 

Der Validator wird derzeit aktiv weiterentwickelt, um eine vollständige Validierung von DCAT.AP.de zu ermöglichen. Dazu werden die SHACL-Shapes von [DCAT-AP](https://github.com/SEMICeu/DCAT-AP/tree/2.1.0-draft/releases/2.1.0) angepasst und eingebunden.
Die folgenden Informationen können daher unvollständig sein und die Funktion des Validators kann streckenweise nicht garantiert werden.

:warning: :warning: :warning: 

* * *

## Überblick über die Test-Profile
Es werden die folgenden Test-Profile zur Verfügung gestellt, die Regeln aus einen Anzahl von Dateien kombinieren, um bedarfsgerecht testen zu können:

Test-Profil                                                        | [A](#a---dcat-ap-de-importsttl) | [B](#b---dcat-ap-de-liststtl) | [C](#c---nal-liststtl) | [D](#d---dcat-ap-de-shapes-specificationttl) | [E](#e---dcat-ap-reasonable-rangesttl) | [F](#f---dcat-ap_210_shacl_shapesttl) | [G](#g---dcat-ap_210_shacl_shapes_recommendedttl) | [H](#h---dcat-ap-de-import-liststtl) | [I](#i---dcat-ap-de-shapes-impliedrulesttl) |
-------------------------------------------------------------------|---|---|---|---|---|---|---|---|---|
DCAT-AP.de 1.1 - nur Spezifikation (1.1)                           | X | X | X | X |   |   |   |   |   |
DCAT-AP 2.1 - nur Mandatory (Auswahl)                              | X |   |   |   | X | X |   |   |   |
DCAT-AP 2.1 - Mandatory & Recommended (Auswahl)                    | X |   |   |   | X | X | X |   |   |
DCAT-AP.de 1.1 Spezifikation & DCAT-AP 2.1 Mandatory               | X | X | X | X | X | X |   |   |   |
DCAT-AP.de 1.1 Spezifikation & DCAT-AP 2.1 Mandatory & Recommended | X | X | X | X | X | X | X |   |   |
DCAT-AP.de 1.1 Konventionen (1, 2, 4-12, 21, 30, 32)               | X |   |   |   |   |   |   | X | X |
alles zusammen                                                     | X | X | X | X | X | X | X | X | X |

\# | Dateiname                                                                       | Intern/Extern
---|---------------------------------------------------------------------------------|---------------
 A | [dcat-ap-de-imports.ttl](#a---dcat-ap-de-importsttl)                            | intern
 B | [dcat-ap-de-lists.ttl](#b---dcat-ap-de-liststtl)                                | intern
 C | [nal-lists.ttl](#c---nal-liststtl)                                              | intern
 D | [dcat-ap-de-shapes-specification.ttl](#d---dcat-ap-de-shapes-specificationttl)  | intern
 E | [dcat-ap-reasonable-ranges.ttl](#e---dcat-ap-reasonable-rangesttl)              | intern (Auswahl)
 F | [dcat-ap_2.1.0_shacl_shapes.ttl](#f---dcat-ap_210_shacl_shapesttl)              | extern
 G | [dcat-ap_2.1.0_shacl_shapes_recommended.ttl](#g---dcat-ap_210_shacl_shapes_recommendedttl) | extern
 H | [dcat-ap-de-import-lists.ttl](#h---dcat-ap-de-import-liststtl)                  | intern
 I | [dcat-ap-de-shapes-impliedRules.ttl](#i---dcat-ap-de-shapes-impliedrulesttl)    | intern

* * *

## Inhalt der Dateien

### A - dcat-ap-de-imports.ttl
Basierend auf dem SHACL-Import von DCAT-AP (https://github.com/SEMICeu/DCAT-AP) wurden die folgenden Listen importiert:
- http://xmlns.com/foaf/spec/index.rdf
- http://www.w3.org/2006/vcard/ns.ttl
- http://www.w3.org/ns/org.ttl

Dadurch wird sichergestellt, `foaf:Person`, `foaf:Organization`, `org:Organization` und die sonstigen enthaltenen Subklassen von `foaf:Agent` als Klasse genutzt werden dürfen, wenn ein `foaf:Agent` erlaubt ist.
Vergleichbares gilt für die Subklassen von `vcard:Kind`.

* * *

### B - dcat-ap-de-lists.ttl
Um die Validität von Eigenschaften prüfen zu können, wurden die folgenden externen Listen in SHACL-Listen umgewandelt:
- https://www.dcat-ap.de/def/contributors/20190531/
- https://www.dcat-ap.de/def/datasetTypes/1_0/
- https://www.dcat-ap.de/def/hashAlgorithms/1_0/
- https://www.dcat-ap.de/def/licenses/20190731/
- https://www.dcat-ap.de/def/plannedAvailability/1_0/
- https://www.dcat-ap.de/def/politicalGeocoding/Level/1_0/
- https://www.dcat-ap.de/def/politicalGeocoding/districtKey/20190731/
- https://www.dcat-ap.de/def/politicalGeocoding/regionalKey/20191231/
- https://www.dcat-ap.de/def/politicalGeocoding/stateKey/20100401/

Dieses Vorgehen soll zu Gunsten von `skos:inSchema` und dem Import von Listen aufgegeben werden. Siehe  **[H - dcat-ap-de-import-lists.ttl](#h---dcat-ap-de-import-liststtl)**.

* * *

### C - nal-lists.ttl
Um die Validität von Eigenschaften prüfen zu können, wurden die folgende externe Listen in eine SHACL-Liste umgewandelt:
- http://publications.europa.eu/resource/authority/frequency/

Dieses Vorgehen soll zu Gunsten von `skos:inSchema` und dem Import von Listen aufgegeben werden. Siehe  **[H - dcat-ap-de-import-lists.ttl](#h---dcat-ap-de-import-liststtl)**.

* * *

### D - dcat-ap-de-shapes-specification.ttl
*Zelle sind nur befüllt, wenn DCAT-AP.de 1.0.2 von DCAT-AP 1.2.1 abweicht.*

Zentrale Datei zur Überprüfung gemäß der Spezifikation DCAT-AP.de. Es werden jedoch lediglich die Dinge getestet, in denen sich DCAT-AP.de von DCAT-AP unterscheidet. Für eine Vollständige Prüfung werden die hier verwendeten Shapes mit denen von DCAT-AP gemeinsam getestet.

Klasse  | Eigenschaft                       | Verbindlichkeit | Range         | Card. | Shape (_Prüfung)
--------|-----------------------------------|-----------------|---------------|-------|----------------------------
Dataset | dcatde:contributorID              | optional        | rdfs:Resource | 0..n  | Dataset_Spec_contributorID_Ex<br>Dataset_Spec_contributorID_IRI<br>Dataset_Spec_contributorID_List
Dataset | dcatde:qualityProcessURI          | optional        | rdfs:Resource | 0..1  | Dataset_Spec_qualityProcessURI_Ex<br>Dataset_Spec_qualityProcessURI_Max<br>Dataset_Spec_qualityProcessURI_IRI
Dataset | dcatde:originator                 | optional        | foaf:Agent    | 0..n  | Dataset_Spec_originator_Ex<br>Dataset_Spec_originator_foafAgent
Dataset | dcatde:maintainer                 | optional        | foaf:Agent    | 0..n  | Dataset_Spec_maintainer_Ex<br>Dataset_Spec_maintainer_foafAgent
Dataset | dct:contributor                   | optional        | foaf:Agent    | 0..n  | Dataset_Spec_contributor_Ex<br>Dataset_Spec_contributor_foafAgent
Dataset | dct:creator                       | optional        | foaf:Agent    | 0..n  | Dataset_Spec_creator_Ex<br>Dataset_Spec_creator_foafAgent
Dataset | dcat:granularity                  | optional        | skos:Concept  | 0..1  | Dataset_Spec_granularity_Ex<br>Dataset_Spec_granularity_Max<br>Dataset_Spec_granularity_IRI
Dataset | dcatde:politicalGeocodingLevelURI | recommended     | rdfs:Resource | 0..n  | Dataset_Spec_politicalGeocodingLevelURI_Ex<br>Dataset_Spec_politicalGeocodingLevelURI_IRI<br>Dataset_Spec_politicalGeocodingLevelURI_List
Dataset | dcatde:politicalGeocodingURI      | recommended     | rdfs:Resource | 0..n  | Dataset_Spec_politicalGeocodingURI_Ex<br>Dataset_Spec_politicalGeocodingURI_IRI<br>Dataset_Spec_politicalGeocodingURI_List
Dataset | dcatde:geocodingDescription       | optional        | rdfs:Literal  | 0..n  | Dataset_Spec_geocodingDescription_Ex<br>Dataset_Spec_geocodingDescription_Literal
Dataset | dcatde:legalBasis                 | optional        | rdfs:Literal  | 0..n  | Dataset_Spec_legalBasis_Ex<br>Dataset_Spec_legalBasis_Literal
Distribution | dct:description                 | optional     |               |       | Distribution_Spec_dct_description_Ex
Distribution | dct:title                       | recommended  |               |       | Distribution_Spec_dct_title_Ex
Distribution | dct:modified                    | recommended  |               |       | Distribution_Spec_dct_modified_Ex
Distribution | dcatde:plannedAvailability      | recommended  | rdfs:Resource | 0..1  | Distribution_Spec_plannedAvailability_Ex<br>Distribution_Spec_plannedAvailability_Max<br>Distribution_Spec_plannedAvailability_IRI<br>Distribution_Spec_plannedAvailability_List
Distribution | dcatde:licenseAttributionByText | optional     | rdfs:Literal  | 0..n  | Distribution_Spec_licenseAttributionByText_Ex<br>Distribution_Spec_licenseAttributionByText_Literal
Checksum     | spdx:algorithm                  |              | rdfs:Resource |       | Distribution_Spec_spdx_Checksum_Algo_List

**Prüfungen:**
Suffix       | Typ             | Beschreibung
------------ | --------------- | ----------------------------------------
_Ex          | **Existenz**    | Prüft, ob eine Eigenschaft vorhanden ist.
_IRI         | **IRI**         | Prüft, ob das Objekt des Tripels eine IRI ist.
_List        | **Gelistet**    | Prüft, ob das Objekt des Tripels im kontrollierten Vokabular enthalten ist.
_Max         | **Maximalzahl** | Prüft, ob die angegebene maximale Kardinalität eingehalten wird.
_foafAgent   | **foaf:Agent**  | Prüft, ob das Objekt der Tripels ein foaf:Agent ist.
_Literal     | **Literal**     | Prüft, ob das Objekt der Tripels ein Literal ist.

* * *

### E - dcat-ap-reasonable-ranges.ttl
**Quelle:** https://github.com/SEMICeu/DCAT-AP/blob/2.1.0-draft/releases/2.1.0/dcat-ap_2.1.0_shacl_range.ttl

Es wird versucht, die Klassenzugehörigkeit von Objekten zu prüfen. Dies kann bei  extern verlinkten Daten nicht erfolgen. Daher wurde die `sh:severity sh:Warning` gewählt und in der Fehlermeldung darauf hingewiesen, dass dies der Grund des Fehlers sein kann.

Die Prüfungen wurden auf folgende Ranges beschränkt:

 \#   | Subjekt              | Prädikat            | Objekt 
------|----------------------|---------------------|--------------------------------
 #01. | `dcat:CatalogRecord` | `foaf:primaryTopic` | `dcat:Catalog`, `dcat:Dataset`
 #02. | `dcat:CatalogRecord` | `dct:source`        | `dcat:CatalogRecord`
 #03. | `dcat:Catalog`       | `dct:hasPart`       | `dcat:Catalog`
 #04. | `dcat:Catalog`       | `dct:isPartOf`      | `dcat:Catalog`
 #05. | `dcat:Catalog`       | `dcat:record`       | `dcat:CatalogRecord`
 #06. | `dcat:Catalog`       | `dcat:catalog`      | `dcat:Catalog`
 #07. | `dcat:Catalog`       | `dct:creator`       | `foaf:Agent`
 #08. | `dcat:Catalog`       | `dcat:dataset`      | `dcat:Dataset`
 #09. | `dcat:Catalog`       | `dct:publisher`     | `foaf:Agent`
 #10. | `dcat:Dataset`       | `dcat:contactPoint` | `vcard:Kind`
 #11. | `dcat:Dataset`       | `dcat:distribution` | `dcat:Distribution`
 #12. | `dcat:Dataset`       | `dct:publisher`     | `foaf:Agent`
 #13. | `dcat:Dataset`       | `dct:temporal`      | `dct:PeriodOfTime`
 #14. | `dcat:Dataset`       | `dct:hasVersion`    | `dcat:Dataset`
 #15. | `dcat:Dataset`       | `dct:isVersionOf`   | `dcat:Dataset`
 #16. | `dcat:Dataset`       | `dct:source`        | `dcat:Dataset`
 #17. | `dcat:Dataset`       | `adms:identifier`   | `adms:Identifier`
 #18. | `dcat:Dataset`       | `adms:sample`       | `dcat:Distribution`
 #19. | `dcat:Dataset`       | `dct:creator`       | `foaf:Agent`
 #20. | `dcat:Distribution`  | `spdx:checksum`     | `spdx:Checksum`
 #21. | `dct:PeriodOfTime`   | `time:hasBeginning` | `time:Instant`
 #22. | `dct:PeriodOfTime`   | `time:hasEnd`       | `time:Instant`
 
**ToDos**
- prüfen, ob die Range von 1. korrekt ist
- schema/dcat Zeitperioden hinzufügen

* * *

### F - dcat-ap_2.1.0_shacl_shapes.ttl
**Externe Quelle:** https://github.com/SEMICeu/DCAT-AP/blob/2.1.0-draft/releases/2.1.0/dcat-ap_2.1.0_shacl_shapes.ttl

Die von der SEMIC bereitgestellten SHACL-Shapes führen die folgenden Prüfungen für alle Pflicht-Eigenschaften durch:
- Mindestzahl
- Maximalzahl
- `nodeKind` (Literal, IRI)

Bei allen empfohlenen Eigenschaften wird ihre Maximalzahl und der `nodeKind` geprüft.

Alle Regelverletzungen werden als `sh:Violation` gekennzeichnet.

Die Prüfung erfolgt für
- `dcat:CatalogRecord`
- `dcat:Catalog`
- `dcat:DataService`
- `dcat:Dataset`
- `dcat:Distribution`
- `dcat:Relationship`
- `foaf:Agent`
- `skos:ConceptScheme`
- `skos:Concept`
- `adms:Identifier`
- `dct:LicenseDocument`
- `dct:Location`
- `dct:PeriodOfTime`
- `spdx:Checksum`

**Bekannte Probleme**
- für `dct:PeriodOfTime` werden die `schema`-Eigenschaften getestet
- `spdx:Checksum` erlaubt *nur* SHA1
- es werden bereits Klassen geprüft, die in DCAT-AP.de 1.1 nicht enthalten sind

* * *

### G - dcat-ap_2.1.0_shacl_shapes_recommended.ttl
**Externe Quelle:** https://github.com/SEMICeu/DCAT-AP/blob/2.1.0-draft/releases/2.1.0/dcat-ap_2.1.0_shacl_shapes_recommended.ttl

Die von der SEMIC bereitgestellten SHACL-Shapes prüfen alle empfohlenen Eigenschaften, ob sie existieren. (Die erlaubte Höchstzahl und ihr `nodeKind` werden bereits bei **[F - dcat-ap_2.1.0_shacl_shapes.ttl](#f---dcat-ap_210_shacl_shapesttl)** geprüft.)

Alle Regelverletzungen werden als `sh:Warning` gekennzeichnet.

Die Prüfung erfolgt für
- `dcat:CatalogRecord`
- `dcat:Catalog`
- `dcat:DataService`
- `dcat:Dataset`
- `dcat:Distribution`
- `foaf:Agent`
- `dct:LicenseDocument`
- `dct:Location`
- `dct:PeriodOfTime`

**Bekannte Probleme**
- für `dct:PeriodOfTime` wird, verwendet man etwas anderes als `dcat:startDate`/`dcat:endDate`, immer eine Warnung ausgegeben
- es werden bereits Klassen geprüft, die in DCAT-AP.de 1.1 nicht enthalten sind

* * *

### H - dcat-ap-de-import-lists.ttl
Importiert die folgenden kontrollierten Vokabulare:
  - http://publications.europa.eu/resource/authority/data-theme
  - https://www.dcat-ap.de/def/licenses/20200715.rdf

Ihr Import erlaubt es dann zu prüfen, ob ein Wert zur jeweiligen Liste gehört. Z.B.:

```
[
    sh:hasValue <http://publications.europa.eu/resource/authority/data-theme> ;
    sh:nodeKind sh:IRI ;
    sh:path skos:inScheme ;
]
```
Dieses Vorgehen soll auf alle kontrollierte Vokabulare ausgeweitet werden. (Siehe **[B - dcat-ap-de-lists.ttl](#b---dcat-ap-de-liststtl)** und **[C - nal-lists.ttl](#c---nal-liststtl)**.)

* * *

### I - dcat-ap-de-shapes-impliedRules.ttl
In dieser Datei werden die SHACL-Shapes zusammengefasst, testen sollen, ob die Kovnentionen des Konventionenhandbuchs eingehalten werden.

Getestet werden die folgenden Konventionen:
- 1 und 2
- 4 bis 7
- 8 bis 12
- 21, 30 und 32

**Bekannte Probleme**
- zum Teil unklar, wie eine Konvention exakt gemeint ist
- manche Konventionen machen inhaltliche Vorgaben, die technisch nicht geprüft werden können

* * *

## Bekannte Probleme / übergreifende ToDos

* SPDX akzeptiert nicht die URIs von DCAT-AP.de
* von DCAT-AP.de 1.0.2 auf 1.1 umstellen

* * *
## Kontakt und Lizenz
Feedback gerne als GitHub Issue oder per E-Mail an info@govdata.de.

(C) CC BY 4.0 ']init[ AG fuer GovData'
