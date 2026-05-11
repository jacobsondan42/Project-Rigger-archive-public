# Project Rigger archive bundle — 2026-05-10

23 files extracted from /mnt/project/ for migration to GitHub-hosted archive tier per Entry 30 (forthcoming) codification.

## Directory layout

- `spines/` — 6 superseded `framework_decisions_record*.md` files (R1). Contains framework methodology, codifications, audit observations. **Recommended visibility: PUBLIC.**
- `handoffs_pre_protocol/` — 7 handoffs from before the timestamped-handoff convention (Entries pre-17, dated 2026-04-30 through 2026-05-08). May reference operational specifics, stakeholders by name, framework-emergence context. **Recommended visibility: PRIVATE.**
- `handoffs_chain_entry_archive/` — 10 chain-entry-producing handoffs older than the inline-retention horizon (Entries ~17 through ~23, T204202Z through T033000Z). Mostly framework discipline content but may reference operational context. **Recommended visibility: PRIVATE.**

## Sensitivity recommendation rationale

- **Spines as public:** the framework_decisions_record files are pure methodology — codifications, glossary cross-references, principles. No PII, no city operational data, no stakeholder names beyond the records-keeping discipline itself.
- **Handoffs as private (default):** handoffs are conversational records of a thread's work. They tend to be lower-formality and may name stakeholders, reference operational specifics, or carry candid framing that's appropriate for an internal record but not for public visibility.

You can override per-file. Move any file between directories before pushing.

## What to do with this bundle

1. Unzip locally.
2. Review each file's content if you want to adjust the public/private split.
3. Push `spines/` (or your final public set) to your **public** GitHub repo at the repo root, preserving directory names.
4. Push `handoffs_pre_protocol/` and `handoffs_chain_entry_archive/` (or your final private set) to your **private** GitHub repo at the repo root.
5. Reply to the conversation with: (a) public repo URL + default branch, (b) private repo URL + default branch.

## Integrity check

`_bundle_sha256.txt` contains SHA-256 hashes for each file. After pushing to GitHub, the manifest I produce in project knowledge will include these hashes. Future audit operations can fetch the raw GitHub URL and verify byte-equality against the manifest hash — this gives you tamper-evidence on the archive.
