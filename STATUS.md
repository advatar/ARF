# Status

## EUDI Reference Stack Vendoring and Assurance

- [x] Create the tracking issue with scope, selection rules, verification plan, and acceptance criteria: https://github.com/advatar/ARF/issues/1
- [x] Inventory the authoritative EUDI wallet, issuer, verifier, trust/status, specification, and conformance repositories.
- [x] Derive first-party repository dependencies from the selected roots' build manifests.
- [x] Document included repositories, roles, pins, dependency relationships, and exclusions.
- [x] Add the reviewed repository set as pinned Git submodules grouped under `sources/`.
- [x] Verify recursive submodule initialization, gitlink integrity, and clean repository state.
- [ ] Establish reproducible build and test baselines for every selected component.
- [ ] Produce a dependency-by-dependency formal-assurance matrix.
- [ ] Reuse applicable Lean, Tamarin, Rust-kernel, conformance-vector, fuzzing, and mutation work from EUWallet, VCIssuer, and VCVerifier.
- [ ] Implement and verify the formal-assurance plan without treating external certification or unproved cryptographic/platform dependencies as verified.

The current phase is repository inventory and immutable vendoring. Formal
verification is a subsequent phase and remains unchecked until evidence exists
for each claim and dependency boundary.

Vendoring outcome: 46 official first-party repositories are pinned under
`sources/`. Recursive initialization, official-origin URL validation, clean
submodule checks, and Git whitespace checks pass. Git LFS payloads for the
testing application remain intentionally unfetched; its source and pointer
files are pinned, and required payloads must be fetched for the relevant test
baseline.
