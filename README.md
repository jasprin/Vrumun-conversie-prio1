# Vrumun conversie dataset Prio1

## Patient (mother)
_Should have_
* Add _gender extension with the Dutch display “Vrouw”

## Organization
_**Must have**_
* Add organization.type.coding:
    * system: http://nictiz.nl/fhir/NamingSystem/organization-type
    * code: G3
    * display: Verloskundigenpraktijk
* Change telecom.extension:TelecomType.system to http://nictiz.nl/fhir/StructureDefinition/zib-ContactInformation-TelecomType

## Practitioner
Has no Practitioner.name, so decide what to do with this resource.

## EpisodeOfCare
_Should have_
* EpisodeOfCare.type.coding.display is in English; change to Dutch “observatie betreffende zwangerschap".

## Pregnancy (Condition)
_**Must have**_
* Change Condition.code.coding.code to:
    * code: 118185001
    * display: bevinding betreffende zwangerschap
* Add Condition.context with a reference to the EpisodeOfCare; there is already a reference from EpisodeOfCare.diagnosis to zib-Pregnancy, so you could use that to create a reference back.

## Gravidity
_Should have_
* Remove profile http://fhir.nl/fhir/StructureDefinition/nl-core-observation
* Change display of LOINC 11996-6 in Observation.code.coding to "Zwangerschappen [aantal] d.m.v. rapportage".
* Add to Observation.code.coding:
    * system: http://snomed.info/sct
    * code: 161732006
    * display: aantal zwangerschappen 

## Parity
_Should have_
* Remove profile http://fhir.nl/fhir/StructureDefinition/nl-core-observation
* Change display of LOINC 11977-6 in Observation.code.coding to "Pariteit [aantal] d.m.v. rapportage".
* Add to Observation.code.coding:
    * system: http://snomed.info/sct 
    * code: 364325004
    * display: pariteit 


## A terme datum
Current bundle: 11778-8 is the estimated delivery date in PWD 2.3 <br>
_**Must have**_
* Profiles must be:
    * http://fhir.nl/fhir/StructureDefinition/nl-core-observation
    * http://nictiz.nl/fhir/StructureDefinition/bc-PregnancyObservation
* Change Observation.code.coding to:
    * system: http://snomed.info/sct
    * code: 161714006
    * display: geschatte datum van partus

## Bloedgroep
_Should have_
* Remove profile http://fhir.nl/fhir/StructureDefinition/nl-core-observation
* Display of Observation.category.coding 49581000146104 is in English; change to Dutch "bevinding betreffende laboratoriumonderzoek".
* Display of Observation.code.coding 883-9 is in English; change to Dutch "AB0-bloedgroep [type] in bloed".
* Display of Observation.valueCodeableConcept.coding is in English; values should be:
    * 112144000 bloedgroep A
    * 112149005 bloedgroep B
    * 165743006 bloedgroep AB
    * 58460004 bloedgroep O
    * UNK onbekend
    * NI geen informatie

## Rhesus D
_**Must have**_
* Change Observation.code.coding to:
    * code: 1305-2
    * display: D Ag [aanwezigheid] in bloed

_Should have_
* Remove profile http://fhir.nl/fhir/StructureDefinition/nl-core-observation
* Display of Observation.category.coding 49581000146104 is in English; change to Dutch "bevinding betreffende laboratoriumonderzoek".
* Display of Observation.valueCodeableConcept.coding is in English; values should be:
    * 165747007 fenotype D-positief
    * 165746003 RhD-negatief
    * UNK onbekend
    * NI geen informatie

## Rhesus c
_Should have_
* Remove profile http://fhir.nl/fhir/StructureDefinition/nl-core-observation
* Display of Observation.category.coding 49581000146104 is in English; change to Dutch "bevinding betreffende laboratoriumonderzoek".
* Display of Observation.code.coding 1159-3 is in English; change to Dutch "Kleine c Ag [aanwezigheid] in erytrocyten".
* Display of Observation.valueCodeableConcept.coding is in English; values should be:
    * 733120009 fenotype c-positief
    * 733119003 fenotype c-negatief
    * UNK onbekend
    * NI geen informatie

## Hb
_**Must have**_
* Change Observation.code.coding to:
    * code: 93846-4
    * display: Hemoglobine [mol/volume] in veneus bloed

_Should have_
* Remove profile http://fhir.nl/fhir/StructureDefinition/nl-core-observation
* Display of Observation.category.coding 49581000146104 is in English; change to Dutch "bevinding betreffende laboratoriumonderzoek".

## Wijze einde zwangerschap
Remove the resource, because it doesn't exist anymore in PWD 3.2 and would need to be mapped first (probably not an easy mapping).

## Datum einde zwangerschap
_Should have_
* Display of Observation.code.coding is in English; change to Dutch "datum van einde van zwangerschap".

## Hoeveelheid bloedverlies
_**Must have**_
* Change Observation.valueQuantity.code to "ml" (we'll also ask Vrumun to fix the typo).

_Should have_
* Display of Observation.code.coding is in English; change to Dutch "bloedverlies durante partu".

## Tijdstip actief meepersen
_Should have_
* Display of Observation.code.coding is in English; change to Dutch "begin van persen tijdens partus".
* Remove the focus extension to the child Patient
* Add display to Observation.context

## Zwangerschapsduur
_**Must have**_
* Change Observation.valueQuantity.system to "http://unitsofmeasure.org".

_Should have_
* Remove profile http://fhir.nl/fhir/StructureDefinition/nl-core-observation
* Add display to Observation.context

## Apgarscore
_Should have_
* Remove profile http://fhir.nl/fhir/StructureDefinition/nl-core-observation
* Observation.subject is missing a display, but not enough information to add this.
* Add display to Observation.context

## Geboortegewicht
_**Must have**_
* Add to Observation.code.coding:
    * system: http://loinc.org 
    * code: 29463-7"
    * display: Lichaamsgewicht [massa]

_Should have_
* Change display of LOINC 8339-4 in Observation.code.coding to "Lichaamsgewicht^bij geboorte [massa] d.m.v. meting".
* Observation.subject is missing a display, but not enough information to add this.
* Add display to Observation.context

## Delivery
_Should have_
* Display of Observation.category.coding 386637004 is in English; change to Dutch "obstetrische verrichting".
* Display of Observation.code.coding 236973005 is in English; change to Dutch "verlossing".
* Add display to Procedure.reasonReference

## Birth
_Should have_
* Add display to Procedure.partOf
* Display of Observation.category.coding 386637004 is in English; change to Dutch "obstetrische verrichting".
* Display of Observation.code.coding 3950001 is in English; change to Dutch "geboorte".
* Procedure.subject is missing a display, but not enough information to add this.
* Add display to Observation.context
* Add display to Procedure.reasonReference

## Patient (Child)
Mostly empty in this bundle, needs some more testing.

## Validation
```
java -jar validator_cli.jar -version 3.0 -ig nictiz.fhir.nl.stu3.geboortezorg#1.3.3 -display-issues-are-warnings -sct nl -language nl -html-output validation.html fhir/*.json
```