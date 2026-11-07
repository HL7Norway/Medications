# CORRECTIONS.md — Medications

Base: HL7Norway/Medications@f757b7c (master). User authorized implementation of all viable proposals.

## Implemented

1. **`readme` → `README.md`** — replaced 4-byte file ("Test") with proper README.md with purpose, structure, versioning, license.
2. **`.gitignore`** — expanded with fsh-generated/, output/, temp/, *.zip, *.log, .DS_Store, Thumbs.db.

## Not implemented (requires maintainer decision or clinical review)
- REA-003: review of `draft` status of FHIR profiles (clinical domain).
- REA-004: external dependency `no-basis-Medication` — requires maintainer confirmation.

## Validation
- Static review completed.
- Not executed: FHIR/SUSHI build (not applicable).
