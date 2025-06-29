# AIP-2: Authority Signature Validation

- **Author**: Actio Core Team  
- **Status**: Final  
- **Created**: 2025-06-29

## Overview

This AIP defines how the Actio Protocol validates that action codes and transaction memos are signed by a trusted protocol authority. This ensures that codes cannot be spoofed, reused, or injected from unauthorized sources.

## Motivation

To protect users and service providers from fraudulent or tampered action codes, and to maintain a secure trust model across apps using the Actio Protocol.

## Specification

### Requirements for Validation

1. The `iss` (issuer) field in the memo must match the expected protocol authority public key.
2. The code or action request must be signed using the authority’s private key.
3. The signature must be verifiable against the code payload (or memo) and the public key (`iss`).
4. The verifier must fetch the current trusted authority list (initially from `https://service.ota.codes/.well-known/authority-registry.json`).

### Validation Steps

1. Parse the memo string from the transaction.
2. Extract the `iss` field and fetch the authority list.
3. Verify that `iss` is included in the trusted authorities.
4. Validate the cryptographic signature against the code body.

## Example Use

When a dApp receives an incoming transaction with a memo:
- It extracts the `actioncodes:` memo.
- Validates that the `iss` field is trusted.
- Uses the signature embedded in the code (or payload) to validate authenticity.

## Notes

- Signature format and structure are defined in AIP-0 and AIP-1.
- Future protocol versions may allow rotating authorities or delegating issuance to wallets.

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