# HPDS Acute Admissions & Discharge Catalogue Demonstrator

An interactive, self-contained demonstrator showing how the proposed **Healthcare Pathway Description Standard (HPDS) WD 0.3** can be applied to an existing acute admissions and discharge clinical pathway catalogue.

The demonstrator uses the **UHSx Acute Admissions & Discharge Clinical Pathway Catalogue** as source material and explores whether a spreadsheet-based catalogue can be projected into governed, technology-neutral healthcare pathway business artefacts while keeping local implementation detail separate.

> **Status:** Informative demonstrator. HPDS WD 0.3 is a Working Draft. The imported catalogue rows are not asserted to be conformant HPDS pathway definitions, clinically approved pathways, or authoritative descriptions of current local workflow.

## Why this demonstrator exists

Clinical pathway catalogues are often useful operational documents, but their structure is usually local to a particular spreadsheet, programme, EPR implementation or modelling exercise.

HPDS explores a different proposition: that a healthcare pathway can be managed as a **persistent, governed, technology-neutral business artefact** with explicit identity, lifecycle, provenance, structure, semantics and relationships.

This demonstrator tests that proposition against a substantial existing catalogue rather than against a synthetic example.

Its central design separates:

```text
PathwayCatalogue
        ↓
CatalogueEntry
        ↓
HealthcarePathway
        ↓
PathwayImplementation
        ↓
Pathway instance
```

The first four concepts are represented by the HPDS model. A pathway instance, meaning the actual course of care experienced by an individual, is outside the normative scope of the demonstrator.

## What is in the demonstrator

The HTML application contains **56 source pathway families** organised into seven acute-care catalogue groups.

It provides eight interactive views:

1. **Overview**  
   Introduces the catalogue-first proposition and the distinction between pathway definition, catalogue entry, local implementation and patient-level pathway instance.

2. **Browse catalogue**  
   Searches and filters the 56 pathway families by clinical group, readiness priority and evidence status.

3. **Pathway definition**  
   Projects a selected catalogue row into HPDS-oriented concepts while preserving the original source text and identifying missing authoring information.

4. **Definition vs implementation**  
   Separates enduring clinical and business meaning from local systems, sites, EPR capabilities, interfaces and implementation-specific detail.

5. **Conformance lab**  
   Compares each source row with the HPDS WD 0.3 minimum pathway-definition dataset. This is a completeness assessment, not a conformance declaration.

6. **24-field mapping**  
   Shows how each source catalogue field maps to the HPDS conceptual model and where decomposition or further authoring would be required.

7. **Catalogue anatomy**  
   Shows how spreadsheet rows, catalogue entries, pathway definitions, structured elements and implementation mappings relate.

8. **Evidence & discovery**  
   Retains the source register and local discovery questions so that provenance and unresolved implementation questions remain visible.

## Key design principles demonstrated

### Catalogue first

The catalogue is treated as a governed collection of pathway definitions rather than as the definition of the pathway model itself.

### Technology-neutral pathway definition

The pathway definition contains enduring clinical and business meaning.

Named local systems, sites, EPR products, interfaces and operational arrangements belong to `PathwayImplementation`.

This means that replacing an EPR, PAS or integration product should not require the clinical pathway identity itself to change.

### Definition before implementation

The demonstrator distinguishes between:

- what the pathway is intended to achieve;
- the activities, roles, information and decisions it requires;
- how a particular organisation chooses to realise it.

### Evidence and authority are different

Source provenance is preserved for each catalogue row.

An item being well evidenced does **not** mean that it is clinically approved, operationally authoritative or HPDS conformant.

### Missing information is not invented

Where the source catalogue does not provide required HPDS information, the interface displays an **Authoring gap** rather than silently inferring a value.

Typical gaps include:

- purpose;
- owner;
- version;
- lifecycle status;
- authority status;
- intended use;
- expected outcomes;
- formal decision-point declarations.

## Source catalogue

The underlying catalogue was developed as an acute admissions and discharge reference resource for University Hospitals Sussex.

The demonstrator includes:

- 56 pathway families;
- seven clinical groups;
- 24 working catalogue fields;
- evidence references;
- local validation questions;
- EPR and integration-readiness information.

The source catalogue contains both clinical/business content and implementation-specific material. One of the main purposes of the demonstrator is to separate those two layers.

## HPDS mapping

Examples of source-to-HPDS mappings include:

| Catalogue field | HPDS interpretation |
| --- | --- |
| Pathway ID | `HealthcarePathway.identifier` |
| Pathway Family | `HealthcarePathway.name` |
| Clinical Trigger / Referral Context | `Population` and `EntryPoint` candidate content |
| Service Role | `Role` and/or `Service` |
| Typical Investigation / Procedure(s) | `Activity` |
| Pathway Phase | `PathwayStage` |
| Key Upstream Information | `InformationRequirement` |
| Service Outputs / Information Generated | `InformationProduct` |
| Downstream Destination / Decision | `ExitPoint`, and where justified `DecisionPoint` / `PathwayBranch` |
| Key Clinical Data Objects | `ClinicalConcept` and information-model content |
| Source IDs | `EvidenceSource` references |
| Known Organisation Site / Service Context | `PathwayImplementation` |
| Required EPR Capabilities | implementation / assurance metadata |
| Local Validation Questions | implementation-authoring aid |

The mapping is deliberately cautious. Free text in a spreadsheet is treated as **candidate source content**, not automatically as a formally structured HPDS element.

## Conformance model

HPDS WD 0.3 defines four cumulative conformance levels:

- **Level 1: Catalogue-ready**  
  Persistent identity, minimum pathway description, governance metadata and a human-readable catalogue record.

- **Level 2: Structured**  
  Identified pathway elements with explicit structural and behavioural relationships.

- **Level 3: Semantically bound**  
  Clinically significant concepts and mandatory information requirements carry versioned semantic bindings or are explicitly declared local terms.

- **Level 4: Computably specified**  
  Selected criteria and temporal constraints can be represented using a declared computable expression profile.

The demonstrator does **not** claim that imported source rows meet Level 1. It shows which elements can be mapped from the existing catalogue and which require additional authorised pathway authoring.

## How to use the demonstrator

Start with **Browse catalogue** and select a pathway family of interest.

Then use the views in sequence:

```text
Browse source catalogue
        ↓
Inspect HPDS pathway projection
        ↓
Review definition / implementation separation
        ↓
Examine conformance gaps
        ↓
Review field mappings
        ↓
Trace evidence and local discovery questions
```

The demonstrator is particularly useful for workshops involving:

- clinical pathway owners;
- clinical informatics teams;
- enterprise and solution architects;
- EPR programme teams;
- interoperability specialists;
- information governance teams;
- service designers;
- digital assurance teams.

It can be used to discuss what belongs in a stable pathway definition and what should remain specific to a local implementation.

## Running locally

The demonstrator is a single self-contained HTML5 file.

No package installation, build process, web server or external JavaScript library is required.

Open:

```text
index.html
```

in a modern web browser.

The application works offline. Links to external evidence sources obviously require internet access.

## GitHub Pages

If the file is stored as `index.html` at the root of the repository, it can be published directly using GitHub Pages.

Typical setup:

1. Open the repository **Settings**.
2. Select **Pages**.
3. Choose **Deploy from a branch**.
4. Select the branch containing `index.html`, usually `main`.
5. Select the repository root as the publishing folder.
6. Save.

GitHub will then provide the public Pages URL.

## Technical design

The demonstrator is deliberately lightweight:

- semantic HTML5;
- embedded CSS;
- vanilla JavaScript;
- embedded JSON application data;
- no framework;
- no CDN;
- no external runtime dependency;
- responsive desktop/mobile layout;
- light and dark themes;
- print styling;
- JSON projection export for individual pathways.

Because the source data is embedded in the HTML, the demonstrator can be distributed as a single file.

## Limitations

This is a demonstrator, not a production pathway-management application.

Important limitations include:

- HPDS WD 0.3 is still a Working Draft;
- source catalogue rows are not automatically HPDS-conformant pathway definitions;
- generated pathway-flow sketches are informative and are not Level 2 behavioural models;
- candidate mappings require clinical and governance validation;
- local organisational workflow may differ from the source catalogue;
- named systems and interfaces reflect implementation evidence, not enduring pathway semantics;
- the demonstrator does not execute clinical workflow;
- it does not make clinical decisions;
- it does not replace clinical governance, safety assurance or formal standards conformance testing.

## Relationship to implementation technologies

HPDS is not intended to replace technologies or standards such as:

- HL7 FHIR;
- BPMN;
- CMMN;
- DMN;
- workflow/orchestration platforms;
- EPR systems;
- PAS;
- shared care records;
- terminology services.

Instead, HPDS is intended to describe the **pathway as an enterprise and clinical business artefact**, which can then be mapped to appropriate technical realisations.

## Repository status

This repository should currently be treated as an **experimental reference implementation and discussion resource**.

Feedback is particularly useful on:

- whether the pathway / implementation boundary is clear;
- whether the HPDS minimum dataset is sufficient for catalogue use;
- whether the four conformance levels are useful;
- whether pathway relationships and specialisation are expressive enough;
- whether the standard adds value beyond existing spreadsheet catalogues;
- whether the model supports cross-organisational care as well as acute-provider pathways;
- where the proposed model overlaps unnecessarily with existing healthcare or process standards.

## Licence and reuse

No licence is asserted by this README.

Before redistributing or reusing source catalogue material, evidence extracts or organisational content, check the applicable rights and licences for those sources.

The HPDS specification itself should carry its own explicit licensing and publication terms before wider reuse is encouraged.

## Files

```text
index.html     Interactive HPDS WD 0.3 Acute Admissions & Discharge demonstrator
README.md      This file
```

## About HPDS

**Healthcare Pathway Description Standard (HPDS)** is an experimental standards proposal for representing healthcare pathways as governed, technology-neutral business artefacts suitable for cataloguing, comparison, specialisation, provenance, semantic binding and implementation mapping.

The current demonstrator uses **HPDS WD 0.3**.
