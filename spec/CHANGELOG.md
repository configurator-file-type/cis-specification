# CHANGELOG

This file tracks the version history of the CIS (Configure-to-Order Interface
Standard) File Format Specification. Entries are ordered most-recent-first.

Until October 2026 the CTO and CIS specifications shared one repository and one
changelog. The CTO entries are in the CTO repository: <https://github.com/configurator-file-type/cto-specification/blob/main/spec/CHANGELOG.md>.

The pre-release drafts v0.1.0 to v0.1.2 are kept in `spec/cis/v0.1/v0.1.0/` to
`v0.1.2/`.

Every pull request that changes the specification adds an entry under
**Unreleased**, linking the pull request. When a version is published, those
entries move under a new version heading.

---

## Unreleased

_No changes yet._

---

## [CIS] v0.1.3 — April 19, 2026

**Optional ports.** Adds the `required: boolean` field to ports, enabling optional ports within a CIS standard. Optional ports may be present on one side of a connection plane and absent on the other; the configurator silently treats unmated optional ports as terminated at the manufacturing stage. This addition supports the common case where a single CIS standard governs both fully-equipped products (e.g., a kitchen pod with hot water) and reduced-feature products (e.g., a closet pod without hot water).

### Added

- §6.1 — `required: boolean` field on port schema, default `true`
- §6.5 rule 4 — optional-port presence asymmetry handling
- §6.5.1 — manufacturing implications of permissive optional ports
- §9.6 — adding `required: false` ports is a backward-compatible MINOR bump

---

## [CIS] v0.1.2 — April 18, 2026

**Connection signature registry.** Replaces the abstract `gender` field on ports with a material-aware `connection_signature` field drawn from a fixed registry (Appendix F). This change reflects the physical reality that connection topology (PEX barb-to-barb via intermediate pipe, copper male-to-female direct thread, PVC slip joints, flange-to-flange via gasket) varies by material and cannot be captured by a single male/female axis.

### Added

- Appendix F — Connection Signature Registry, with 39+ signatures across 7 categories (water supply, DWV, gas, electrical, data, HVAC, structural)
- §6.1 — `connection_signature` field replacing `gender`
- §6.2 — three signature patterns: same-with-intermediate, same-direct, gendered-direct
- §6.5 — port-pair mating rules including registry table lookup
- §7.1 — `intermediate_connector` block on utility connections (required when signatures are same-to-same-with-intermediate)
- §9.5 — registry governance: new signatures via MINOR bump, removed via MAJOR

### Changed

- §6.4 — mirror geometry rules updated for signature complementarity
- §11.4 — validation rules updated for signatures

---

## [CIS] v0.1.1 — April 18, 2026

**Connection plane reframing.** Sides are properties of the connection plane (defined in the CIS file), not properties of the product. A product's face *addresses* a side by reaching toward the plane from that side.

### Added

- §1.3 — Terminology entries for "Connection Plane," "Sides," "Upstream / Downstream"
- §5.4 — explicit rule that side names are scoped to their CIS file (not globally unique)
- §10.3 — `{MFG}-INT-{upstream}-{downstream}` naming convention for proprietary standards, with chain-order semantics

### Changed

- §2.2 and §5 — language reworked to describe sides as properties of the connection plane, not the product
- §15.2 — `interface_roles` framed as a rotation-lock validation rule, not just an informational mapping
- §15.3 — added warnings-vs-errors philosophy for design-time vs. manufacturing-ready

---

## [CIS] v0.1.0 — April 18, 2026

**Initial publication.** First version of the CIS file format specification. Establishes the baseline structure: top-level metadata, sides, ports with geometry, utility connections, structural connections, versioning, and the open-vs-proprietary distinction.

### Added

- Initial 16-section specification covering file structure, schema, sidedness, port geometry, utility/structural connections, versioning, MIME type, validation, and conformance
- Companion to the CTO file format specification (released in coordination)

---

## Earlier versions

The CIS specification did not exist before v0.1.0 (April 18, 2026).
