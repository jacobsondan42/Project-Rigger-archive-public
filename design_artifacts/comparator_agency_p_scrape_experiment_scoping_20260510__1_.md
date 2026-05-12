# Comparator-Agency P-Scrape Experiment — Forward-Pointer Scoping

**Status:** Forward-pointer document. Scopes a deliberately-bounded P-lens-only experiment to test whether structural patterns surfaced in the SB seven-director cohort work generalize across comparator agencies, or are SB-specific. Not yet codified in `framework_decisions_record.md`; this artifact is the carry-forward instrument until codification.

**Provenance:** Conversational emergence (not scoped pass). Surfaced 2026-05-10 in conversation about scaling validation beyond case-driven thought experiments. Captured at the moment the decision to preserve this experiment was made, per the framework's records-keeping discipline ("must survive this conversation"). Reader should treat this artifact as load-bearing-for-trajectory but pre-validation; the deferred questions section flags what must be resolved before operational application.

## Scope

Apply the SB seven-director cohort profiling process to a deliberately-bounded set of comparator agencies, using only P-lens (public mosaic) data sources. Test whether the structural patterns surfaced in the SB cohort — vacancy-cascade, perennial-bridesmaid, sacrificial-chair, shadow-influence-decoupling, concentrated-cohort-rejection event — replicate across agencies, or are SB-specific.

## Comparator agencies (v1 candidate set)

From the v1 architecture comparator set per `Handoff_document_-_20260430.md`:
- South San Francisco
- Hayward
- Menlo Park
- SamTrans

Minimum to test replication: 2 agencies. Ideal for cross-agency variance: 4. Selection criteria for narrowing if needed: structural similarity to SB substrate (council-manager form, comparable size, similar director-tier layering); avoid pre-selecting for known patterns.

## Data sources (P-lens nodes; maps to NodeMosaicEntry)

- **Transparent California** — payroll history per-position; high-confidence on prior-FY role+pay; lags ~12 months
- **CalOpps** — job postings, recruitment patterns, posted-then-pulled signals
- **LinkedIn** — self-curated current role, transition narratives; aspirational-framing bias
- **ZoomInfo / RocketReach** — B2B database lag patterns (useful for staleness diagnostic)
- **Council/board agenda packets** — staff-report attribution at scale (high-leverage node; closest available proxy for portfolio/standing-functions data without O-lens access)
- **Local news coverage** — dated transitions, settlement records, departure framings
- **Agency websites and directories** — current org chart, position listings
- **ICMA membership directories** — professional credentialing

## Schema mapping

Maps cleanly to existing entities specified in `data_model_adds_cohort_findings.md` and `cohort_temporal_record.md`:

- `NodeMosaicEntry` — one entry per (subject, claim, node) tuple with raw value, normalized value, retrieval date, confidence-per-node
- `DisagreementPatternView` — derived view per (subject, claim type) when multiple node entries exist
- `cohort_temporal_record.md` Events Log — dated transitions by subject
- `cohort_temporal_record.md` People Index — operational profile summary per profiled subject
- `cohort_temporal_record.md` Findings Log — structural patterns surfaced from the comparator work
- `cohort_temporal_record.md` Source Bias Registry — disclosed contributor-toward-subject dispositions (sparse for P-lens-only work; entries note where SB-derived priors might bias the comparator read)

Principal ETL challenges: identity resolution across nodes (name variations, transition-timing inconsistency); date normalization given lag between event and any node updating. Both have provenance-field surfaces in the schema.

## Falsifier framework

The experiment's value comes from disconfirmation as much as confirmation. Pre-register predictions before scraping any comparator agency:
- For each SB-surfaced pattern, predict either replication or SB-specificity, with structural reasoning.
- Replication = pattern instance found in ≥1 comparator agency with similar structural features.
- SB-specific = pattern absent across all comparator agencies despite structural similarity in the substrate.
- Patterns surfacing in comparators but not predicted by SB findings are net-new architectural surfaces and warrant their own carve-out per the framework's discipline of carving-out-as-discipline.

## Deferred questions (must resolve before operational application)

1. **Agent-as-interpret-layer drift across agencies.** The framework was developed with SB as the primary instance; applying it to comparator agencies introduces a Goodhart risk if the framework's categories were shaped by SB-specific structure. Meta-AAR cadence at experiment milestones (per the `meta_aar_verification_discipline_arc_20260509.md` template) is the standing remedy. Apply at minimum once per comparator agency completion.

2. **Scrape ethics and disclosure framing.** P-lens data is public, but compiling it into a profile crosses a different threshold than any single source. The SB cohort work has carried this implicitly because the framework's author is at SB; comparator-agency subjects have no such relationship to the framework. The disclosure framing warrants explicit thought before any operational application of comparator-agency findings beyond the experiment itself.

3. **Operational vs research framing firewall.** The comparator-agency profiles produced by this experiment should be flagged as research-only and not flow into any operational reference-datasheet rendering or cross-org connection mapping until the disclosure question is resolved. Schema-level firewall (analogous to `layer_assignment` for utility-function data) is the candidate enforcement mechanism; alternative is operational discipline with audit.

4. **Methodology specification.** Sequencing, sampling, ETL design, identity-resolution rules, confidence-calibration-by-node-and-claim-type — all forward work. This document is scoping, not specification.

## What this document is not

- Not a methodology specification.
- Not a chain entry — codification follows pressure-testing per the framework's diagnose-before-codify discipline.
- Not authorization to begin scraping — deferred questions warrant resolution first.
- Not a commitment to all four comparator agencies — minimum is 2.

## Cross-references

- `cohort_temporal_record.md` — operational records the experiment would extend
- `data_model_adds_cohort_findings.md` — `NodeMosaicEntry` and `DisagreementPatternView` schema definitions
- `framework_design_three_lens_v2.md` — three-lens model and lens-coupling patterns the experiment tests
- `meta_aar_verification_discipline_arc_20260509.md` — meta-AAR template for experiment-milestone reflection
- `architecture_pass_fractal_findings_20260508.md` — falsifier-framework methodology precedent
- `Handoff_document_-_20260430.md` — v1 comparator agency set origin
- `framework_decisions_record.md` — chain entry codifying this experiment is forward work; this artifact is the carry-forward instrument until then
