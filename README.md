# DCAT-AP.de SHACL-Validation (BETA)
*SHACL-Shapes für DCAT-AP.de*

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

Test-Profil                                                        | A | B | C | D | E | F | G | H | I |
-------------------------------------------------------------------|---|---|---|---|---|---|---|---|---|
DCAT-AP.de 1.1 - nur Spezifikation (1.1)                           | X | X | X | X |   |   |   |   |   |
DCAT-AP 2.1 - nur Mandatory (Auswahl)                              | X |   |   |   | X | X |   |   |   |
DCAT-AP 2.1 - Mandatory & Recommended (Auswahl)                    | X |   |   |   | X | X | X |   |   |
DCAT-AP.de 1.1 Spezifikation & DCAT-AP 2.1 Mandatory               | X | X | X | X | X | X |   |   |   |
DCAT-AP.de 1.1 Spezifikation & DCAT-AP 2.1 Mandatory & Recommended | X | X | X | X | X | X | X |   |   |
DCAT-AP.de 1.1 Konventionen (1, 2, 4-12, 21, 30, 32)               | X |   |   |   |   |   |   | X | X |
alles zusammen                                                     | X | X | X | X | X | X | X | X | X |


\# | Dateiname                                  | Intern/Extern
---|--------------------------------------------|---------------
 A | dcat-ap-de-imports.ttl                     | intern
 B | dcat-ap-de-lists.ttl                       | intern
 C | nal-lists.ttl                              | intern
 D | dcat-ap-de-shapes-specification.ttl        | intern
 E | dcat-ap-reasonable-ranges.ttl              | intern (Auswahl)
 F | dcat-ap_2.1.0_shacl_shapes.ttl             | extern
 G | dcat-ap_2.1.0_shacl_shapes_recommended.ttl | extern
 H | dcat-ap-de-import-lists.ttl                | intern
 I | dcat-ap-de-shapes-impliedRules.ttl         | intern

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

Dieses Vorgehen soll zu Gunsten von `skos:inSchema` und dem Import von Listen aufgegeben werden. Siehe  **H - dcat-ap-de-import-lists.ttl**.

* * *

### C - nal-lists.ttl
Um die Validität von Eigenschaften prüfen zu können, wurden die folgende externe Listen in eine SHACL-Liste umgewandelt:
- http://publications.europa.eu/resource/authority/frequency/

Dieses Vorgehen soll zu Gunsten von `skos:inSchema` und dem Import von Listen aufgegeben werden. Siehe  **H - dcat-ap-de-import-lists.ttl**.

* * *

### D - dcat-ap-de-shapes-specification.ttl
*Zelle sind nur befüllt, wenn DCAT-AP.de 1.0.2 von DCAT-AP 1.2.1 abweicht.*

Zentrale Datei zur Überprüfung gemäß der Spezifikation DCAT-AP.de. 

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
*tbd*
* * *

### F - dcat-ap_2.1.0_shacl_shapes.ttl
*tbd*
* * *

### G - dcat-ap_2.1.0_shacl_shapes_recommended.ttl
*tbd*
* * *

### H - dcat-ap-de-import-lists.ttl
*tbd*
* * *

### I - dcat-ap-de-shapes-impliedRules.ttl
*tbd*
* * *

## Bekannte Probleme / übergreifende ToDos

* SPDX akzeptiert nicht die URIs von DCAT-AP.de
* von DCAT-AP.de 1.0.2 auf 1.1 umstellen

* * *
## Kontakt und Lizenz
Feedback gerne als GitHub Issue oder per E-Mail an info@govdata.de.

(C) CC BY 4.0 ']init[ AG fuer GovData'
