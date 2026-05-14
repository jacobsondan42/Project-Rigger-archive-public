# JD Decomposition Records — Burlingame

**Status:** Updated canonical instance of the per-agency lateral reference file for Burlingame intake. Third-spec landing (Zoning Technician) reframes the agency file from water-cohort-only to agency-wide, formalizing what the filename convention always implied: this file's primitive unit is the agency (City of Burlingame), with cohorts/departments as sub-organizations. The water cohort remains the substantive majority of records; the Zoning Technician landing is the first non-water spec and the first Planning Department spec in the agency file. Composed under the working-window discipline: per-spec skeleton → record → rollup staging.

**Filename convention:** `jd_decomposition_records_<agency>_<UTC-timestamp>.md` under Timestamped lateral versioning (Cross-session handshake protocol sub-part 1(c)). Agency identifier is single-token at the municipal level; departmental/cohort organization happens within the file via `org_unit` per-record metadata and Section 4 subsection structure.

**Rubric version applied:** v2.0 — `rubric_jd_decomposition_20260511T230000Z.md`.

**Specs landed at this canonical timestamp:** 4 total (3 Water Division + 1 Planning Department).
- Water Division (9-spec cohort, 3 landed): Water Division Manager (partial fidelity), Water System Operator Trainee (verbatim), Water System Operator (verbatim).
- Planning Department (cohort cardinality TBD, 1 landed): Zoning Technician (verbatim).

**Recovery provenance.** The substantive decomposition work for the Burlingame cohort was originally executed in conversation thread `c12c0652-966a-46b0-820f-258b2abb9749` (2026-05-12 PT) but was not canonicalized at composition; the generator scripts (`gen_bg_water.py`, `specs_bg_*.py`, runner) and rendered artifact existed only in that session's filesystem and were lost at session boundary. This file reconstructs from conversation-history recovery via `conversation_search`, marking per-record fidelity (verbatim-recovered / partial / placeholder-for-source-rederivation). The recovery loss is itself a worked instance of the §Q lossy-state anti-pattern surfaced at Thread 11 close and a worked instance of the broader principle this file's existence operationalizes: **structured-data artifacts must be canonicalized at composition, not deferred.**

**Migration note.** The existing `jd_decomposition_records_20260515T030000Z.md` monolith (17 records across SB / Hayward / SSF / Samtrans / Menlo Park / Newark) will be migrated to per-agency files in a follow-on chain entry, per stakeholder decision to migrate-rather-than-freeze. Until that migration lands, the monolith remains the canonical source for those 17 records. Cross-agency synthesis (envelope-design patterns, substrate-orthogonality findings, cone-hypothesis pressure-test record, manager-isn't-generalized reframe) will live in a separate `jd_decomposition_synthesis_<ts>.md` lateral instantiated alongside the migration.

---

## Section 1 — Agency schema and conventions

### Class code conventions

Burlingame uses a letter-prefix system observed across multiple departments:
- **S-prefix** (e.g., S502, S507, S605): non-exempt classifications, primarily in AFSCME bargaining units. Operations-trades and journey-level classes in the Water Division carry S-prefix codes.
- **B-prefix** (e.g., B500, B-501, B503): exempt classifications, primarily in BAMM Unit. Supervisor and management classes in the Water Division carry B-prefix codes.
- **A-prefix** (e.g., A110): observed first on the Zoning Technician (Planning Department) landing. Schema-discovery in this canonical instance; semantics of the A-prefix not yet established. The A110 / S/B distinction may correlate with department (Planning vs Public Works) or with classification family rather than exempt/non-exempt status — Zoning Technician is AFSCME 829 Maintenance Unit Non-Exempt, parallel to S-prefix non-exempt water classes. Schema-discovery is iterative; additional non-water specs will populate the A-prefix semantic interpretation.

**Known data anomaly:** `S507` is shared by two distinct classifications — Water Quality and Meter Technician (WQMT) and Water Service and Operations Technician (WST). Both specs carry S507 in footers. Status: unresolved data anomaly; likely HR data error or migration artifact. Tracked as a `duplicate_class_code_flag` on both records when those records land.

**Schema-discovery note.** The class-code prefix discovery is now multi-instance: S and B prefixes were observed during the original water-cohort intake; A prefix was observed during the first non-water spec intake. This validates the protocol's implicit assumption that schema-discovery is iterative across multi-cohort agency intakes rather than one-shot at first acquisition. Candidate protocol-update item flagged for the protocol-revision batch.

### Bargaining units present in this agency intake

| Unit | Specs | Org unit | Exempt status |
|---|---|---|---|
| AFSCME 829 Maintenance Unit | WSOT, WSO | Water Division | Non-Exempt |
| AFSCME 829 Maintenance Unit | Zoning Technician (A110) | Planning Department | Non-Exempt |
| AFSCME 2190 | WST, WMR, WQMT | Water Division | Non-Exempt |
| AFSCME 829 (Worker class) | WQMLW | Water Division | Non-Exempt |
| AFSCME 829 EXEMPT | WQS | Water Division | Exempt — bargaining-unit asymmetry |
| BAMM Unit | WOS, WDM | Water Division | Exempt |

**Bargaining-unit asymmetry at the supervisor stratum** (within Water Division). WQS is in AFSCME 829 EXEMPT (workers' union, exempt status) while WOS is in BAMM Unit (management union, exempt). Both are supervisor-class equivalents structurally; the union assignment differs. Likely historical artifact of how the two ladders accreted into a single division. Worth flagging in the trust-schema / bias-disclosure axis.

**Cross-department bargaining-unit anomaly** (new at this canonical instance). Zoning Technician (Planning Department) is in **AFSCME 829 Maintenance Unit** — the same bargaining unit as Water System Operator Trainee and Water System Operator (heavy-labor field positions in Water Division). A counter-based knowledge-worker class in the Maintenance Unit is structurally surprising; one would predict Planning Department clerical/technical classes to be in a different bargaining unit (e.g., AFSCME 2190 or a Planning-specific unit). Possible explanations: (a) Burlingame's smaller-municipality bargaining-unit organization is intentionally broader than function-typed; (b) Zoning Technician (1993 vintage) was originally classified into Maintenance Unit and never re-organized despite Planning Department migration; (c) historical artifact of when the Planning Department was a sub-function of Public Works. Worth flagging for HR-cycle reconciliation review.

### JD design house autonomy-language hierarchy

Burlingame uses a four-tier autonomy framing in the front-matter "Supervision Received" or class-summary lines:

1. **"Under direction"** — used at management stratum (WDM, WQS).
2. **"Under general direction"** — used at journey stratum in older specs (e.g., WQMT 2008).
3. **"Under general supervision"** — used at lead stratum in newer specs (WQMLW 2015) and at WSO formal framing.
4. **"Under close supervision"** — used at trainee/entry stratum (WSOT formal framing).

**Cross-cycle direction-language inversion observed.** WQMT (Aug 2008) uses "Under general direction" while WQMLW (revised April 2015) uses "Under general supervision" — the higher-stratum class has *less autonomous* formal language. This is a cross-cycle inversion: the 2008 and 2015 specs were written in incompatible registers, not under a consistent autonomy hierarchy. Implication for cone-hypothesis testing: the autonomy-language signal is noisy in this corpus, and scope-qualifier signals (individual_task → crew_member → crew_lead → crew_supervisor → division_management) are the cleaner cone-measurement axis for operations-trades.

**Spec-vs-description tension.** WSO formal framing says "Under close supervision" but the work description in the same spec says "Independently, or as a member of a crew." Direct JD-design tension between HR formal language and operational truth. Worth flagging as `spec_internal_consistency_flag`.

### Title-change history

**September 2024 retitling.** Two classes were renamed in September 2024 with no substance change to duties:
- Maintenance Worker I → Water System Operator Trainee (WSOT)
- Water Maintenance Worker II → Water System Operator (WSO)

Both spec footers carry explicit `FORMER TITLE:` and `SEPTEMBER 2024 (TITLE CHANGE)` markers. This is a title-design-as-policy-lever instance — the agency itself documents the title-vs-substance separation directly on the spec, aligning with the framework's title-de-reification posture. Tracked as `title_change_provenance` field on those records.

**Deprecated titles referenced by un-updated specs.** The Water Operations Supervisor spec (revised 12/9/2011) references "Assistant Water Superintendent" as the next-higher class; this title was renamed to "Water Division Manager" in the 2017 revision cycle but the 2011 WOS spec was never updated. Tracked as `spec_staleness_flag` on the WOS record. The Water Meter Repairer spec references "Water Maintenance Worker" and "Service Worker" essential duties; these are deprecated titles superseded by Water System Operator / Water Service and Operations Technician at the September 2024 retitling. Tracked as cross-reference gaps in Section 2.

**Extreme-vintage staleness (cross-department).** The Zoning Technician spec carries footer date `1993` with no subsequent revision marker — 33 years stale at this canonical instance. This is the staleness extreme observed so far in the agency intake; the within-water staleness floor was 2011 (WOS at ~15 years). The 1993 vintage manifests in several content artifacts: (a) the spec includes "use microfiche machines" as a skill requirement; (b) the K/A/S section references "modern office procedures and basic clerical skills" as if in contrast to non-modern alternatives (1993 register); (c) the spec lacks the modern boilerplate framing ("under close supervision" / "under general supervision" tier conventions) the water cohort uses; (d) duplicate phrasing in Essential Functions ("collecting and analyzing data" appears twice in the same paragraph, suggesting copy-edit drift). Tracked as `spec_staleness_flag: extreme_vintage` on the Zoning Technician record. The water cohort's HR review-cycle status (in progress, SB-1100) presumably does not cover Planning Department specs; whether Planning has its own review-cycle status is a forward-work surface.

### Salary band structure

Salary bands are not consistently visible on the spec PDFs in this cohort. Where visible, recorded per-spec. Where not visible, marked as `salary_band: not_visible_on_spec`. Cross-agency comparison (e.g., WDM's salary band relative to SB Public Works Director Matthew Lee's compensation per `san_bruno_seed_export.md`) requires supplemental data acquisition.

### HR review-cycle status

Burlingame HR is currently revising water-utility class specs as part of an in-progress review cycle (referenced as the SB-1100 review-in-progress flag in source materials). This is editorial pressure on the corpus state: spec staleness and accumulated reference-drift are exactly what the review should surface and fix. **Forward work opportunity:** post-review re-fetch of the same specs would give direct cross-cycle data on what the editorial intervention actually changes — direct evidence on lock-in-stasis vs accumulated-drift hypotheses.

---

## Section 2 — Data acquisition protocol

### Source

- **Primary source:** Burlingame city government class spec PDFs published at `burlingame.org/DocumentCenter/View/<docId>/<title>-PDF`.
- **Fetch status:** `web_fetch` on `burlingame.org` returned `host_not_allowed` from the egress proxy (2026-05-12 PT session). Direct web fetch is blocked in this environment.
- **Resolution:** Stakeholder uploaded the nine PDFs to `/mnt/user-data/uploads/` on 2026-05-12 PT. Spec records reference both the original URL (for provenance) and the upload filename.

### Source file inventory

| Spec ID | Title | Org unit | Upload filename | Source URL pattern |
|---|---|---|---|---|
| JDR_BG_WSOT | Water System Operator Trainee | Water Division | `Water_System_Operator_Trainee_-_September_2024.pdf` | `/DocumentCenter/View/...` |
| JDR_BG_WSO | Water System Operator | Water Division | `Water_System_Operator_-_September_2024.pdf` | `/DocumentCenter/View/...` |
| JDR_BG_WST | Water Service and Operations Technician | Water Division | `Water_Service_and_Operations_Technician__PDF_.pdf` | `/DocumentCenter/View/1076/...` |
| JDR_BG_WMR | Water Meter Repairer | Water Division | (TBD) | `/DocumentCenter/View/...` |
| JDR_BG_WQMT | Water Quality and Meter Technician | Water Division | `Water_Quality_and_Meter_Technician__PDF_.pdf` | `/DocumentCenter/View/1074/...` |
| JDR_BG_WQMLW | Water Quality and Meter Lead Worker | Water Division | (TBD) | `/DocumentCenter/View/...` |
| JDR_BG_WOS | Water Operations Supervisor | Water Division | `Water_Operations_Supervisor__PDF_.pdf` | `/DocumentCenter/View/...` |
| JDR_BG_WQS | Water Quality Supervisor | Water Division | `Water_Quality_Supervisor__PDF_.pdf` | `/DocumentCenter/View/...` |
| JDR_BG_WDM | Water Division Manager | Water Division | `Water_Division_Manager__PDF_.pdf` | `/DocumentCenter/View/...` |
| JDR_BG_ZT | Zoning Technician | Planning Department | `Zoning_Technician__PDF_.pdf` | `/DocumentCenter/View/...` |

URLs marked TBD will be reconstructed from the source PDFs when re-uploaded for the gap-filling sessions.

**Cross-department spec-template-reuse observation.** The Zoning Technician PDF carries the page footer text "WATER SERVICE & OPERATIONS TECHNCIAN" (note: misspelled "TECHNCIAN") on both pages — directly inherited from the Water Service and Operations Technician spec template at composition time. The body content is Planning Department appropriate but the footer was never updated. This is direct evidence that Burlingame HR composes specs from prior-spec templates and that footer text is not a reliable provenance signal for spec-content classification. Worth flagging at protocol level: source-inventory validation should not rely on PDF footer text matching the spec title. Candidate protocol-update item for the protocol-revision batch.

### Cross-reference gap registry

Generalized framework feature instantiated in this cohort. Records any spec that references another classification we don't have decomposition records for, with status:

- `existing_not_acquired` — class exists per the agency's published catalog but we don't have its spec
- `deprecated_renamed_to_existing` — referenced title has been renamed; the current title is one we have or could acquire
- `out_of_scope_adjacent` — class exists but sits outside the cohort scope (different department or function family)

| Gap ID | Referenced class | Status | From specs | Context |
|---|---|---|---|---|
| XRG_BG_001 | Lead Water System Operator | existing_not_acquired | JDR_BG_WSO, JDR_BG_WOS | WSO SUPERVISION RECEIVED AND EXERCISED: "Receives general supervision from the Lead Water System Operator and Supervisor positions." Now confirmed at verbatim fidelity from WSO source. Closing this gap would complete the Operations-ladder cone-hypothesis test at the leadworker stratum. The Lead WSO sits between WSO (journey) and WOS (supervisor) on the Operations ladder. |
| XRG_BG_002 | Assistant Water Superintendent | deprecated_renamed_to_existing | JDR_BG_WOS | WOS (2011) references this title; renamed to Water Division Manager in 2017 revision cycle. WOS spec was not updated to reflect the rename. |
| XRG_BG_003 | Water Maintenance Worker | deprecated_renamed_to_existing | JDR_BG_WMR | Referenced by WMR ("See Water Maintenance Worker essential duties"). Renamed to Water System Operator in September 2024. |
| XRG_BG_004 | Service Worker | deprecated_renamed_to_existing | JDR_BG_WMR | Referenced by WMR. Likely renamed to Water Service and Operations Technician at the September 2024 retitling. |
| XRG_BG_005 | Deputy Director of Public Works Operations | out_of_scope_adjacent | JDR_BG_WDM | WDM's next-higher class in the org chart. Upward extension target for cone-hypothesis testing; would also test whether a divergence-point pattern (multiple division managers → one deputy) is a fifth envelope-design pattern. |
| XRG_BG_006 | Meter Reader | out_of_scope_adjacent | JDR_BG_WQMT, JDR_BG_WQMLW | Referenced for absence backup; separate sub-function family. |
| XRG_BG_007 | Irrigation Specialist | out_of_scope_adjacent | JDR_BG_WST | Referenced for coordination on well/irrigation; Parks Department adjacent class. |
| XRG_BG_008 | water service worker | deprecated_renamed_to_existing | JDR_BG_WSOT | WSOT Other Duties: "read water meters and assist water service worker." Lowercase informal flow-text reference. Probably the same target as XRG_BG_004 (Service Worker) — both likely renamed to Water Service and Operations Technician. Distinct entry from XRG_BG_004 preserved because the source-citation text differs ("water service worker" vs "Service Worker") and definitive consolidation would require HR confirmation. Relationship-to-XRG_BG_004 flagged for stakeholder reconciliation. |
| XRG_BG_009 | Planner | existing_not_acquired | JDR_BG_ZT | Zoning Technician DEFINITION: "works under the supervision of the Planner and City Planner." First Planning Department supervisory-chain reference. Status existing_not_acquired pending Burlingame Planning Department catalog acquisition. Likely the journey-tier Planning Department class above Zoning Technician. |
| XRG_BG_010 | City Planner | existing_not_acquired | JDR_BG_ZT | Zoning Technician DEFINITION: "works under the supervision of the Planner and City Planner." Second Planning Department supervisory-chain reference. Status existing_not_acquired. Likely the management-tier Planning Department class above the Planner class. The "Planner and City Planner" dual-reference suggests a two-tier supervisory chain above Zoning Technician parallel to the Water Division's WOS→WDM chain above WSOT. |

---

## Section 3 — Per-spec records

### JDR_BG_WDM — Water Division Manager

**Recovery fidelity at this canonical instance:** Verbatim-recovered from conversation history for functions 001-010 (full kingdom/substrate/confidence codings preserved); bullet text recovered for 011, 012, 014 with kingdom/substrate codings *reconstructed from bullet text* pending source re-derivation (marked per-function); residual 013 recovered from cohort-shared classification with WQS. Confidence-of-recovery field added per function.

#### RoleRealizationEnvelope

```yaml
envelope_id: RRE_BG_WDM_001
classification_ref: Burlingame Water Division Manager (B500)
envelope_description: |
  Management-class position at the convergence of Burlingame's two parallel
  water-utility ladders (Operations + Quality/Meter). Single position class;
  the manager directs both supervisor classes (Water Operations Supervisor
  and Water Quality Supervisor) and the crews reporting to them. Carries
  accountability for "the reliable supply of safe drinking water to the
  Burlingame community" — canonical management-class framing.
cardinality_estimate: |
  1 deployment (single position class; one incumbent at any time).
typical_realization_summary: |
  Division-level work planning + crew supervision via subordinate supervisors;
  Water Division budget ownership including Capital Outlay purchase authority;
  regulatory liaison with Department of Health Services and other agencies;
  plan review and approval for new buildings/remodels; ordinance drafting
  participation; complex-project hands-on supervision; citizen complaint
  resolution; regional agency representation.
outer_bound_summary: |
  Full convergence-point manager realization: deputy-by-default to Deputy
  Director of Public Works Operations; acts up in Deputy absence ("Will
  assume responsible charge of the department in the absence of the Deputy
  Director"). Working-manager retention — even at management stratum,
  hands-on supervision of "the more difficult construction and repair
  projects" with drawing interpretation and crew layout direction.
envelope_width_estimate: wide
evidence_basis: single-deployment primary-source decomposition; cross-ladder convergence pattern observed
notes: |
  Convergence-point manager pattern (4th envelope-design pattern). Kingdom-mix
  at the convergence pulls from both upstream ladders rather than being a pure
  extension of either. Differentiated from analyst-cohort single-ladder
  progression (MA → Sr MA → Principal MA). Acts-up signal toward Deputy
  Director indicates one-tier-above-default authority ceiling.
```

#### JDDecompositionRecord

```yaml
spec_id: JDR_BG_WDM
title: Burlingame Water Division Manager
class_code: B500
source_url: (recover from re-upload)
source_file: Water_Division_Manager__PDF_.pdf
established: (not visible on spec; pre-2017)
revised: June 2017; Revised CC August 21, 2017
salary_band: not_visible_on_spec
bargaining_unit: BAMM Unit, Exempt
envelope_width: wide
cardinality_estimate: 1 deployment
level_designation: management
parallel_ladder: Convergence (above Operations and Quality_Meter ladders)
essential_duty_count: 14
title_change_provenance: null
spec_staleness_flag: null
duplicate_class_code_flag: null
notes: |
  Convergence-point manager at the top of both parallel ladders. Single
  position class. Deputy-by-default to Deputy Director of Public Works
  Operations. Cleanest management-class spec in the Burlingame cohort —
  no analyst-titled-as-manager ambiguity (vs PA Principal MA).
recovery_provenance: |
  Verbatim recovery from conversation_search on chat
  c12c0652-966a-46b0-820f-258b2abb9749 (2026-05-12 PT). Functions 001-010
  recovered with full codings; 011-012-014 with bullet text only (codings
  reconstructed); 013 as residual (cohort-shared with WQS).
```

#### ExtractedFunctions

```yaml
- function_id: EF_BG_WDM_001
  source_text: "Plans, assigns, supervises, schedules and monitors the work of crews performing a variety of tasks related to the maintenance and operation of the water distribution system and all of its appurtenances; assumes the responsibility for the reliable supply of safe drinking water to the Burlingame community."
  interpreted_description: Division-level work planning + assignment + scheduling + monitoring of crews; reliability accountability for safe drinking water supply
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 65, Protective: 20, Mediative: 15}
  envelope_substrate: people
  envelope_weight: Core
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 65, Protective: 20, Mediative: 15}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: lead
  level_calibration: |
    WDM — management-class verb stack: plans/assigns/supervises/schedules/monitors.
    "Assumes responsibility for reliable supply" is canonical management framing.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: h
  recovery_fidelity: verbatim
  notes: Highest Allocative concentration in a single bullet across the cohort. Management-strata signal.

- function_id: EF_BG_WDM_002
  source_text: "Participates in the development and implementation of goals, objectives, policies, and procedures; evaluates work methods and procedures for improving Division performance and meeting goals; ensures that goals are achieved; forecasts the needs and resources of the Water Division; assists in assessing current and long-range goals and objectives."
  interpreted_description: Strategic goal/policy development + work-method evaluation + long-range needs forecasting at division scope
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 40, Generative: 30, Interpretive: 20, Mediative: 10}
  envelope_substrate: systems
  envelope_weight: Core
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 40, Generative: 30, Interpretive: 20, Mediative: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: monthly
  primacy_signal: lead
  level_calibration: WDM — long-range emphasis distinguishes from supervisors (who participate but don't own forecasting)
  canonical_function_mapping: null
  kingdom_confidence: m
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Generative tail at management stratum signals program-creation authority distinct from supervisor-tier procedure-evaluation.

- function_id: EF_BG_WDM_003
  source_text: "Participates in the development of the Water Division budget relative to the water distribution system; prepares reports; monitors program budget; monitors expenditures and purchases approved Capital Outlay equipment."
  interpreted_description: Division-level budget development + report preparation + budget monitoring + Capital Outlay purchase authority
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 70, Mediative: 15, Interpretive: 15}
  envelope_substrate: capital
  envelope_weight: Core
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 70, Mediative: 15, Interpretive: 15}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: monthly
  primacy_signal: lead
  level_calibration: |
    WDM — Capital Outlay purchase authority is the management-vs-supervisor
    discriminator. WQS only "monitors assigned program budgets"; WDM
    "purchases approved Capital Outlay equipment."
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: h
  recovery_fidelity: verbatim
  notes: Capital authority distinguishes WDM from supervisors. WQS only monitors; WDM purchases.

- function_id: EF_BG_WDM_004
  source_text: "Participates in the selection, training, and evaluation of personnel; assumes responsibility for motivating and evaluating assigned personnel; provides necessary training; recommends and initiates disciplinary procedures as is appropriate; ensures safe work practices and programs."
  interpreted_description: Personnel selection + training + evaluation + discipline initiation + safe-work-practices oversight
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 70, Mediative: 15, Protective: 15}
  envelope_substrate: people
  envelope_weight: Core
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 70, Mediative: 15, Protective: 15}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: monthly
  primacy_signal: lead
  level_calibration: |
    WDM — "recommends AND initiates" disciplinary procedures (vs supervisors
    who only "recommend"). Verb-pair shift is a direct authority-level
    diagnostic.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: h
  recovery_fidelity: verbatim
  notes: Discipline-initiation authority distinguishes WDM from supervisor stratum.

- function_id: EF_BG_WDM_005
  source_text: "Prepares and submits technical reports related to water quality and consumption budget."
  interpreted_description: Technical report preparation on water quality and consumption budget
  envelope_primary_kingdom: Interpretive
  envelope_kingdom_composition: {Generative: 50, Interpretive: 50}
  envelope_substrate: information
  envelope_weight: Ancillary
  typical_primary_kingdom: Interpretive
  typical_kingdom_composition: {Generative: 50, Interpretive: 50}
  typical_weight: Ancillary
  envelope_to_typical_rationale: null
  frequency_signal: monthly
  primacy_signal: mid
  level_calibration: null
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: h
  recovery_fidelity: verbatim
  notes: null

- function_id: EF_BG_WDM_006
  source_text: "Attends, coordinates and collaborates with regional agencies on water issues."
  interpreted_description: Regional agency coordination and collaboration on water issues (boundary-spanning at regional scope)
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 100}
  envelope_substrate: people
  envelope_weight: Core
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 100}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: monthly
  primacy_signal: lead
  level_calibration: WDM — regional-scope boundary-spanning distinguishes from supervisors' external-agency interactions which are narrower in scope
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: h
  recovery_fidelity: verbatim
  notes: Pure Mediative on people substrate; regional scope is the discriminator from supervisor-tier external-agency work.

- function_id: EF_BG_WDM_007
  source_text: "Develops and monitors work programs to meet the needs of the water division, Department of Health Services and other regulating boards."
  interpreted_description: Regulatory-driven work program development (DHS + boards) and monitoring
  envelope_primary_kingdom: Generative
  envelope_kingdom_composition: {Generative: 40, Allocative: 30, Protective: 30}
  envelope_substrate: systems
  envelope_weight: Core
  typical_primary_kingdom: Generative
  typical_kingdom_composition: {Generative: 40, Allocative: 30, Protective: 30}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: monthly
  primacy_signal: lead
  level_calibration: null
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Regulatory-driven program-development is a management-tier signature function (regulatory-compliance ownership).

- function_id: EF_BG_WDM_008
  source_text: "Provides direction for the scheduling of routine and emergency repair of water mains, services, reservoirs and pumping stations."
  interpreted_description: Repair scheduling direction at division scope (routine + emergency)
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 70, Protective: 30}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 70, Protective: 30}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: WDM directs supervisors who direct crews (management-tier direction, not direct crew direction)
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: h
  recovery_fidelity: verbatim
  notes: null

- function_id: EF_BG_WDM_009
  source_text: "Supervises the more difficult construction and repair projects, and inspects the work of contractors; interprets drawings and lays out work for crews."
  interpreted_description: Complex-project hands-on supervision + contractor inspection + drawing interpretation + work layout for crews
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 50, Interpretive: 30, Mediative: 20}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 50, Interpretive: 30, Mediative: 20}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    WDM — "more difficult" qualifier signals that routine work is delegated to
    supervisors; manager retains hands-on supervision of complex work only.
    Working-manager retention pattern at management stratum.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: h
  recovery_fidelity: verbatim
  notes: Working-manager retention signal — even at management stratum, hands-on supervision of complex work persists.

- function_id: EF_BG_WDM_010
  source_text: "Examines and approves plans submitted for water to new buildings and remodels; assists in drafting proposed City ordinances regarding potable water; suggests improvements in division procedures; meets with citizens to discuss water services and resolves complaints."
  interpreted_description: Plan approval (new buildings/remodels) + City ordinance drafting participation + procedure-improvement suggestions + citizen complaint resolution
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 35, Mediative: 30, Generative: 25, Interpretive: 10}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 35, Mediative: 30, Generative: 25, Interpretive: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: WDM — ordinance-drafting authority is a management-signature function operating at City-policy level
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Ordinance drafting = Generative authority at City-policy level. Plan approval = Allocative authority. Multi-kingdom function with substantive content in each.

- function_id: EF_BG_WDM_011
  source_text: "Directs the repair and installation of water mains, meters, flushing of hydrants, tapping of mains and installation and repairs of water services."
  interpreted_description: Operational direction across full water-distribution maintenance and installation portfolio
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 55, Protective: 30, Mediative: 15}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 55, Protective: 30, Mediative: 15}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: WDM — broad operational-direction verb across mains/meters/hydrants/services suggests division-wide direction-scope
  canonical_function_mapping: null
  kingdom_confidence: m
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: m
  recovery_fidelity: reconstructed_from_bullet_text
  notes: |
    Kingdom/substrate codings reconstructed from bullet text — verbatim record
    not recovered in conversation history. Pattern-matched to EF_BG_WDM_008
    (repair scheduling direction) which is structurally similar; expect minor
    drift on confirmation. Pending source re-derivation.

- function_id: EF_BG_WDM_012
  source_text: "Supervises and inspects work performed by contractors regarding water services, water mains and fire lines."
  interpreted_description: Contractor supervision and inspection for water services/mains/fire lines
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 40, Allocative: 30, Interpretive: 30}
  envelope_substrate: people
  envelope_weight: Core
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 40, Allocative: 30, Interpretive: 30}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: null
  canonical_function_mapping: null
  kingdom_confidence: m
  substrate_confidence: m
  weight_confidence: m
  segmentation_confidence: h
  mapping_confidence: m
  recovery_fidelity: reconstructed_from_bullet_text
  notes: |
    Codings reconstructed from bullet text. Distinct from EF_BG_WDM_009
    (which is broader: "more difficult construction and repair projects"
    plus drawing interpretation) — 012 is narrower-scope contractor
    inspection on three specific infrastructure categories. Pending
    source re-derivation.

- function_id: EF_BG_WDM_014
  source_text: "Establishes positive working relationships with representatives of community organizations, state/local agencies and associations, City management and staff, and the public."
  interpreted_description: Multi-direction boundary-spanning relationship establishment (community orgs + state/local agencies + City management + public)
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 100}
  envelope_substrate: people
  envelope_weight: Ancillary
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 100}
  typical_weight: Ancillary
  envelope_to_typical_rationale: null
  frequency_signal: ongoing
  primacy_signal: mid
  level_calibration: null
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: m
  segmentation_confidence: h
  mapping_confidence: m
  recovery_fidelity: reconstructed_from_bullet_text
  notes: |
    Codings reconstructed from bullet text. Pure Mediative on people
    substrate, similar to EF_BG_WDM_006 (regional agency coordination)
    but broader audience (community orgs + agencies + City staff + public
    rather than regional agencies alone). Weight likely Ancillary
    (relationship-establishment as ongoing posture, not discrete duty).
    Pending source re-derivation.
```

#### ImmaterialResiduals

```yaml
- residual_id: IR_BG_WDM_001
  source_text: "May be required to work during other than normal duty hours, including evenings, weekends, and holidays."
  residual_type: role_attribute
  residual_category: working_condition_statement
  notes: |
    Working-condition statement (after-hours availability requirement),
    not a function-bearing duty. Same residual appears in WQS spec
    (IR_BG_WQS_001) — cohort-shared residual pattern. Position-availability
    constraint applicable to all supervisor-and-above strata in the
    Burlingame water cohort.
  recovery_fidelity: verbatim
```

#### Notes_global

```
Front-matter: "Under direction" (top-tier autonomy framing in the Burlingame
hierarchy). "Will assume responsible charge of the department in the absence
of the Deputy Director" — manager-acts-up signal toward next-higher class
(Deputy Director of Public Works Operations, tracked as XRG_BG_005).
Bargaining unit BAMM Unit, Exempt. 14 essential-duty bullets producing
13 ExtractedFunctions + 1 ImmaterialResidual. Convergence-point manager
above both parallel ladders (Operations + Quality/Meter).
```

### JDR_BG_WSOT — Water System Operator Trainee

**Recovery fidelity at this canonical instance:** Verbatim from primary-source PDF (`Water_System_Operator_Trainee_-_September_2024.pdf`) uploaded 2026-05-12 PT. All ExtractedFunctions land at `recovery_fidelity: verbatim`. First spec in the agency file decomposed at full primary-source fidelity (Water Division Manager was reconstructed from conversation history; this record is the first verbatim-source instance).

#### RoleRealizationEnvelope

```yaml
envelope_id: RRE_BG_WSOT_001
classification_ref: Burlingame Water System Operator Trainee (S605)
envelope_description: |
  Entry-tier trainee class in the Water Division Operations ladder. Provides
  assistance to journey-tier Water System Operators in the installation,
  maintenance, and repair of the city water distribution system. Operates
  motorized equipment "in a training capacity" — explicit training-status
  framing throughout the spec. Employees may reasonably expect promotion to
  Water System Operator upon one year's satisfactory service, completion of
  probation, and passing a DHS Grade D-1 test. Promotion expectation is
  embedded directly in the spec's DISTINGUISHING CHARACTERISTICS section
  rather than left implicit in HR practice.
cardinality_estimate: |
  1-3 deployments (entry-tier class; multiple incumbents possible during
  active hiring/promotion cycles, single incumbent during steady state).
typical_realization_summary: |
  Heavy manual labor in pipe/main installation; mechanical equipment
  maintenance and cleaning under close supervision; serve as flag person
  in traffic work; meter reading and water-service-worker support as
  assigned. Training-trajectory orientation: all duties framed as
  preparatory to Water System Operator journey-tier work.
outer_bound_summary: |
  Bounded entirely by "Under close supervision" framing and the explicit
  "in a training capacity" qualifier on motorized-equipment operation. No
  acts-up signal; no independent-judgment authority. The ceiling of WSOT
  practice is by spec design the floor of WSO practice — the
  promotion-expectation language formalizes that boundary.
envelope_width_estimate: narrow
evidence_basis: single-spec primary-source decomposition; verbatim recovery from upload
notes: |
  Cleanest entry-tier instance in the Burlingame cohort. Two-tier duty
  structure (Essential Duties + Other Duties) — first cohort instance of
  this segmentation pattern (Water Division Manager used unified bullet
  list; Water Service and Operations Technician uses paragraph form).
  Candidate finding for protocol: Essential Duties → Core weight,
  Other Duties → Ancillary weight as default mapping. Applied here and
  noted as a recurrence-test candidate for second-agency intake.
```

#### JDDecompositionRecord

```yaml
spec_id: JDR_BG_WSOT
title: Burlingame Water System Operator Trainee
class_code: S605
source_url: (recover from re-upload)
source_file: Water_System_Operator_Trainee_-_September_2024.pdf
established: (not visible on spec; pre-2022 — predates this spec's substantive revision)
revised:
  substantive: May 2022
  administrative_title_change: September 2024
  source_attribution: |
    Footer carries two dated lines — "REVISED: MAY 2022" and
    "SEPTEMBER 2024 (TITLE CHANGE)" — capturing distinct revision events.
    Multi-event structure preserved here as a candidate v2.1 schema
    extension; current rubric collapses to single `revised:` value.
salary_band: not_visible_on_spec
bargaining_unit: AFSCME 829 Maintenance Unit, Non-Exempt
envelope_width: narrow
cardinality_estimate: 1-3 deployments
level_designation: trainee
parallel_ladder: Operations
essential_duty_count: 4
other_duty_count: 3
title_change_provenance:
  prior_title: Maintenance Worker I
  new_title: Water System Operator Trainee
  change_date: September 2024
  substance_change: false
  source: explicit FORMER TITLE footer marker + SEPTEMBER 2024 (TITLE CHANGE) line
spec_staleness_flag: null
duplicate_class_code_flag: null
internal_consistency_flag: |
  Typo in DISTINGUISHING CHARACTERISTICS: "completion of probation, and
  for t, passing a DHS Grade D-1 test" — "for t" appears to be a corrupted
  "for it" or similar fragment. Preserved verbatim; flagged for HR-cycle
  correction. Also: possessive forms throughout ("Water System Operator
  Trainee's class") appear to be intended plurals — not a substance issue.
promotion_expectation_provenance:
  candidate_field: true
  source: DISTINGUISHING CHARACTERISTICS section
  expectation: |
    Promotion to Water System Operator class
  conditions: |
    Completion of one year's satisfactory service; completion of probation;
    passing a DHS Grade D-1 test
  notes: |
    Embedded labor-relations commitment in the spec text. Candidate v2.1
    schema field flagged in protocol Appendix D; recurrence-test pending
    on second-agency intake.
notes: |
  Entry-tier in the Operations ladder. First verbatim-source decomposition
  in the agency file. Two-tier duty structure produces a clean Core/Ancillary
  split across Essential/Other duty bullets — the hypothesis that this
  mapping is reliable will be pressure-tested at the second agency.
recovery_provenance: |
  Verbatim recovery from primary-source PDF uploaded to /mnt/user-data/uploads/
  on 2026-05-12 PT. All ExtractedFunctions at recovery_fidelity: verbatim.
```

#### ExtractedFunctions

```yaml
- function_id: EF_BG_WSOT_001
  source_text: "Assists in laying pipe and water lines"
  interpreted_description: Trainee participates in pipe and water-line installation as a crew member; "assists" framing indicates support role to journey-tier workers
  envelope_primary_kingdom: Generative
  envelope_kingdom_composition: {Generative: 75, Protective: 25}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Generative
  typical_kingdom_composition: {Generative: 75, Protective: 25}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: assist
  level_calibration: |
    WSOT — trainee verb stack: "Assists." No autonomy markers. Generative
    content (creating new pipe runs) at minimum-autonomy primacy.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Pure physical_infrastructure substrate at Core weight. Trainee assist-tier primacy is the cleanest cone-hypothesis floor signal in the cohort.

- function_id: EF_BG_WSOT_002
  source_text: "assists in making taps and connections to mains"
  interpreted_description: Trainee participates in service-tap and main-connection work; same assist framing as F1
  envelope_primary_kingdom: Generative
  envelope_kingdom_composition: {Generative: 75, Protective: 25}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Generative
  typical_kingdom_composition: {Generative: 75, Protective: 25}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: assist
  level_calibration: WSOT — same verb stack as F1; less frequent in the work cycle (taps/connections are episodic).
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Paired with F1 in the Essential-Duties source; coding intentionally identical.

- function_id: EF_BG_WSOT_003
  source_text: "assists in the maintenance of mechanical equipment"
  interpreted_description: Trainee participates in preventive and corrective maintenance of pumps, motors, valves, and other mechanical assets in the distribution system
  envelope_primary_kingdom: Protective
  envelope_kingdom_composition: {Protective: 70, Generative: 20, Mediative: 10}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Protective
  typical_kingdom_composition: {Protective: 70, Generative: 20, Mediative: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: assist
  level_calibration: WSOT — protective verb stack ("maintenance") at assist primacy; the work content preserves existing infrastructure function.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Generative tail captures the repair-replace component within maintenance work; Mediative tail captures coordination with crew lead/journey worker during maintenance procedures.

- function_id: EF_BG_WSOT_004
  source_text: "cleans mechanical equipment and maintains basic tools used on the job"
  interpreted_description: Trainee performs equipment cleaning and tool upkeep, typically independently as the trainee-tier work item assigned without close supervision
  envelope_primary_kingdom: Protective
  envelope_kingdom_composition: {Protective: 80, Generative: 20}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Protective
  typical_kingdom_composition: {Protective: 80, Generative: 20}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: lead
  level_calibration: |
    WSOT — primacy shift from "assist" to "lead" at this function. Cleaning
    and tool maintenance is the canonical trainee-independent work — the
    duty a trainee owns even when the journey-tier crew is engaged in
    higher-skill work. Primacy signal documents the trainee's
    ladder-of-independence within the role.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: First "lead" primacy signal in WSOT — diagnostic for the entry-tier function that scaffolds independent work.

- function_id: EF_BG_WSOT_005
  source_text: "Serve as flag person when working in traffic"
  interpreted_description: Trainee provides traffic-control flagging at work sites where the crew operates in or adjacent to vehicular traffic; safety-critical role despite trainee status
  envelope_primary_kingdom: Protective
  envelope_kingdom_composition: {Protective: 85, Mediative: 15}
  envelope_substrate: physical_infrastructure
  envelope_weight: Ancillary
  typical_primary_kingdom: Protective
  typical_kingdom_composition: {Protective: 85, Mediative: 15}
  typical_weight: Ancillary
  envelope_to_typical_rationale: null
  frequency_signal: occasional
  primacy_signal: lead
  level_calibration: |
    WSOT — traffic-control flagging is an independent post (one person,
    one role) so primacy is lead even at trainee tier. The Ancillary weight
    reflects the Other Duties placement in the source. The "lead" primacy
    on an "Other Duty" is a Core-vs-Ancillary-isn't-the-same-as-lead-vs-assist
    signal worth flagging — weight (Essential/Other) and primacy
    (lead/assist) are independent axes.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: m
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: |
    Substrate confidence medium because flagging operates at the
    people-traffic interface — substrate could be argued as "people"
    (drivers + crew) but the work is physically located in the traffic
    environment and is primarily safety-of-physical-operations. Conservative
    single-substrate coding as physical_infrastructure with note.

- function_id: EF_BG_WSOT_006
  source_text: "read water meters and assist water service worker"
  interpreted_description: Bundled duty combining meter reading (data capture for billing pipeline) with general assistance to the water service worker; "Water Service Worker" is almost certainly a deprecated title for Water Service and Operations Technician
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 60, Protective: 25, Generative: 15}
  envelope_substrate: information
  envelope_weight: Ancillary
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 60, Protective: 25, Generative: 15}
  typical_weight: Ancillary
  envelope_to_typical_rationale: null
  frequency_signal: occasional
  primacy_signal: assist
  level_calibration: |
    WSOT — bundled meter-reading + worker-assistance bullet. Meter reading
    is Mediative (data → billing) with information substrate. "Assist water
    service worker" reverts to the broader assist framing. Function bundled
    per WDM convention (single-bullet multi-clause stays as one function).
  canonical_function_mapping: null
  kingdom_confidence: m
  substrate_confidence: l
  weight_confidence: h
  segmentation_confidence: m
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: |
    Lowest-confidence function in the WSOT record. Two issues: (1) the
    bundled structure muddies kingdom coding — meter reading and
    worker-assistance are different work-substrates; (2) the "water service
    worker" reference is almost certainly a deprecated title (Water Service
    and Operations Technician is the current title — see new gap entry
    XRG_BG_WSW logged this session). Substrate confidence low because the
    function operates at information/people interface. Candidate for
    splitting in a v2.1 re-decomposition.
```

#### ImmaterialResiduals

```yaml
- residual_id: IR_BG_WSOT_001
  source_text: "work in confined spaces"
  residual_type: role_attribute
  residual_category: working_condition_statement
  notes: |
    Listed in Other Duties but functions as an environmental qualification
    rather than an action-bearing duty. Cross-listed in the Physical/Mental/
    Environmental Working Conditions section, confirming the working-condition
    classification. Reflects underground-vault, manhole, and meter-pit work
    environments common to water distribution. Not decomposed into Kingdoms
    framework — environmental qualifications operate at a different
    abstraction level than work content.
  recovery_fidelity: verbatim

- residual_id: IR_BG_WSOT_002
  source_text: "operates motorized equipment in a training capacity"
  residual_type: role_attribute
  residual_category: scope_framing
  notes: |
    DEFINITION-section framing rather than a specific duty bullet. Folded
    into envelope_description but not extracted as a discrete function
    because the operative semantics ("in a training capacity") signal the
    framing applies to whatever motorized-equipment operation occurs across
    F1-F6 rather than describing its own discrete activity. The
    training-capacity qualifier is the key trainee-class signal carried
    through to all functions.
  recovery_fidelity: verbatim

- residual_id: IR_BG_WSOT_003
  source_text: "Employees hired in this position may reasonably expect promotion to the Water System Operator class upon completion of one year's satisfactory service, completion of probation, and for t, passing a DHS Grade D-1 test."
  residual_type: role_attribute
  residual_category: promotion_expectation
  notes: |
    DISTINGUISHING CHARACTERISTICS section content. Carried into the
    JDDecompositionRecord's promotion_expectation_provenance field as a
    structured-data candidate. Worth treating as a residual because the
    content is a labor-relations attribute of the role rather than a duty
    decomposable into Kingdoms. First cohort instance of this residual
    category; flagged for protocol promotion-expectation field codification
    pending recurrence test.
  recovery_fidelity: verbatim
```

#### Notes_global

```
Front-matter: "Under close supervision" (lowest-tier autonomy framing in
the Burlingame hierarchy). Entry-tier class in the Operations ladder.
Two-tier duty structure (Essential Duties + Other Duties) — first cohort
instance of this segmentation pattern; candidate finding for Essential→Core,
Other→Ancillary default weight mapping. Bargaining unit AFSCME 829
Maintenance Unit, Non-Exempt. 6 ExtractedFunctions (4 Core from Essential
Duties + 2 Ancillary from Other Duties) + 3 ImmaterialResiduals (1 from
Other Duties acting as working-condition; 1 scope-framing from DEFINITION;
1 promotion-expectation from DISTINGUISHING CHARACTERISTICS). Title change
September 2024 from Maintenance Worker I; substantive revision was earlier
(May 2022) — dual-event revision history captured in the revised: field
as a candidate schema extension. Allocative content: 0% — confirms prior
cohort-level finding of 0.0% WSOT Allocative at full verbatim fidelity;
cleanest cone-hypothesis floor signal in the cohort. Substrate distribution
dominated by physical_infrastructure (5 of 6 functions); information
substrate appears once at the meter-reading/worker-assist bundled function.
Three new cross-reference gaps surfaced from this spec — see Section 2
updates.
```

### JDR_BG_ZT — Zoning Technician

**Recovery fidelity at this canonical instance:** Verbatim from primary-source PDF (`Zoning_Technician__PDF_.pdf`) uploaded 2026-05-12 PT. All ExtractedFunctions land at `recovery_fidelity: verbatim`. First non-Water-Division spec in the agency file; first verbatim instance of a paragraph-form Essential Functions section requiring clause-level segmentation rather than bullet-level.

#### RoleRealizationEnvelope

```yaml
envelope_id: RRE_BG_ZT_001
classification_ref: Burlingame Zoning Technician (A110)
envelope_description: |
  Entry-level position in the Planning Department, working under supervision
  of the Planner and City Planner. Operates as a knowledge-worker
  individual contributor across a wide work portfolio: plan-conformance
  review, counter/telephone public service interpreting zoning and code
  requirements, staff report writing, data collection and analysis,
  graphics preparation, application processing, environmental
  assessment preparation, public notice and legal-procedure
  implementation, code enforcement, and business-license / home-occupation
  permit review. Despite "entry-level" framing, the verb stack is
  independent (checks, works, writes, prepares, processes, enforces) —
  no "assists" hedging language anywhere in the spec. Cross-department
  diagnostic: Burlingame's "entry-level" designation has different
  operational meaning across departments — at Water Division it means
  trainee-with-assist-primacy; at Planning Department it means
  lowest-IC-with-lead-primacy.
cardinality_estimate: |
  1-2 deployments (small-municipality Planning Department; entry-IC
  position; likely single incumbent at steady state, occasional second
  during active hiring).
typical_realization_summary: |
  Counter-based public service plus desk-based analytical and clerical work.
  Code/regulation interpretation as the substantive throughline across most
  functions. Wide work portfolio with lead-primacy on each work item; the
  Planner / City Planner supervisory chain provides oversight but not
  task-by-task direction.
outer_bound_summary: |
  No acts-up signal; no supervisory authority over others. Bounded by the
  Planner and City Planner supervisory chain. The wide work portfolio is
  the position's defining characteristic — not depth in any single
  function but breadth across the Planning Department's IC workload.
envelope_width_estimate: wide
evidence_basis: single-spec primary-source decomposition; verbatim recovery from upload
notes: |
  First non-water spec in the Burlingame agency file. Substantively distinct
  from the water cohort in both substrate (information-dominant, not
  physical_infrastructure-dominant) and verb stack (lead-primacy throughout,
  not assist-primacy). Validates the substrate-orthogonality finding from
  PA analyst cohort comparator at intra-agency scale: same Kingdoms
  framework, dramatically different substrate distribution, this time
  between departments within a single municipal employer rather than across
  employers. Extreme-vintage spec (1993, no subsequent revision) — content
  artifacts include microfiche reference and duplicate "data collection"
  phrasing. Worth flagging for Planning Department HR review-cycle
  re-acquisition.
```

#### JDDecompositionRecord

```yaml
spec_id: JDR_BG_ZT
title: Burlingame Zoning Technician
class_code: A110
org_unit: Planning Department
source_url: (recover from re-upload)
source_file: Zoning_Technician__PDF_.pdf
established: 1993 (presumed — earliest dated marker on spec)
revised:
  substantive: 1993 (no subsequent revision marker visible on spec)
  administrative_title_change: null
  source_attribution: |
    Footer carries only "1993" with no REVISED or TITLE CHANGE markers.
    This is the agency-wide staleness extreme so far observed (33 years).
salary_band: not_visible_on_spec
bargaining_unit: AFSCME 829 Maintenance Unit, Non-Exempt
envelope_width: wide
cardinality_estimate: 1-2 deployments
level_designation: entry_IC
parallel_ladder: Planning (single ladder; structure beyond Zoning Technician → Planner → City Planner not yet acquired)
essential_duty_count: 10 (paragraph-form Essential Functions, clause-segmented)
other_duty_count: 0
title_change_provenance: null
spec_staleness_flag: extreme_vintage
  vintage_year: 1993
  years_stale: 33 (at canonical instance May 2026)
  evidence:
    - "Use microfiche machines" listed as a skill requirement (1993-era technology reference, near-obsolete by 2026)
    - "modern office procedures" framed as if in contrast to non-modern alternatives (1993 register)
    - Duplicate phrasing in Essential Functions: "collecting and analyzing data" appears twice in the same paragraph
    - Lacks "under [close|general] supervision/direction" boilerplate that water cohort uses
duplicate_class_code_flag: null
internal_consistency_flag: |
  Duplicate phrasing in Essential Functions: "collecting and analyzing data"
  (mid-paragraph) and "data collection and analysis" (end-of-paragraph)
  appear to be the same duty re-stated, suggesting copy-edit drift during
  composition. Treated as a single function (EF_BG_ZT_004) with note.
  Also: PDF page footer reads "WATER SERVICE & OPERATIONS TECHNCIAN" on
  both pages — template-reuse copy-paste artifact from a different spec;
  the body content is Planning Department appropriate but the footer was
  never updated.
promotion_expectation_provenance: null
notes: |
  First Planning Department spec in the agency intake. Verb-stack
  independence (lead-primacy throughout) distinguishes the Planning
  Department entry-tier from the Water Division entry-tier (assist-primacy
  trainee class). Wide work portfolio (10 distinct functions in a single
  paragraph) at entry-IC level — different envelope-design pattern than
  the water cohort's vertical-progression-cone entry tier. Candidate
  pattern observation: Planning Department may instantiate a
  "wide-portfolio entry-IC" envelope-design that the water cohort doesn't
  contain. Recurrence-test pending on second Planning Department spec
  acquisition (Planner or City Planner classes).
recovery_provenance: |
  Verbatim recovery from primary-source PDF uploaded to /mnt/user-data/uploads/
  on 2026-05-12 PT. All ExtractedFunctions at recovery_fidelity: verbatim.
```

#### ExtractedFunctions

```yaml
- function_id: EF_BG_ZT_001
  source_text: "Checks plans for conformance with regulations"
  interpreted_description: Reviews submitted plans (architectural, engineering, development) against zoning, sign, and code regulations; identifies non-conformance and routes for resolution
  envelope_primary_kingdom: Interpretive
  envelope_kingdom_composition: {Interpretive: 60, Protective: 30, Mediative: 10}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Interpretive
  typical_kingdom_composition: {Interpretive: 60, Protective: 30, Mediative: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — independent verb stack ("Checks"). The IC is the
    rule-application primary, even at "entry-level" Planning Department
    framing. Protective tail captures the conformance-enforcement aspect
    (catching violations protects community/regulatory compliance);
    Mediative tail captures routing of non-conformance to applicant for
    correction.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Cleanest Interpretive instance in the agency file so far — direct rule-application work at IC weight.

- function_id: EF_BG_ZT_002
  source_text: "works at the counter and on the telephone with the public interpreting zoning, sign and other code requirements"
  interpreted_description: Counter-based and telephone public service: interprets zoning regulations, sign code, and other codes for members of the public seeking guidance on property/development questions
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 50, Interpretive: 40, Protective: 10}
  envelope_substrate: people
  envelope_weight: Core
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 50, Interpretive: 40, Protective: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — public-facing IC work. Mediative-primary because the
    work is translating regulations into actionable guidance for public;
    Interpretive secondary because rule-interpretation is the substantive
    core of the translation. Substrate "people" because the work operates
    on members of the public (their understanding, their planning
    decisions) rather than on documents.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: First "people" substrate at Core weight in the agency file outside the management tier (WDM, supervisor classes). Entry-IC public-service is the cohort-distinct substrate signature for Planning Department.

- function_id: EF_BG_ZT_003
  source_text: "writing staff reports"
  interpreted_description: Drafts staff reports for Planning Commission, City Council, or internal use synthesizing analysis of zoning/development matters
  envelope_primary_kingdom: Generative
  envelope_kingdom_composition: {Generative: 50, Interpretive: 35, Mediative: 15}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Generative
  typical_kingdom_composition: {Generative: 50, Interpretive: 35, Mediative: 15}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — staff report authorship is independent generative work.
    The Interpretive tail captures the analytical content of the reports;
    Mediative tail captures the cross-stakeholder routing the reports
    facilitate.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Generative kingdom at entry-IC tier — distinctive from water cohort where Generative is concentrated at the journey-tier construction work (laying pipe, making connections).

- function_id: EF_BG_ZT_004
  source_text: "collecting and analyzing data" (also appears as "data collection and analysis" at end of paragraph — treated as same function)
  interpreted_description: Collects zoning/planning data from various sources and conducts analysis; supports staff reports, environmental assessments, and code-enforcement decisions
  envelope_primary_kingdom: Interpretive
  envelope_kingdom_composition: {Interpretive: 60, Mediative: 30, Generative: 10}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Interpretive
  typical_kingdom_composition: {Interpretive: 60, Mediative: 30, Generative: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — data analysis is independent analytical work.
    Interpretive primacy because the work surfaces patterns and meaning
    from data; Mediative captures the collection-from-sources component.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: m
  segmentation_confidence: m
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: |
    Source text duplication ("collecting and analyzing data" + "data
    collection and analysis") preserved as single function. Segmentation
    confidence medium because the duplicate could be argued as two
    distinct functions (collection vs analysis) that the spec
    drafter merged in copy-edit. Conservative single-function coding.

- function_id: EF_BG_ZT_005
  source_text: "preparing graphics and illustrations"
  interpreted_description: Prepares maps, charts, graphics, and illustrations supporting staff reports, public notices, and planning displays; uses GIS map system
  envelope_primary_kingdom: Generative
  envelope_kingdom_composition: {Generative: 70, Mediative: 20, Interpretive: 10}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Generative
  typical_kingdom_composition: {Generative: 70, Mediative: 20, Interpretive: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — graphics preparation is creative output work.
    Generative-dominant. Mediative captures the audience-orientation
    (graphics communicate to specific audiences); Interpretive captures
    the data-to-visual translation step.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: 1993-era spec lists "use microfiche machines" alongside GIS — the technology juxtaposition is itself diagnostic of the spec's staleness.

- function_id: EF_BG_ZT_006
  source_text: "processing applications"
  interpreted_description: Routes development, zoning, and use-permit applications through the review workflow; tracks status; ensures completeness
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 60, Interpretive: 30, Protective: 10}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 60, Interpretive: 30, Protective: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — application processing is workflow-coordination work.
    Mediative-primary. Interpretive tail captures the completeness-check
    /eligibility-assessment aspect.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: null

- function_id: EF_BG_ZT_007
  source_text: "preparing environmental assessments"
  interpreted_description: Drafts environmental assessment documents (likely CEQA-related given California municipality context); evaluates environmental impact of proposed projects
  envelope_primary_kingdom: Interpretive
  envelope_kingdom_composition: {Interpretive: 55, Generative: 35, Protective: 10}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Interpretive
  typical_kingdom_composition: {Interpretive: 55, Generative: 35, Protective: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: monthly
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — environmental assessment preparation involves significant
    Interpretive analytical content (evaluating environmental impact) plus
    Generative drafting. At entry-IC tier this is notable scope — typically
    environmental review at this level of substance is journey-tier work.
    Possible diagnostic that the 1993 spec assigned a higher work scope
    than current Planning Department practice would; or that the spec
    overstates the actual work envelope.
  canonical_function_mapping: null
  kingdom_confidence: m
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: |
    Kingdom confidence medium because the function description is brief
    ("preparing environmental assessments") and the actual realization at
    entry-IC tier may be lighter than the verb implies — possibly more
    administrative-routing than substantive analytical authorship. Without
    more recent revision, the function's true envelope is uncertain.

- function_id: EF_BG_ZT_008
  source_text: "preparing public notices and implementing legal procedures"
  interpreted_description: Drafts public notices (hearings, code enforcement, application processing); implements the legal procedural steps (publication, mailing, posting) required by code and law
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 40, Protective: 30, Generative: 30}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 40, Protective: 30, Generative: 30}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — bundled public notice + legal procedure implementation.
    Mediative-primary (the notices are external communication; the legal
    procedures are workflow). Protective tail captures the
    procedural-correctness function (legal procedures protect against
    challenge); Generative tail captures notice drafting.
  canonical_function_mapping: null
  kingdom_confidence: m
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: m
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Bundled function (public notices + legal procedures) preserved per single-clause source structure. Candidate for splitting in v2.1 re-decomposition if needed.

- function_id: EF_BG_ZT_009
  source_text: "code enforcement"
  interpreted_description: Enforces zoning, sign, and other municipal codes; investigates complaints; engages with property owners and tenants on violations; routes through formal enforcement procedures as needed
  envelope_primary_kingdom: Protective
  envelope_kingdom_composition: {Protective: 50, Interpretive: 30, Mediative: 20}
  envelope_substrate: people
  envelope_weight: Core
  typical_primary_kingdom: Protective
  typical_kingdom_composition: {Protective: 50, Interpretive: 30, Mediative: 20}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — code enforcement is regulation-protection work operating
    on property owners and tenants. Protective primary; Interpretive
    captures the code-application aspect; Mediative captures violator-
    interaction. Substrate "people" because the work operates on
    property-owner behavior (compliance) rather than on documents — the
    documents are the artifact of the work, not its substrate.
  canonical_function_mapping: null
  kingdom_confidence: m
  substrate_confidence: m
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: |
    Substrate confidence medium because code enforcement operates across
    multiple substrate types (people behavior + physical property
    conditions + information/regulations). Conservative people-substrate
    coding captures the dominant operative locus (changing property-owner
    behavior is the desired outcome).

- function_id: EF_BG_ZT_010
  source_text: "reviewing business license and home occupation permits"
  interpreted_description: Reviews business license applications and home occupation permit applications against zoning code requirements; approves, conditions, or rejects per criteria
  envelope_primary_kingdom: Interpretive
  envelope_kingdom_composition: {Interpretive: 55, Mediative: 30, Protective: 15}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Interpretive
  typical_kingdom_composition: {Interpretive: 55, Mediative: 30, Protective: 15}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    Zoning Tech — permit-review work is rule-application against
    applications. Interpretive primary; Mediative captures approval-routing;
    Protective captures the gate-keeping function.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: null
```

#### ImmaterialResiduals

```yaml
- residual_id: IR_BG_ZT_001
  source_text: "ability to climb, crouch, and crawl on site inspections"
  residual_type: role_attribute
  residual_category: working_condition_statement
  notes: |
    PHYSICAL/MENTAL/ENVIRONMENTAL WORKING CONDITIONS section content.
    Site-inspection physical demands. Not decomposed as a function
    because it qualifies *how* the inspection work happens rather than
    naming it as a distinct duty. Site inspection itself is implicitly
    folded into code enforcement (EF_BG_ZT_009) and plan-checking
    (EF_BG_ZT_001) where on-site verification is plausibly part of the
    work realization. Worth flagging because a "site inspection" function
    is missing from the explicit Essential Functions paragraph — likely
    spec omission from the 1993 vintage.
  recovery_fidelity: verbatim

- residual_id: IR_BG_ZT_002
  source_text: "ability to learn GIS map system and use microfiche machines"
  residual_type: role_attribute
  residual_category: skill_requirement
  notes: |
    Skill-section content. GIS map system use is part of EF_BG_ZT_005
    (graphics preparation). Microfiche machine use is staleness-evidence:
    the 1993 vintage references a technology that is near-obsolete by
    2026. Folded into the spec_staleness_flag evidence rather than treated
    as an active function. Marker of the spec's age and the absence of
    revision.
  recovery_fidelity: verbatim

- residual_id: IR_BG_ZT_003
  source_text: "Establish and maintain cooperative working relationships with professions in various disciplines; be calm in stressful situations; ability to be tactful and diplomatic in dealing with the public"
  residual_type: role_attribute
  residual_category: interpersonal_qualification
  notes: |
    PHYSICAL/MENTAL/ENVIRONMENTAL WORKING CONDITIONS section content
    describing interpersonal qualifications. Not function-bearing —
    these qualify the *manner* of work in public-facing functions
    (especially EF_BG_ZT_002 counter/telephone work and EF_BG_ZT_009
    code enforcement) rather than naming distinct work content.
  recovery_fidelity: verbatim
```

#### Notes_global

```
Front-matter: no "Under [close|general] supervision/direction" boilerplate —
the 1993 spec predates the autonomy-language conventions the water cohort
uses. Supervision framing is one short clause in DEFINITION ("works under
the supervision of the Planner and City Planner"). Verb stack throughout
Essential Functions is independent: "Checks," "works," "writing,"
"collecting," "preparing," "processing," "reviewing." No "assists" hedging.
This is the entry-IC envelope-design pattern at lead-primacy, distinct
from the water cohort's entry-trainee assist-primacy pattern. Bargaining
unit AFSCME 829 Maintenance Unit, Non-Exempt (cross-department anomaly —
same bargaining unit as Water System Operator Trainee despite Planning
Department classification). 10 ExtractedFunctions from paragraph-form
Essential Functions section (clause-segmented; one bundled function for
"public notices + legal procedures") + 3 ImmaterialResiduals (working
conditions + skill requirements + interpersonal qualifications).
Allocative content: 0% across all functions (consistent with entry-IC
status; no work-direction, no resource allocation). Substrate distribution
is information-dominant (8 of 10 functions) with people substrate at the
public-facing functions (EF_BG_ZT_002 counter service, EF_BG_ZT_009 code
enforcement). First Planning Department spec at canonical instance; the
"wide-portfolio entry-IC" envelope-design is a candidate pattern not yet
observed in the water cohort. Two new cross-reference gap entries
(XRG_BG_009 Planner, XRG_BG_010 City Planner) surfaced — the Planning
Department's supervisory-chain catalog above Zoning Technician.
```

### JDR_BG_WSO — Water System Operator

**Recovery fidelity at this canonical instance:** Verbatim from primary-source PDF (`Water_System_Operator_-_September_2024.pdf`) uploaded 2026-05-12 PT. All ExtractedFunctions land at `recovery_fidelity: verbatim`. Journey-tier pair to Water System Operator Trainee in the Operations ladder; the trainee → journey progression is now established at verbatim fidelity from both ends.

#### RoleRealizationEnvelope

```yaml
envelope_id: RRE_BG_WSO_001
classification_ref: Burlingame Water System Operator (S503)
envelope_description: |
  Journey-tier class in the Water Division Operations ladder. Performs
  skilled and semi-skilled work in installation, maintenance, and repair
  of the city water system, "Independently, or as a member of a crew" per
  the ESSENTIAL FUNCTIONS framing. Receives general supervision from
  Lead Water System Operator and Supervisor positions (per SUPERVISION
  RECEIVED AND EXERCISED section), with formal DEFINITION framing of
  "Under close supervision" — a spec-internal autonomy-language anomaly
  detailed in the JDDecompositionRecord. Operates the full equipment
  range: backhoe, trencher trucks, tapping machine, boring machine, and
  associated hand and power tools. Participates in training and
  supervision of Water System Operator Trainees as assigned — first
  Allocative content in the Operations ladder.
cardinality_estimate: |
  3-6 deployments (journey-tier class; multiple incumbents typical to
  cover work distribution + rotation + on-call coverage).
typical_realization_summary: |
  Skilled installation/repair/replacement of water-system infrastructure
  (mains, copper tubing, hydrants, valves, meters, meter boxes); pumping
  equipment minor repairs; pipe-location work via electronic detection;
  excavation and concrete restoration; grade-stake reading for service
  installation. Night call and weekend duty on rotation. Trainee
  supervision and direction of seasonal/temporary workers as assigned.
outer_bound_summary: |
  Bounded above by the Lead Water System Operator and Supervisor classes
  (per SUPERVISION RECEIVED). Acts-up to trainee-supervision regularly;
  acts-up to seasonal/temporary-worker direction conditionally. The
  ESSENTIAL FUNCTIONS framing "Independently, or as a member of a crew"
  is the journey-tier autonomy signal that distinguishes WSO from WSOT
  (where every Essential Duty begins with "Assists"). The "Under close
  supervision" framing in DEFINITION is inconsistent with this autonomy
  signal — flagged.
envelope_width_estimate: medium
evidence_basis: single-spec primary-source decomposition; verbatim recovery from upload
notes: |
  Cleanest journey-tier instance in the Burlingame cohort. Companion
  record to WSOT (trainee tier) — the WSOT → WSO progression is now
  verbatim-fidelity at both ends, enabling clean cone-hypothesis testing
  on the Operations ladder's lower segment. Three-way spec-internal
  autonomy framing inconsistency is the most striking quality-anomaly
  observation: DEFINITION says "Under close supervision," SUPERVISION
  RECEIVED says "general supervision," ESSENTIAL FUNCTIONS says
  "Independently, or as a member of a crew." Three different framings
  in one spec — flagged as spec_internal_consistency.
```

#### JDDecompositionRecord

```yaml
spec_id: JDR_BG_WSO
title: Burlingame Water System Operator
class_code: S503
org_unit: Water Division
source_url: (recover from re-upload)
source_file: Water_System_Operator_-_September_2024.pdf
established: (not visible on spec; pre-2021 — predates this spec's substantive revision)
revised:
  substantive: August 2021
  administrative_title_change: September 2024
  source_attribution: |
    Footer carries two dated lines — "REVISED: AUGUST 2021" and
    "SEPTEMBER 2024 (TITLE CHANGE)" — capturing distinct revision events.
    Same dual-event pattern as WSOT's MAY 2022 + SEPTEMBER 2024.
    Second-instance pressure-test of the multi-event revision-history
    schema candidate.
salary_band: not_visible_on_spec
bargaining_unit: AFSCME 829 Maintenance Unit, Non-Exempt
envelope_width: medium
cardinality_estimate: 3-6 deployments
level_designation: journey
parallel_ladder: Operations
essential_duty_count: 11 (paragraph-form Essential Functions; clause-segmented)
other_duty_count: 1 (SUPERVISION RECEIVED AND EXERCISED section's "May provide direction for seasonal or temporary workers" treated as Ancillary duty)
title_change_provenance:
  prior_title: Water Maintenance Worker II
  new_title: Water System Operator
  change_date: September 2024
  substance_change: false
  source: explicit FORMER TITLE footer marker + SEPTEMBER 2024 (TITLE CHANGE) line
  cohort_pattern: |
    Pairs with WSOT's Maintenance Worker I → Water System Operator Trainee
    retitling. Both retitlings dated September 2024. The "I/II" → "Trainee/Operator"
    rename is a coordinated title-design-as-policy-lever action across the
    Operations ladder entry+journey strata. Three-instance pattern
    (WSOT, WSO, and possibly other Sept-2024 retitlings) would promote
    this to a documented agency-level pattern.
spec_staleness_flag: null
duplicate_class_code_flag: null
spec_internal_consistency_flag: |
  Three-way autonomy-language inconsistency within a single spec —
  the most striking quality anomaly observed in the cohort so far:
    - DEFINITION: "Under close supervision, performs skilled and semi-skilled work..."
    - SUPERVISION RECEIVED AND EXERCISED: "Receives general supervision from the Lead Water System Operator and Supervisor positions."
    - ESSENTIAL FUNCTIONS (first sentence): "Independently, or as a member of a crew, performs skilled and semi-skilled work..."
  Three different autonomy framings — "close supervision," "general supervision,"
  and "independently/crew" — in one spec, with the Essential Functions framing
  being the most operationally consequential. Most likely explanation: the
  DEFINITION boilerplate was inherited from a template (possibly the WSOT
  template, where "close supervision" is correct) and never updated when WSO
  was revised in August 2021. The protocol's Section 1 (existing) flagged the
  "Under close supervision" vs "Independently, or as a member of a crew"
  tension; this canonical instance adds the third framing (general supervision
  in SUPERVISION RECEIVED) for full triangulation.

  Also: typo throughout — "Water System Operator Trainee's" used as plural
  in multiple places ("supervision of Water System Operator Trainee's as
  assigned"). Standard grammar would be "Trainees." Preserved verbatim;
  same pattern observed in WSOT's distinguishing-characteristics text.

  Also: "DISTINGUISING CHARACTERISTICS" header in body — missing "H"
  (should be "DISTINGUISHING"). Same kind of typo as WSOT's "for t" fragment.
  Both September-2024-retitled specs have minor textual errors suggesting
  light editorial attention at the title-change revision.
promotion_expectation_provenance:
  candidate_field: true
  source: DISTINGUISHING CHARACTERISTICS section
  expectation: |
    Promotion from Water System Operator Trainee class; alternatively,
    direct hire from outside with at least one year of equivalent
    experience to WSOT
  conditions: |
    Performance of WSOT-class duties for one year (internal pathway);
    or, for external hires, one year of prior experience equivalent
    to WSOT in another jurisdiction
  notes: |
    Second cohort instance of promotion_expectation_provenance. Pairs with
    WSOT's promotion-to-WSO expectation; together the two specs establish
    a closed promotion-pathway pair (each spec documents its end of the
    pathway). Two-instance recurrence — promotes the candidate field
    closer to v2.1 rubric codification.
notes: |
  Journey-tier in the Operations ladder. Second verbatim-source decomposition
  in the Operations ladder (after WSOT). The WSOT → WSO progression now
  establishes the cone-hypothesis lower-segment at verbatim fidelity.
  Three-way autonomy framing inconsistency is the most diagnostic quality
  signal in this spec.
recovery_provenance: |
  Verbatim recovery from primary-source PDF uploaded to /mnt/user-data/uploads/
  on 2026-05-12 PT. All ExtractedFunctions at recovery_fidelity: verbatim.
```

#### ExtractedFunctions

```yaml
- function_id: EF_BG_WSO_001
  source_text: "Performs night call and weekend duty"
  interpreted_description: Provides on-call coverage during nights and weekends per rotation schedule; responds to system events and emergencies during off-hours
  envelope_primary_kingdom: Protective
  envelope_kingdom_composition: {Protective: 60, Generative: 20, Mediative: 20}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Protective
  typical_kingdom_composition: {Protective: 60, Generative: 20, Mediative: 20}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: occasional
  primacy_signal: lead
  level_calibration: |
    WSO — first journey-tier function. Off-hours availability and emergency
    response is a journey-tier responsibility (trainee class doesn't carry
    this). Lead primacy because during off-hours the on-call WSO is the
    primary responder; Protective primary because the work content is
    preserving system operations.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: First on-call/emergency-response signal in the cohort.

- function_id: EF_BG_WSO_002
  source_text: "may be required to read water meters when assigned"
  interpreted_description: Reads water meters when assigned; supports meter-reading workload during peak periods or coverage gaps; not a primary daily responsibility for WSO
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 70, Interpretive: 20, Protective: 10}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 70, Interpretive: 20, Protective: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: occasional
  primacy_signal: lead
  level_calibration: |
    WSO — parallel to WSOT F6 (meter reading) but at journey tier.
    "when assigned" hedge indicates conditional realization, but the
    function appears in Essential Functions so weight remains Core.
    Reading meters is the same Mediative/information work regardless
    of tier; the journey-vs-trainee distinction shows up in the
    primacy (lead at WSO; assist-bundled at WSOT F6).
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: m
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Cohort-shared function with WSOT F6 (different primacy at different tier).

- function_id: EF_BG_WSO_003
  source_text: "Operates backhoe, trencher trucks"
  interpreted_description: Operates heavy excavation and trenching equipment in support of installation and repair work; backhoe for general excavation, trencher trucks for linear pipe-trench preparation
  envelope_primary_kingdom: Generative
  envelope_kingdom_composition: {Generative: 60, Protective: 30, Mediative: 10}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Generative
  typical_kingdom_composition: {Generative: 60, Protective: 30, Mediative: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: lead
  level_calibration: |
    WSO — independent equipment operation. The motorized-equipment
    operation that WSOT does "in a training capacity" is now done at
    full operator authority. Generative primary because the work content
    creates the conditions for new installation (excavation precedes
    pipe-laying).
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: First independent-equipment-operation signal at canonical fidelity. Contrasts with WSOT's "in a training capacity" qualifier.

- function_id: EF_BG_WSO_004
  source_text: "sets up and operates a tapping machine and a boring machine"
  interpreted_description: Sets up and operates specialized water-utility equipment for creating service taps to mains and boring under obstructions for pipe installation
  envelope_primary_kingdom: Generative
  envelope_kingdom_composition: {Generative: 75, Protective: 25}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Generative
  typical_kingdom_composition: {Generative: 75, Protective: 25}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    WSO — specialized water-utility equipment operation. This is the
    journey-tier evolution of WSOT F2 ("assists in making taps and
    connections to mains"); WSOT assists, WSO sets up and operates.
    Generative-dominant because the work creates new connections to the
    distribution system.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Cohort-shared function family with WSOT F2 (tap/connection work). Tier-progression shows in primacy and equipment-authority.

- function_id: EF_BG_WSO_005
  source_text: "Measures and cuts pipes"
  interpreted_description: Measures and cuts pipe to length for installation; preparatory step to mains/service-line installation work
  envelope_primary_kingdom: Generative
  envelope_kingdom_composition: {Generative: 70, Protective: 30}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Generative
  typical_kingdom_composition: {Generative: 70, Protective: 30}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: lead
  level_calibration: |
    WSO — preparation work for installation. Generative primary
    (creating fit-for-installation pieces). The pair F5+F6 is the core
    journey-tier installation workflow: measure/cut, then install.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: null

- function_id: EF_BG_WSO_006
  source_text: "installs, repairs and replaces mains, copper tubing, hydrants, valves, meters and meter boxes"
  interpreted_description: Core skilled installation, repair, and replacement work across the breadth of water distribution components — mains, copper tubing (service lines), hydrants, valves, meters, and meter boxes
  envelope_primary_kingdom: Generative
  envelope_kingdom_composition: {Generative: 50, Protective: 45, Mediative: 5}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Generative
  typical_kingdom_composition: {Generative: 50, Protective: 45, Mediative: 5}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: lead
  level_calibration: |
    WSO — THE CORE JOURNEY-TIER FUNCTION. The verb stack
    "installs/repairs/replaces" spans both Generative (new installation)
    and Protective (repair/replace existing). Mixed kingdom composition
    reflects the dual character; in any given week the function realizes
    as some mix of new installation and existing-system maintenance.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Cohort-shared function family with WSOT F1 (assists in laying pipe and water lines); WSO is the lead-primacy realization of this work.

- function_id: EF_BG_WSO_007
  source_text: "Performs minor repairs to pumping equipment such as repacking valves and replacing diaphragms"
  interpreted_description: Performs minor repairs to pumping equipment — repacking valves, replacing diaphragms, similar mechanical maintenance — but not major pumping-system overhaul or replacement
  envelope_primary_kingdom: Protective
  envelope_kingdom_composition: {Protective: 75, Generative: 25}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Protective
  typical_kingdom_composition: {Protective: 75, Generative: 25}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    WSO — pumping equipment maintenance at journey tier. The "minor
    repairs" qualifier indicates scope boundary: complex pumping repairs
    presumably escalate to a higher tier or specialty class. Protective
    primary; Generative tail captures the replace-component aspect.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Cohort-shared function family with WSOT F3 (assists in maintenance of mechanical equipment); WSO is the lead-primacy realization.

- function_id: EF_BG_WSO_008
  source_text: "Uses electronic detection equipment to locate pipes"
  interpreted_description: Uses electronic detection equipment (USA Locates equipment) to identify underground pipe locations prior to excavation; critical safety/protective function preventing damage to underground utilities
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 40, Interpretive: 30, Protective: 30}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 40, Interpretive: 30, Protective: 30}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    WSO — pipe location is a precondition for excavation. Substrate is
    information (operating on/via detection signals) rather than
    physical_infrastructure (the pipes themselves) because the work
    content is reading detection signals and translating them into
    excavation-planning data. Mediative primary; Interpretive captures
    the signal-to-location translation; Protective captures the damage-
    prevention function.
  canonical_function_mapping: null
  kingdom_confidence: m
  substrate_confidence: m
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Second information-substrate function in the WSO record (alongside F2 meter reading and F10 grade-stake reading). Information substrate is the secondary substrate signature at journey tier.

- function_id: EF_BG_WSO_009
  source_text: "Excavates, repairs leak; fills and compacts excavations, and replaces removed concrete"
  interpreted_description: Excavation work (creating access to underground infrastructure); leak repair (the protective work the excavation enables); site restoration (filling, compacting, concrete replacement)
  envelope_primary_kingdom: Protective
  envelope_kingdom_composition: {Protective: 50, Generative: 45, Mediative: 5}
  envelope_substrate: physical_infrastructure
  envelope_weight: Core
  typical_primary_kingdom: Protective
  typical_kingdom_composition: {Protective: 50, Generative: 45, Mediative: 5}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: daily
  primacy_signal: lead
  level_calibration: |
    WSO — bundled excavation + leak repair + site restoration workflow.
    Mixed kingdom: Protective for leak repair (the operative purpose),
    Generative for excavation and concrete-restoration (creating the
    conditions and restoring the site). One source clause, multiple
    distinct work components — kept bundled per single-clause source
    structure.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: m
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: Segmentation confidence medium — the bundled clause could be argued as 2-3 distinct functions. Conservative single-function coding.

- function_id: EF_BG_WSO_010
  source_text: "Reads grade stakes for water service, meter height and fire hydrants"
  interpreted_description: Reads survey grade stakes and translates the data into installation parameters for water service, meter, and hydrant placement (depth, height, alignment)
  envelope_primary_kingdom: Mediative
  envelope_kingdom_composition: {Mediative: 55, Interpretive: 35, Generative: 10}
  envelope_substrate: information
  envelope_weight: Core
  typical_primary_kingdom: Mediative
  typical_kingdom_composition: {Mediative: 55, Interpretive: 35, Generative: 10}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    WSO — grade-stake reading is data extraction (Mediative) with
    significant Interpretive content (translating stake data into
    physical installation parameters). Information substrate. This is
    the only function in the WSO record where the operation is
    primarily on information rather than on infrastructure.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: null

- function_id: EF_BG_WSO_011
  source_text: "assists in training and supervising Water System Operator Trainee's as assigned"
  interpreted_description: Provides on-the-job training to Water System Operator Trainees; supervises trainee work when assigned by Lead WSO or Supervisor; first Allocative content in the Operations ladder
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 60, Mediative: 25, Protective: 15}
  envelope_substrate: people
  envelope_weight: Core
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 60, Mediative: 25, Protective: 15}
  typical_weight: Core
  envelope_to_typical_rationale: null
  frequency_signal: weekly
  primacy_signal: lead
  level_calibration: |
    WSO — FIRST ALLOCATIVE CONTENT IN THE OPERATIONS LADDER. The
    journey-tier carries trainee-supervision responsibility, instantiating
    the cone-hypothesis prediction that some Allocative content appears
    at journey tier (above the 0% trainee floor). The "assists in"
    hedge is real — WSO is not the primary supervisor; trainee
    supervision flows formally through the Lead WSO and Supervisor.
    WSO's role is on-the-job training delegation. Allocative primary
    because work direction is the operative content; Mediative captures
    the cross-stratum knowledge-transfer; Protective captures the
    trainee-safety-and-quality oversight component.
  canonical_function_mapping: null
  kingdom_confidence: h
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: |
    Most diagnostic function in the WSO record for cone-hypothesis
    testing. The 60% Allocative composition is moderate (vs WDM's
    F1 at 65% Allocative for full management work); journey-tier
    has supervision responsibility but at "assist" delegation rather
    than primary ownership. People substrate appears for the first
    time in the Operations ladder at this function.

- function_id: EF_BG_WSO_012
  source_text: "May provide direction for seasonal or temporary workers"
  interpreted_description: Conditional duty — when seasonal or temporary workers are deployed in the division, WSO may be assigned to provide direction to them; secondary Allocative content beyond trainee supervision
  envelope_primary_kingdom: Allocative
  envelope_kingdom_composition: {Allocative: 50, Mediative: 30, Protective: 20}
  envelope_substrate: people
  envelope_weight: Ancillary
  typical_primary_kingdom: Allocative
  typical_kingdom_composition: {Allocative: 50, Mediative: 30, Protective: 20}
  typical_weight: Ancillary
  envelope_to_typical_rationale: null
  frequency_signal: occasional
  primacy_signal: lead
  level_calibration: |
    WSO — SECOND ALLOCATIVE CONTENT, captured from the SUPERVISION
    RECEIVED AND EXERCISED section rather than ESSENTIAL FUNCTIONS.
    "May provide direction" is conditional ("may") and weight is
    Ancillary because the duty is not in the Essential Functions
    section. Allocative primary because the work is direction-of-others;
    less Allocative concentration than F11 because seasonal/temporary
    direction is less structured than trainee supervision.
  canonical_function_mapping: null
  kingdom_confidence: m
  substrate_confidence: h
  weight_confidence: h
  segmentation_confidence: h
  mapping_confidence: l
  recovery_fidelity: verbatim
  notes: |
    Cross-section extraction — function lives in SUPERVISION RECEIVED
    AND EXERCISED, not Essential Functions. Captures duty content the
    Essential Functions section omits. Worth flagging for protocol:
    function extraction should scan all spec sections that contain
    duty-bearing language, not just Essential Functions. The protocol's
    Section 5 implicitly assumes Essential Functions is the duty-
    bearing section; the WSO case shows that supervision-section
    content can also be duty-bearing.
```

#### ImmaterialResiduals

```yaml
- residual_id: IR_BG_WSO_001
  source_text: "Remains calm and works extended hours in emergency situations"
  residual_type: role_attribute
  residual_category: working_condition_statement
  notes: |
    PHYSICAL/MENTAL/ENVIRONMENTAL WORKING CONDITIONS section content.
    Captures the emotional/temporal demands of emergency response —
    related to but distinct from the F1 night-call/weekend-duty function.
    Not function-bearing on its own (qualifies how F1 work is realized).
  recovery_fidelity: verbatim

- residual_id: IR_BG_WSO_002
  source_text: |
    DISTINGUISHING CHARACTERISTICS: "All positions assigned to the class require the ability to work independently, exercising judgment and initiative, and operate the full range of assigned equipment in a safe, efficient, and proper manner."
  residual_type: role_attribute
  residual_category: autonomy_framing
  notes: |
    Distinguishing-characteristics framing of journey-tier autonomy.
    Not a duty bullet but a structural statement about the class's
    autonomy expectation. Folded into envelope_description and
    spec_internal_consistency_flag (one of three autonomy framings in
    the spec). Captured as residual because the content is structurally
    important but not duty-bearing.
  recovery_fidelity: verbatim
```

#### Notes_global

```
Front-matter shows three-way autonomy framing inconsistency: DEFINITION
"Under close supervision," SUPERVISION RECEIVED "general supervision,"
ESSENTIAL FUNCTIONS "Independently, or as a member of a crew." Three
different framings in one spec — most striking quality anomaly in
the cohort so far. Journey-tier in the Operations ladder. 12 ExtractedFunctions
(11 from Essential Functions paragraph + 1 from SUPERVISION RECEIVED section)
+ 2 ImmaterialResiduals. F11 and F12 are the Allocative-content functions —
F11 from trainee supervision (Core, Essential Functions), F12 from
seasonal/temporary worker direction (Ancillary, supervision section).
Together they establish journey-tier Allocative content at ~5-9% range
(exact value pending script computation), confirming the cone-hypothesis
prediction that Allocative rises from 0% at trainee tier to some
journey-tier intermediate value. Substrate distribution is dominantly
physical_infrastructure (8 of 12 functions) with information substrate
at the data-collection functions (F2, F8, F10) and people substrate at
the Allocative functions (F11, F12). Title change September 2024 from
Water Maintenance Worker II; substantive revision was earlier (August 2021).
"WSOT → WSO" promotion-pathway provenance from DISTINGUISHING CHARACTERISTICS
pairs with WSOT's promotion-to-WSO expectation. Recurrence-test confirmation
of the promotion_expectation_provenance candidate field — two-instance
within-cohort pressure-test passed; ready for v2.1 promotion
once cross-agency recurrence is observed.
```

---

## Section 4 — Within-agency rollups

### WDM kingdom rollup (computed from this file's WDM record)

Computed from the 13 ExtractedFunctions in `JDR_BG_WDM` Section 3. Aggregation method documented per table; the §Q anti-pattern is mitigated by computing rollups from the same in-memory record set that the per-function YAML was rendered from rather than from a separately-maintained summary.

**Unweighted kingdom mix (envelope, all functions):**

| Kingdom | % | Source |
|---|---|---|
| Allocative | 39.6% | Sum of envelope_kingdom_composition.Allocative across 13 functions ÷ 13 |
| Mediative | 27.7% | Same method |
| Interpretive | 11.9% | Same method |
| Generative | 11.2% | Same method |
| Protective | 9.6% | Same method |

**Core-weighted kingdom mix (Core = 1.0, Ancillary = 0.5):**

| Kingdom | % |
|---|---|
| Allocative | 42.9% |
| Mediative | 25.0% (approx; recompute on full audit) |
| Interpretive | 11.5% |
| Generative | 11.5% |
| Protective | 10.4% |

**Recovery delta note (§Q reflexive observation).** Conversation-history recovery surfaced a prior reported WDM Allocative of **44.6%**. The above computation produces 39.6% unweighted / 42.9% Core-weighted. Delta of ~2-5 points is attributable to three functions reconstructed from bullet text only (EF_BG_WDM_011, EF_BG_WDM_012, EF_BG_WDM_014) where my reconstructed kingdom_composition may differ from the original. When the source PDF is re-uploaded and the three functions are re-decomposed at high fidelity, the rollup should be recomputed and the canonical value updated. Both the prior reported value and the current computed value are preserved in this artifact; the §Q discipline asks for the delta to be displayed, not papered over.

### WDM substrate distribution (Core-weighted, all functions)

| Substrate | % | Functions contributing |
|---|---|---|
| people | 37.5% | 001, 004, 006, 012 (Core); 014 (Ancillary) |
| physical_infrastructure | 25.0% | 008, 009, 011 (Core) |
| systems | 16.7% | 002, 007 (Core) |
| information | 12.5% | 010 (Core); 005 (Ancillary) |
| capital | 8.3% | 003 (Core) |

WDM substrate distribution is **people-dominant at 37.5%**, with physical_infrastructure as secondary at 25%. This is consistent with the framework expectation that management-tier classes shift toward people substrate (operating on the people who operate on the infrastructure) rather than directly on the infrastructure itself. WDM at 37.5% people is the high end of the within-cohort substrate-shift pattern noted in the cohort-level findings below.

### WSOT kingdom rollup (computed from this file's WSOT record)

Computed from the 6 ExtractedFunctions in `JDR_BG_WSOT` Section 3 at verbatim recovery fidelity, via `wsot_rollup.py` co-canonical computation script.

**Unweighted kingdom mix (envelope, all functions):**

| Kingdom | % | Source |
|---|---|---|
| Protective | 51.67% | Sum of envelope_kingdom_composition.Protective across 6 functions ÷ 6 |
| Generative | 34.17% | Same method |
| Mediative | 14.17% | Same method |
| Allocative | 0.00% | No Allocative content in any WSOT function — clean cone-hypothesis floor |
| Interpretive | 0.00% | No Interpretive content |

Sum: 100.01% (rounding artifact).

**Core-weighted kingdom mix (Core = 1.0, Ancillary = 0.5):**

| Kingdom | % |
|---|---|
| Protective | 51.00% |
| Generative | 39.50% |
| Mediative | 9.50% |
| Allocative | 0.00% |
| Interpretive | 0.00% |

The Core-weighted distribution shifts modestly from unweighted: Mediative compresses (from 14.17% to 9.50%) because the Mediative content concentrates in the Ancillary-weighted F6 (meter reading) and is therefore discounted. Generative *rises* (from 34.17% to 39.50%) because Generative is concentrated in Core-weighted F1, F2 (pipe-laying, tap-making). Protective is stable because it's distributed across both Core and Ancillary functions.

**Allocative=0% confirmation.** Prior cohort-level finding (recovery-from-conversation) reported WSOT Allocative at 0.0%. This canonical verbatim-fidelity computation confirms 0.0% at both unweighted and Core-weighted methods. The ladder-progression table below can therefore retire the recovery-from-conversation caveat on the WSOT row.

### WSOT substrate distribution (Core-weighted)

| Substrate | % | Functions contributing |
|---|---|---|
| physical_infrastructure | 90.00% | F1, F2, F3, F4 (Core, full-weight); F5 (Ancillary, half-weight) |
| information | 10.00% | F6 (Ancillary, half-weight) |

WSOT substrate distribution is **physical_infrastructure-dominant at 90.00%** Core-weighted — the highest physical_infrastructure concentration in the cohort. Prior cohort-level finding reported "WSOT (entry-tier) is 86.7% physical_infrastructure" from recovery-from-conversation; the canonical computation here yields 90.00%, a 3.3-point upward delta. The delta is attributable to the F5 (flag person) substrate coding: I assigned physical_infrastructure with note that people substrate is arguable; the recovery-from-conversation likely assigned people or a mixed substrate at that function. The delta sits within the within-function substrate-coding judgment band rather than indicating a substantive error.

Notable: information substrate appears at WSOT *only* through the meter-reading bundled function — the lowest-confidence function in the record. The information substrate signal at trainee tier is therefore the weakest link in the cohort's substrate-mapping evidence chain. Re-decomposition with F6 split into two functions (meter reading separated from worker-assistance) would clarify the information vs people substrate allocation.

### WSO kingdom rollup (computed from this file's WSO record)

Computed from the 12 ExtractedFunctions in `JDR_BG_WSO` Section 3 at verbatim recovery fidelity, via `wso_rollup.py` co-canonical computation script.

**Unweighted kingdom mix (envelope, all functions):**

| Kingdom | % |
|---|---|
| Protective | 32.50% |
| Generative | 29.58% |
| Mediative | 21.67% |
| Allocative | 9.17% |
| Interpretive | 7.08% |

**Core-weighted kingdom mix (Core = 1.0, Ancillary = 0.5):**

| Kingdom | % |
|---|---|
| Protective | 33.04% |
| Generative | 30.87% |
| Mediative | 21.30% |
| Allocative | 7.39% |
| Interpretive | 7.39% |

**Allocative-progression cone confirmation.** WSOT verbatim Allocative was 0.00%; WSO verbatim Allocative is 7.39% Core-weighted / 9.17% unweighted. Cone-monotonicity confirmed at trainee → journey progression in the Operations ladder. The Allocative content sources at journey tier are F11 (trainee supervision, Core, in Essential Functions) and F12 (seasonal/temporary worker direction, Ancillary, in SUPERVISION RECEIVED section). The prior recovery-from-conversation value (6.2%) sits between my unweighted and Core-weighted computed values — within judgment-band; the delta is attributable to my inclusion of F12 (extracted from SUPERVISION RECEIVED, which the recovery-from-conversation likely did not segment as a function).

**Protective primary at journey tier** — Protective dominates the kingdom mix at WSO (~33%) reflecting the high concentration of maintenance/repair/restoration work in the journey-tier function list (F1 night-call, F6 install/repair/replace, F7 pumping repair, F9 leak repair). Generative is close behind at ~31% reflecting the new-installation work content (F3-F5, F6, F9). The Protective/Generative balance is characteristic of journey-tier installation+maintenance work where each function realizes as some mix of new and existing-system work.

### WSO substrate distribution (Core-weighted)

| Substrate | % | Functions contributing |
|---|---|---|
| physical_infrastructure | 60.87% | F1, F3, F4, F5, F6, F7, F9 (Core) |
| information | 26.09% | F2, F8, F10 (Core) |
| people | 13.04% | F11 (Core), F12 (Ancillary, half-weight) |

WSO substrate distribution shows the first cohort instance of **three-substrate spread at a single class**: physical_infrastructure dominant (61%) but with substantive information (26%) and people (13%) components. This is the journey-tier substrate signature — wider than WSOT's narrow physical_infrastructure-dominant 90/10 split and narrower than WDM's people-dominant management-tier profile. The substrate-shift across strata pattern observed cohort-wide is now visible within the Operations ladder at full canonical fidelity:

| Stratum | Spec | physical_infrastructure | information | people | Fidelity |
|---|---|---|---|---|---|
| trainee | WSOT | 90.00% | 10.00% | 0.00% | verbatim |
| journey | WSO | 60.87% | 26.09% | 13.04% | verbatim |
| management | WDM | 25.00% | 12.50% | 37.50% | partial (3 functions reconstructed) |

The trainee → journey → management substrate-shift is monotonic decreasing for physical_infrastructure (90 → 61 → 25%) and monotonic increasing for people (0 → 13 → 38%). Information substrate peaks at the journey tier (26%) and recedes at management — consistent with the pattern that data-collection / detection / measurement work concentrates at the operational stratum while management substrate shifts to people-direction.

### Ladder-progression update (Operations ladder, WSOT + WSO rows at verbatim fidelity)

| Stratum | Spec | Allocative % | Fidelity |
|---|---|---|---|
| trainee | WSOT | 0.00% (Core-weighted); 0.00% (unweighted) | verbatim (this file) |
| journey | WSO | 7.39% (Core-weighted); 9.17% (unweighted) | verbatim (this file) |
| lead | (XRG_BG_001 — Lead WSO not acquired) | (gap) | — |
| supervisor | WOS | 39.1% (recovery-from-conversation) | pending verbatim re-decomposition |
| manager (convergence) | WDM | 44.6% (prior); 39.6%-42.9% (this file's recompute, partial fidelity) | partial (3 functions reconstructed) |

WSOT + WSO rows at verbatim fidelity establish the cone-hypothesis lower segment at full canonical fidelity: monotonic Allocative rise from 0% → 7.39% on the Operations ladder's trainee → journey progression. The prior recovery-from-conversation value (6.2%) sits within judgment-band of the current 7.39% Core-weighted computation; delta of ~1.2 points is attributable to my inclusion of F12 (May provide direction for seasonal or temporary workers, captured from SUPERVISION RECEIVED section, Ancillary weight). The cone-hypothesis ceiling at supervisor and manager tiers remains pending verbatim re-decomposition (WOS still recovery-from-conversation; WDM partial-fidelity).

The substrate-shift across strata is also now verbatim-fidelity at the lower segment: physical_infrastructure 90% → 61% (trainee → journey), with information rising 10% → 26% and people emerging from 0% → 13%.

### Cohort-level findings (recovered from conversation history; pending full re-canonicalization)

The following findings were computed in the original Burlingame decomposition session (chat `c12c0652-...`, 2026-05-12 PT) and are recorded here as recovery-from-conversation. They will be recomputed and canonical-stamped when all nine specs are landed in this file.

**Allocative ladder progressions (recovery-from-conversation):**

*Operations ladder:*

| Stratum | Spec | Allocative % |
|---|---|---|
| trainee | WSOT | 0.0% |
| journey | WSO | 6.2% |
| lead | (XRG_BG_001 — Lead WSO not acquired) | (gap) |
| supervisor | WOS | 39.1% |
| manager (convergence) | WDM | 44.6% (prior); 39.6%-42.9% (this file's recompute, partial-fidelity recovery) |

Monotonic Allocative rise across the strata. Cleaner cone-test surface than analyst-cohort progressions because operations-trades strata are explicitly named.

*Quality/Meter ladder:*

| Stratum | Spec | Allocative % |
|---|---|---|
| entry | WMR | 3.6% |
| journey | WQMT | 16.7% |
| lead | WQMLW | 34.5% |
| supervisor | WQS | 28.6% |
| manager (convergence) | WDM | 44.6% (shared convergence-point with Operations) |

**Quality/Meter ladder breaks Allocative monotonicity in an instructive way** — the dip at WQS (28.6% vs WQMLW's 34.5%) is structurally diagnostic. WQS has 22 essential-duty bullets (richest spec in the cohort) covering supervision + direct water sampling + regulatory research + UWMP implementation + cross-connection control + agency representation. Allocative *content* rises with strata, but Allocative *percentage* dilutes because higher-strata supervisors get loaded with more *types* of work alongside supervision. WDM is highest precisely because it's purely management-class with the technical work delegated downward. **Refinement to the manager-isn't-generalized reframe:** Allocative content scales with strata, but the percentage signal is confounded by content-portfolio breadth. The cleaner signal is *absolute Allocative magnitude per work area* rather than percentage of total.

**Cohort-weighted substrate distribution (recovery-from-conversation):**

| Substrate | % |
|---|---|
| physical_infrastructure | 39.9% |
| information | 22.2% |
| people | 19.5% |
| systems | 8.4% |
| capital | 6.5% |

Cross-cohort comparator: PA analyst cohort was ~70% information, minimal physical_infrastructure. **Substrate orthogonality confirmed** — same kingdom framework, dramatically different substrate distribution. Kingdoms describe *what kind* of work activity; substrates describe *what* the work operates on. Independent axes.

**Within-cohort substrate shift across strata (recovery-from-conversation):** WSOT (entry-tier) is 86.7% physical_infrastructure; supervisor classes (WOS, WQS, WDM) shift toward people substrate (29-40% people range; WDM at 37.5% per this file's computation). The strata progression involves both kingdom-shift and substrate-shift, on independent dimensions.

### Envelope-design patterns instantiated by this agency

Per the cross-agency synthesis layer (to be instantiated when migration lands), Burlingame water cohort instantiates all four envelope-design patterns:

1. **Vertical-progression cone** — Operations ladder (WSOT → WSO → [gap] → WOS → WDM) and Quality/Meter ladder (WMR → WQMT → WQMLW → WQS → WDM). Cleaner than analyst-cohort progressions due to explicitly named strata.

2. **Narrow-specialty hold-position** — WMR (Water Meter Repairer). High Protective + Interpretive, minimal Allocative. Career-track-distinct from the parallel ladders. Pattern matches PA Crime Analyst + Payroll Analyst.

3. **Sub-function-activation hub** — WST (Water Service and Operations Technician). Multiple sub-function activations (SCADA + well operations + customer service + Water Conservation Program). Same pattern as PA BA's department-deployment activations but at IC-stratum rather than journey-stratum. Confirms hub-with-spokes envelope-design is not strata-specific.

4. **Convergence-point manager** — WDM. NEW pattern surfaced by this cohort. Sits at the convergence of two parallel ladders; both supervisor classes report up to WDM; WDM directs both crews. Kingdom-mix at the convergence pulls from both upstream ladders (weighted blend of WOS + WQS rather than pure extension of either). Different from analyst-cohort's single-ladder progression. **Forward work surface:** Deputy Director of Public Works Operations (XRG_BG_005) acquisition would test whether the divergence-point above WDM (multiple division managers → one deputy) is a fifth envelope-design pattern.

### Water Division findings worth flagging

- **Bargaining-unit asymmetry at supervisor stratum.** WQS in AFSCME 829 EXEMPT vs WOS in BAMM Unit. Both supervisor-class structurally; union assignment differs. Historical artifact of ladder accretion.
- **Spec staleness on Operations side relative to Quality side.** WOS (2011) carries deprecated "Assistant Water Superintendent" reference; WQS (2017) uses current "Water Division Manager" reference. Six-year reference-staleness gap. SB-1100 review-cycle should surface and resolve.
- **Direction-language cross-cycle inversion.** WQMT (2008) "Under general direction" vs WQMLW (2015) "Under general supervision" — higher-stratum class has *less autonomous* formal language. Specs written in incompatible registers. Implication: scope-qualifier signal preferred over autonomy-language signal for cone measurement in operations-trades families.
- **Duplicate class code S507.** Shared by WQMT and WST. Data anomaly; resolution unresolved.
- **September 2024 title-design-as-policy-lever instance.** Two specs (WSOT, WSO) retitled from Maintenance Worker I/II with no substance change. Agency-documented title-vs-substance separation, directly aligned with framework's title-de-reification posture.

### Planning Department rollups (single-spec sample, Zoning Technician)

Computed from 10 ExtractedFunctions in `JDR_BG_ZT` Section 3 at verbatim recovery fidelity, via `zt_rollup.py` co-canonical computation script. All ZT functions are Core weight (no Other Duties in the source spec), so unweighted and Core-weighted produce identical results.

**Kingdom mix (unweighted, identical to Core-weighted):**

| Kingdom | % |
|---|---|
| Interpretive | 37.50% |
| Mediative | 27.50% |
| Generative | 19.50% |
| Protective | 15.50% |
| Allocative | 0.00% |

**Substrate distribution (Core-weighted):**

| Substrate | % | Functions contributing |
|---|---|---|
| information | 80.00% | F1, F3, F4, F5, F6, F7, F8, F10 |
| people | 20.00% | F2 (counter/telephone public service), F9 (code enforcement) |

### Planning Department findings worth flagging

- **Extreme-vintage staleness.** Zoning Technician carries footer date 1993 with no subsequent revision — 33 years stale at canonical instance. Agency-wide staleness extreme (water cohort's max was 15 years at WOS 2011). Content artifacts include microfiche reference, "modern office procedures" 1993-register framing, duplicate "data collection and analysis" phrasing, and absence of the "under [close|general] supervision/direction" autonomy-language convention the water cohort uses.
- **Cross-department bargaining-unit anomaly.** Zoning Technician is in AFSCME 829 Maintenance Unit despite being a Planning Department knowledge-worker class. Same bargaining unit as Water System Operator Trainee (heavy-labor Water Division class). Possible explanations: smaller-municipality bargaining-unit organization is broader than function-typed; historical artifact of when Planning was a sub-function of Public Works; spec was never re-organized. Worth HR-cycle reconciliation review.
- **Template-reuse copy-paste artifact.** Zoning Technician PDF page footer reads "WATER SERVICE & OPERATIONS TECHNCIAN" — directly inherited from a Water Division spec template; never updated. Direct evidence that Burlingame HR composes specs from prior-spec templates and that footer text is not a reliable provenance signal.
- **Entry-IC envelope-design pattern distinct from water cohort.** Zoning Technician is "entry-level" by department status but operates with lead-primacy across a wide work portfolio (10 functions, all Core, no "assists" hedging). The water cohort's entry tier (WSOT) is a trainee class with assist-primacy. Same "entry-level" label, structurally different envelope. Candidate pattern: "wide-portfolio entry-IC" as a fifth envelope-design pattern (alongside the four already documented in the synthesis layer).

### Cross-department findings (Water Division vs Planning Department)

The Zoning Technician landing makes possible the first within-agency cross-department comparison. Two findings emerge from the single-spec Planning sample against the two-spec Water sample:

**Substrate-orthogonality confirmed at intra-agency scale.** Same Kingdoms framework, dramatically different substrate distribution:

| Department | Spec | Dominant substrate | Secondary |
|---|---|---|---|
| Water Division (entry) | WSOT | physical_infrastructure 90% | information 10% |
| Water Division (management) | WDM | people 37.5% | physical_infrastructure 25% |
| Planning Department (entry) | Zoning Technician | information 80% | people 20% |

The substrate orthogonality previously observed between Burlingame water cohort and PA analyst cohort (cross-agency) is now observed *within* Burlingame between Water Division and Planning Department. This strengthens the substrate-as-orthogonal-axis hypothesis: substrate is a function of work-content, not of agency or organizational level, and varies systematically across departments doing different kinds of work even within the same employer.

**Allocative-floor consistency across departments at entry tier.** Both WSOT (Water Division trainee) and Zoning Technician (Planning Department entry-IC) compute 0.00% Allocative at full canonical fidelity. The cone-hypothesis floor at 0% Allocative holds at entry tier regardless of department / substrate / verb-stack. This is a useful cross-department confirmation of the cone-hypothesis floor; the cone-hypothesis ceiling (management tier ~40-45% Allocative) is only tested at WDM so far within Burlingame and will need a Planning Department management spec for cross-department ceiling confirmation.

**Envelope-design pattern divergence at entry tier.** The four envelope-design patterns documented from the water cohort (vertical-progression cone, narrow-specialty hold-position, sub-function-activation hub, convergence-point manager) all describe ladders or positions within a single function family. The Zoning Technician spec presents a different shape: a single position class at entry-IC tier with a wide work portfolio across 10 distinct functions, no ladder-progression upward visible from the single-spec sample. Candidate fifth pattern: "wide-portfolio entry-IC" — entry-tier IC class with broad work distribution at lead-primacy. Recurrence-test pending on Planner / City Planner acquisition (which would test whether the Planning Department ladder above Zoning Technician is a cone-progression like Water Division's or a different structure entirely).

---

## Section 5 — Cross-agency integration hooks

### Synthesis file reference

Cross-agency findings live in `jd_decomposition_synthesis_<ts>.md` (to be instantiated alongside the monolith migration). The synthesis file will hold:
- The four envelope-design patterns (with per-agency instances)
- Substrate-orthogonality hypothesis and cross-cohort evidence
- Cone-hypothesis cumulative pressure-test record
- Manager-isn't-generalized reframe with cross-agency Allocative concentration data
- §M Layer 2 skill-mapping cross-agency rollups (when produced)

Until the synthesis file is instantiated, the cross-agency findings remain in their original homes (Entry 38 spine, prior cohort addenda referenced in conversation history). This section will be updated with concrete pointers when the synthesis file lands.

### Comparator references

- **PA analyst cohort** — primary substrate-orthogonality comparator. Burlingame's physical_infrastructure dominance (~40% cohort-weighted) vs PA-analyst's information dominance (~70%) is the strongest cross-cohort substrate signal in the corpus.
- **Hayward MA cohort** (in monolith) — level-progression magnitude comparator. Hayward's flat ~16% Allocative across MA I/II/Sr (shared function pool) vs Burlingame's monotonic Allocative rise across operations-trades strata. Both are level-progression instances but the underlying JD-design house differs in how level differentiation is encoded.
- **Menlo Park ISM + Newark SIM** (in monolith) — strata-analogue management-class comparators. Burlingame WDM as a clean management-class spec offers a third instance for the manager-isn't-generalized reframe; cross-comparison should yield refined Allocative-concentration benchmarks.

### Framework-level contributions this agency made

To be populated as cohort findings are folded into framework-level codification. Anticipated contributions (one-instance articulations from the 2026-05-12 thread, awaiting recurrence-threshold confirmation):
- **Convergence-point manager** as fourth envelope-design pattern (WDM at the convergence of Operations + Quality/Meter ladders).
- **Cross-reference gap registry** as generalized structured-data feature (not Burlingame-specific).
- **Title-change provenance**, **spec staleness flag**, **duplicate class code flag** as candidate v2.1 rubric extensions.
- **Scope-qualifier signal vs autonomy-language signal** as cleaner cone-measurement axis for operations-trades families.
- **Within-cohort substrate shift across strata** observation (entry-tier physical_infrastructure → supervisor-tier people; both axes move on different dimensions as you climb).

---

*Composed 2026-05-12 18:02 UTC at fourth canonical instance (Water System Operator landing). Prior canonicals at 2026-05-12 17:10 UTC (first per-agency-file instance, WDM from conversation-history recovery), 2026-05-12 17:34 UTC (WSOT verbatim), and 2026-05-12 17:50 UTC (Zoning Technician verbatim + agency-wide reframe). This instance lands the journey-tier pair to WSOT in the Operations ladder, establishing the cone-hypothesis lower segment (trainee → journey) at full verbatim fidelity. Subsequent appends will advance the canonical timestamp at real composition time per protocol Section 8 discipline. **Recovery provenance summary at this instance:** WDM record carries the recovery-from-conversation provenance from the first instance (partial fidelity, 3 functions reconstructed); WSOT, Zoning Technician, and WSO records are fully verbatim from primary-source PDFs. **Timestamp note:** The project chain's most recent handoffs carry later stamps (Thread 11 close at `20260516T080000Z`), making this file's timestamp non-monotonic vs the chain. The non-monotonicity is preserved deliberately: real composition time is the reconstruction anchor; the apparent regression reflects a real cross-session date discrepancy between this session's clock and prior sessions' clocks.*
