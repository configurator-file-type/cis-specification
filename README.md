# CIS File Format Specification

This repository hosts the open specification for the **CIS file format** (`.cis` files): machine-readable connection interface standards for Configure-to-Order (CTO) building products. Its companion, the **CTO file format** (`.cto` files) for building configurations and product definitions, is in [cto-specification](https://github.com/configurator-file-type/cto-specification).

The specification is developed by the **CIS Specification Working Group** of the **Configurator File Type Project**, a series of [Joint Development Foundation](https://www.jointdevelopment.org/) Projects, LLC (Linux Foundation). Membership is free and open to any party with a direct and material interest. The work originated at, and continues to be edited by, the [Center for Offsite Construction (CfOC) at NYIT](https://centerforoffsiteconstruction.org).

Specifications are licensed under the [Community Specification License 1.0](LICENSES/Community-Specification-License-1.0.md); source code is licensed under [Apache-2.0](LICENSES/Apache-2.0.txt). See [`LICENSE.md`](LICENSE.md).

**New here?** Start with the [new contributor guide](docs/ONBOARDING.md).

---

## Current version

| Specification | Latest published version | Working draft (includes unreleased changes) |
|---|---|---|
| CIS File Format | **v0.1.3**, [`spec/cis/v0.1/v0.1.3/cis-specification-v0.1.3.md`](spec/cis/v0.1/v0.1.3/cis-specification-v0.1.3.md) | [`spec/cis/specification.md`](spec/cis/specification.md) |

Released: April 19, 2026. See [CHANGELOG.md](spec/CHANGELOG.md) for version history, including changes merged since the last release.

Cite a published version, not the working draft. Each published version has a
frozen copy in its own version folder and, from the next release on, a tagged
[GitHub Release](https://github.com/configurator-file-type/cis-specification/releases).

---

## What this specification does

### The CIS file format (`.cis`)

The CIS file format is the companion specification to CTO. CIS files document **connection interface standards** as machine-readable artifacts — including connection plane sides, port geometry, port connection signatures, utility requirements, and structural handshakes.

A `.cis` file:

- Defines the two sides of a connection plane (e.g., `dwelling_unit_side` / `building_services_side`)
- Specifies port positions, tolerances, and connection signatures within each side
- Describes utility requirements (pipe specs, ASTM standards, pressure ranges) at each port
- Documents structural handshakes (bolts, alignment pins, load transfer)
- Distinguishes open standards (publicly registered) from proprietary catalog-internal standards

A `.cto` element file declares conformance to one or more `.cis` files via the `declares_interface` block. The CIS file is the source of truth for connection-plane specifics; the CTO file is the source of truth for product-specific geometry, lifecycle, and the rotation-lock binding between product faces and CIS sides.

### The companion CTO file format

The CTO file format (`.cto`) describes building products and the buildings composed from them. It is developed by the CTO Specification Working Group in its own repository: <https://github.com/configurator-file-type/cto-specification>. For why connection interfaces have their own format, see [Why two specifications?](https://github.com/configurator-file-type/cto-specification#why-two-specifications) in the CTO repository.

---

## Repository structure

```
cis-specification/
├── README.md                     ← this file
├── Scope.md                      ← what this Working Group covers (sets patent scope)
├── Governance.md                 ← roles, decisions, approvals
├── CONTRIBUTING.md               ← the contribution rules
├── MAINTAINERS.md                ← who holds which role
├── MEMBERS.md                    ← Project Members and who has Joined this Working Group
├── Notices.md                    ← conduct contacts, license acceptances, exclusions
├── CODE_OF_CONDUCT.md
├── LICENSE.md                    ← which license applies to what
├── LICENSES/                     ← full license texts
├── docs/
│   └── ONBOARDING.md             ← new contributor guide
├── spec/
│   ├── README.md                 ← how the spec files are organized
│   ├── CHANGELOG.md              ← version history, with an "Unreleased" section
│   └── cis/
│       ├── specification.md                        ← working draft: every PR edits this
│       └── v0.1/
│           ├── v0.1.0/ … v0.1.2/                   ← published: earlier CIS drafts (frozen)
│           └── v0.1.3/cis-specification-v0.1.3.md  ← published: CIS v0.1.3 (frozen, latest)
└── examples/
    └── cis/
        └── CfOC-ICC-1220-v0.2.0.cis   ← first example CIS file
```

The specification has one living file, `spec/cis/specification.md`. Every change is a pull request against that file, so reviewers see exactly what changed. When the Working Group approves a new version, a Maintainer copies the living file into a new folder named for the full version (for example `spec/cis/v0.1.4/`), tags that commit (`cis-v0.1.4`) and creates a GitHub Release. Version folders, tags and Releases are never edited afterwards. See [`spec/README.md`](spec/README.md).

---

## Getting started

**If you're a standards engineer authoring a connection standard:**
Read the CIS spec ([`spec/cis/specification.md`](spec/cis/specification.md)) end-to-end. The CIS spec §15 explains the relationship to CTO files. The example file at [`examples/cis/CfOC-ICC-1220-v0.2.0.cis`](examples/cis/CfOC-ICC-1220-v0.2.0.cis) is the canonical reference for what a fully-conformant CIS file looks like.

**If you're a software developer building a CTO parser or configurator:**
Start with the CTO spec in the [CTO repository](https://github.com/configurator-file-type/cto-specification). The CIS spec in this repository is normative for any CIS files referenced by CTO files; conformant parsers must be able to parse them.

**If you're a manufacturer authoring an element file:**
Read the CTO spec first ([CTO repository](https://github.com/configurator-file-type/cto-specification)), then CIS spec §15 (Relationship to the CTO File Format) for the division of labor between the two file types.

**If you're a decision-maker evaluating these formats for adoption:**
Read [`cto-file-format-intro.md`](https://github.com/configurator-file-type/cto-specification/blob/main/cto-file-format-intro.md) in the CTO repository for a prose overview of both formats.

---

## Design philosophy

The CIS specification follows the design principle stated in CTO v0.2.0 (§2.8): **specifications must speak to humans as well as to parsers**. Three audiences read these specs — software developers, standards engineers, and decision-makers — and schema definitions alone serve only the first.

Every section, block, and field benefits from prose that explains its purpose, scope, and explicit exclusions in plain language. Where a concept has counterintuitive scope — for example, `clearance_zones` describes *external* clearance only, not internal product operations — the spec makes this explicit. When in doubt, we write more prose, not less.

This principle applies to contributions: when proposing changes, please draft prose-first and JSON-second.

---

## Contributing

Issues and pull requests about the CIS specification are welcome in this repository: <https://github.com/configurator-file-type/cis-specification>. Issues about the CTO specification belong in <https://github.com/configurator-file-type/cto-specification>. Earlier copies of these repositories hosted elsewhere are no longer the place to contribute.

Anyone can open a pull request; Project membership is not required. Read the [new contributor guide](docs/ONBOARDING.md) first, then [`CONTRIBUTING.md`](CONTRIBUTING.md). Contributions to the specification carry the copyright and patent commitments of the Community Specification License, within the [Scope](Scope.md) of the CIS Specification Working Group.

---

## License

Specifications: [Community Specification License 1.0](LICENSES/Community-Specification-License-1.0.md). Source code: [Apache License 2.0](LICENSES/Apache-2.0.txt). Details, and the warranty disclaimer that applies to everything here, are in [`LICENSE.md`](LICENSE.md). Implementations may be commercially proprietary or open source; the specifications themselves are open and royalty-free.

---

## Editors and contributors

Current role holders under the Project's governance are listed in [`MAINTAINERS.md`](MAINTAINERS.md).

**Editors:**
- Jason Van Nest, Center for Offsite Construction
- Mathew Ford, Center for Offsite Construction

**Contributors:**
- Michael Nolan, CfOC BIM/VDC Research Fellow
- Steve DeWitt, CfOC Senior Research Fellow
- Sam Williams, CfOC Senior Research Fellow

**Acknowledgments:**
The v0.2.0 / v0.1.3 paired release was driven by the authoring of the first real CIS files (CfOC-ICC-1220 v0.2.0) and the first element file (LBS K01-UM kitchen pod), which surfaced 22 spec observations during a single intensive session. Approximately one-third of those observations are addressed in v0.2.0; the remainder are tracked for future releases.
