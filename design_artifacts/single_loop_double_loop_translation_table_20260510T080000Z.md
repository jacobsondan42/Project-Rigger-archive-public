# Translation Table — Single-Loop vs Double-Loop Learning ↔ Active Codification Arc

**Timestamp:** `20260510T080000Z` (initial version).

**Status:** Companion artifact to `single_loop_double_loop_pilot_instructions_20260509.md`. Cross-reference map between the deferred M (single-loop vs double-loop learning codification, queued for the post-major-patch arc) and the active S codification arc currently being sequenced (Entries 27–30 candidate sequence, lands accumulator at 15/15 and triggers the major-patch handoff).

**Provenance shape:** Stakeholder direction at fresh-playground session: *"don't lose any threads of the little-but-useful connections elsewhere. To the extent we separate/divorce tasks, let's just name that and say we need a translation table to get them to balance"* + *"translation table should be a time-stamped artifact to verify it's the latest in the list if that's what we're using."*

**Versioning convention:** Append-only timestamped artifact. Each new version produces a new timestamped filename; prior versions become orphans at their timestamps. The latest timestamp is canonical. README pointer should track the latest version when this artifact category is referenced from the chain (which will happen when the first S codification entry in the active arc adds a forward-connection to the table).

**Update protocol:** When an S codification entry in the active arc adds a forward-connection to this table (the entry's outcome substantively touches a row), a new timestamped version of this artifact is produced as part of that entry's deliverables. The new version retains all prior rows plus updates the relevant row's "Forward-connected by" column with the entry reference. The deferred M loads the latest version at execution time as part of its reading list.

---

## Connection table

Each row names a candidate connection between the deferred M and active or potential framework work. Status: **Explicit** = attested in canonical records (specific citation given); **Claim** = analytical claim made at translation-table-authoring time, deferred M validates / refines / rejects.

| # | Candidate connection | Status | What deferred M owes | Forward-connected by |
|---|----------------------|--------|----------------------|----------------------|
| 1 | Verification ladder construction (Entries 17–20) as primary double-loop substrate | **Explicit** (meta-AAR Phase 1) | Codify; use as worked instance | Pending |
| 2 | Tapeworm-recursion + paired-versioning response (Entry 24) as second load-bearing double-loop instance | **Explicit** (meta-AAR Phase 4) | Codify; use as worked instance | Pending |
| 3 | Stakeholder operational pragmatism as double-loop trigger when single-loop diagnostic loops cannot self-correct | **Explicit** (meta-AAR Phase 2 Lessons) | Codify the trigger function; cross-reference with the separate stakeholder-operational-pragmatism codification candidate (M-3, four observed instances, holding for substantive recurrence) | Pending |
| 4 | Operationalized-minimum vs core-insight gap as the same single-loop/double-loop pattern at the principle-articulation level (operationalized-minimum ≈ single-loop articulation locked to specific cases; core-insight ≈ double-loop articulation naming the more general operation) | Claim | Validate, refine, or reject; if validated, candidate co-codification with the operationalized-minimum/core-insight architectural-decision-deferred item | Pending |
| 5 | Hash-mechanical linkage as recursively-applicable framework pattern; the recursive applicability claim likely requires single-loop/double-loop frame as the governing frame for why hash-mechanical is the right structural response across instances (chain integrity at genesis; hash-manifest at Entry 19; modification-confirmation at Entry 20) | Claim | Validate; if validated, hash-mechanical-linkage codification (M-3 carry-forward at four instances) gains single-loop/double-loop as governing frame on its codification | Pending |
| 6 | Mechanism-agnostic discipline response as a *type* of double-loop move (rules-of-frame change because mechanism is unknown — diagnose-before-codify, rename-as-navigation, paired-versioning all share this shape) | Claim | Validate; if validated, the mechanism-agnostic pattern's codification gains explicit double-loop classification | Pending |
| 7 | Chain audit dimension as double-loop response to the append-only-vs-retrospective-observation tension (rules of the chain didn't change to allow amendment; a new dimension was added) | Claim | Validate; chain audit dimension generalization (S, three-scale recurrence threshold, currently at two scales) gains double-loop classification on its codification | Pending |
| 8 | Granularity-insight resolution protocol three-case hierarchy (meta-principle relation / operating-principle relation / error term) likely needs single-loop/double-loop as governing analytical posture; "error term" as first-class framework category crosses both frames since error term is single-loop diagnostic concept (residual after compression) being elevated to framework-level analytical category | Claim | Validate; granularity-insight resolution protocol codification (S, new candidate from session-close anchors) cross-references single-loop/double-loop on its codification | Pending |
| 9 | Reflexive principle #23 application (verify claims mechanically against records) as primary single-loop discipline of the framework, with chain-hash authentication as primary double-loop layer (#23 tightens within-rules; chain-hash establishes the rules) | Claim | Validate; if confirmed, names a primary single-loop / primary double-loop pair that may anchor the codified principle | Pending |

---

## Reading guide

For the **active codification arc**, when a chain entry's outcome substantively touches a row above, the entry adds a "Forward connection to deferred M" subsection naming the row number(s) and what the connection is. The next timestamped version of this table is then produced as part of the entry's deliverables, updating the "Forward-connected by" column for the touched row(s).

For the **deferred M** at execution time, this table is the obligation map. Each Explicit row is a worked instance to use; each Claim row is a hypothesis to validate, refine, or reject. The state of the "Forward-connected by" column at deferred-M-execution time tells the M which connections have been pre-touched by S work and which need to be addressed fresh.

---

## Provenance

- **Initial version composed:** Late evening 2026-05-09 PT (UTC `20260510T080000Z`), as part of the fresh-playground session that produced the companion pilot instructions document and the session-close handoff (`handoff_20260510T080000Z.md`).
- **Chain head at authoring:** `280bc4166a1d400bbf30c515b8970c0067dfaa41e37feca7e1dc5c185b5ad4be` (Entry 26).
- **Companion:** `single_loop_double_loop_pilot_instructions_20260509.md`.
- **Cross-references:** `meta_aar_verification_discipline_arc_20260509.md` (Phases 1, 2, 4 substantive pressure-tests for Explicit rows); `framework_decisions_record_20260510T033000Z.md` (Entry 26, current chain head); `cohort_temporal_record_mod3.md` (Framework Finding #23 names single-loop/double-loop in operational records).
- **Status of integration:** None yet. This artifact category and its update protocol have no canonical chain reference yet; the first chain reference will land when the first S codification entry in the active arc adds a forward-connection.
- **Codification candidate surfaced by this artifact's existence:** "Translation table as a framework artifact category" (companion to the "scoped-project pilot instructions" artifact category). First canonical instance is this document. Codify on second canonical instance per the framework's recurrence-based codification discipline.
