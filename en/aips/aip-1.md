
# AIP-1: Protocol Memo Format

- **Author**: Actio Core Team  
- **Status**: Final  
- **Created**: 2025-06-29

## Overview

This AIP defines the canonical memo format used in Actio-powered transactions. The memo encodes authoritative metadata that allows transactions to be verified, traced, and trusted.

## Motivation

To ensure each transaction processed via Actio is traceable, validated, and cryptographically anchored to both an issuer and an initiator. This enables cross-system trust, analytics, and branding without compromising privacy or requiring off-chain assumptions.

## Specification

The memo format is a URL-style key-value structure prefixed by `actioncodes:`.

### Format

```
actioncodes:ver=1&pre=PREFIX&ini=INITIATOR&iss=ISSUER&int=INTENDED
```

- `ver`: Protocol version (e.g. `1`)
- `pre`: Registered prefix (e.g. `DEFAULT`, or a brand-specific prefix like `JUP`)
- `ini`: Initiator wallet public key (who initiated the code or transaction)
- `iss`: Issuer wallet public key (who signed or authorized the code)
- `int`: Intended recipient wallet public key

### Example

```
actioncodes:ver=1&pre=DEFAULT&ini=CCCCZSgqUBsmFLceNwgFBJC3mL5N8Be67WjRh1jhgzJ5&iss=CCCCZSgqUBsmFLceNwgFBJC3mL5N8Be67WjRh1jhgzJ5&int=761UVEYf7fqu6VSTi8uR9DepWUyxMR47sb4YeUmVL8CV
```

## Validation

Validation requires:

1. Parsing the memo.
2. Ensuring the issuer matches a known protocol authority.
3. Verifying that the memo signature is cryptographically correct (see [AIP-2](./aip-2.md)).

## Notes

- The memo is publicly visible on-chain.
- It avoids including any sensitive or encrypted data.
- This format may be extended in future protocol versions and ready to use with other blockchains.

---

Copyright 2025 Actio Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.