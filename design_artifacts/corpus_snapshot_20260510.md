# Project Rigger — Current-State Corpus Snapshot

**Status:** Compression-dividend artifact for the architecture pass on the corpus per `architecture_pass_corpus_scoping_20260510.md`. Single-document view of what is canonical, what is superseded, what is carry-forward, and where each lives. Intended as the navigation aid that lets subsequent sessions orient without traversing the full 84-file corpus. Tier D (carry-forward) until recursive-updates session codifies it.

**Composed against chain head:** Entry 29 (`23f40190d15e10cf590b0bbe8b93ab9a6d51a4c2268ab3b626cbebc059b31d2f`), verified via `verify_entry_29.py` 58/58 PASS at pass open.

## Pre-snapshot tier handling note

This snapshot captures the corpus *as-of pass open*, before R1–R8 of the findings artifact (`architecture_pass_corpus_findings_20260510.md`) are applied by the recursive-updates session. After the recursive-updates session lands, this snapshot is superseded by a post-update version produced under R3's restructured README + `README_changelog.md` shape. Until then, this is the authoritative single-doc current-state view.

## Canonical surface (what a fresh session needs)

Just these files, in this order, are the operational entry surface:

| # | File | Purpose | Size |
|---|---|---|---|
| 1 | `README.md` | Reading-order entry point + canonical-artifact pointers + cross-session handshake protocol | 31 KB |
| 2 | `framework_decisions_record_20260510T140000Z.md` | Chain spine through Entry 29 | 399 KB |
| 3 | `verify_entry_29.py` | Post-commit verification for Entry 29 (run on session open) | 15 KB |
| 4 | `handoff_20260510T140000Z.md` | Most-recent chain-entry handoff | 24 KB |
| 5 | `handoff_20260510_session_end_lightweight.md` | Most-recent session-output handoff (lightweight cadence) | 10 KB |
| 6 | `architecture_pass_corpus_scoping_20260510.md` | Active forward-pointer for this pass | 21 KB |
| 7 | `framework_principles.md` | Constitutional principles (pre-Entry-25 state — flagged stale) | 18 KB |
| 8 | `framework_design_three_lens_v2.md` | Three-lens model | 17 KB |
| 9 | `core_principles_for_agent_behavior.md` | Agent behavior principles (pre-Entry-25 state — flagged stale) | 30 KB |
| 10 | `cohort_temporal_record_mod3.md` | Operational records | 107 KB |
| 11 | `project_rigger_glossary_mod5.md` | Terminology reference | 75 KB |

**Subtotal: 11 files, 747 KB.** This is the operational reading surface. Everything else in /mnt/project/ is either:
- Live canonical but secondary (design docs, typologies, domain models, audits-currently-active) — read-on-demand from README pointers
- Historical fossil (older spine timestamps, mod-N predecessors, archived handoffs) — preserved for provenance
- Forward-pointing or in-flight (this pass's outputs, comparator scoping, etc.)

## Live secondary canonical (read on demand from README)

Referenced by README reading order but not in the operational entry surface. These are durable artifacts that subsequent sessions consult based on need:

| Category | Files | Aggregate size |
|---|---|---|
| Design docs | `aar_capture_design.md`, `coordinator_synthesis_design.md`, `explainer_agent_design.md`, `learning_library_design.md`, `reference_datasheet_design.md`, `character_sheet_template_design.md` | 130 KB |
| Domain models | `data_model_adds_onboarding_and_mentorship.md`, `data_model_adds_cohort_findings.md`, `role_definitions_onboarding_and_mentorship.md` | 72 KB |
| Typologies | `role_pathology_typology.md`, `trusted_talent_network_typology.md` | 46 KB |
| Findings | `architecture_pass_fractal_findings_20260508.md`, `compression_restructure_findings_20260509.md` | 50 KB |
| Meta-AAR | `meta_aar_verification_discipline_arc_20260509.md` | 45 KB |
| Stakeholder-facing | `nick_readme.md`, `nick_whats_changed_briefing.md` | 18 KB |
| Translation tables | `single_loop_double_loop_pilot_instructions_20260509.md`, `single_loop_double_loop_translation_table_20260510T080000Z.md` | 21 KB |
| Templates | `_readme_template.md`, `_whats_changed_template.md` | 12 KB |
| Pending stakeholder action | `city_attorney_consult_brief_records_act.md` | 10 KB |

**Subtotal: 19 files, 404 KB.**

## Historical fossils (provenance-only, candidates for archive per R1–R5)

Currently in /mnt/project/ but their canonical function has been superseded. Recursive-updates session per R1–R5 moves these to `_archive/` (mechanism TBD per open question 1):

| Category | Files | Aggregate size |
|---|---|---|
| Pre-T140000Z spine versions (R1) | `framework_decisions_record.md`, 5 timestamped predecessors (T010156Z, T021500Z, T033000Z, T100000Z, T120000Z) | 1.94 MB |
| Pre-mod4 glossary versions (R2 partial) | `project_rigger_glossary.md`, `_mod1`, `_mod2`, `_mod3` | 222 KB |
| Pre-mod2 cohort versions (R2 partial) | `cohort_temporal_record.md`, `_mod1` | 172 KB |
| Pre-protocol legacy handoffs (R5) | `Handoff_document_-_20260430_evening.md`, `Handoff_document_-_20260505.md` | 67 KB |
| Earlier chain-entry handoffs beyond N=5 inline window (R5) | ~7–10 of the 14 timestamped handoffs (specific selection at recursive-updates time) | ~150 KB |
| Effort-only / non-chain handoffs (R5) | A subset of the timestamped handoffs that did not produce chain entries | ~50 KB |
| Audits whose findings have been integrated | `records_keeping_audit_20260507.md`, `data_integrity_audit_20260508.md` | 65 KB |
| Forward-pointers superseded by canonical | `course_corrections_data_and_replication_20260507.md`, `san_bruno_seed_export.md` | 38 KB |
| Substantive seeds (selective retention) | `Handoff_document_-_20260430.md` keeps inline (substantive); orphan-track handoffs already marked | — |

**Estimated archive footprint: ~2.7 MB out of 4.4 MB total corpus (61%).** Post-archive, the inline /mnt/project/ would be approximately 1.7 MB.

## Carry-forward (not-yet-canonical, in-flight)

| File | Status | Disposition |
|---|---|---|
| `handoff_20260510_session_end_lightweight.md` | First lightweight-cadence instance | Lift to canonical via R6 codification |
| `comparator_agency_p_scrape_experiment_scoping_20260510__1_.md` | Forward-pointer for external experiment | Becomes Tier C lateral after recursive-updates renames to drop `__1_` suffix |
| `architecture_pass_corpus_scoping_20260510.md` | This pass's scoping doc | Becomes Tier C lateral after this pass closes |
| `architecture_pass_corpus_findings_20260510.md` (this pass's primary deliverable) | Tier D until codified | Becomes Tier C lateral after recursive-updates session |
| `corpus_snapshot_20260510.md` (this file) | Tier D until codified | Becomes Tier C lateral after recursive-updates session; superseded by post-update snapshot |
| `meta_aar_corpus_recompression_20260510.md` (this pass's AAR) | Tier D until codified | Becomes Tier C lateral after recursive-updates session |
| `chain_entry_text_corpus_recompression_20260510.md` (chain entry draft) | Tier D | Folded into new timestamped spine by recursive-updates session |

## Out-of-scope (different project)

- Ronak seed bundle (mentioned in lightweight handoff; intended for separate Claude project)

## Out-of-frame (operational, not framework)

- `FY27_Transmittal_Letter_DRAFT.docx` (per README adjacent-documents block)

## Cross-session handshake at pass open (per README protocol)

- **Chain head:** `23f40190d15e10cf590b0bbe8b93ab9a6d51a4c2268ab3b626cbebc059b31d2f` (Entry 29)
- **Verify status:** 58/58 PASS via `verify_entry_29.py /mnt/project/`
- **Per-thread session limiters at pass open:** effort accumulator 0/15; handoff-instance counter 0/1
- **Carry-forward open work:** R1–R8 from findings artifact for recursive-updates session (split across ≥2 sessions per per-thread limiters)
- **Audit observations queued:** three (per findings §5)

## Cross-references

- `architecture_pass_corpus_findings_20260510.md` — primary findings; this snapshot is the navigation companion
- `meta_aar_corpus_recompression_20260510.md` — methodology AAR
- `chain_entry_text_corpus_recompression_20260510.md` — chain entry draft
- `architecture_pass_corpus_scoping_20260510.md` — scoping precedent for this pass
- `README.md` — current canonical entry point (will be restructured per R3)

---

*Provenance: Snapshot composed 2026-05-10 PT alongside the findings artifact. Tier D until the recursive-updates session codifies it. Intended utility horizon: until the post-recursive-updates snapshot replaces it.*
