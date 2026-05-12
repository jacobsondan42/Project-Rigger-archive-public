# Architecture Pass on Corpus — Forward-Pointer Scoping

**Status:** Forward-pointer document. Scopes the carried-forward architecture pass on the framework's own records-keeping corpus, surfaced in `handoff_20260510_session_end_lightweight.md` under the operational trigger of ~60% project knowledge capacity with observable complexity-creep markers (lateral file proliferation, mod-N versioning accumulation, redundant text across timestamped spine instances, growing reading-order overhead in `README.md`). Not yet a chain entry; the substantive pass produces that. This artifact is the carry-forward instrument until the pass runs.

**Provenance:** Produced in a dedicated scoping session 2026-05-10 PT per the three-step sequencing recommended in the lightweight session-end handoff (scoping → substantive pass → recursive updates). First instance of the dedicated-scoping-session shape applied to a framework-internal architecture pass — the comparator-agency scoping precedent (`comparator_agency_p_scrape_experiment_scoping_20260510.md`) was for an external-facing experiment; this is reflexive on the framework itself. Chain head at production time: Entry 29 (with the integrity flag noted below). Reader should treat this artifact as load-bearing-for-trajectory but pre-substantive-pass; the pass itself is empowered to refine the framing it inherits, per the diagnose-before-codify discipline.

## Scope

Apply structural-recompression discipline to the framework's records-keeping corpus. The pass identifies what is structural vs. historical, surfaces compression opportunities at the structural-replacement cadence rather than the per-record incremental cadence, and produces recommendations the recursive-updates session will apply.

The pass is itself the first reflexive instance of the structural-recompression candidate concept surfaced in the lightweight handoff — it operationalizes the concept by being the concept's first worked example. This reflexivity is a feature, not an ambiguity: the pass should expect to refine the structural-recompression articulation as it surfaces what does and does not work.

## Corpus tiering (the four-tier scheme the pass operates against)

The pass treats the corpus in four tiers, each with different handling discipline:

**Tier A — Chain spine + verify scripts.** Integrity-bearing. Includes `framework_decisions_record.md` and its mod-N / timestamped successors, all `verify_entry_N.py` scripts, the chain head hash itself. Discipline: touch carefully; chain entries are append-only by hash construction and cannot be rewritten without breaking the chain. The pass may *recommend* spine-side actions (annotation, audit-dimension move per Entry 25 / Entry 29 precedent, future-spine timestamp consolidation) but does not modify spine entries directly.

**Tier B — Canonical reference docs.** Live load-bearing surfaces referenced by current operational work. Includes `framework_principles.md`, `core_principles_for_agent_behavior.md`, `project_rigger_glossary_mod5.md`, `README.md`, `nick_readme.md`, `cohort_temporal_record_mod3.md`, the design docs (`aar_capture_design.md`, `coordinator_synthesis_design.md`, `explainer_agent_design.md`, `learning_library_design.md`, `reference_datasheet_design.md`, `character_sheet_template_design.md`), `framework_design_three_lens_v2.md`, `framework_principles.md`. Discipline: structural-recompression candidate; consolidations and restructures are in-scope for recommendation. Replacement of mod-N versions with consolidated successors is in-scope.

**Tier C — Lateral artifacts.** Handoffs, mod-N predecessors superseded by current canonical, design docs that may have been absorbed elsewhere, AAR artifacts, audit artifacts, typology artifacts, conceptual scoping artifacts. Discipline: the highest-density compression target. Each artifact gets categorized: live-load-bearing (keep), provenance-only (candidate-archive), superseded (candidate-deletion-after-snapshot), referenced-by-canonical (preserve link, possibly slim content), orphaned (candidate-archive-or-delete).

**Tier D — Carry-forward / not-yet-canonical.** Includes the comparator scoping artifact, the lightweight session-end handoff itself, the conversation-derived conceptual content not yet in canonical form (statistics analogy, evolution/markets analogy from the lightweight handoff). Discipline: the pass should decide for each whether it lands in Tier B as canonical, becomes a Tier C lateral artifact, or remains carry-forward. Out-of-scope: the Ronak seed bundle (different project entirely).

## Methodology framework (falsifier-style axes for structural-vs-historical categorization)

Each artifact in scope is tested against four axes. An artifact's profile across the axes determines its handling category. The axes are separable: an artifact may be load-bearing-now but orphaned-by-current-canonical, or referenced-but-superseded, etc. The combinations matter; the typology of profiles is itself a candidate finding.

1. **Load-bearing-now vs. provenance-only.** Does any current operational surface (canonical reference docs, current chain head, agent reading list, Nick / Ronak briefings) actively depend on this artifact's content, or does it exist solely as historical record of a moment that has since been superseded? Provenance-only artifacts are not without value (they preserve the framework's audit-of-itself capacity), but they belong in a different tier of access than load-bearing artifacts.

2. **Referenced-by-current-canonical vs. orphaned.** Is the artifact named in current canonical files (README, glossary, principles, current-chain-entry handoffs, latest mod-N versions of cohort_temporal_record / glossary / framework_decisions_record), or has it become a graph orphan? Orphaned artifacts may still be valuable but signal compression opportunity by their orphan status.

3. **Superseded vs. live.** Has a later artifact replaced this one's function (mod-N successor, consolidated rewrite, structural-replacement)? Live artifacts get preserved as canonical; superseded artifacts become candidates for archive-after-snapshot or deletion-with-history-preserved-in-spine.

4. **Per-record incremental vs. structural-replacement candidate.** Is the artifact's complexity well-handled by per-record patches (the discipline so far), or has it crossed the threshold where the structure itself needs replacement? This axis is the structural-recompression test directly: artifacts that fail it are the pass's primary compression targets.

The pass should expect *passes-some-axes-fails-others* profiles to be common, not exceptional. The combinations are themselves the diagnostic content.

## Deliverable shape commitments

The substantive pass commits to producing:

- **Findings artifact** at `/mnt/user-data/outputs/architecture_pass_corpus_findings_<date>.md`, structured analogously to `architecture_pass_fractal_findings_20260508.md`. Includes methodology, anchored worked examples (a handful at depth, the rest characterized compactly), per-tier categorizations, structural-recompression candidates with rationale, downstream passes carved out, open questions for follow-up.

- **Chain entry** in `framework_decisions_record_<UTC-timestamp>.md` (per the timestamped filename convention codified in Entry 29's glossary entry) capturing the architectural decisions the findings imply. Includes hash manifest discipline per Entry 29 codification.

- **"Current state" snapshot artifact** at `/mnt/user-data/outputs/corpus_snapshot_<date>.md`, providing a single-document view of what is canonical, what is superseded, what is in carry-forward, and where each lives. The snapshot is the pass's compression dividend — a tighter base for subsequent sessions to navigate.

- **Recommendations**, not executions, for lateral-file rationalization. The pass produces the categorization and the proposed actions; the recursive-updates session executes (deletions, archive moves, consolidated rewrites). This separation preserves the diagnose-before-codify discipline and prevents the pass from spending its capacity on application work rather than diagnostic work.

- **Meta-AAR** at `/mnt/user-data/outputs/meta_aar_corpus_recompression_<date>.md` per the `meta_aar_verification_discipline_arc_20260509.md` template. Records the pass's own arc, surfaces strain points, evaluates whether the methodology worked. Composed at the close of the substantive pass session, before the recursive-updates session begins.

## What the pass deliberately does not do

Carving these out at scoping time prevents scope creep from absorbing the pass's capacity:

- **Does not rewrite chain entries.** The chain is append-only by hash construction. Audit-dimension moves (per Entry 25 / Entry 29 precedent) are the available mechanism for surfacing chain-historical inconsistencies; full rewrites are not.

- **Does not modify verify scripts beyond annotation.** Each `verify_entry_N.py` is the canonical verification for its entry and is itself integrity-bearing. The pass may recommend a future verification consolidation (an open question — see deferred items below) but does not modify scripts in the pass session.

- **Does not revise principles documents** (`framework_principles.md`, `core_principles_for_agent_behavior.md`) **except where they are entangled with records-keeping discipline.** Principle revisions are separate work and should be carved out as their own pass if surfaced as needed.

- **Does not execute deletions, archive moves, or consolidated rewrites.** Those land in the recursive-updates session. The pass produces categorizations and recommendations; the recursive-updates session executes against them.

- **Does not pursue the still-pending downstream passes from the fractal findings:** Bayesian network of compression-conditioning inputs; temporal/environmental drift; data-model-binary-bias. Those remain carved out per `architecture_pass_fractal_findings_20260508.md` and are not absorbed into this pass.

- **Does not touch the Ronak seed bundle or the comparator scoping artifact's substantive content.** The Ronak bundle is for a different project. The comparator scoping is in-scope for tier-categorization (Tier D currently, may move to Tier B as canonical) but its substantive falsifier framework and deferred questions are not revised by this pass.

## Carry-forward concepts to integrate

Three concepts surfaced in `handoff_20260510_session_end_lightweight.md` are candidates for codification as part of this pass, since the pass is itself the worked example of each:

- **Structural-recompression as candidate framework concept.** The pass is the first reflexive instance. Codification candidates: glossary entry; sub-pattern under compression mechanism children (alongside practice-as-compiler, selection-as-compiler); operating constraint covering when-to-patch vs. when-to-replace. The pass should commit to at least the glossary entry and propose the broader codification options for the chain entry to resolve.

- **Lightweight session-end handoff cadence as discipline pattern.** The lightweight handoff itself is the first instance. The pass produces additional instances of *its own* handoffs (scoping-session close, substantive-pass close, recursive-updates close), which together pressure-test whether the cadence pattern recurs naturally or requires explicit codification. Codification candidates: glossary entry; chain entry articulating handoff-cadence-tier discipline; absorbed into existing thin-handoff codification (Entry 15) as a tier-extension.

- **Conversation-derived conceptual content.** The statistics-analogy mapping (shape-from-inside, samples-with-known-bias, recursive edge-touching, system-level fractal as self-referential statistical exercise) and the evolution/markets/framework spectrum mapping (selection processes ordered by feedback speed and introspective capacity; framework as deliberate-closed-loop fully-explicit standing-aware position). Codification candidates: glossary entries for the named operations; cross-reference notes in `architecture_pass_fractal_findings_20260508.md` connecting the system-level fractal meta-finding to the broader selection-process family; explicit articulation of agent-as-interpret-layer's position on the spectrum. The pass should fold these in where compression-recommendation work surfaces them naturally; full codification of all three may not fit in the pass's capacity and the residue carves out as deferred.

## Reflexivity discipline

The pass operationalizes constitutional principle #1 (compression should be directional and surfaced) reflexively on the framework's own corpus. The reflexivity warrants explicit treatment:

- **The pass states its compression direction and conditioning inputs surfaced.** What is the pass compressing toward (a tighter, more navigable corpus base) and away from (lateral file proliferation, mod-N accumulation, timestamped-spine redundancy)? What conditioning inputs shaped its decisions (operational trigger of ~60% capacity, the structural-recompression concept, the four-tier scheme, the four-axis methodology)? These are recorded in the findings artifact's preamble.

- **The meta-AAR captures methodology strain.** The pass's own methodology may strain at points (the four-axis framework may need refinement mid-pass; tier boundaries may turn out to be fuzzier than scoped; some artifacts may resist categorization). The meta-AAR records strain explicitly, per the verification-discipline-arc precedent.

- **The pass treats its own outputs as Tier D until codification.** The findings, snapshot, and recursive-updates recommendations are themselves carry-forward / not-yet-canonical until the chain entry codifies them. This prevents the pass from claiming canonical status for its own work prematurely — the diagnose-before-codify discipline applied to the diagnostic work itself.

## Future-trigger codification target

The pass should produce explicit criteria for when to re-run a corpus architecture pass. Candidate triggers:

- Project knowledge capacity above a named threshold (current trigger was ~60%; the codified threshold may be the same or refined).
- Observable complexity-creep markers above a named count (current observation: lateral file proliferation, mod-N accumulation, timestamped-spine redundancy, README reading-order overhead).
- Time-since-last-pass above a named horizon (no precedent yet — this is the first such pass on the corpus).
- Stakeholder-surfaced friction (an inability to navigate the corpus efficiently in operational work).

The codified criteria become a glossary entry or operating-constraint addition, allowing future sessions to recognize the pass as recurring discipline rather than one-off cleanup.

## Open integrity flag (must surface in the pass's first turn)

The chain head hash differs between the two most recent handoffs:

- `handoff_20260510T140000Z.md` cites: `23f40190d15e10cf590b0bbe8b93ab9a6d51a4c2268ab3b626cbebc059b31d2f`
- `handoff_20260510_session_end_lightweight.md` cites: `23f40190d15e10cf590b0bbe8b93ab9a6d51a4c2268ab3b626cbebc059b30aaa`

Same first 60 hex chars; differ in the last 4. The T140000Z handoff is the chain-entry-producing handoff with full verify discipline (verify_entry_29.py 58/58 PASS reported); the lightweight handoff was produced without verify-script run. Most likely a transcription drift in the lightweight handoff. The pass's first turn should run `verify_entry_29.py /mnt/project/` to ground-truth the chain head, then record the resolution as an audit-dimension observation per Entry 25 / Entry 29 precedent. This is not blocking for the pass; it is exactly the kind of cross-handoff consistency surface the pass should care about and surface explicitly.

## Deferred questions (must resolve in the pass itself, deliberately not in scoping)

1. **What's the right tier-boundary discipline when an artifact spans tiers?** Several candidates: design docs that have been substantively absorbed into `core_principles_for_agent_behavior.md` (Tier B canonical) but still exist as separate files (Tier C lateral). The categorization rule may need refinement during the pass.

2. **Verification-script consolidation.** Twenty-nine `verify_entry_N.py` scripts accumulate substantial redundancy (PRIOR_HASHES and EXPECTED_HASHES dicts mostly contain prior-entry expected hashes that haven't changed). A consolidated verification mechanism is a compression candidate but is integrity-bearing and out-of-scope for this pass to execute. The pass should decide whether to *recommend* the consolidation (and what shape) or carve it out as its own subsequent pass.

3. **Cohort temporal record mod-N pattern.** Currently at mod3. Subsequent mods will accumulate. The pass should decide whether mod-N versioning is the right discipline for a frequently-updated artifact, or whether a different update mechanism (in-place updates with append-only change-log; periodic consolidation snapshots; spine-style timestamping) compresses better.

4. **Project_rigger_glossary mod-N pattern.** Same shape as above, currently at mod5. Same question.

5. **Handoff retention discipline.** Currently every handoff is retained. As session frequency continues, the handoff layer will dominate the corpus. Candidates: archive handoffs older than N entries; consolidate runs of handoffs into per-arc summaries; preserve only chain-entry-producing handoffs in canonical project knowledge with thin handoffs archived. The pass should produce a recommendation; the recursive-updates session executes.

6. **Conceptual content not-yet-codified.** Statistics analogy, evolution/markets analogy, structural-recompression itself, lightweight cadence — how much of this gets codified in the pass's chain entry vs. carved out as forward work? Capacity discipline: the pass should commit to a maximum number of codifications and defer the rest.

7. **Reflexive-pass cadence vs. exhaustive single-pass.** The pass may surface more compression candidates than fit in a single substantive pass session. Decision rule: bound the pass to N codifications and carve out the residue, or extend the pass over multiple sessions in a single chain. Lean: the former, since the structural-recompression concept itself argues against single-pass exhaustiveness.

## What this document is not

- Not a methodology specification at the resolution the substantive pass requires. The four-axis falsifier framework is a starting point; the pass will refine it.
- Not a chain entry. Codification follows pressure-testing per the framework's diagnose-before-codify discipline.
- Not authorization to execute deletions, archive moves, or consolidated rewrites. Those land in the recursive-updates session, after the pass produces categorizations and recommendations.
- Not a commitment to all carry-forward concept codifications. The pass commits to *at least* the structural-recompression glossary entry; the rest is capacity-permitting.
- Not a replacement for the lightweight session-end handoff that surfaced the pass. Both artifacts are carry-forward instruments at different cadences.

## Cross-references

- `handoff_20260510_session_end_lightweight.md` — surfacing handoff; the operational trigger and recommended sequencing originate here
- `handoff_20260510T140000Z.md` — most recent chain-entry-producing handoff; chain head reference for the integrity flag
- `comparator_agency_p_scrape_experiment_scoping_20260510.md` — format precedent for forward-pointer scoping artifact
- `architecture_pass_fractal_findings_20260508.md` — methodology precedent for what the substantive pass's findings artifact looks like; also the source of carved-out downstream passes still pending
- `handoff_20260508.md` — setup-handoff precedent (the pass's setup-handoff at scoping-session close will follow this shape)
- `meta_aar_verification_discipline_arc_20260509.md` — meta-AAR template precedent the pass commits to following
- `framework_decisions_record_20260510T140000Z.md` — chain spine; Entry 29 codifications (timestamped filename convention, handoff hash manifest, co-equal session limiters with per-thread reset) are operative for the pass
- `project_rigger_glossary_mod5.md` — current canonical glossary; structural-recompression candidate codification lands as new entry here (mod6) if the pass commits
- `core_principles_for_agent_behavior.md` — constitutional principle #1 (compression directional and surfaced) is what the pass operationalizes reflexively
- `framework_principles.md` — broader principles surface; pass touches only at entanglement points
- `README.md` — reading-order overhead is one of the complexity-creep markers; pass produces a reading-order recommendation
- `cohort_temporal_record_mod3.md` — mod-N pattern subject of deferred question 3
- `framework_decisions_record.md` — chain entry codifying this pass is forward work; this artifact is the carry-forward instrument until then

---

*Provenance: Scoping artifact written 2026-05-10 PT against chain head Entry 29 (per the integrity flag, the canonical hash is the T140000Z citation; the scoping session itself does not advance the chain). First instance of dedicated-scoping-session shape applied to a framework-internal architecture pass. Companion to `handoff_20260510_session_end_lightweight.md` as the carry-forward instruments shaping the next substantive session.*
