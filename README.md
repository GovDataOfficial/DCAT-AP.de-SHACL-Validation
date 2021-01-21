# DCAT-AP.de SHACL-Validation (BETA)
*SHACL-Shapes für DCAT-AP.de*

## Inhalt
- [DCAT-AP.de SHACL-Validation (BETA)](#dcat-apde-shacl-validation-beta)
  - [Inhalt](#inhalt)
  - [Einleitung](#einleitung)
  - [Verfügbarkeit und Verwendung](#verfügbarkeit-und-verwendung)
  - [FAQ - Häufig gestellte Fragen](#faq---häufig-gestellte-fragen)
    - [Was ist DCAT-AP.de?](#was-ist-dcat-apde)
    - [Was ist SHACL?](#was-ist-shacl)
    - [Was ist eine Validierung?](#was-ist-eine-validierung)
    - [Was ist das Interoperability-Test-Bed (ITB) und warum wird es verwendet?](#was-ist-das-interoperability-test-bed-itb-und-warum-wird-es-verwendet)
    - [Wie kann ich den DCAT-AP.de Validator als Docker-File selber betreiben?](#wie-kann-ich-den-dcat-apde-validator-als-docker-file-selber-betreiben)
    - [Wofür kann ich den DCAT-AP.de Validator (BETA) nutzen?](#wofür-kann-ich-den-dcat-apde-validator-beta-nutzen)
      - [1.	DCAT-AP – Validierung](#1dcat-ap--validierung)
      - [2.	DCAT-AP.de – Validierung](#2dcat-apde--validierung)
      - [3.	DCAT-AP.de zur Anbindung an das GovData-Portal  - Validierung](#3dcat-apde-zur-anbindung-an-das-govdata-portal----validierung)
    - [Was bedeuten die Validierungsergebnisse?](#was-bedeuten-die-validierungsergebnisse)
    - [Wie kann ich die Validierungsergebnisse auswerten?](#wie-kann-ich-die-validierungsergebnisse-auswerten)
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
  
  
## Einleitung
Dieses Repo soll als Erläuterung zur Verwendung der DCAT-AP.de SHACL-Validation unter https://www.itb.ec.europa.eu/shacl/dcat-ap.de/upload dienen. Der Validator selbst soll dabei unterstützen DCAT-AP.de konforme Metadaten zu erstellen. Aktuell befindet sich der Validator in einer Beta-Testphase. Unterstützen Sie uns, indem Sie aufkommende Fragen oder Fehlfunktionen als Issue aufnehmen unter: https://github.com/GovDataOfficial/DCAT-AP.de-SHACL-Validation/issues 


## Verfügbarkeit und Verwendung
Wir empfehlen, den Validator über die Webseite zu verwenden: **https://www.itb.ec.europa.eu/shacl/dcat-ap.de/upload**

Weitere Varianten werden auf https://www.itb.ec.europa.eu/docs/guides/latest/validatingRDF/index.html#step-6-use-the-validator beschrieben.


* * *
:warning: :warning: :warning: 

Der Validator wird derzeit aktiv weiterentwickelt, um eine vollständige Validierung von DCAT.AP.de zu ermöglichen. Dazu werden die SHACL-Shapes von [DCAT-AP](https://github.com/SEMICeu/DCAT-AP/tree/2.1.0-draft/releases/2.1.0) angepasst und eingebunden.
Die folgenden Informationen können daher unvollständig sein und die Funktion des Validators kann streckenweise nicht garantiert werden.

:warning: :warning: :warning: 

* * *

## FAQ - Häufig gestellte Fragen

### Was ist DCAT-AP.de? 
DCAT-AP.de ist der Metadatenstandard zum Austausch von offenen Verwaltungsdaten. DCAT-AP.de ist die Ableitung des Europäischen Standards [DCAT-AP](https://github.com/SEMICeu/DCAT-AP/tree/master/releases) und verwendet international etablierte Vokabulare. DCAT-AP.de bietet ein RDF-Vokabular das der Austausch von Metadaten offener Verwaltungsdaten für Open Data-Portale von der kommunalen  bis zur euopäischen Ebene ermöglicht. Weitere Infos zu DCAT-AP.de finden Sie unter: https://www.dcat-ap.de/def/ 

### Was ist SHACL?
Die Shapes Constraint Language (SHACL) ist eine Sprache, die RDF-Graphen (wie Metadatensätze von DCAT-AP.de) gegen bestimmte Bedingungen validiert – sie also prüft. Als Prüfschema werden wiederum eigene Graphen, sogenannte SHACL-Shapes eingesetzt. Weitere Infos zu SHACL finden Sie unter: https://www.w3.org/TR/shacl/ 

### Was ist eine Validierung? 
Eine Validierung ist eine Überprüfung der Einhaltung bestimmter Regeln. DCAT-AP.de z.B. schreibt bestimmte Angaben als verpflichtend vor oder trifft Regelungen zum Wertebereich bestimmter Angaben. Ein Datensatz in DCAT-AP.de muss beispielsweise zwingend einen Titel und eine Beschreibung haben. Wird der Datensatz einer Kategorie zugeordnet, muss das Dataset Theme Vocabulary genutzt werden (http://publications.europa.eu/resource/authority/data-theme). Eine Validierung überprüft die Einhaltung dieser Regeln.  

### Was ist das Interoperability-Test-Bed (ITB) und warum wird es verwendet?  
Mit dem ITB bietet die EU-Kommission Lösungen zur Validierung an. Das ITB wird von der EU zur Validierung von DCAT-AP offiziell empfohlen und steht kostenfrei zur Nutzung für DCAT-AP.de zur Verfügung. Wir verwenden das Online-Tool, da es uns einfach und kostengünstig ermöglicht eigene DCAT-AP.de SHACL-Shapes als Prüfschema für alle zugänglich zur Verfügung zu stellen. Dabei stellen wie (die GKSt GovData) nur die Prüfschemata in Form von SHACL-Shapes bereit. Der eigentliche Validierungsvorgang wird durch das ITB erledigt. Weitere Infos zu ITB finden Sie unter: https://joinup.ec.europa.eu/collection/interoperability-test-bed-repository/solution/interoperability-test-bed/about

### Wie kann ich den DCAT-AP.de Validator als Docker-File selber betreiben?
(tbd)

### Wofür kann ich den DCAT-AP.de Validator (BETA) nutzen?
Der Validator ermöglicht es Ihnen unter *„Zu validierender Inhalt“* verschiedene Inhalte aus verschiedenen Quellen zu prüfen. Sie können entweder eine Datei oder eine URI prüfen oder über *"Direkte Eingabe"* direkt den Inhalt eingeben. Damit der Inhalt richtig erkannt wird, kann es z.B. bei fehlender Dateiendung nötig sein, dass Sie zusätzlich die verwendete *„Syntax des Inhalts“* angeben.

Der Umfang des zu validierenden Inhalts kann dabei variieren insbesondere können (a) einzelne Metadatensätze auf ihre Konformität hin überprüft werden, (b) mehrere in einem Katalog zusammengestellte Metadatensätze auf ihre Konformität hin überprüft werden oder (c) der Inhalt von Harvesting-Endpunkte seitenweise auf seine Konformität hin überprüft werden. 

Bei *„zu verwendendes Profil“*  können Sie verschiedene SHACL-Shapes also Prüfschemen auswählen, die teilweise kombiniert werden. (Detailliertere Informationen zu den Test-Profilen finden Sie im Abschnitt Überblick über die Test-Profile dieser ReadMe). Die unterschiedlichen Testprofilen sollen unterschiedlichste Testbedarfe abdecken, diese lassen sich generell in 3 Ebenen unterscheiden: 

#### 1.	DCAT-AP – Validierung
Wollen Sie überprüfen, ob Ihre Metadaten dem aktuellen Standard des Europäischen Metadatenmodell DCAT-AP entsprechen, stehen Ihnen folgende Profile zur Auswahl: 
   - a.)   DCAT-AP 2.1 - nur Mandatory (Auswahl)  
  Dieses Profil prüft alle Pflicht-Eigenschaften der aktuellen DCAT-AP 2.1 
  
   - b.)   DCAT-AP 2.1 – Mandatory & Recommended (Auswahl)   
    Dieses Profil prüft zusätzlich zu a.) noch die  empfohlenen-Eigenschaften der DCAT-AP 2.1 
    
   Hinweis: Weitere Infos wie z.B. bekannte Probleme unter: Test-Profile. Hier werden die offiziellen Shapes der Pflegestelle für DCAT-AP (Bis 31.12.2020 SEMIC) verwendet. 
   
#### 2.	DCAT-AP.de – Validierung
Wollen Sie überprüfen, ob Ihre Daten der aktuellen DCAT-AP.de 1.1 entspricht, stehen Ihnen folgende Profile zur Auswahl:

  - a.)	DCAT-AP.de 1.1 – nur Spezifikation (1.1)  
  Dieses Profil testet nur die Dinge bei denen DCAT-AP.de vom europäischen Standard abweicht. Z.B. neue Eigenschaften wie dcatde:contributorID
  
  - b.)	DCAT-AP.de 1.1 Spezifikation + DCAT-AP 2.1 Mandatory  
  Dieses Profil testet die Pflicht-Eigenschaften des europäischen DCAT-AP 2.1 und die Dinge bei denen DCAT-AP.de vom europäischen Standard abweicht.
  
  - c.)	DCAT-AP.de 1.1 Spezifikation + DCAT-AP 2.1 Mandatory + Recommended  
  Dieses Profil testet die Pflicht- und die empfohlenen Eigenschaften des europäischen DCAT-AP 2.1 und die Dinge bei denen DCAT-AP.de vom europäischen Standard abweicht.

Hinweis: Weitere Infos wie z.B. bekannte Probleme unter: Test-Profile. DCAT-AP-de 1.1 basiert auf der DCAT-AP v1.1. Es werden dennoch die Shapes der DCAT-AP v2.1 verwendet, da a) die Shapes der v1.1 in sich nicht valide waren und somit die Qualität der Validierungsergebnisse mangelhaft und b) die neuen Klassen, die in der DCAT-AP v2.1 geprüft werden, aber noch in der DCAT-AP.de 1.1 vorhanden sind nach unseren Tests nicht zu Fehlern führen. Bekanntes Problem: für dct:PeriodOfTime verwendet DCAT-AP 2.1 etwas anderes als dcat:startDate/dcat:endDate, deshalb wird hier immer eine Warnung ausgegeben.

#### 3.	DCAT-AP.de zur Anbindung an das GovData-Portal  - Validierung
Zur Bereitstellung der DCAT-AP.de-Metadaten an das GovData-Portal gibt es ergänzend zu Spezifikation noch zusätzliche Vorschriften, die in einem Konventionenhandbuch festgehalten wurden (https://www.dcat-ap.de/def/dcatde/1.1/implRules.pdf). Wollen Sie überprüfen ob ihre Metadaten DCAT-AP.de entsprechen und an GovData angeliefert werden können, stehen Ihnen folgende Profile zur Auswahl:

  - a.)	DCAT-AP.de Konventionen (1,2,4-12,21,30,32)   
  Dieses Profil testet die folgenden Konventionen 1 und 2, 4 bis 12, 21, 30 und 32 der Konventionenhandbuchs unter: https://www.dcat-ap.de/def/dcatde/1.1/implRules.pdf (Die      Validierung der übrigen Konventionen ließ sich bis dato noch nicht realisieren, wird aber weiter verfolgt, siehe hierzu Hinweis). 
  
  - b.)	Alles Zusammen  
  Dieses Profil testet die Pflicht- und die empfohlenen Eigenschaften des europäischen DCAT-AP 2.1, die Dinge bei denen DCAT-AP.de vom europäischen Standard abweicht und die Konventionen 1 und 2, 4 bis 12, 21, 30 und 32 des Konventionenhandbuchs. 

Hinweis: Für einige der Konventionen konnte kein Prüfschema erstellt werden, was häufig daran lag, dass a) die Formulierungen zum Teil unscharf sind und b) manche inhaltliche Vorgaben der Konventionen nicht überprüft werden können. Diese Punkte sollen bei der künftigen Weiterentwicklung des Standards DCAT-AP.de (https://github.com/GovDataOfficial/DCAT-AP.de) aufgegriffen werden.

### Was bedeuten die Validierungsergebnisse? 
SHACL unterscheidet generell in drei Arten von Fehlern. 
  - a.)	Fehler (Violation)  
  Diese Fehlermeldung sollte immer dann ausgegeben werden, wenn der Verstoß zu nicht-konformen Metadaten führt. 
    - Hier ein Beispiel:  
    Das Profil „DCAT-AP.de 1.1 Konventionen (1,2,4-12,21,30,32) prüft ob die obligatorisch zu nutzende Eigenschaft dcatde:contributorID vorhanden ist. Bei einem Verstoß kommt folgende rot hinterlegte Fehlermeldung:  
        *Pflicht (K12): Alle Datenstrukturen, die direkt an das GovData Portal geliefert werden, MÜSSEN ihre Herkunft über eine eindeutige Kennzeichnung des Datenbereitstellers über die DatenbereitstellerID (dcatde:contributorID) ausweisen. - Seite 13
Ort:[Fokusknoten] - [https://ckan.govdata.de/dataset/1c292363-5a7c-4131-9bb8-9ac05fdf34c6] - [Ergebnispfad] - [http://dcat-ap.de/def/dcatde/contributorID]*

  - b.) Warnung (Warning)  
  Diese Fehlermeldung sollte immer dann ausgegeben werden, wenn der Verstoß mit einer empfohlenen Eigenschaft zusammenhängt. 
    - Hier ein Beispiel:   
    Das Profil „DCAT-AP.de 1.1 Konventionen (1,2,4-12,21,30,32) prüft ob die empfohlen zu nutzende Eigenschaft dcatde:politicalGeocodingLevelURI vorhanden ist. Bei einem Verstoß kommt folgende gelb hinterlegte Fehlermeldung:   
*Empfohlen: dcatde:politicalGeocodingLevelURI ist nicht vorhanden! Sie sollten mittels dcatde:politicalGeocodingLevelURI die prinzipielle Verwaltungsebene, von der das Dataset erhoben und eingestellt wurde, angeben. Es wird empfohlen, folgende Liste zu verwenden: https://www.dcat-ap.de/def/politicalGeocoding/Level/
Ort:[Fokusknoten] - [https://ckan.govdata.de/dataset/1c292363-5a7c-4131-9bb8-9ac05fdf34c6] - [Ergebnispfad] - [http://dcat-ap.de/def/dcatde/politicalGeocodingLevelURI]Test:[Shape] - [http://dcat-ap.de/def/dcatde/1.0.2/#Dataset_politicalGeocodingLevelURI_Ex]*

  - c.)	Nachrichten (Info)  
  Diese Nachricht sollte immer dann ausgegeben werden, wenn der Verstoß mit einer optionalen Eigenschaft zusammenhängt. 
    - Hier ein Beispiel:  
    Das Profil „DCAT-AP.de 1.1 Konventionen (1,2,4-12,21,30,32) prüft ob die optional zu nutzende Eigenschaft dcatde:qualityProcessURI vorhanden ist. Bei einem Verstoß kommt folgende grau hinterlegte Fehlermeldung:   
*Optional (K02): Sie könnten mittels dcatde:qualityProcessURI auf eine Webseite, die den Prozess zur Qualitätssicherung des Datasets beschreibt, verweisen.
Ort:[Fokusknoten] - [https://ckan.govdata.de/dataset/1c292363-5a7c-4131-9bb8-9ac05fdf34c6] - [Ergebnispfad] - [http://dcat-ap.de/def/dcatde/qualityProcessURI]*

Hinweis: Bei den von der SEMIC bereitgestellten Prüfschemen zu DCAT-AP kam es beim Tests immer wieder zu Fehlermeldungen, die sich keinem konkreten Datensatz (Ort[Fokusknoten] zuordnen lassen. Wir sind bereits im Austausch mit der SEMIC zur Nachbesserung der Prüfschemen. Falls Sie weitere unverständliche Fehlerbeschreibungen finden, erstellen Sie gerne ein Issue in diesem Github-Repo. Vielen Dank für Ihre Mithilfe! 

### Wie kann ich die Validierungsergebnisse auswerten? 

Neben der Ansicht im Browser bietet der Validator die Möglichkeit den Validierungsbericht herunterzuladen. Hierzu stehen verschiedene Formate, wie PDF, Turtle oder RDF-XML zur Verfügung. 

Hinweis: Insbesondere bei der Validierung von mehreren Datensätzen ist es häufig aufgrund der Anzahl der Fehlermeldungen schwer die Übersicht zu gewinnen. Hier stößt das ITB-Online-Tool aktuell noch an seine Grenzen. Wenn Sie die Möglichkeit haben könnten Auswertungen der maschinenlesbaren Validierungsberichte wie RDF-XML hilfreich sein. Teilen Sie uns auch gerne Ihre Erfahrungen oder Tipps mit, so dass auch andere davon profitieren können. :+1: 



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

 \#  | Subjekt              | Prädikat            | Objekt 
-----|----------------------|---------------------|--------------------------------
 #01 | `dcat:CatalogRecord` | `foaf:primaryTopic` | `dcat:Catalog`, `dcat:Dataset`
 #02 | `dcat:CatalogRecord` | `dct:source`        | `dcat:CatalogRecord`
 #03 | `dcat:Catalog`       | `dct:hasPart`       | `dcat:Catalog`
 #04 | `dcat:Catalog`       | `dct:isPartOf`      | `dcat:Catalog`
 #05 | `dcat:Catalog`       | `dcat:record`       | `dcat:CatalogRecord`
 #06 | `dcat:Catalog`       | `dcat:catalog`      | `dcat:Catalog`
 #07 | `dcat:Catalog`       | `dct:creator`       | `foaf:Agent`
 #08 | `dcat:Catalog`       | `dcat:dataset`      | `dcat:Dataset`
 #09 | `dcat:Catalog`       | `dct:publisher`     | `foaf:Agent`
 #10 | `dcat:Dataset`       | `dcat:contactPoint` | `vcard:Kind`
 #11 | `dcat:Dataset`       | `dcat:distribution` | `dcat:Distribution`
 #12 | `dcat:Dataset`       | `dct:publisher`     | `foaf:Agent`
 #13 | `dcat:Dataset`       | `dct:temporal`      | `dct:PeriodOfTime`
 #14 | `dcat:Dataset`       | `dct:hasVersion`    | `dcat:Dataset`
 #15 | `dcat:Dataset`       | `dct:isVersionOf`   | `dcat:Dataset`
 #16 | `dcat:Dataset`       | `dct:source`        | `dcat:Dataset`
 #17 | `dcat:Dataset`       | `adms:identifier`   | `adms:Identifier`
 #18 | `dcat:Dataset`       | `adms:sample`       | `dcat:Distribution`
 #19 | `dcat:Dataset`       | `dct:creator`       | `foaf:Agent`
 #20 | `dcat:Distribution`  | `spdx:checksum`     | `spdx:Checksum`
 #21 | `dct:PeriodOfTime`   | `time:hasBeginning` | `time:Instant`
 #22 | `dct:PeriodOfTime`   | `time:hasEnd`       | `time:Instant`
 
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
- für `dct:PeriodOfTime` werden die `schema`-Eigenschaften nicht getestet (für DCAT-AP.de 1.1 noch relevant)
- `spdx:Checksum` erlaubt *nur* SHA1
- es werden bereits Klassen geprüft, die in DCAT-AP.de 1.1 nicht enthalten sind (führt nicht zu Fehlern)

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
- es werden bereits Klassen geprüft, die in DCAT-AP.de 1.1 nicht enthalten sind (führt nicht zu Fehlern)

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
