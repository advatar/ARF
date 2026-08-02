# EUDI Reference Repository Boundary

## Selection method

The inventory was taken from the official
`eu-digital-identity-wallet` GitHub organization on 2 August 2026. Root
applications and services were selected by ecosystem role. Their SwiftPM,
Gradle, Maven, Python, Docker, and repository documentation were then inspected
to identify first-party EUDI source repositories.

The authoritative machine-readable URL and commit inventory is `.gitmodules`
plus the gitlinks in this repository. `git submodule status --recursive`
prints the exact pins.

## Included roots

### Normative and conformance inputs

- `eudi-doc-architecture-and-reference-framework`
- `eudi-doc-standards-and-technical-specifications`
- `eudi-doc-attestation-rulebooks-catalog`
- `eudi-doc-functional-conformance-assessment`
- `eudi-doc-testing-application`
- `eudi-itb`

These repositories define the architecture, technical profiles, credential
rulebooks, and official functional/conformance evidence against which the code
must be assessed. Documentation is a verification input, not executable proof.

### Wallet and verifier applications

- `eudi-app-ios-wallet-ui`
- `eudi-app-android-wallet-ui`
- `eudi-app-multiplatform-verifier-ui`
- `eudi-web-verifier`

The web verifier is paired with the verifier endpoint but is application UI,
not the trusted verification kernel.

### Wallet cores

- `eudi-lib-ios-wallet-kit`
- `eudi-lib-android-wallet-core`

### Reference services

- `eudi-srv-pid-issuer`
- `eudi-srv-verifier-endpoint`
- `eudi-srv-wallet-provider`
- `eudi-srv-trust-validator`
- `eudi-srv-status-validator-py`
- `eudi-srv-statuslist-py`
- `keycloak-client-attestation-auth-ext`

The upstream verifier endpoint and wallet provider explicitly describe
themselves as development/reference software rather than production-grade
services. Inclusion here does not change that assurance status.

## Included first-party library closure

### Swift and iOS

- `SwiftCopyableMacro`
- `eudi-lib-ios-iso18013-data-model`
- `eudi-lib-ios-iso18013-data-transfer`
- `eudi-lib-ios-iso18013-security`
- `eudi-lib-ios-openid4vci-swift`
- `eudi-lib-ios-openid4vp-swift`
- `eudi-lib-ios-presentation-exchange-swift`
- `eudi-lib-ios-rqes-csc-swift`
- `eudi-lib-ios-rqes-kit`
- `eudi-lib-ios-rqes-ui`
- `eudi-lib-ios-statium-swift`
- `eudi-lib-ios-wallet-storage`
- `eudi-lib-sdjwt-swift`
- `eudi-lib-podofo`

### Kotlin, JVM, Android, and multiplatform

- `eudi-lib-android-iso18013-data-transfer`
- `eudi-lib-android-rqes-core`
- `eudi-lib-android-rqes-ui`
- `eudi-lib-android-wallet-document-manager`
- `eudi-lib-android-verifier-core`
- `eudi-lib-jvm-openid4vci-kt`
- `eudi-lib-jvm-openid4vp-kt`
- `eudi-lib-jvm-presentation-exchange-kt`
- `eudi-lib-jvm-rqes-csc-kt`
- `eudi-lib-jvm-sdjwt-kt`
- `eudi-lib-jvm-trust-manager-kt`
- `eudi-lib-kmp-etsi-1196x2`
- `eudi-lib-kmp-statium`

This is the first-party source closure, not the complete transitive software
bill of materials. External libraries, runtimes, operating-system services,
cryptographic providers, container images, trust anchors, and hosted services
must be resolved from lockfiles and build outputs in the next phase.

## Deliberate exclusions

- Age-verification (`av-*`) repositories: a separate use-case profile/fork,
  not a dependency of the selected general EUDI roots.
- Demo business applications, booking/recruitment examples, and issuing
  frontends: integration examples rather than trusted protocol dependencies.
- Alternative Python issuer and web-signing/QTSP demonstrations: parallel
  implementations, not dependencies of the selected PID issuer/verifier roots.
- Roadmap, DevHub/site, CI infrastructure, and transfer-issue repositories:
  project operations or explanatory material rather than executable/normative
  dependencies.
- `idpy-oidc`, `openid4v`, and `pyMDOC-CBOR`: relevant to the excluded Python
  issuer path; add them only if that alternative implementation enters scope.

An excluded repository must be added if a reproducible selected-root build
proves it is a runtime, build, conformance, or normative dependency.

## Formal-assurance direction

The target is not a single undifferentiated claim that "all code is verified."
Each pinned artifact will receive explicit claims and assumptions across:

1. normative requirement traceability;
2. issuance, presentation, holder-binding, replay, and trust/status protocols;
3. parser, codec, state-machine, and policy-kernel correctness;
4. cryptographic-provider and platform contracts;
5. refinement from formal models to executable decision boundaries;
6. conformance, differential, fuzz, mutation, and end-to-end testing; and
7. operational and external-certification evidence.

The existing EUWallet, VCIssuer, and VCVerifier Lean/Tamarin/Rust work is
candidate evidence and reusable scaffolding. It must be mapped to these exact
versions and cannot be transferred as proof without a demonstrated refinement
or equivalence relation.
