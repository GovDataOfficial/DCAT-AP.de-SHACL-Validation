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

Klasse  | Eigenschaft                       | Verbindlichkeit | Range         | Card. | Prüfung : Shape
--------|-----------------------------------|-----------------|---------------|-------|----------------------------
Dataset | dcatde:contributorID              | optional        | rdfs:Resource | 0..n  | Existenz: Dataset_Spec_contributorID_1, IRI: Dataset_Spec_contributorID_2, Gelistet: Dataset_Spec_contributorID_3
Dataset | dcatde:qualityProcessURI          | optional        | rdfs:Resource | 0..1  | Existenz: Dataset_Spec_qualityProcessURI_1, Maximalzahl: Dataset_Spec_qualityProcessURI_2, IRI: Dataset_Spec_qualityProcessURI_3
Dataset | dcatde:originator                 | optional        | foaf:Agent    | 0..n  | Existenz: Dataset_Spec_originator_1, foaf:Agent: Dataset_Spec_originator_2
Dataset | dcatde:maintainer                 | optional        | foaf:Agent    | 0..n  | Existenz: Dataset_Spec_maintainer_1, foaf:Agent: Dataset_Spec_maintainer_2
Dataset | dct:contributor                   | optional        | foaf:Agent    | 0..n  | Existenz: Dataset_Spec_contributor_1, foaf:Agent: Dataset_Spec_contributor_2
Dataset | dct:creator                       | optional        | foaf:Agent    | 0..n  | Existenz: Dataset_Spec_creator_1, foaf:Agent: Dataset_Spec_creator_2
Dataset | dcat:granularity                  | optional        | skos:Concept  | 0..1  | Existenz: Dataset_Spec_granularity_1, Maximalzahl: Dataset_Spec_granularity_2, IRI: Dataset_Spec_granularity_3
Dataset | dcatde:politicalGeocodingLevelURI | recommended     | rdfs:Resource | 0..n  | Existenz: Dataset_Spec_politicalGeocodingLevelURI_1, IRI: Dataset_Spec_politicalGeocodingLevelURI_2, Gelistet: Dataset_Spec_politicalGeocodingLevelURI_3
Dataset | dcatde:politicalGeocodingURI      | recommended     | rdfs:Resource | 0..n  | Existenz: Dataset_Spec_politicalGeocodingURI_1, IRI: Dataset_Spec_politicalGeocodingURI_2, Gelistet: Dataset_Spec_politicalGeocodingURI_3
Dataset | dcatde:geocodingDescription       | optional        | rdfs:Literal  | 0..n  | Existenz: Dataset_Spec_geocodingDescription_1, Literal: Dataset_Spec_geocodingDescription_2
Dataset | dcatde:legalBasis                 | optional        | rdfs:Literal  | 0..n  | Existenz: Dataset_Spec_legalBasis_1, Literal: Dataset_Spec_legalBasis_2
Distribution | dct:description                 | optional     |               |       | Existenz: Distribution_Spec_dct_description_1
Distribution | dct:title                       | recommended  |               |       | Existenz: Distribution_Spec_dct_title_1
Distribution | dct:modified                    | recommended  |               |       | Existenz: Distribution_Spec_dct_modified_1
Distribution | dcatde:plannedAvailability      | recommended  | rdfs:Resource | 0..1  | Existenz: Distribution_Spec_plannedAvailability_1, Maximalzahl: Distribution_Spec_plannedAvailability_2, IRI: Distribution_Spec_plannedAvailability_3, Gelistet: Distribution_Spec_plannedAvailability_4
Distribution | dcatde:licenseAttributionByText | optional     | rdfs:Literal  | 0..n  | Existenz: Distribution_Spec_licenseAttributionByText_1, Literal: Distribution_Spec_licenseAttributionByText_2

**Prüfungen:**
- **Existenz:** Prüft, ob eine Eigenschaft vorhanden ist.
- **IRI:** Prüft, ob das Objekt des Tripels eine IRI ist.
- **Gelistet:** Prüft, ob das Objekt des Tripels im kontrollierten Vokabular enthalten ist.
- **Maximalzahl:** Prüft, ob die angegebene maximale Kardinalität eingehalten wird.
- **foaf:Agent:** Prüft, ob das Objekt der Tripels ein foaf:Agent ist.
- **Literal:** Prüft, ob das Objekt der Tripels ein Literal ist.

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
