# Architecture Pass on Corpus — Findings

**Status:** Findings artifact for the substantive architecture pass scoped by `architecture_pass_corpus_scoping_20260510.md`. Treated as Tier D (carry-forward, not-yet-canonical) per the scoping doc's reflexivity discipline until the chain entry codifies what it implies. Recursive-updates session runs against the recommendations in §6.

**Provenance:** Composed 2026-05-10 PT against chain head Entry 29 (`23f40190d15e10cf590b0bbe8b93ab9a6d51a4c2268ab3b626cbebc059b31d2f`, ground-truthed via `verify_entry_29.py` 58/58 PASS at pass open). Companion to `corpus_snapshot_20260510.md` (the compression-dividend artifact) and `meta_aar_corpus_recompression_20260510.md` (the methodology AAR). Chain-entry text drafted separately at `chain_entry_text_corpus_recompression_20260510.md` for the recursive-updates session to fold into a fresh timestamped spine.

## §0. Compression direction and conditioning inputs surfaced

Per the reflexivity discipline of the scoping doc, the pass states what it is compressing toward and the inputs that shaped its calls.

**Compressing toward:** A tighter, more navigable corpus base where (a) the canonical surface is recoverable from a single small set of files, (b) historical fossils are preserved in a defined-tier with one access path rather than scattered into the canonical reading order, (c) reading-order overhead in `README.md` is bounded, (d) mod-N and timestamped-spine accumulation has explicit retention discipline rather than open-ended retention.

**Compressing away from:** Lateral file proliferation that crowds the live canonical surface; mod-N pyramids retained without retention rule; timestamped spines accumulated under a structurally-false "byte-prefix" claim; verify-script accumulation without a consolidation horizon; reading-order metadata (especially the README "Last updated" parenthetical at 343 words single-sentence) that grew faster than the framework's reading-order itself.

**Conditioning inputs:** (1) Operational trigger of ~60% project knowledge capacity surfaced in `handoff_20260510_session_end_lightweight.md`. (2) The structural-recompression candidate concept from the lightweight handoff — this pass is its first reflexive worked example. (3) The four-tier scheme and four-axis falsifier methodology in the scoping doc. (4) Empirical inventory data (corpus stats §1, byte-level diffs §2.1) that ground the recommendations rather than letting them rest on intuition. (5) The framework's own diagnose-before-codify discipline — recommendations are bounded by what the inventory pressure-tests, not what the methodology suggests in principle.

## §1. Corpus inventory at pass open

84 files, 4.4 MB total. Breakdown by structural category (not yet by tier — that follows in §3):

| Category | Files | Bytes | % corpus |
|---|---|---|---|
| Spine series (`framework_decisions_record*`) | 7 (1 static + 6 timestamped) | 2.34 MB | 53% |
| Verify scripts (`verify_entry_17–29.py`) | 13 | 264 KB | 6% |
| Cohort series (`cohort_temporal_record*`) | 4 (orig + mod1–mod3) | 380 KB | 9% |
| Glossary series (`project_rigger_glossary*`) | 6 (orig + mod1–mod5) | 368 KB | 8% |
| Handoffs (mixed conventions) | 18 | 392 KB | 9% |
| Design docs (canonical) | 6 | 130 KB | 3% |
| Findings/typology/audit artifacts | 7 | 210 KB | 5% |
| Principles + reading entry points | 5 | 105 KB | 2% |
| Other lateral (templates, briefs, seeds, scoping) | 18 | 220 KB | 5% |

Two sibling-series categories (spine and mod-N reference docs) account for 70% of the corpus by bytes. The compression candidates concentrate there.

## §2. Anchored worked examples (a handful at depth)

Per scoping doc commitment, four worked examples at depth surface compression candidates concretely. The remainder are characterized compactly in §3.

### §2.1. Spine series — the byte-prefix property is structurally false

**Empirical test.** Entry 24's codification claimed: "older spine timestamps are byte-identical prefixes of newer ones since the chain is append-only by construction." Tested by `cmp -n <prior_size> prior.md current.md` for each consecutive pair of timestamped spine files. **Result: every comparison returned NOT-prefix.** Concrete instance: T120000Z (374,956 bytes) and T140000Z (399,276 bytes) diverge at character 353,054 (line 423). T140000Z's byte 353,054 is the start of `### Entry 29 — …`, while T120000Z's byte 353,054 is the start of `## Append protocol`.

**Mechanism.** Each new entry is inserted into the spine *before* the trailing "Append protocol" section, not appended at file end. This shifts all subsequent bytes by the entry's length. Append-only-by-content-hash (the chain integrity property) is preserved — entries chain on `prior_entry_hash`/`this_entry_hash` regardless of file position — but append-only-by-file-position (the Entry 24 claim) was never true.

**Implications.**
- The Entry 24 codification's "byte-identical prefix" justification for retaining all timestamped spines is structurally invalid. The justification was that older spines are recoverable from newer ones for free (since they're prefixes); under the actual file structure they are not.
- Every prior timestamped spine is a complete-but-orphaned full-chain record at its respective timestamp. Six of them (T010156Z, T021500Z, T033000Z, T100000Z, T120000Z, plus the static `framework_decisions_record.md`) total 1.94 MB of bytes that the canonical T140000Z fully supersedes content-wise (the Entry-N text is preserved in T140000Z; only the per-spine "Last updated" chrome differs).
- This is also a chain-audit-dimension move opportunity: Entry 24's codification needs an audit observation correcting the byte-prefix claim. Surfacing the correction is required by the framework's own recursive-edge-touching discipline.

**Recommendation (R1).** Move the six superseded spines (5 timestamped + 1 static) from the canonical project-knowledge surface to a `_archive/` subdirectory or analogous archive tier. Retain T140000Z as the sole canonical spine. Record the move in the chain audit dimension move (third canonical instance — see §4). Update Entry 24's codification text via audit observation rather than rewrite.

### §2.2. Mod-N pyramids on cohort and glossary — full retention without retention rule

**Empirical test.** Inventoried the cohort and glossary series:

| File | Size | Δ from prior |
|---|---|---|
| `cohort_temporal_record.md` (pre-mod-N) | 75 KB | (baseline) |
| `cohort_temporal_record_mod1.md` | 97 KB | +22 KB |
| `cohort_temporal_record_mod2.md` | 99 KB | +2 KB |
| `cohort_temporal_record_mod3.md` (canonical) | 107 KB | +8 KB |
| `project_rigger_glossary.md` (pre-mod-N) | 44 KB | (baseline) |
| `project_rigger_glossary_mod1.md` | 55 KB | +11 KB |
| `project_rigger_glossary_mod2.md` | 60 KB | +5 KB |
| `project_rigger_glossary_mod3.md` | 63 KB | +3 KB |
| `project_rigger_glossary_mod4.md` | 67 KB | +4 KB |
| `project_rigger_glossary_mod5.md` (canonical) | 75 KB | +8 KB |

**Mechanism.** Per Entry 24's codification: "All prior mod versions are retained in the file library as historical snapshots — append-only by construction, not rolling-deleted; practical comparison utility is typically against the most-recent ~5 versions but no version is discarded."

**Implications.**
- The cohort series at mod3 occupies 380 KB to preserve ~32 KB of unique content addition since the original.
- The glossary series at mod5 occupies 368 KB to preserve ~31 KB of unique content addition since the original.
- The "no version discarded" rule scales linearly with mod count and was codified before pressure-test of what cost would feel like at mod10 or mod20. At current cadence (one mod every ~1–3 entries on the glossary), reaching mod10 within 30 entries is plausible.
- Deferred questions 3 and 4 in the scoping doc surfaced this exact issue. The pass's empirical answer: the mod-N retention rule needs a horizon. Candidates: keep last N mods inline + archive earlier; periodic consolidation snapshots that supersede a run of mods; in-place updates with append-only change-log on the canonical file (sidesteps mod-N retention entirely but loses tapeworm-recursion bypass property).

**Recommendation (R2).** Retain the most-recent two mods inline (current canonical + immediate predecessor for diff utility). Archive earlier mods to `_archive/`. Codify the "last-N-inline + archive earlier" rule at glossary level as an addition to the existing `Mod-N versioning` entry. The "no version discarded" property is preserved (archived mods are still in the file library, just not in the canonical reading surface) while reading-overhead and storage growth become bounded.

### §2.3. README.md — reading-order metadata growing faster than the reading order

**Empirical test.** Counted words in the README's "Last updated" parenthetical (line 5): **343 words, single sentence.** Counted lines of the actual reading-order section (`## Reading order`): the section itself contains 18 numbered items. Counted words in the "Cross-session handshake protocol" intro paragraph (line 69): another ~600 words single-sentence parenthetical describing every entry's vacuous-application of the meta-discipline.

**Mechanism.** Each chain entry's "Last updated" refresh accumulates substance into the parenthetical describing what changed (rather than displacing the prior text). Each entry that doesn't add a new protocol component appends a "vacuous-application N times" clause to the cross-session handshake protocol intro paragraph. Both surfaces grew monotonically.

**Implications.**
- The README is the *entry point* — its function is to point readers efficiently to records, not to retell the framework's content. Its current state inverts that: the "Last updated" line carries entry-summary substance that more properly belongs in the chain entry itself or in a dedicated changelog.
- The cross-session handshake protocol intro paragraph carries the vacuous-application audit trail for the meta-discipline. That audit trail is genuinely useful but doesn't belong in an intro paragraph — it belongs in a separate "discipline application log" section, or in the chain entries that record each application.
- README maintenance has become a heavy-touch activity per chain entry, when its codified discipline (component #11 of the protocol: "Update this when the document landscape changes (new file added, file replaced, structure shifted), not when content within existing files changes") would predict light-touch.

**Recommendation (R3).** Restructure README to (a) move the "Last updated" parenthetical content to a separate `README_changelog.md` lateral artifact carrying the per-entry summaries; (b) move the cross-session handshake protocol intro paragraph's vacuous-application clauses to a separate "discipline application log" section at the bottom of the document or to a dedicated lateral artifact; (c) keep the README's main-body content focused on reading order, canonical-artifact pointers, and reading-discipline guidance. Target post-restructure README size: ≤ ~150 lines (currently 104 lines but disproportionately heavy in the parentheticals — the line count understates the content density).

### §2.4. Verify scripts — accumulation pattern with one mid-series refactoring already in evidence

**Empirical test.** Counted line counts of `verify_entry_17.py` through `verify_entry_29.py`:

```
17: 221    21: 459    25: 524    29: 231
18: 290    22: 479    26: 456
19: 378    23: 479    27: 534
20: 450    24: 512    28: 233
```

**Mechanism.** Scripts 17–27 grew steadily as later scripts inherited prior `EXPECTED_HASHES` and `PRIOR_HASHES` dicts plus prior `CONTENT_CHECKS` lists. Then 28 dropped sharply (534 → 233 lines) and 29 stayed small (231 lines). The drop suggests an implicit refactoring around Entry 28 to scope each verify script to its own entry's modifications only, rather than carrying forward the full inherited check set.

**Implications.**
- The post-27 refactoring is the right shape (each verify_entry_N.py covers Entry N's modifications, not Entry 1–N's). It happened ad-hoc without explicit codification — Entries 28 and 29 just produced smaller scripts. The discipline is currently undocumented.
- The pre-28 scripts (17–27) carry redundant content that is structurally superseded by the refactoring but not yet rationalized.
- Deferred question 2 in the scoping doc proposed a "consolidated verification mechanism" as an out-of-scope next pass. The actual situation is more nuanced: a partial consolidation already happened in practice; what's needed is (a) codification of the post-27 scope-discipline and (b) decision on whether to retroactively scope-down 17–27 or leave them as historical artifacts.

**Recommendation (R4).** Codify the per-entry verify-script scoping discipline explicitly (each script covers its own entry's modifications only, not inherited from prior). Leave scripts 17–27 as-is — they are historical artifacts and their per-entry scope is preserved within their CONTENT_CHECKS even if the dicts include redundant inheritance. Carve out a separate small future pass to evaluate whether the inherited dicts in 17–27 should be retroactively trimmed. Add a glossary entry naming the discipline: candidate name "Per-entry verify script scope".

## §3. Per-tier categorization (the rest characterized compactly)

### Tier A — Chain spine + verify scripts (integrity-bearing)

| File(s) | Status | Action |
|---|---|---|
| `framework_decisions_record_20260510T140000Z.md` | Live canonical | Keep |
| `framework_decisions_record.md`, `_T010156Z`, `_T021500Z`, `_T033000Z`, `_T100000Z`, `_T120000Z` (6 files, 1.94 MB) | Superseded historical fossils | Archive (R1) |
| `verify_entry_29.py` | Live canonical | Keep |
| `verify_entry_17.py`–`verify_entry_28.py` | Per-entry historical | Keep in canonical (each is the canonical verification for its entry; redundancy in dicts noted but not rationalized — see R4) |

### Tier B — Canonical reference docs (structural-recompression candidates)

| File(s) | Status | Action |
|---|---|---|
| `framework_principles.md` | Live canonical (pre-Entry-25 state — carried-forward principle revisions never landed) | Keep; flag as stale-relative-to-current-canonical-work |
| `core_principles_for_agent_behavior.md` | Live canonical (same staleness flag) | Keep; flag |
| `framework_design_three_lens_v2.md` | Live canonical | Keep |
| `project_rigger_glossary_mod5.md` | Live canonical | Keep |
| `project_rigger_glossary_mod[1-4].md`, `project_rigger_glossary.md` (5 files, 290 KB) | Mod-N pyramid below current | Archive mods 1–3; retain mod4 + mod5 inline per R2 |
| `cohort_temporal_record_mod3.md` | Live canonical | Keep |
| `cohort_temporal_record_mod[12].md`, `cohort_temporal_record.md` (3 files, 270 KB) | Mod-N pyramid below current | Archive orig + mod1; retain mod2 + mod3 inline per R2 |
| `README.md` | Live canonical (reading-order overhead) | Restructure per R3 |
| `nick_readme.md`, `nick_whats_changed_briefing.md` | Live canonical (stakeholder-facing) | Keep |
| Design docs (`aar_capture_design.md`, `coordinator_synthesis_design.md`, `explainer_agent_design.md`, `learning_library_design.md`, `reference_datasheet_design.md`, `character_sheet_template_design.md`) | Live canonical (referenced in README reading order) | Keep |
| Domain models (`data_model_adds_onboarding_and_mentorship.md`, `data_model_adds_cohort_findings.md`, `role_definitions_onboarding_and_mentorship.md`) | Live canonical | Keep |
| Typologies (`role_pathology_typology.md`, `trusted_talent_network_typology.md`) | Live canonical | Keep |

### Tier C — Lateral artifacts (highest-density compression target)

| File(s) | Status | Action |
|---|---|---|
| 18 handoffs (mixed conventions, 392 KB) | See deferred-question-5 resolution below | See R5 |
| `_readme_template.md`, `_whats_changed_template.md` | Templates, lightly referenced | Keep — small footprint, useful for new artifact creation |
| `architecture_pass_fractal_findings_20260508.md` | Live canonical (forward-pointing for principle revisions still pending) | Keep |
| `compression_restructure_findings_20260509.md` | Live canonical (same status) | Keep |
| `meta_aar_verification_discipline_arc_20260509.md` | Live canonical (template precedent for this pass's meta-AAR) | Keep |
| `records_keeping_audit_20260507.md`, `data_integrity_audit_20260508.md` | Provenance-only (audit findings have been integrated; audits themselves are historical) | Candidate-archive |
| `course_corrections_data_and_replication_20260507.md` | Provenance-only with orphan-track header (per README adjacent-documents block) | Candidate-archive |
| `single_loop_double_loop_pilot_instructions_20260509.md`, `single_loop_double_loop_translation_table_20260510T080000Z.md` | Live canonical (translation-table protocol active per Entry 29 codification adherence) | Keep |
| `city_attorney_consult_brief_records_act.md` | Live (pending stakeholder action on records-act exposure per recent handoffs) | Keep |
| `san_bruno_seed_export.md` | Provenance-only (initial seed; framework has long since superseded) | Candidate-archive |
| `Handoff_document_-_20260430.md`, `Handoff_document_-_20260430_evening.md`, `Handoff_document_-_20260505.md` | Pre-protocol-codification handoffs (legacy filename convention; substantial substantive content per `Handoff_document_-_20260430.md`) | Selective: keep `Handoff_document_-_20260430.md` (substantive seed), archive the other two |
| `handoff_20260507_evening.md` | Orphan-track per README adjacent-documents block | Keep (already flagged) |
| `character_sheet_template_design.md`, `course_corrections_data_and_replication_20260507.md` | Orphan-track per README adjacent-documents block | Already handled above |
| `FY27_Transmittal_Letter_DRAFT.docx` (per README) | Operational, not framework | Keep, out of scope for this pass |

### Tier D — Carry-forward / not-yet-canonical

| File | Status | Action |
|---|---|---|
| `handoff_20260510_session_end_lightweight.md` | First instance of lightweight cadence | Lift to Tier B canonical via codification of lightweight-cadence pattern (see §4) |
| `comparator_agency_p_scrape_experiment_scoping_20260510.md` (note `__1_` filename suffix is a transmission artifact) | Forward-pointer for external-facing experiment | Keep as Tier C lateral; rename to drop `__1_` suffix in recursive-updates session |
| `architecture_pass_corpus_scoping_20260510.md` | Scoping doc for this pass | Keep as Tier C lateral after this pass closes |
| **Outputs of this pass** (this findings doc, snapshot, meta-AAR, chain entry text) | Tier D until codified by chain entry | Becomes Tier C lateral once recursive-updates session lands the chain entry |

### Handoff retention discipline (deferred question 5 resolution)

**Recommendation (R5).** Three-tier handoff retention:
1. **Inline canonical:** the most-recent chain-entry-producing handoff (currently `handoff_20260510T140000Z.md`). One file at a time.
2. **Recent inline:** the previous N=5 chain-entry-producing handoffs. Provides recent-history navigability.
3. **Archive:** all earlier handoffs, including non-chain-entry handoffs (effort-only sessions, orphan-track) and pre-protocol legacy handoffs. Move to `_archive/`.

Rationale: chain-entry-producing handoffs are the durable cross-session continuity anchors. Effort-only and lightweight handoffs are valuable for arc reconstruction but don't bear cross-session continuity; they belong in archive. The N=5 inline window (~7 KB × 5 = ~35 KB) keeps the live surface small while preserving navigability.

## §4. Carry-forward concept codifications

The scoping doc commits to *at least* the structural-recompression glossary entry and proposes the broader codification options. The pass's calls:

**Codify in the chain entry (commit):**

1. **Structural recompression** — glossary entry. Definition: when incremental compression has accumulated beyond what the existing structure can hold without becoming a compression failure of its own, replace the structure rather than continue patching. First reflexive worked example is this pass. Sibling concept to existing per-record incremental compression machinery; operates at a slower cadence and a larger unit of replacement. Distinguished from rename-as-navigation (Entry 23) by scope: rename-as-navigation handles single-file transit failures; structural recompression handles cross-file structural-replacement candidates.

2. **Lightweight session-end handoff cadence** — extend the existing thin-handoff codification (Entry 15) with a tier addition. Two tiers under the same thin-handoff format: chain-entry-producing handoffs (full discipline including verify-script reference and hash manifest) and session-output handoffs (no chain entry, no verify run, lighter-weight). First instance: `handoff_20260510_session_end_lightweight.md`. Pressure-tested by this pass's own scoping handoff (the scoping doc itself functions as a session-output handoff at lightweight tier — second instance) and by this pass's eventual close handoff. The codification is glossary-level; the chain entry references it.

3. **Per-entry verify-script scope discipline** — glossary entry. Definition: each `verify_entry_N.py` covers Entry N's modifications only; prior-entry checks are the responsibility of prior-entry verify scripts and are not inherited. Discovered as already-applied discipline post-Entry-27. Codification regularizes the practice. (R4)

4. **Mod-N retention horizon** — extend the existing `Mod-N versioning` glossary entry. Default retention: the most-recent two mods inline; earlier mods archived. Preserves the "no version discarded" property at file-library level while bounding canonical-surface growth.

5. **Handoff retention discipline** — extend the existing `Cross-session handshake protocol` README section with the three-tier scheme. (R5)

6. **Chain audit dimension move third canonical instance** — three audit observations in this pass:
   - Entry 24's spine "byte-prefix" claim is structurally false (§2.1); audit observation supersedes the prefix-extension justification while preserving the timestamped-spine discipline itself.
   - Entry 24's mod-N "no version discarded" rule was codified without a retention horizon; the (R2) horizon-codification is the operational successor.
   - The transmission-drift instance in `handoff_20260510_session_end_lightweight.md` (chain head `…b30aaa` vs canonical `…b31d2f`) per the integrity-flag resolution at pass open is a small audit observation.

**Carve out for future work (do not commit in this pass):**

- The conversational-derived conceptual content (statistics analogy, evolution/markets analogy) flagged in the lightweight handoff. These are substantive enough to warrant their own scoped session rather than being absorbed into a pass focused on structural-recompression of the records-keeping corpus.
- Promotion of pass-shape labeling from glossary to handshake-protocol-component status (the still-pending Entry 30 candidate from prior planning). Scoped out of this pass per the scoping doc's explicit carve-out.
- The fractal-findings carved-out passes (Bayesian network, temporal/environmental drift, data-model-binary-bias). Scoped out per the scoping doc.
- Verify-script consolidation across entries 17–27 (separate from R4's discipline codification). Carved out as its own future small pass.

## §5. Chain audit observations

Recorded here per the chain audit dimension move's third canonical instance (Entry 25 first; Entry 29 second; this pass third):

**Audit observation #1.** Entry 24's codification of the timestamped-spine discipline included the claim: "older spine timestamps are byte-identical prefixes of newer ones since the chain is append-only by construction." This claim is structurally false at the file-byte level. Empirical test via `cmp` shows the first divergence is at the position where the new entry is inserted (before the trailing "Append protocol" section), not at the prior-entry-end position. Chain-hash integrity (which depends on entry content hashing, not file position) is preserved. The discipline itself remains operative and useful — the mistake is in the byte-prefix justification, not in the timestamped-spine value proposition. Recommended remedy: amend the codification text via audit observation in the recursive-updates session's chain entry; preserve the timestamped-spine discipline.

**Audit observation #2.** Entry 24's codification of mod-N versioning included the rule: "All prior mod versions are retained in the file library as historical snapshots — append-only by construction, not rolling-deleted." The rule was codified without a retention horizon, and pressure-test through five glossary mods + three cohort mods produced the linear-growth pattern documented in §2.2. The (R2) horizon-codification is the operational successor.

**Audit observation #3.** `handoff_20260510_session_end_lightweight.md` cited chain head `23f40190d15e10cf590b0bbe8b93ab9a6d51a4c2268ab3b626cbebc059b30aaa` (last 4 hex chars `b30aaa`); canonical chain head per `verify_entry_29.py` is `…b31d2f`. Difference is transcription drift in the lightweight handoff (no verify-script run was performed for that handoff, by lightweight-cadence design). No chain divergence. Surfaced per the scoping doc's required-first-turn integrity flag.

## §6. Recommendations summary (apply checklist for the recursive-updates session)

In dependency order:

| # | Action | Files affected | Effort | Notes |
|---|---|---|---|---|
| R1 | Create `_archive/` subdirectory; move 6 superseded spine files | `framework_decisions_record.md`, 5 timestamped predecessors of T140000Z | M | Updates R3's spine pointer in README |
| R2 | Move pre-mod3 cohort + pre-mod4 glossary versions to `_archive/`; codify retention horizon | 4 cohort + 5 glossary files | M | Codification at glossary level |
| R3 | Restructure README: move Last-Updated parenthetical → `README_changelog.md`; move handshake-protocol vacuous-application clauses → discipline-application-log section or lateral; preserve canonical-artifact pointers | `README.md`, new `README_changelog.md` | L | Touches the entry point — extra care; new file should mirror the chain-entry-summary-per-entry shape |
| R4 | Codify per-entry verify-script scope discipline at glossary level | New glossary entry | S | No file moves; codification only |
| R5 | Apply three-tier handoff retention; archive earlier handoffs | ~10 handoffs to archive | M | Keep most-recent 6 chain-entry handoffs inline + lightweight handoff |
| R6 | Codify structural-recompression glossary entry | New glossary entry | S | Companion: extend Mod-N versioning entry per R2; extend thin-handoff codification per lightweight-cadence sub-tier |
| R7 | Apply chain audit observations #1–#3 to a new chain entry | New timestamped spine | M | Incorporates all of R1–R6's codifications |
| R8 | Update `nick_readme.md` if README structural changes affect the stakeholder-facing entry point | `nick_readme.md` | S | Conditional on R3 outcome |

Total effort estimate for recursive-updates session: L–XL (roughly 20–30 effort units across multiple chain entries if applied as a series). May warrant splitting across two recursive-updates sessions per the per-thread session-limiter discipline.

## §7. What this pass deliberately did not do (carry-forwards confirmed)

Per the scoping doc's carve-outs, surfaced again here so the recursive-updates session inherits a clean carry-forward boundary:

- Did not modify any chain entry. Audit observations are the only chain-historical mechanism applied.
- Did not modify any verify script. R4 codifies the post-27 discipline but does not retroactively trim 17–27.
- Did not revise `framework_principles.md` or `core_principles_for_agent_behavior.md`. The carried-forward principle revisions remain in carry-forward; this pass surfaces their staleness as a Tier B flag but does not act on it.
- Did not pursue the still-pending downstream passes from the fractal findings (Bayesian network, temporal/environmental drift, data-model-binary-bias).
- Did not touch the Ronak seed bundle or the comparator scoping artifact's substantive content.
- Did not execute deletions, archive moves, or consolidated rewrites. All R1–R8 actions are recommendations for the recursive-updates session.
- Did not codify the conversational-derived conceptual content (statistics analogy, evolution/markets/framework spectrum). Carved out for separate scoped session.

## §8. Open questions for the recursive-updates session

1. **`_archive/` mechanics.** The framework's prior practice has been "orphaned historical fossils remain at canonical project knowledge under their original filenames" (per Entry 24's spine codification and the README's adjacent-documents block). This pass recommends establishing an archive tier; the recursive-updates session needs to decide whether `_archive/` is a literal subdirectory in `/mnt/project/`, a separate project knowledge surface, or another mechanism. Operational constraint: stakeholder needs to be able to retrieve archived files when needed without the archive tier polluting the canonical reading surface.

2. **README restructuring scope.** R3 may pull in adjacent restructures (e.g., the cross-session handshake protocol section's nine numbered components could each move to dedicated lateral docs with the README pointing to them). Recommend the recursive-updates session bounds R3 to the Last-Updated and vacuous-application clauses and carves out further structural moves.

3. **Recursive-updates session count.** R1–R8 is more than fits in a single session under the per-thread session-limiter discipline (15-unit effort cap; N=1 chain-entry handoff per thread). Recommend splitting into ≥2 sessions, with R1–R5 in the first (file moves + retention codifications) and R6–R8 in the second (structural-recompression codification + chain entry + downstream propagation).

4. **What gets carried forward into a future architecture pass on the corpus.** This pass is the first such pass. Its meta-AAR establishes whether the methodology worked. Future-trigger criteria (deferred from scoping) should be codified after the meta-AAR's evaluation, candidates: project knowledge above a refined threshold; structural-recompression candidate count above a named threshold; time-since-last-pass; stakeholder-surfaced friction.

## §9. Cross-references

- `architecture_pass_corpus_scoping_20260510.md` — the scoping doc this findings artifact responds to
- `corpus_snapshot_20260510.md` — companion compression-dividend artifact (current-state single-doc view)
- `meta_aar_corpus_recompression_20260510.md` — companion methodology AAR
- `chain_entry_text_corpus_recompression_20260510.md` — chain entry draft for the recursive-updates session to fold into a new timestamped spine
- `framework_decisions_record_20260510T140000Z.md` (Entry 29) — chain head at pass open
- `verify_entry_29.py` — verify script run at pass open (58/58 PASS)
- `architecture_pass_fractal_findings_20260508.md` — methodology precedent for findings-artifact shape
- `meta_aar_verification_discipline_arc_20260509.md` — template precedent for the meta-AAR
- `handoff_20260510_session_end_lightweight.md` — surfacing handoff for the carried-forward pass
- `handoff_20260510T140000Z.md` — most recent chain-entry handoff (chain head reference)

---

*Provenance: Findings artifact composed 2026-05-10 PT against chain head Entry 29. First reflexive instance of structural-recompression discipline applied to the framework's own records-keeping corpus. Treated as Tier D (carry-forward, not-yet-canonical) until the recursive-updates session's chain entry codifies what this pass surfaces.*
