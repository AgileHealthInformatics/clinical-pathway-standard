# HPDS Frailty & Multimorbidity Neighbourhood Care Demonstrator

An interactive, self-contained demonstrator showing how the proposed **Healthcare Pathway Description Standard (HPDS) WD 0.3** could be used to describe, catalogue and analyse **frailty and multimorbidity neighbourhood-care pathways**.

The demonstrator explores a catalogue-first approach in which the pathway is treated as a **governed, technology-neutral business artefact**, distinct from the organisations, systems and interfaces used to implement it locally.

> **Status:** Informative demonstrator only. HPDS WD 0.3 is a Working Draft. The catalogue is a reference catalogue for local validation. It does not assert that any locality currently operates these pathways, that any pathway is clinically approved, or that the catalogue is HPDS conformant.

## Why this demonstrator exists

Neighbourhood care is a useful test for a pathway-description standard because the end-to-end model of care commonly spans multiple organisational and professional boundaries.

A frailty or multimorbidity pathway may involve:

- the person and their carers;
- general practice;
- community nursing and therapy;
- pharmacy;
- social care;
- mental health;
- urgent community response;
- virtual wards and hospital-at-home;
- acute services;
- care homes;
- voluntary, community, faith and social enterprise organisations.

No single provider or EPR necessarily owns the complete journey.

HPDS therefore asks whether the pathway itself can be represented independently as a stable artefact around which services, information and local implementations can be coordinated.

The core model demonstrated is:

```text
PathwayCatalogue
        ↓
CatalogueEntry
        ↓
HealthcarePathway
        ↓
PathwayImplementation
```

The catalogue supports discovery and governance. The `HealthcarePathway` carries the enduring clinical and business meaning. `PathwayImplementation` records how a locality realises that definition using particular organisations, teams, systems, interfaces and local deviations.

## Operability, not interoperability alone

This demonstrator deliberately uses **operability** as the broader architectural concern.

A pathway is operable when its meaning, responsibilities, information, decisions, transitions and controls remain understandable and usable across professional, organisational, technical and temporal boundaries.

Technical and semantic interoperability remain important, but they are treated as **enabling components of operability**, not as evidence that the pathway as a whole can operate successfully.

For example, systems may exchange data correctly while the pathway still fails because:

- responsibility is unclear;
- information is unavailable to the right role;
- tasks are not coordinated;
- plans are duplicated or out of date;
- escalation routes are ambiguous;
- information arrives too late to support a decision.

## Catalogue contents

The embedded reference catalogue currently contains:

- **38 catalogue entries**;
- **35 care pathways**;
- **3 governance processes**;
- **9 coordination domains**;
- **33 working catalogue fields**;
- **16 public evidence sources**, plus two project/design sources;
- **40 local discovery questions**.

The three governance-process entries are retained because they are relevant to operating and assuring neighbourhood care, but they are **not claimed as `HealthcarePathway` definitions**. Their subject is the service or operating model rather than an individual subject of care.

## Coordination domains

The catalogue is organised into nine domains:

1. **Population identification & enrolment**  
   Identifying people who may benefit from proactive neighbourhood coordination and deciding how they enter the model.

2. **Holistic assessment & personalised planning**  
   Comprehensive assessment, what-matters discussions, care planning, carer needs and functional or cognitive review.

3. **Medicines & multimorbidity optimisation**  
   Structured medication review, polypharmacy, treatment burden, adherence and community-pharmacy support.

4. **Proactive neighbourhood coordination**  
   MDT review, longitudinal monitoring, social prescribing, falls prevention and proactive care-home support.

5. **Deterioration & urgent neighbourhood response**  
   Recognition and management of deterioration in the person's usual residence, including UCR and escalation.

6. **Admission avoidance & hospital-at-home**  
   Step-up virtual wards, same-day specialist assessment and community diagnostics that support acute care outside hospital.

7. **Transitions, discharge & recovery**  
   Hospital discharge, reablement, step-down virtual wards and post-discharge reconciliation.

8. **Cognition, advance care & palliative coordination**  
   Dementia coordination, advance care planning, escalation preferences and palliative/end-of-life care.

9. **Governance, review & learning**  
   Care-plan review after significant change and supporting governance processes for learning, information quality and outcomes.

These are **catalogue classifications**, not pathway stages.

## Interactive views

The demonstrator contains nine views.

### 1. Overview

Introduces the catalogue-first proposition, the definition/implementation separation and the distinction between operability and interoperability.

It also shows current catalogue status, including the remaining Level 1 authoring gaps.

### 2. Browse catalogue

Search and filter all 38 entries by coordination domain and evidence status.

Each entry displays its:

- catalogue ID;
- domain;
- pathway family;
- artefact class;
- lifecycle status;
- coordinating function;
- evidence status.

Selecting an entry opens the HPDS artefact view.

### 3. HPDS artefact

Projects the selected working-catalogue row into HPDS WD 0.3 concepts.

The view separates:

- pathway-definition content;
- information and operability;
- evidence;
- the draft JSON projection.

It preserves the original source text and identifies unresolved authoring requirements rather than inventing values.

Each care-pathway entry has:

- a separate catalogue-entry ID;
- a pathway-definition URI;
- version `0.1.0`;
- lifecycle status `draft`;
- authority status `unapproved`;
- intended use `analysis; service-design`.

Pathway owners, explicit exit points/criteria and principal stages remain authoring gaps.

### 4. Neighbourhood orchestration

Shows a **schematic**, not an executable workflow.

The selected person or population is placed at the centre, surrounded by participating services and roles, with the care-coordination function shown separately.

The view helps ask:

- who participates;
- who coordinates;
- what information must be shared;
- what decisions or escalations matter;
- what the shared care plan must contain;
- what dependencies must be satisfied.

It also analyses recurring services and coordination capabilities across the selected domain.

### 5. Single Patient Record lens

Uses each pathway to ask three separate questions:

1. **What must the SPR surface?**
2. **What information does the pathway update?**
3. **What orchestration still has to occur outside the shared record?**

This is intended to prevent a shared record from being treated as synonymous with coordinated care.

The architectural distinction is:

```text
HPDS
describes what coordinated care requires

SPR
provides part of the shared information environment

local systems and orchestration services
perform the operational work
```

### 6. HPDS conformance levels

Shows the four cumulative WD 0.3 conformance levels:

- **Level 1: Catalogue-ready**
- **Level 2: Structured**
- **Level 3: Semantically bound**
- **Level 4: Computably specified**

Level 1 is shown as the **initial target**, not the current state.

For each entry, the demonstrator performs a source-to-standard completeness assessment against the WD 0.3 minimum dataset. This is not a conformance declaration.

### 7. Reference definition versus local implementation

Shows the separation between the reference pathway and its local realisation.

The reference definition contains clinical and business meaning such as:

- population;
- purpose;
- activities;
- decisions;
- roles and services;
- information requirements;
- intended outcomes.

The implementation layer is where a locality records:

- implementing organisations;
- named teams;
- local services and locations;
- systems and records;
- interfaces and information exchanges;
- automation artefacts;
- assurance evidence;
- deviations;
- local additions and measures;
- validation status.

The demonstrator reads the implementation structure embedded from the working catalogue.

### 8. Field mapping

Maps all **33 working catalogue fields** to their intended HPDS WD 0.3 target or boundary.

Examples include:

| Working catalogue field | HPDS interpretation |
| --- | --- |
| Pathway ID | `CatalogueEntry.entryIdentifier` |
| Pathway Definition URI | `HealthcarePathway.identifier` |
| Pathway Family | `HealthcarePathway.name` |
| Target Person / Population | `Population.inclusionCriterion` |
| Trigger / Entry Context | `EntryPoint.criterion` |
| Purpose | `HealthcarePathway.purpose` |
| Desired Outcomes | `Outcome` |
| Participating Services / Roles | `Role` / `Service` |
| Principal Activities | `Activity` |
| Key Decisions / Escalation Points | `DecisionPoint` candidate content |
| Care Setting(s) | `CareSetting` |
| Key Upstream Information | `InformationRequirement` |
| Information Produced / Updated | `InformationProduct` |
| Key Clinical / Social Data Objects | `ClinicalConcept` |
| Interoperability Requirements | `InteroperabilityRequirement` |
| Source IDs | `EvidenceSource` references |
| Related Pathways (Candidate) | pathway relationships such as `includes`, `transitionsTo`, `escalatesTo` |

Two fields are deliberately represented as extensions pending further standards work:

- **Care Coordinator / Accountable Function**
- **Required Digital & Care Coordination Capabilities**

### 9. Evidence & discovery

Contains three tabs:

- **Source register**
- **Catalogue metadata**
- **Discovery questions**

The source register includes project/design sources and public guidance from NHS England, NICE and the British Geriatrics Society.

Evidence provenance is deliberately kept separate from clinical authority.

A pathway being well supported by guidance does not make the catalogue entry clinically approved or operationally authoritative.

## Candidate pathway relationships

The catalogue contains a `Related Pathways (Candidate)` field using relationships such as:

- `includes`
- `transitionsTo`
- `escalatesTo`

These relationships are analytical candidates derived from the pathway text and require clinical validation.

The demonstrator exports `includes` where it can be represented directly. `transitionsTo` and `escalatesTo` remain candidate content until the relevant exit points, events, branches or decision elements have been formally authored.

## Draft JSON export

Individual entries can be exported as:

```text
<PATHWAY-ID>_HPDS_WD03_draft_projection.json
```

The export uses HPDS WD 0.3 property names and structure and contains:

- the catalogue entry;
- the draft pathway definition;
- evidence references;
- provenance;
- constraints;
- extensions;
- candidate relationship content;
- an explicit list of authoring gaps.

The JSON is intentionally labelled a **draft projection**.

It does not claim conformance merely because source content can be mapped into the HPDS structure.

Governance-process entries are also explicitly identified as outside the claimed population of HPDS pathway definitions.

## Catalogue governance

Current catalogue metadata includes:

```text
Catalogue version:       0.1.0
Release date:            2026-09-17
Publisher:               Agile Health Informatics Ltd (working catalogue)
Governance authority:    Not yet assigned
Target conformance:      Level 1 for care-pathway entries
Current conformance:     Not claimed
```

The outstanding Level 1 issues recorded by the demonstrator include:

- pathway owner;
- exit points and exit criteria;
- principal stages;
- catalogue governance authority.

## Recommended way to use the demonstrator

A useful workshop sequence is:

```text
1. Select a pathway family
        ↓
2. Review the HPDS artefact
        ↓
3. Examine neighbourhood orchestration
        ↓
4. Apply the SPR lens
        ↓
5. Review conformance / authoring gaps
        ↓
6. Define the local implementation
        ↓
7. Validate against evidence and discovery questions
```

The starting point should be the **model of care**, not a technology choice.

For example, a team considering deterioration of a frail person at home can first establish:

- what the pathway is trying to achieve;
- who should participate;
- what decisions need to be made;
- what information is required;
- what must be visible through an SPR;
- what still requires task coordination or workflow;
- what local systems and services actually implement those requirements.

## Intended audiences

The demonstrator may be useful to:

- clinical pathway owners;
- neighbourhood-care leaders;
- clinical informaticians;
- enterprise and solution architects;
- EPR and shared-record programmes;
- interoperability and data specialists;
- service designers;
- information-governance teams;
- digital and clinical-safety assurance teams;
- standards developers.

## Running locally

The application is a single self-contained HTML5 file.

No package installation, build process, web server or external JavaScript library is required.

Rename the supplied file to:

```text
index.html
```

if necessary, then open it in a modern browser.

The application itself works offline. Links to public evidence sources require internet access.

## Publishing with GitHub Pages

If `index.html` is stored at the repository root:

1. Open the repository **Settings**.
2. Select **Pages**.
3. Choose **Deploy from a branch**.
4. Select the publishing branch, normally `main`.
5. Select the repository root.
6. Save.

GitHub Pages will publish the demonstrator as a static site.

## Technical design

The demonstrator deliberately has no external runtime dependency.

It uses:

- semantic HTML5;
- embedded CSS;
- vanilla JavaScript;
- inline SVG;
- embedded JSON application data;
- responsive layout;
- accessible controls;
- light/dark theme;
- print styling;
- context-sensitive help;
- client-side filtering and navigation;
- draft JSON export.

The complete catalogue and source register are embedded in the HTML so the demonstrator can be distributed as a single file.

## Limitations

This is a standards demonstrator, not a production pathway-management or workflow application.

Important limitations include:

- HPDS WD 0.3 remains a Working Draft;
- the catalogue is a reference model for local validation;
- no current HPDS conformance is claimed;
- pathway relationships require clinical validation;
- generated orchestration diagrams are schematic;
- Level 2 structural and behavioural graphs have not been fully authored;
- Level 3 semantic bindings have not been completed;
- Level 4 computable criteria are not implemented;
- local implementation data are largely unvalidated;
- the demonstrator does not make clinical decisions;
- the demonstrator does not execute clinical workflow;
- source evidence does not confer local clinical authority.

## Relationship to other standards and technologies

HPDS is not intended to replace implementation or exchange standards.

A pathway described in HPDS may subsequently be realised or projected using technologies such as:

- HL7 FHIR;
- BPMN;
- CMMN;
- DMN;
- workflow or orchestration platforms;
- EPR systems;
- shared care records;
- terminology services;
- local integration services.

HPDS addresses a different problem: maintaining the **pathway itself** as a reusable, governed, technology-neutral clinical and business artefact.

## Repository status

This repository should currently be treated as an **experimental reference implementation and discussion resource**.

Feedback is especially useful on:

- whether the pathway/implementation boundary is clear;
- whether operability is a useful organising concept;
- whether the minimum dataset is sufficient for catalogue use;
- whether the four conformance levels are coherent;
- whether care coordination requires an explicit first-class HPDS relationship;
- whether digital/care-coordination capabilities should remain derived or become part of the model;
- whether the relationship model is sufficient for neighbourhood pathways;
- whether reference pathways can be specialised locally without fragmentation;
- whether the model complements rather than duplicates existing clinical, process and interoperability standards.

## Files

A minimal repository can contain:

```text
index.html    Frailty & Multimorbidity Neighbourhood Care HPDS demonstrator
README.md     This file
```

The working spreadsheet catalogue and HPDS WD 0.3 specification may be maintained separately or added to the repository where publication rights and version control permit.

## About HPDS

The **Healthcare Pathway Description Standard (HPDS)** is an experimental standards proposal for representing healthcare pathways as governed, technology-neutral business artefacts suitable for:

- cataloguing and discovery;
- versioning and lifecycle management;
- clinical and business description;
- provenance and evidence;
- semantic binding;
- pathway relationships and specialisation;
- local implementation mapping;
- conformance assessment.

This demonstrator uses **HPDS WD 0.3** and the **Frailty and Multimorbidity Neighbourhood Care Pathway Catalogue 0.1.0**.
