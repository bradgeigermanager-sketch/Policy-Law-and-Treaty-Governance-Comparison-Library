# Governance‑OS Schema Evolution Policy

This document defines how schemas, engines, and UI models evolve over time within the Governance‑OS project. It ensures stability, backward compatibility, and predictable versioning for all downstream consumers.

---

## 1. Versioning Model

Governance‑OS uses **Semantic Versioning (SemVer)**:

- **MAJOR** — Breaking changes  
- **MINOR** — Backward‑compatible feature additions  
- **PATCH** — Backward‑compatible fixes or clarifications  

Examples:

- `1.4.0 → 2.0.0` — breaking schema change  
- `1.4.0 → 1.5.0` — new engine, new schema fields  
- `1.4.0 → 1.4.1` — typo fix, description update  

---

## 2. What Counts as a Breaking Change

A change is considered **breaking** if it:

- Removes a field  
- Renames a field  
- Changes a field’s type  
- Changes required → optional or optional → required  
- Alters semantics of an existing field  
- Removes or renames a schema file  
- Changes `$id` of a schema  

---

## 3. Backward‑Compatible Changes

These are **safe** under MINOR or PATCH:

- Adding new optional fields  
- Adding new schema files  
- Adding new engine definitions  
- Adding new UI panels  
- Adding new enums (if consumers can ignore unknown values)  
- Improving descriptions or examples  

---

## 4. Deprecation Policy

When a field or schema is planned for removal:

1. It is marked with `"deprecated": true`  
2. It remains for **two MINOR versions**  
3. Removal occurs in the next MAJOR release  

---

## 5. Stability Guarantees

- All schemas under `schemas/core/` are **stable**  
- All schemas under `schemas/instruments/` are **stable**  
- All schemas under `schemas/impacts/` are **stable**  
- Engine schemas may evolve more rapidly but follow SemVer  
- UI schemas are considered **soft‑stable** (safe to extend)  

---

## 6. Change Proposal Process

Every schema change must include:

- A description of the change  
- A justification  
- A compatibility assessment  
- A version bump classification  

---

## 7. Release Workflow Integration

The release automation workflow:

- Detects breaking changes via commit messages  
- Generates changelogs  
- Tags releases  
- Publishes schema bundles  

This policy ensures that automated releases remain predictable and safe.

---

## 8. Long‑Term Stability

Governance‑OS aims for:

- Predictable schema evolution  
- Strong backward compatibility  
- Clear migration paths  
- Machine‑readable version metadata  

This policy is binding for all contributors.
