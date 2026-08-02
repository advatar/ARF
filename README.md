# EUDI Reference Stack Assurance Workspace

This repository pins the European Commission's EUDI reference wallet,
credential issuer, verifier, trust/status, specification, and conformance
sources as Git submodules. It is an independent assurance workspace, not an
official EU repository and not a certification claim.

See [STACK.md](STACK.md) for the selection boundary and dependency groups, and
[STATUS.md](STATUS.md) for the verification roadmap.

## Checkout

```sh
GIT_LFS_SKIP_SMUDGE=1 git submodule update --init --recursive --depth 1
```

`eudi-doc-testing-application` uses Git LFS. The command above checks out its
source and LFS pointer files without downloading large test artifacts. Fetch
the required LFS objects explicitly when executing those tests.

Every gitlink is an immutable source pin. Several applications consume
published Maven or Swift package releases that may not equal the default-branch
commit pinned for the corresponding source repository. The formal-assurance
phase must resolve and record every consumed artifact version before making a
claim about the executable stack.
