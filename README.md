# DCAT-AP.de SHACL-Validation (BETA)
*SHACL-Shapes für DCAT-AP.de*

## Verfügbarkeit
Der Validator ist Online unter https://www.itb.ec.europa.eu/shacl/dcat-ap.de/upload verfügbar.
Eine Offline-Java-Version kann unter https://www.itb.ec.europa.eu/shacl-offline/dcat-ap.de/validator.jar bezogen werden.

## Umfang
Die vorliegenden Shapes prüfen die Eigenschaften, die das deutsche DCAT-AP.de 1.0.2 Spezifikationsdokument zusätzlich oder abweichend vom europäischen DCAT-AP 1.2.1 Standard festlegt. (Hinweis: Eine Weiterentwicklung der Shapes um die Prüfung der DCAT-AP.de Konventionenhandbuch-Konformität ist aktuell in Arbeit. Parallel hierzu beteiligt sich die GKSt GovData an der Weiterentwicklung der Shapes für den europäischen Metadatenstandard DCAT-AP.)   

### Nicht geprüft wird
- ob es valides [DCAT](https://www.w3.org/TR/vocab-dcat/) ist
- ob es valides [DCAT-AP](https://github.com/SEMICeu/DCAT-AP) ist
- ob das [Konventionenhandbuch](https://www.dcat-ap.de/def/) eingehalten wird

### Geprüft wird
*Zelle sind nur befüllt, wenn DCAT-AP.de 1.0.2 von DCAT-AP 1.2.1 abweicht.*

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

**Prüfungen:**
Suffix       | Type            | Beschreibung
------------ | --------------- | ----------------------------------------
_Ex          | **Existenz**    | Prüft, ob eine Eigenschaft vorhanden ist.
_IRI         | **IRI**         | Prüft, ob das Objekt des Tripels eine IRI ist.
_List        | **Gelistet**    | Prüft, ob das Objekt des Tripels im kontrollierten Vokabular enthalten ist.
_Max         | **Maximalzahl** | Prüft, ob die angegebene maximale Kardinalität eingehalten wird.
_foafAgent   | **foaf:Agent**  | Prüft, ob das Objekt der Tripels ein foaf:Agent ist.
_Literal     | **Literal**     | Prüft, ob das Objekt der Tripels ein Literal ist.

### Listen
Um die Validität von Eigenschaften prüfen zu können, wurden die folgenden externen Listen in SHACL-Listen umgewandelt:
**dcat-ap-de-lists.ttl:**
- https://www.dcat-ap.de/def/contributors/20190531/
- https://www.dcat-ap.de/def/datasetTypes/1_0/
- https://www.dcat-ap.de/def/hashAlgorithms/1_0/
- https://www.dcat-ap.de/def/licenses/20190731/
- https://www.dcat-ap.de/def/plannedAvailability/1_0/
- https://www.dcat-ap.de/def/politicalGeocoding/Level/1_0/
- https://www.dcat-ap.de/def/politicalGeocoding/districtKey/20190731/
- https://www.dcat-ap.de/def/politicalGeocoding/regionalKey/20191231/
- https://www.dcat-ap.de/def/politicalGeocoding/stateKey/20100401/

**nal-lists.ttl:**
- http://publications.europa.eu/resource/authority/frequency/


## Kontakt und Lizenz
Feedback gerne als GitHub Issue oder per E-Mail an info@govdata.de.

(C) CC BY 4.0 ']init[ AG fuer GovData'
