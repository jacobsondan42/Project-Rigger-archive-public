# JD Decomposition Records — Burlingame

**Status:** First canonical instance of the per-agency lateral reference file for Burlingame water utility decomposition. Inaugurates the per-agency-file architecture proposed in Thread 12 (replacing the prior monolithic `jd_decomposition_records_<ts>.md` shape). Composed under the working-window discipline: incremental per-spec append with full re-canonicalization at each timestamp.

**Filename convention:** `jd_decomposition_records_<agency>_<UTC-timestamp>.md` under Timestamped lateral versioning (Cross-session handshake protocol sub-part 1(c)).

**Rubric version applied:** v2.0 — `rubric_jd_decomposition_20260511T230000Z.md`.

**Specs landed at this canonical timestamp:** 1 of 9 (Water Division Manager).

**Recovery provenance.** The substantive decomposition work for the Burlingame cohort was originally executed in conversation thread `c12c0652-966a-46b0-820f-258b2abb9749` (2026-05-12 PT) but was not canonicalized at composition; the generator scripts (`gen_bg_water.py`, `specs_bg_*.py`, runner) and rendered artifact existed only in that session's filesystem and were lost at session boundary. This file reconstructs from conversation-history recovery via `conversation_search`, marking per-record fidelity (verbatim-recovered / partial / placeholder-for-source-rederivation). The recovery loss is itself a worked instance of the §Q lossy-state anti-pattern surfaced at Thread 11 close and a worked instance of the broader principle this file's existence operationalizes: **structured-data artifacts must be canonicalized at composition, not deferred.**

**Migration note.** The existing `jd_decomposition_records_20260515T030000Z.md` monolith (17 records across SB / Hayward / SSF / Samtrans / Menlo Park / Newark) will be migrated to per-agency files in a follow-on chain entry, per stakeholder decision to migrate-rather-than-freeze. Until that migration lands, the monolith remains the canonical source for those 17 records. Cross-agency synthesis (envelope-design patterns, substrate-orthogonality findings, cone-hypothesis pressure-test record, manager-isn't-generalized reframe) will live in a separate `jd_decomposition_synthesis_<ts>.md` lateral instantiated alongside the migration.

---

## Section 1 — Agency schema and conventions

### Class code conventions

Burlingame uses a letter-prefix system:
- **S-prefix** (e.g., S502, S507, S605): non-exempt classifications, primarily in AFSCME bargaining units. Operations-trades and journey-level classes carry S-prefix codes.
- **B-prefix** (e.g., B500, B-501, B503): exempt classifications, primarily in BAMM Unit. Supervisor and management classes carry B-prefix codes.

**Known data anomaly:** `S507` is shared by two distinct classifications — Water Quality and Meter Technician (WQMT) and Water Service and Operations Technician (WST). Both specs carry S507 in footers. Status: unresolved data anomaly; likely HR data error or migration artifact. Tracked as a `duplicate_class_code_flag` on both records when those records land.

### Bargaining units present in this cohort

| Unit | Specs | Exempt status |
|---|---|---|
| AFSCME 829 Maintenance Unit | WSOT, WSO | Non-Exempt |
| AFSCME 2190 | WST, WMR, WQMT | Non-Exempt |
| AFSCME 829 (Worker class) | WQMLW | Non-Exempt |
| AFSCME 829 EXEMPT | WQS | Exempt — bargaining-unit asymmetry |
| BAMM Unit | WOS, WDM | Exempt |

**Bargaining-unit asymmetry at the supervisor stratum.** WQS is in AFSCME 829 EXEMPT (workers' union, exempt status) while WOS is in BAMM Unit (management union, exempt). Both are supervisor-class equivalents structurally; the union assignment differs. Likely historical artifact of how the two ladders accreted into a single division. Worth flagging in the trust-schema / bias-disclosure axis.

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

| Spec ID | Title | Upload filename | Source URL pattern |
|---|---|---|---|
| JDR_BG_WSOT | Water System Operator Trainee | `Water_System_Operator_Trainee_-_September_2024.pdf` | `/DocumentCenter/View/...` |
| JDR_BG_WSO | Water System Operator | (TBD — recover from conversation) | `/DocumentCenter/View/...` |
| JDR_BG_WST | Water Service and Operations Technician | `Water_Service_and_Operations_Technician__PDF_.pdf` | `/DocumentCenter/View/1076/...` |
| JDR_BG_WMR | Water Meter Repairer | (TBD) | `/DocumentCenter/View/...` |
| JDR_BG_WQMT | Water Quality and Meter Technician | `Water_Quality_and_Meter_Technician__PDF_.pdf` | `/DocumentCenter/View/1074/...` |
| JDR_BG_WQMLW | Water Quality and Meter Lead Worker | (TBD) | `/DocumentCenter/View/...` |
| JDR_BG_WOS | Water Operations Supervisor | `Water_Operations_Supervisor__PDF_.pdf` | `/DocumentCenter/View/...` |
| JDR_BG_WQS | Water Quality Supervisor | (TBD) | `/DocumentCenter/View/...` |
| JDR_BG_WDM | Water Division Manager | `Water_Division_Manager__PDF_.pdf` | `/DocumentCenter/View/...` |

URLs marked TBD will be reconstructed from the source PDFs when re-uploaded for the gap-filling sessions.

### Cross-reference gap registry

Generalized framework feature instantiated in this cohort. Records any spec that references another classification we don't have decomposition records for, with status:

- `existing_not_acquired` — class exists per the agency's published catalog but we don't have its spec
- `deprecated_renamed_to_existing` — referenced title has been renamed; the current title is one we have or could acquire
- `out_of_scope_adjacent` — class exists but sits outside the cohort scope (different department or function family)

| Gap ID | Referenced class | Status | From specs | Context |
|---|---|---|---|---|
| XRG_BG_001 | Lead Water System Operator | existing_not_acquired | JDR_BG_WSO, JDR_BG_WOS | WSO Supervision Received: "Receives general supervision from the Lead Water System Operator and Supervisor positions." Closing this gap would complete the Operations-ladder cone-hypothesis test at the leadworker stratum. |
| XRG_BG_002 | Assistant Water Superintendent | deprecated_renamed_to_existing | JDR_BG_WOS | WOS (2011) references this title; renamed to Water Division Manager in 2017 revision cycle. WOS spec was not updated to reflect the rename. |
| XRG_BG_003 | Water Maintenance Worker | deprecated_renamed_to_existing | JDR_BG_WMR | Referenced by WMR ("See Water Maintenance Worker essential duties"). Renamed to Water System Operator in September 2024. |
| XRG_BG_004 | Service Worker | deprecated_renamed_to_existing | JDR_BG_WMR | Referenced by WMR. Likely renamed to Water Service and Operations Technician at the September 2024 retitling. |
| XRG_BG_005 | Deputy Director of Public Works Operations | out_of_scope_adjacent | JDR_BG_WDM | WDM's next-higher class in the org chart. Upward extension target for cone-hypothesis testing; would also test whether a divergence-point pattern (multiple division managers → one deputy) is a fifth envelope-design pattern. |
| XRG_BG_006 | Meter Reader | out_of_scope_adjacent | JDR_BG_WQMT, JDR_BG_WQMLW | Referenced for absence backup; separate sub-function family. |
| XRG_BG_007 | Irrigation Specialist | out_of_scope_adjacent | JDR_BG_WST | Referenced for coordination on well/irrigation; Parks Department adjacent class. |

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

### Agency-specific findings worth flagging

- **Bargaining-unit asymmetry at supervisor stratum.** WQS in AFSCME 829 EXEMPT vs WOS in BAMM Unit. Both supervisor-class structurally; union assignment differs. Historical artifact of ladder accretion.
- **Spec staleness on Operations side relative to Quality side.** WOS (2011) carries deprecated "Assistant Water Superintendent" reference; WQS (2017) uses current "Water Division Manager" reference. Six-year reference-staleness gap. SB-1100 review-cycle should surface and resolve.
- **Direction-language cross-cycle inversion.** WQMT (2008) "Under general direction" vs WQMLW (2015) "Under general supervision" — higher-stratum class has *less autonomous* formal language. Specs written in incompatible registers. Implication: scope-qualifier signal preferred over autonomy-language signal for cone measurement in operations-trades families.
- **Duplicate class code S507.** Shared by WQMT and WST. Data anomaly; resolution unresolved.
- **September 2024 title-design-as-policy-lever instance.** Two specs (WSOT, WSO) retitled from Maintenance Worker I/II with no substance change. Agency-documented title-vs-substance separation, directly aligned with framework's title-de-reification posture.

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

*Composed 2026-05-12 17:10 UTC at first per-agency-file canonical instance. Recovery-from-conversation provenance throughout Section 3 and Section 4 (when populated). Subsequent appends will advance the canonical timestamp; this file at `20260512T171048Z` is the first instance of the architecture. **Timestamp note:** This file's timestamp reflects real composition time (Tuesday May 12, 2026, 17:10:48 UTC) rather than scheduled-slot logic. The project chain's most recent handoffs carry later stamps (Thread 11 close at `20260516T080000Z`), making this file's timestamp non-monotonic vs the chain. The non-monotonicity is preserved deliberately: real composition time is the reconstruction anchor; the apparent regression reflects a real cross-session date discrepancy between this session's clock and prior sessions' clocks.*
