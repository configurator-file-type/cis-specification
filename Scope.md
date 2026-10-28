# Scope

> **Status: DRAFT for Working Group approval.** Each Working Group Charter
> (JDF v.6.0, 2026-06-23) says the Working Group Scope is "as set forth in the
> Working Group repository's Scope.md file" and gives the initial text. That
> initial text is reproduced word for word in Section 1 below. Everything
> after it is interpretation, added so that contributors and their counsel can
> tell what is and is not covered. Remove this note on merge.

This file sets the Scope of the **CIS Specification Working Group**, which develops the
CIS File Format Specification (`.cis`) in this repository. Under the
Community Specification License 1.0, the Scope establishes the outer bounds of
each Contributor's and Licensee's patent commitment. Material outside the
Scope is not subject to the licensing obligations of the Working Group.

Every pull request to this repository is a Contribution to the
CIS Specification Working Group only. The CTO Specification Working Group develops the
CTO File Format Specification in its own repository, with its own
Scope: <https://github.com/configurator-file-type/cto-specification/blob/main/Scope.md>.

Any changes of Scope are not retroactive. A change to the Scope text in 1.1 is a
change to the basis on which existing Working Group Participants made
their commitments; it requires the Approval of the Working Group and of the
Steering Committee, and notice to every Working Group Participant.

---

## 1. CIS Specification Working Group

### 1.1 Scope

As established by the CIS Specification Working Group Charter:

> Develop, maintain, and version the .CIS file format specification, including
> connection plane definitions, port topology and signature schema, utility
> requirement vocabulary, structural handshake encoding, sample files, and the
> public registry format for open connection interface standards, for use in
> defining and publishing connection interface standards consumed by .CTO
> product specifications.

### 1.2 What this includes

The Working Group reads the `.CIS` file format specification as comprising the
specification of:

1. **File structure.** The structure, serialization, encoding, file extension
   and media type of `.cis` files.
2. **Connection planes and sides.** The data model by which a connection plane
   and its two sides are defined and named.
3. **Ports.** The representation of ports and port clusters, including position,
   tolerance, geometric envelope and the coordinate conventions that make them
   unambiguous.
4. **Connection signatures.** The vocabulary and rules by which the physical
   form of a port is identified, including gendered and non-gendered pairings,
   mating rules between signatures and the identification of intermediate
   connectors.
5. **Utility and structural requirements.** The representation of utility
   requirements (such as service type, material, referenced product standards
   and operating ranges) and structural requirements (such as fasteners,
   alignment features and load transfer) at a port or connection plane.
6. **Identity and registry scope.** The identification, naming, publisher and
   licensing metadata of a `.cis` file, and the distinction between openly
   registered and catalog-internal standards.
7. **Public registry format.** The data format in which open connection
   interface standards are listed, identified, versioned and retrieved from a
   public registry, so that any software can resolve a reference to a `.cis`
   file.
8. **Versioning and compatibility.** Version identification and the rules that
   determine which versions of a standard may mate.
9. **Validation and conformance.** Validation rules for `.cis` files,
   conformance requirements for software that reads, writes or validates them,
   and the rules by which software determines from two `.cis`-conformant
   declarations whether a connection is valid.
10. **Relationship to CTO.** The reference mechanism between `.cis` files and
   `.cto` files, developed in coordination with the CTO Specification Working Group.
11. **Supporting materials.** Schemas, example files, test files, conformance
    test suites, glossaries and explanatory documents that support the items
    above.

### 1.3 What this does not include

The following are outside the Scope of the CIS Specification Working Group:

1. **The content of any connection interface standard.** The physical,
   dimensional, material and performance requirements of a particular standard
   (for example CfOC-ICC-1220 or CfOC-ICC-1230, or any manufacturer's
   proprietary interface) are developed and owned by that standard's publisher.
   The Working Group specifies the file that carries such a standard, not the
   standard itself. Example `.cis` files in this repository illustrate the
   format and do not bring the standards they encode into Scope.
2. The design, engineering, manufacture or installation of any physical
   connector, fitting, fastener, port or connection method.
3. The CTO file format, which is the Scope of the CTO Specification Working
   Group (https://github.com/configurator-file-type/cto-specification).
4. The operation, hosting, governance or commercial terms of any registry, and
   the process by which any body submits, approves or ballots an interface
   standard. The registry *format* is in Scope (1.2, item 7); running a registry
   is not.
5. The internal design of any software, other than the behavior required for
   conformance under item 9 above.
6. The content of building codes, product standards or law referenced from a
   `.cis` file.
