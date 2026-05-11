# Project Rigger — archive (public)

Public-tier archive of methodology and decisions records from Project Rigger, a workforce and talent framework developed for the City of San Bruno.

## Contents

- **`spines/`** — Superseded `framework_decisions_record*.md` files. These are hash-chained records of architectural decisions; each one is a complete-but-orphaned full-chain record at its timestamp. The current canonical spine lives in the active working surface, not here.

## What this archive is for

Cold-storage preservation of the records-keeping chain with public visibility. Files here are reachable via `https://raw.githubusercontent.com/jacobsondan42/Project-Rigger-archive-public/main/<path>` for future audit operations that need to verify chain-historical claims.

## What this archive is not for

- It is not the active framework.
- It does not contain operational handoffs, stakeholder-specific records, or city-internal context (those are in a separate private archive).
- It is not maintained as a working surface — files are write-once on archive.

## Integrity

Each file is referenced from an `_archive_manifest.md` in the canonical working surface with a SHA-256 hash captured at archive time. Verify byte-equality by computing `sha256sum` over the fetched raw-URL content and matching against the manifest entry.

## License

CC BY 4.0 — see `LICENSE` and `NOTICE`. Attribution required. Methodology and worked examples are both in scope of the grant.
