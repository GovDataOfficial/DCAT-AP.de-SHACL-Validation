# DCAT-AP.de SHACL-Validation (BETA)
*SHACL-Shapes für DCAT-AP.de*

## Verfügbarkeit
Der Validator ist Online unter https://www.itb.ec.europa.eu/shacl/dcat-ap.de/upload verfügbar.
Eine Offline-Java-Version kann unter https://www.itb.ec.europa.eu/shacl-offline/dcat-ap.de/validator.jar bezogen werden.

## Umfang
Die vorliegenden Shapes prüfen die Eigenschaften, die das deutsche DCAT-AP.de 1.0.2 Spezifikationsdokument zusätzlich oder abweichend vom europäischen DCAT-AP 1.2.1 Standard festlegt.

### Nicht geprüft wird
- ob es valides [DCAT](https://www.w3.org/TR/vocab-dcat/) ist
- ob es valides [DCAT-AP](https://github.com/SEMICeu/DCAT-AP) ist
- ob das [Konventionenhandbuch](https://www.dcat-ap.de/def/) eingehalten wird

### Geprüft wird
*Zelle sind nur befüllt, wenn DCAT-AP.de 1.0.2 von DCAT-AP 1.2.1 abweicht.*

Klasse  | Eigenschaft                       | Verbindlichkeit | Range         | Card. | Prüfung : SHAPE
--------|-----------------------------------|-----------------|---------------|-------|----------
Dataset | dcatde:contributorID              | optional        | rdfs:Resource | 0..n  | Dataset_Spec_contributorID_1, Dataset_Spec_contributorID_2, Dataset_Spec_contributorID_3
Dataset | dcatde:qualityProcessURI          | optional        | rdfs:Resource | 0..1  | Dataset_Spec_qualityProcessURI_1, Dataset_Spec_qualityProcessURI_2, Dataset_Spec_qualityProcessURI_3
Dataset | dcatde:originator                 | optional        | foaf:Agent    | 0..n  | Dataset_Spec_originator_1, Dataset_Spec_originator_2
Dataset | dcatde:maintainer                 | optional        | foaf:Agent    | 0..n  | Dataset_Spec_maintainer_1, Dataset_Spec_maintainer_2
Dataset | dct:contributor                   | optional        | foaf:Agent    | 0..n  | Dataset_Spec_contributor_1, Dataset_Spec_contributor_2
Dataset | dct:creator                       | optional        | foaf:Agent    | 0..n  | Dataset_Spec_creator_1, Dataset_Spec_creator_2
Dataset | dcat:granularity                  | optional        | skos:Concept  | 0..1  | Dataset_Spec_granularity_1, Dataset_Spec_granularity_2, Dataset_Spec_granularity_3
Dataset | dcatde:politicalGeocodingLevelURI | recommended     | rdfs:Resource | 0..n  | Dataset_Spec_politicalGeocodingLevelURI_1, Dataset_Spec_politicalGeocodingLevelURI_2, Dataset_Spec_politicalGeocodingLevelURI_3
Dataset | dcatde:politicalGeocodingURI      | recommended     | rdfs:Resource | 0..n  | Dataset_Spec_politicalGeocodingURI_1, Dataset_Spec_politicalGeocodingURI_2, Dataset_Spec_politicalGeocodingURI_3
Dataset | dcatde:geocodingDescription       | optional        | rdfs:Literal  | 0..n  | Dataset_Spec_geocodingDescription_1, Dataset_Spec_geocodingDescription_2
Dataset | dcatde:legalBasis                 | optional        | rdfs:Literal  | 0..n  | Dataset_Spec_legalBasis_1, Dataset_Spec_legalBasis_2
Distribution | dct:description                 | optional     |               |       | Distribution_Spec_dct_description_1
Distribution | dct:title                       | recommended  |               |       | Distribution_Spec_dct_title_1
Distribution | dct:modified                    | recommended  |               |       | Distribution_Spec_dct_modified_1
Distribution | dcatde:plannedAvailability      | recommended  | rdfs:Resource | 0..1  | Distribution_Spec_plannedAvailability_1, Distribution_Spec_plannedAvailability_2, Distribution_Spec_plannedAvailability_3, Distribution_Spec_plannedAvailability_4
Distribution | dcatde:licenseAttributionByText | optional     | rdfs:Literal  | 0..n  | Distribution_Spec_licenseAttributionByText_1, Distribution_Spec_licenseAttributionByText_2

### Listen
Um die Validität von Eigenschaften prüfen zu können, wurden die folgenden externen Listen in SHACL-Listen umgewandelt:
- TBD

## Kontakt und Lizenz
Feedback gerne als GitHub Issue oder per E-Mail an info@govdata.de.

(C) CC BY 4.0 ']init[ AG fuer GovData'