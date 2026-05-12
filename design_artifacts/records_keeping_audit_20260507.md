# Records-Keeping Audit — Project Rigger Documentation

**Date:** 2026-05-07
**Status:** Draft for review. Working artifact applying the framework's own records-keeping discipline to the project's own documentation.
**Origin:** End-of-day session 2026-05-07. After completing the glossary v2 update, Dan asked for an audit of where information explicit in conversations and implicit in design documents is not properly stored per the framework's design principles.

---

## What this audit is

The framework's principle is that records-keeping is the load-bearing value: capture rather than recommend, surface rather than smooth, mark provenance, treat outputs as visibly provisional. The audit applies that discipline reflexively to the project's own corpus, identifying where the discipline has not been applied to itself.

The audit is not exhaustive. It catches the gaps a structured pass through the corpus surfaces; a more thorough pass would surface more. The level of granularity is "things significant enough to be worth fixing" rather than "every minor inconsistency."

## Method

I read the README, both principles documents, the v2 framework design, the cohort findings data model, the cohort temporal record, the four handoffs, and skimmed the remaining design documents. I looked for four kinds of gaps: (1) information present in conversation or handoff prose but missing from the operational records the framework calls for; (2) concepts referenced or worked-example'd somewhere but not formally captured anywhere; (3) documents promised in next-work lists or referenced as cross-refs but never created; (4) discipline applied inconsistently across the corpus.

---

## The structural observation

Before listing specific gaps, the structural observation that organizes them: the cohort temporal record was instantiated mid-thread on 2026-05-07 as the framework's records-keeping discipline applied to the cohort profile work. That date is the inflection point. Everything done before 2026-05-07 — three handoffs of substantial design work, the 2026-05-06 thread that built Dan's character sheet, position portfolio, and Alex's profile, and the 2026-05-05 thread that scoped the bidirectional JD instrument — lives in handoff prose rather than in the operational records the framework specifies. The pre-2026-05-07 corpus is approximately 70% of the project's content but contributes approximately 20% of the operational records.

A second-order observation falls out. The project has design documents for surfaces that do not yet exist (coordinator synthesis, reference datasheet, explainer agent) but lacks design documents for things that should exist as project artifacts — the bidirectional JD instrument, the rotation entity, performance-management surface, day-one self-exercise interface, CM dashboard flag-something-wrong portion. The build hierarchy is upside-down relative to the dependency order in the handoffs' next-work lists.

A third-order observation, which Dan flagged separately: the project's own author is the most-documented person in the corpus and the one whose documentation least follows the framework's structure. Dan's standing functions table, kingdom composition with shadow-role flag, provenance timeline, working genius profile, demonstrated competencies, and cross-departmental relationship map all live in `handoff_20260506.md` prose rather than in any structured Dan profile artifact, People Index entry, or standing-functions inventory. The spiritual-director case applies to the project itself.

---

## Gap category A — Information explicit in handoffs but missing from operational records

The cohort temporal record's People Index, Events Log, and Open Questions Index are the operational records artifact. Several entries are missing or thin compared to what's documented elsewhere.

**A1. Dan's profile.** `handoff_20260506.md` contains a full Dan record: standing functions table with kingdom-composition tags and substrate, kingdom composition with shadow-role flag, provenance timeline 2009–present, demonstrated competencies, working genius (utility-function layer), organizational context preferences, formative patterns, cross-departmental relationship map. None of this exists in the People Index. Dan also has no entry in the Source Bias Registry (his bias toward himself is structurally an interesting case the framework should accommodate, not skip).

**A2. Alex's profile.** `handoff_20260506.md` contains career arc 1997–present, three indicative documents, key management philosophy, the Menlo Park network analysis, public-record synthesis. The People Index Alex entry (lines 126–133 of cohort_temporal_record.md) is much thinner. Same for the Open Questions Index — it covers seven directors but not Alex; the 10 open questions on Alex from `handoff_20260506.md` line 191 onward are not migrated.

**A3. People referenced in events but missing from People Index.** Pamela Antil (the canonical worked example for the public-perspective-vs-payroll-record gap; appears in events log, network classifications, framework finding #9; no profile entry); Mike Kennedy (perennial-bridesmaid source case, finding #6; no profile entry); Susan Manheimer (interim-presence source case, finding #16; events references; no profile entry); Ryan Johansen (sacrificial-chair predecessor, finding #5; events references; no profile entry); Bobby Magee (predecessor to Pegueros at SB; lawsuit context; no profile); Ari Delay (Mike Ku's predecessor; events references; no profile); Jovan Grogan (Gilli's actual hiring CM, the correction Dan logged; pivotal for understanding the trusted-network classification; no profile).

**A4. Adjacent SB people named in 5/6 org reference but missing.** Esther Garibay (Finance Manager), Bill Mitchell (Interim IT Manager). Both flagged as next-strata-down candidates but not started.

**A5. People referenced as case-specific gaps but missing.** Darcy Smith (former ACM, vacancy-residue source case); Kelly Beggs (Gilli's hire, trusted-colleague pattern); Audrey (Karlen's admin backfill gap); Damian Sandholm (Karlen's deputy backfill gap). All thin by necessity but should have at least placeholder entries to enable forward referencing.

**A6. Source Bias Registry gaps.** Dan's source bias toward Alex is implicit but not declared in the registry. Dan's source bias toward himself is not declared (the framework's bidirectional principle says it should be capturable). Disposition of `vregventura.org` toward Alex is logged but disposition of other public-record sources toward subjects (e.g., Santa Maria farewell coverage for Gilli — moderately positive) isn't formalized.

**A7. Events Log gaps.** Several events referenced in narrative profiles aren't in the chronological log. Examples: Dan's hire at Saratoga by Pegueros in 2023 (mentioned in connection map but not in events log); the 2018 Pegueros promotion to ACM at Menlo Park appears in events but Pegueros's transition Saratoga→SB in 2023 is mentioned in narrative but doesn't have a clean event entry; Dan's consulting period start (December 2023) and Strategic Advisor start (July 2025) are in handoff but not in events log.

---

## Gap category B — Concepts referenced but not formally captured

These are structural patterns or design decisions present in conversation/prose but not promoted to first-class framework status.

**B1. Trusted-talent-network classification.** The cross-org connection map at the end of `cohort_temporal_record.md` ends with a classification scheme (Alex prior-city network, Alex trust-organization-via-vouch network, Pre-Alex SB hires, External non-network, Internal promotion, TBD). This is a worked selection-criterion typology that the framework should formalize — it's load-bearing for understanding why each director is in their seat, and it surfaces in framework_design v2 implicitly without being named.

**B2. Role-as-actually-performed pathologies typology.** Findings #5 (sacrificial-chair) and #6 (perennial-bridesmaid) propose placement in a "framework typology of role-as-actually-performed pathologies." The typology document doesn't exist. It would consolidate spiritual-director case (already in glossary), shadow-role drift (mentioned in finding #5 but not formalized), vacancy-residue (finding #3), sacrificial-chair, perennial-bridesmaid, and weakness-overlap (finding #7) into one taxonomy showing how they relate, when each applies, and what intervention each calls for.

**B3. Defined-contribution-with-vesting principle.** Finding #11 proposes placement in "principles document; data model." The data model side exists (`PortfolioFringeBenefitRecord`). The principles side does not — `framework_principles.md` has 18 principles but no entry for portfolio-as-fringe-benefit as a foundational principle. Given how often the framing is referenced (engagement projection for Pegueros, mobile-fixer reading, etc.), this is load-bearing and should be a named principle.

**B4. Personalized utility projection as recurring view.** Finding #13 proposes placement in "data model — view definition; surfaces in coordinator synthesis." Status: "Logged." Not yet specified in either document.

**B5. Dan's standing functions table.** The instantiated example of standing functions with kingdom composition tags and substrate flags lives in `handoff_20260506.md`. No formal Dan-position-portfolio artifact exists in project knowledge as a file. This matters because it's the reference example for what a real standing functions inventory looks like under the v1 schema.

**B6. The "two corrections" (survivorship bias, bidirectionality).** Stated as design implications of principle #2 in `core_principles_for_agent_behavior.md`. They appear in `framework_principles.md` only implicitly (bidirectionality is mentioned in passing in the executive sponsor section; survivorship bias not mentioned at all). Should be cross-referenced explicitly.

**B7. Comparator-agencies structural findings.** `Handoff_document_-_20260430.md` references five comparator agencies (San Bruno, South San Francisco, Hayward, Menlo Park, SamTrans) with structural findings (parallel-track classifications at SSF and Hayward, bifurcated structures at SamTrans, undifferentiated structures at SB and Menlo Park, the AFSCME-to-Unrepresented boundary at Hayward as a progression-graph employment-relationship change). Architecturally load-bearing but lives only in that handoff.

**B8. Goodhart-on-recognition design decisions.** `Handoff_document_-_20260430.md` end-of-day section commits to "no library highlight feature, no algorithmic curation, no ranking" as design decisions for the learning library. These constraints aren't carried forward into `learning_library_design.md` — the constraint is defined in the handoff but not in the design document it constrains.

**B9. Three audience-specific framings (Council, employees, community).** `Handoff_document_-_20260430_evening.md` has a substantive section on rollout storytelling: capacity-from-development for Council, the substantive answer to employees' question about whether the org values them, continuity of service quality for community, plus the principle-level constraint that the framework should not be presented as the response to the freeze. Substantial design work; lives only in that handoff.

**B10. Bidirectional JD instrument scope.** Fully specified in `Handoff_document_-_20260505.md` (decompose / recompose / triangulate; 70/30 architecture; 3-5 year window; Special Projects Manager test case; admin-tech JDs as second test case). The handoff explicitly says "needs its own design document before build." Document never created.

**B11. Mini development rotation design gap.** `handoff_20260506.md` identifies six open questions about a rotation participant entity (admin tech / cashier / EA / analyst I across kingdoms). The questions are well-formed; the entity is not designed.

---

## Gap category C — Documents referenced but missing

**C1. `framework_design_three_lens.md` v1.** Replaced by v2 on 2026-05-07. The v1 isn't archived as a historical record. The framework's records-keeping principle says lessons should be institutional; the predecessor version is part of the institutional record of how the model evolved.

**C2. Performance-management surface design.** Referenced in `framework_principles.md` #9 and in finding #20 as "TBD doc." Doesn't exist.

**C3. Bidirectional JD instrument design.** See B10.

**C4. Mini development rotation entity design.** See B11.

**C5. Day-one self-exercise interface specification.** Referenced in `Handoff_document_-_20260430.md` next-work list. Never built. The data model has `InformedConsentRecord` and the role definitions describe the day-one flow, but the actual interface that operationalizes the consent steps doesn't have a design doc.

**C6. CM dashboard flag-something-wrong portion.** Recognition portion specified in `learning_library_design.md`. Flag-something-wrong portion explicitly deferred and never picked up.

**C7. Alex's manager-walkthrough notes.** `handoff_20260506.md` line 153 says "in progress; research done; Dan's answers to 10 open questions pending." Never finished.

**C8. Dan's character sheet and position portfolio.** Referenced in `handoff_20260506.md` as "Complete" interactive widgets. They were chat artifacts, not persisted files. Now lost from project knowledge unless re-instantiated.

---

## Gap category D — Cross-reference inconsistencies and minor structural issues

**D1. Filename inconsistency.** README and `framework_principles.md` reference `framework_design_three_lens.md v2`. Actual filename is `framework_design_three_lens_v2.md`. Either rename the file or update references.

**D2. Glossary cross-ref to "Reference datasheet."** I added a "Four-layer authority schema" entry that cross-refs "*Reference datasheet*" but no glossary entry for "Reference datasheet" exists. Add the entry or remove the cross-ref.

**D3. Missing change log.** `cohort_temporal_record.md` line 576 update protocol mentions a "change log section (to be added)." Section never added. Worth adding now since the artifact is actively appended-to.

**D4. ContributionEvent placement.** Treated as part of `PortfolioFringeBenefitRecord` in the data model adds, but the handoff describes it as a separate entity. Decide whether it's a sub-entity or stand-alone and reconcile.

**D5. Visibility-cascading-on-revoke open question.** `coordinator_synthesis_design.md` line 77 flags this as needing confirmation against the principles document. Not yet resolved.

**D6. The scattered "spiritual-director case" references.** It's a glossary entry, a worked example in `Handoff_document_-_20260430.md` blind-spots, an open thread in `Handoff_document_-_20260505.md` blind-spots, applied to Dan's situation in profile work, and architecturally the basis for shadow-influence functions. It would benefit from a single canonical treatment that other places cross-reference to, rather than five partial treatments.

---

## Gap category E — Discipline applied inconsistently across the corpus

**E1. Provenance / origin notes.** Some documents have explicit origin notes (`framework_design_three_lens_v2.md` notes its v1 origin and what triggered v2; `data_model_adds_cohort_findings.md` traces its origin to specific findings). Others don't (`learning_library_design.md`, `role_definitions_onboarding_and_mentorship.md`, `coordinator_synthesis_design.md` headers are thin on this).

**E2. Visibly-provisional framing.** Some documents explicitly call themselves provisional (data model adds, framework v2 status note). Others read as more settled than they are (the role definitions document, the explainer agent design). The framework principle is uniform; the application varies.

**E3. Source-bias disclosure for documents.** Dan's bias toward subjects is logged. The seed export's AI-generated origin is acknowledged. But document-authorship bias more generally isn't tagged. For example: the framework principles document is co-authored by Dan and the AI assistant; that authorship pattern matters for how a future reader weighs claims, and isn't surfaced.

**E4. AAR substrate applied to project decisions.** The framework specifies AAR substrate (intent / outcome / why / lessons / skills) for project work. The handoffs are AAR-adjacent but don't follow the structured substrate. For major framework decisions (the 2D-orientation correction, the v2 framework upgrade, the recast question handling on 2026-05-07), the substrate would produce a richer institutional record than the prose-heavy handoff format. Whether to formalize is a design choice; flagging as a discipline gap.

**E5. Handoff format inconsistency.** The four handoffs vary in structure, depth, and discipline. The 2026-05-07 handoff at 112 lines is much shorter than the others (203, 189, 262 lines). The shorter form may be appropriate when the temporal record is carrying the operational state, but the format shift isn't documented.

---

## Effort estimation

I'll group the work into tiers by character of effort. The estimates assume a focused work session and don't account for context-switching or revisiting design choices.

**Tier 1 — Mechanical migration and cross-reference cleanup.** Low judgment, mostly transcription. Roughly 3.5–4 hours total. This includes A1 through A7 (migrating Dan's profile, Alex's full profile, the 10 open questions, profile entries for the missing people), plus D1–D6 (cross-reference cleanup and the change log section). The People Index migrations are the bulk of the time; everything else is small.

**Tier 2 — Substantive consolidation.** Promoting concepts to first-class status, writing typology documents, backfilling principles. Roughly 6–8 hours total. This covers B1 through B9 (trusted-talent-network classification, role-pathologies typology, defined-contribution principle, comparator-agencies findings, Goodhart-on-recognition design decisions in learning library, three-audience framings, the survivorship/bidirectionality cross-reference) plus E1, E3, E5 (provenance and source-bias backfill across the corpus).

**Tier 3 — Net-new design work.** Higher effort, substantial creative judgment, but each item enables downstream work that's currently blocked. Roughly 15–20 hours total. This covers C2 through C6 (performance-management surface, bidirectional JD instrument, mini-rotation entity, day-one interface, CM dashboard flag-wrong) plus B10 and B11 (the JD instrument and rotation specifically).

**Tier 4 — Maintenance discipline.** Process design for going-forward records-keeping, plus a finishing pass on E2 (visibly-provisional framing) and E4 (AAR-substrate-for-decisions). Roughly 3–5 hours.

**Total: roughly 28–37 hours.** Substantial, but the tiers are independent — Tier 1 is essentially mechanical and could be done in chunks of an hour at a time; Tier 3 is the largest investment and has natural breakpoints between items.

---

## Recommended sequencing

The principles-staging order suggests a sequencing different from raw-effort ordering.

**First: Tier 1 plus B1, B2, B6, B8.** The People Index migrations and the typology consolidations make the rest of the work much easier to navigate, because they create the spine of the operational record. The trusted-talent-network classification (B1) and the role-pathologies typology (B2) are referenced repeatedly elsewhere and clarify other docs. B6 and B8 are quick principles-document edits. Estimated effort: 6–8 hours.

**Second: B5, B10, B11, plus C7 if Dan answers the 10 open questions.** Dan's standing functions inventory becomes a canonical example; the JD instrument and rotation entity are downstream of architectural settling that's now mostly done; Alex's walkthrough notes complete the 5/6 thread. Estimated effort: 6–10 hours.

**Third: Tier 3 remainder (C2, C5, C6) plus B9.** The remaining design surfaces. Performance-management surface is the most-referenced gap; the day-one interface is the entry point for new hires; the CM dashboard flag-wrong is the bidirectionality completion. Estimated effort: 8–10 hours.

**Fourth: Tier 4 maintenance discipline.** This is the records-keeping pattern made systematic going forward — at this point the corpus is in shape and the discipline is to keep it that way. Estimated effort: 3–5 hours.

The full sequence runs ~24–33 hours over an indefinite period; the first phase alone (~6–8 hours) materially improves the project's discipline state and unblocks the rest.

---

## Open questions for Dan

A few choices the audit cannot resolve without input:

**Q1. What level of profile detail is appropriate for the People Index entries on adjacent figures (Magee, Manheimer, Johansen, Antil, Kennedy, etc.)?** The current director profiles are full-section narratives; the next-strata-down profiles (Scott, Lindsay) are lighter. Adjacent figures are referenced in events but not currently profiled. Options: (a) thin one-paragraph entries with role + relevance to current cohort; (b) full sections matching director-profile depth; (c) skip entirely and just keep them in events log. Default recommendation: (a), because they appear repeatedly in network mechanics and structural patterns but aren't current cohort.

**Q2. Should Dan be in the People Index?** The framework treats the project's authors as part of the cohort being analyzed (Dan named in mobile-fixer cluster, in cross-org connection map, in Source Bias Registry as `vregventura.org` parallel). Including Dan as a profiled subject is the rigorous-application reading; excluding him on grounds of role-blurring is the alternative. Default recommendation: include, with a header note about authorship overlap.

**Q3. Where should the role-pathologies typology live?** Options: (a) new file `role_pathologies_typology.md` as a standalone framework document; (b) section within `framework_design_three_lens_v2.md` since it's load-bearing for lens-coupling diagnostics; (c) section within `data_model_adds_cohort_findings.md` since the patterns are operationalized as data-model entities. Default recommendation: (a), with a cross-reference back from the framework v2 doc.

**Q4. Should the bidirectional JD instrument get its design document before or after the performance-management surface?** Both are listed in next-work but neither has been built. The PM surface is referenced in framework principle #9; the JD instrument is referenced in 5/5 handoff and is a self-contained design exercise. Default recommendation: PM surface first because it closes a principles-document loop; JD instrument second.

**Q5. What is the right vehicle for capturing audience-framings (B9), comparator-agencies findings (B7), and Goodhart-on-recognition decisions (B8)?** Options: (a) inline edits into the documents that should hold them (framework_principles, learning_library_design, etc.); (b) a new "framework rollout calibration" document; (c) a "rationale and historical decisions" document that consolidates handoff-only design content. Default recommendation: (a) for B7 and B8 (clear inline targets exist); (b) for B9 since it's substantive enough to stand alone.

**Q6. Maintenance discipline going forward.** The cohort temporal record's pattern (Source Bias Registry, Events Log, People Index, Findings Log, Open Questions, Cross-Org Connections) works for cohort data but doesn't generalize to architecture decisions and design rationale. Should an analogous "architecture decisions log" be created, or should architecture decisions go into AAR-substrate format, or should they continue to live in handoffs with cross-references from a central index? Default recommendation: a thin architecture-decisions log keyed by date with the AAR substrate fields (intent / outcome / why / lessons / skills) — appendable, cross-referencable, applies the framework's own discipline to the framework's own evolution.

---

## Process note for the audit itself

The audit is a working artifact. It should be appended to as the work above is done — a section per completed item with what was done, what was found, what the next step is. That makes the audit itself an AAR-substrate-style record of the discipline-application work. The temporal record discipline pattern applies here too.

Source bias on this audit: the audit was produced by an AI session (Claude) reading the corpus on 2026-05-07 evening at Dan's request. The audit's own framing — what counts as a gap, what counts as substantial vs minor, the effort estimates — is itself a compression choice that Dan should pressure-test rather than accept as authoritative. Particular weaknesses likely: I may be over-counting concepts that feel under-formalized to me but are operationally fine; I may be under-counting things Dan knows about that I missed; the effort estimates are calibrated to my own pace and may not reflect how Dan or a future operator actually does the work.

---

## Progress log (appended as work happens)

### 2026-05-07 evening — first phase executed

Dan authorized first-phase work: Tier 1 plus B1, B2, B6, B8. Session execution:

**Completed:**
- Tier 1 mechanical migration into `cohort_temporal_record.md`: Source Bias Registry expanded (Dan-toward-Alex, Dan-toward-Toney, Dan-toward-self); Events Log expanded with Dan's career time-series 2009 Army through 2025 SB Strategic Advisor; People Index expanded with Dan's full profile (framework author with bidirectionality-principle note), Alex's full profile from 2026-05-06 research, Esther/Bill thin entries, and a new Adjacent figures section covering Antil, Manheimer, Kennedy, Johansen, Magee, Delay, Grogan, Darcy Smith, Kelly Beggs; Open Questions Index expanded with Alex's 10 questions; Change Log section added.
- Tier 2 item B2 (role-pathology typology) executed as a standalone foundational document (`role_pathology_typology.md`), per Dan's Q3 answer that it should be a fundamental evaluation layer parallel to the three-lens model and kingdom composition.
- Q3 reframing: Dan's intuition that role-pathologies were "the kingdom-layer stuff" was caught and corrected — kingdom composition is the work-to-value taxonomy; role-pathologies are the role-vs-performance gap typology; both are foundational evaluation layers but distinct objects.
- D-fixes: filename consistency (`framework_principles.md` updated; old refs in `cohort_temporal_record.md` Findings Log corrected); glossary cross-reference for Reference datasheet (entry added; also added Role-pathology typology entry); Change Log section added in temporal record.
- Q6 starter: `framework_decisions_record.md` instantiated with hash-chained AAR-substrate format. Genesis entry plus first content entry both hashed with SHA-256 over (timestamp + AAR fields + prior_hash). File documents the hash protocol for future entries.

**Deferred to next session:**
- B1 (trusted-talent-network classification as standalone framework finding or in framework_design)
- B6 (survivorship/bidirectionality cross-reference into framework_principles)
- B8 (Goodhart-on-recognition design constraints into learning_library_design)
- All Tier 3 design work (performance-management surface is the priority per Dan's Q4 answer)
- All Tier 4 maintenance discipline work

**Open items surfaced during execution:**
- Q3 raised Q2-adjacent: whether shadow-influence decoupling is correctly placed in the role-pathology typology. The typology document's "Open architectural questions" section flags this as Q2 — alternative is to treat shadow-influence as an *orientation* (parallel to mobile-fixer / cornerstone) rather than as a pathology. Worth resolving in the next session before B1 work proceeds, since trusted-talent-network classification may interact.
- Dan's standing functions table now appears in the People Index as the canonical worked example. Should it ALSO appear as a formal artifact (e.g., as the test case it was originally designed to be, per `handoff_20260506.md`)? Test-case status vs operational-record status may need clarification.
- The hash chain in `framework_decisions_record.md` provides chain integrity but no time-anchoring. A future enhancement could add periodic external anchoring (e.g., hash committed to a public blockchain or to a separate signed log) for stronger tamper-evidence. Out of scope for tonight; flagged for design consideration.

**Next session priorities (recommended):**
1. Resolve the typology Q2 (shadow-influence as pathology vs orientation) before B1 proceeds.
2. Execute B1 (trusted-talent-network classification) — likely as a section in framework_design_three_lens_v2.md or as a section in role_pathology_typology.md, depending on how it composes with the typology.
3. B6 and B8 (small inline edits to existing files).
4. Begin Tier 3 with C2 (performance-management surface design) per Dan's Q4 answer.

The audit will be appended to as that work proceeds.

### 2026-05-08 morning — typology Q2 resolved

Dan's morning message resolved the typology's open Q2 (shadow-influence as pathology vs orientation): "an orientation for me but I do not think that's universal... without a clear valence, just the noted mismatch." Architectural consequence applied across four files:

- `role_pathology_typology.md` — added "Note on valence" section near the foundational rationale; reframed entry 5 (Shadow-influence decoupling) as the valence-neutral case capturing the structural mismatch without assigning valence; updated worked-example table commentary; removed Q2 from open architectural questions and renumbered; added "Resolved questions" section recording the resolution
- `project_rigger_glossary.md` — Role-pathology typology entry rewritten with valence variability; new Shadow-influence decoupling entry added (was a dangling cross-reference — caught and fixed during the propagation, a small instance of category-D residual)
- `cohort_temporal_record.md` — Finding #19 reframed; Change Log entry added
- `framework_decisions_record.md` — Entry 2 appended capturing the decision; chain verified valid (Genesis → Entry 1 → Entry 2; this_hash `a5748c38...`)

Resolution unblocks B1 (trusted-talent-network classification) for next session — the trusted-talent-network classification was deferred yesterday in part because of how it might interact with the shadow-influence framing. With shadow-influence now framed as valence-neutral structural mismatch rather than as a chosen orientation, the trusted-talent-network classification can proceed as its own structural pattern catalog without needing to resolve the orientation-vs-pattern question first.

A small structural observation surfaced during the propagation: the dangling glossary cross-reference for "Shadow-influence decoupling" had been introduced when the v2 framework documents were created (it's been dangling since 2026-05-07 evening) and was caught only during today's propagation. This is a useful precedent — the records-keeping audit's category D (cross-reference inconsistencies) recurs, and warrants a periodic full-corpus pass for dangling refs after substantive changes. Adding to the next-session work list.
