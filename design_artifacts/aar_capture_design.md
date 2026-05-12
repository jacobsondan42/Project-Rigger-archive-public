# AAR Capture Surface Design

## What AAR capture does

The AAR (After-Action Review) capture surface is the framework's primary mechanism for converting events and cycles of work into institutional learning. It serves a population — analysts, managers, leadership, the framework's own author — and produces records that feed the People Index, the Framework Findings Log, and the cohort temporal record's Events Log.

AAR capture is distinct from adjacent surfaces in the framework:

- The **framework_decisions_record** uses the AAR substrate (intent, outcome, why, lessons, skills) but adds hash-chain integrity for architectural decisions specifically. AAR capture is for stakeholder events and cycles; the decisions record is for framework-architecture changes.
- The **cohort temporal record's Events Log** records what happened chronologically. AAR capture records what was learned reflectively. The two compose: events are logged when they occur; AARs are captured after.
- The **reference datasheet** is at-a-glance per-person reference. AAR capture is post-event reflection. The datasheet may surface AAR summaries; the AAR is the source.

The bidirectionality principle (records-keeping principle #20) applies recursively: AAR capture itself is subject to the framework's own discipline, including when the framework's primary author captures AARs on themselves.

## The five-field substrate

Every AAR uses the same five-field substrate, regardless of capture mode:

- **Intent** — what was supposed to happen, what success looked like at the start, both formal and personal goals.
- **Outcome** — what actually happened, what got delivered, what didn't, what conditions changed. Description rather than judgment.
- **Why** — what made the difference between intent and outcome. Internal factors (decisions, preparation), external factors (resourcing, dependencies, surprises), and the structural conditions under which the work was done.
- **Lessons** — what should stay the same, what should change. Captured as paired columns to avoid collapsing same-and-change into prose. Distinguishes lessons for the subject, lessons for the role-as-designed, and lessons for the institutional process.
- **Skills** — skills exercised across the work. At cycle-level, the deepened five-axis schema applies (see below). At event-level, a single textarea is acceptable for short events.

Fields are skippable per the consent architecture. Skipping is not failure; it's a deliberate scope choice. The capture surface should make skipping low-friction so the threshold to start an AAR stays low.

## Capture modes

AAR capture operates in three modes that share substrate but adapt prompts:

**Event-level AAR.** Captures a single decision, action, or moment. Scope is bounded by the event itself (e.g., a specific revenue revision, a specific stakeholder conversation). Skills field can stay shallow or be skipped. Bidirectional capture often noted as "self-directed action; no external support inputs to capture for this event" when the event was solo.

**Cycle-level AAR.** Captures the arc of work across a cycle (a budget cycle, a project, a quarter). Substrate fields are at cycle-scope; the deepened skills schema applies; nested events reference event-level AARs from within the cycle. Bidirectional capture surfaces patterns single-event capture can't (recurring sponsorship, escalating support, capacity built through repeated exposure).

**Self-AAR (bidirectionality reflexive).** Subject is the captor. Source bias is structurally I-lens; the framework's discipline of "analytical with disclosed self-awareness limit" applies. The framework's primary author captures AARs on themselves by the same rules applied to others. This is bidirectionality made operational — the framework profiles its own author, including for events under solo authority and information asymmetry. Self-AARs are particularly valuable as foundational artifacts because they demonstrate the discipline applied without exception.

## The five-axis skills schema

The single skills field is too coarse for cycle-level capture. The deepened schema separates five axes that carry distinct portfolio-development meaning over time:

- **Used** — existing skills exercised across the work. Useful for cross-cycle pattern recognition (which skills consistently get drawn on) and for portfolio currency (skills are perishable; regular exercise keeps them current).
- **Built** — skills that didn't exist before, or that crossed a threshold from rudimentary to functional. The clearest portfolio-development signal — the cycle's new capabilities.
- **Stretched** — existing skills pushed beyond their previous operating envelope. Distinct from "built" because the skill was already there — what changed is its range, depth, or operating envelope.
- **Gaps surfaced** — capabilities noticed missing, surfaced not by failure but by recognizing absence in moments where the skill would have helped. Gap-naming is the highest-trust skill capture; surfacing them requires admitting limit.
- **Supported in others** — skills exercised in service of someone else's development. Bidirectional skill capture; the framework's bidirectionality principle made operational at the skill layer.

The five-axis pattern across multiple cycles is what feeds the portfolio's developmental record. Cross-cycle stability of an axis (skills consistently used) reads differently from cross-cycle progression of an axis (skills built, then used, then supported in others). The five axes are a candidate addition to the AAR template generally; v1 implementation is at cycle-level only, with event-level capture remaining single-textarea until the five-axis pattern proves stable across cycles.

## Nesting: events within cycles

Cycle AARs reference event AARs by ID/title rather than duplicating their content. This keeps the cycle-level surface scannable while preserving the event-level detail. The nested-event reference shows: event title, event date, capture date, status (draft, captured, finalized), and a one-paragraph summary. The full event AAR is a separate artifact.

Nesting beyond two levels (event in cycle in fiscal year) is an open architectural question. v1 supports two levels; deeper nesting may emerge naturally as multi-cycle patterns get captured.

## Findings-triggered surfacing

AARs surface candidate findings during capture — patterns, heuristics, or framework-relevant observations that emerge from the work. Findings are tagged as candidates and require subject confirmation before promotion to the Framework Findings Log. The capture-not-evaluate discipline applies: AARs propose findings, they don't classify or rank them.

Common finding categories surfaced through AAR capture:

- **Operational heuristics** — decision rules observed in use (e.g., "lower-pain-category-of-error" triage).
- **Structural observations** — patterns about how work or organizations are shaped (e.g., late-cycle asymmetry-collapse, ClearGov split-speed publishing).
- **Architectural arguments** — concrete groundings for previously-abstract framework decisions (e.g., the agent-augmented coordinator function justified by a real solo-authority moment).
- **Demonstrated principles** — moments where a framework principle was made operational rather than stated (e.g., bidirectionality reflexive in real time).
- **Pending-review architectural** — findings that require external input before promotion (e.g., records-act exposure pending legal review).

## Bidirectional capture

Per principle #20, AAR capture includes a paired section: "what you received" alongside "what you did with it." The two-column layout makes the principle structural rather than just labeled. Cycle-level bidirectional capture surfaces patterns that single-event capture can't — recurring sponsorship, escalating support, capacity built through repeated exposure to the same kind of work, what the subject offered back to others' development.

The bidirectional section is optional but encouraged. For solo events, it can be marked "self-directed action; no external support inputs to capture for this event" — which is itself a structural observation worth preserving rather than collapsing.

## Layer separation

AAR content spans three layers with different ownership and disclosure properties:

- **Role layer** — content that documents official acts, role records, decisions made in the role, cross-departmental coordination. Almost certainly agency-record territory regardless of where stored. CPRA exposure is structural for this layer.
- **Utility-function layer** — personal preferences, what energizes, long-term aspirations, self-assessed gaps, Working Genius profile. Stronger personal-record claim. Privacy-gated by default in the framework.
- **Private journal layer** (candidate) — user-owned, doesn't touch agency systems at all. Unambiguously personal property. For content adjacent to work but not of work.

The AAR substrate spans layers: Intent and Outcome typically describe agency activity (role layer); Skills and Lessons are mixed; the bidirectional "what you did with it" can be either; reflective content about what the subject is becoming or what they value is utility-function layer.

The layer separation matters legally (CPRA exposure differs by layer), architecturally (different layers may have different storage and access patterns), and operationally (the tool's value proposition must match the legal reality of each layer; see Open architectural questions below).

## Visibility and sharing controls

Per-field visibility controls are load-bearing. Defaults:

- Utility-function-layer fields default to private to subject.
- Role-layer fields default to private during draft, with visibility configurable on finalize. Some role-layer content (e.g., AARs that document official acts) may have agency-record disclosure exposure regardless of subject's visibility choice.
- Private-journal layer (when implemented) is structurally inaccessible to anyone but the subject.

Visibility options for shareable fields:

- Private to me (default)
- Share with manager
- Share with manager + coordinator
- Add to learning library (becomes available as exemplar, attributed to subject)

"Add to learning library" makes the field available as an exemplar that others can learn from, attributed to the subject. "Share with manager + coordinator" surfaces in manager portfolio review and coordinator cross-cohort synthesis without leaving the subject's private record. Finalizing locks the record but doesn't change sharing — the subject can adjust visibility on a finalized AAR at any time.

## Visual rendering standard

Per operating constraint #7 in `core_principles_for_agent_behavior.md`, AAR capture renders as an interactive panel with high-density inline glossary tooltips, expandable sections (e.g., per-field privacy controls collapsed by default), and stable visual encoding across rendering instances. Plain-text rendering is acceptable as a fallback when the surface does not support rich content; it is the lower-fidelity case rather than the default.

The rendered surface includes structural affordances for the friction-reducing principle: skip-this-field controls inline; "switch to conversational" option for users who prefer dialog over form; save-as-draft and defer-to-later affordances; placeholder text in textareas that models what an answer looks like without prescribing content.

## Reproducibility — how to render in future

When asked to set up an AAR (event-level, cycle-level, or self-AAR), the agent renders a widget with the following structure:

**Header card.** Title (e.g., "AAR — [event/cycle name]"), subtitle (subject, date, capture mode, source bias if self-AAR), status pills (draft / scaffold / captured / foundational), brief framing paragraph if scaffold. Use AAR abbr-tooltip for the title.

**Orientation card** (event-level capture for first-time users only). What this is, isn't, voluntary, skippable, deferable, conversational option. Skip for cycle-level or expert users who don't need re-orientation.

**Substrate fields** (5 cards, one per field). Each card: numbered badge, field name (with abbr tooltip), one-line subhead, guiding question with a bolded prompt, textarea (or paired textareas for Lessons stay/change). Skip-this-field affordance per card.

**Skills card.** For cycle-level: five-axis grid (used, built, stretched, gaps surfaced, supported in others), each axis with its own abbr tooltip and prompt and textarea, supported-in-others spans both columns. For event-level: single textarea, marked "to confirm" if agent-suggested.

**Nested events card** (cycle-level only). List of referenced event AARs by title and date with one-paragraph summaries. Placeholder note for events not yet captured.

**Findings triggered card.** Candidate findings surfaced during capture, each with title, status pill (candidate finding / candidate observation / demonstrated / architectural pending review), and one-paragraph detail. Capture-not-evaluate framing.

**Bidirectional capture card.** Two-column layout: "What you received" / "What you did with it." Per-column prompts, textareas. Optional but encouraged.

**Visibility controls** (collapsed by default). Per-field privacy options as a details/summary expansion. Defaults named in the orientation card.

**Footer card.** Save draft, defer to later, switch to conversational. Foot-note about visibility being adjustable.

**Color encoding.** Use the established palette from prior renderings: substrate-field number badges in interpretive purple (#EEEDFE bg / #3C3489 text); built/received in mediative teal (#085041 text); stretched/sent in allocative coral (#993C1D text); gaps in generative pink (#72243E text); supported in others in protective gray (#5F5E5A text). Stable encoding across renderings is load-bearing per constraint #7.

**Glossary tooltips.** Every framework-specific term gets an `abbr` tooltip with definition. Density target: every kingdom name, every principle reference, every acronym, every framework concept used in field labels or guides. Use the dotted-underline affordance to signal hoverability.

**Loading messages.** 2-4 messages, calibrated to the AAR mode and weight (e.g., for serious-topic AARs use boring/descriptive messages per the read_me guidance).

For self-AARs specifically, the header should include "Source bias: I-lens, analytical with self-awareness limit" as a meta-pill, and the framing paragraph should name bidirectionality reflexive operation explicitly.

## Open architectural questions

- **Layer-separation legal definition.** The role-layer / utility-function-layer / private-journal-layer architecture is operationally clear but legally pending. CPRA exposure for role-layer records is likely structural; utility-function-layer content has a stronger personal-record claim; private-journal layer would need to be architecturally isolated from agency systems to support unambiguously-personal framing. City Attorney consult requested; specialist routing expected. Architectural decisions on storage, access, and visibility defaults follow the legal answer.

- **Five-axis skills schema stability.** The five axes (used, built, stretched, gaps surfaced, supported in others) are a candidate; v1 implementation is at cycle-level only. Worth pressure-testing across multiple cycles whether all five carry useful signal or whether some collapse with more use.

- **Nesting beyond two levels.** v1 supports cycle-containing-events. Whether multi-year arcs (fiscal-year-containing-cycles, or career-arc-containing-fiscal-years) want their own nesting level is open. Likely emerges naturally as cross-cycle patterns get captured.

- **AAR archive structure.** Flat versus hierarchical, search affordances, cross-reference between AARs (e.g., manager's cycle AAR vs analyst's cycle AAR for the same cycle) — all open. v1 storage is per-subject and per-event; v2 archive design is downstream of layer-separation legal review.

- **Reproduction across cycle types.** The cycle-level AAR was scaffolded against budget cycles. Project cycles, quarterly cycles, fiscal-year arcs, and engagement cycles may want adapted prompts. Worth pressure-testing whether the budget-calibrated prompts transfer or whether cycle-type-specific prompt sets are needed.

## Status

v1: Live. Event-level capture demonstrated (ISF revenue revision, 2026-05-07). Cycle-level capture scaffolded (FY27 budget cycle, Dan Jacobson, foundational artifact). Self-AAR / bidirectionality reflexive demonstrated. Records-act exposure flagged; legal review pending.

v2 architectural improvements anticipated: agent-augmented coordinator function would surface findings during capture in real time rather than requiring post-hoc review; multi-cycle pattern detection across the five-axis skills schema; private-journal layer if legal review supports it; cycle-type-specific prompt adaptation.

## Cross-references

- `core_principles_for_agent_behavior.md` — operating constraint #7 (visual rendering standard) governs the widget rendering for AAR capture.
- `reference_datasheet_design.md` — datasheet may surface AAR summaries; AAR capture is the source.
- `cohort_temporal_record.md` — Events Log records events; AAR capture records what was learned. The two compose.
- `framework_decisions_record.md` — uses AAR substrate for architectural decisions with hash-chain integrity. AAR capture is the stakeholder-facing analog.
- `coordinator_synthesis_design.md` — coordinator synthesis can be triggered by accumulated AARs across the cohort; AAR capture is one input.
- `learning_library_design.md` — AARs marked "add to learning library" become exemplars in the library; the visibility option is the connection.
- `project_rigger_glossary.md` — entries for AAR, AAR substrate, bidirectionality principle, and related terms.
