# Actio Protocol Specification (Formerly One-Time Action Codes)

Actio Protocol defines an open and composable standard for intent-based transactions using one-time action codes. This specification documents the official AIP (Actio Improvement Proposals) that define how the protocol works, is extended, and integrated.

## Overview

The Actio Protocol allows users to generate, resolve, and confirm intents through a code-based interaction flow. The protocol supports a universal checkout interface, enabling any blockchain interactions across dApps and wallets.

## Core Concepts

- **Action Code**: A short-lived, verifiable, one-time-use code that encodes an intent.
- **Memo**: A Solana transaction memo (memo program v2) string that encodes protocol metadata for trust, validation, and routing.
- **Authority**: The signer that issued and/or initiated the code.
- **Intent**: The purpose of the transaction.
- **Intended For**: The address or purpose of the transaction.
- **Prefix**: An optional on-chain registered namespace identifier used for routing or branding. (e.g. `SOLANALABS` or `JUP`) *Coming with AIP-5*

## AIPs

- [**AIP-0:**](./aips/aip-0.md) (Done) One-Time Action Code Architecture — Establishes the fundamental design of the action code system: a short-lived, verifiable intent tied to a user’s public key.
- [**AIP-1:**](./aips/aip-1.md) (Done) Protocol Memo Format — Defines the canonical memo structure used in every Actio transaction.
- [**AIP-2:**](./aips/aip-2.md) (Done) Authority Signature Validation — Explains how code signatures and memo issuer fields are validated.
- [**AIP-3:**](./aips/aip-3.md) (Done) Intent Resolution & Routing — Describes how intent data is processed and matched against the transaction.
- [**AIP-4:**](./aips/aip-4.md) (Done) Task System — Describes the internal processing model for action task execution.
- [**AIP-5:**](./aips/aip-5.md) (Coming soon) Prefix System — Describes the system for registering and using prefixes for routing and branding along with the prefix registry.
- [**AIP-6:**](./aips/aip-6.md) (Coming soon) On-chain Trust System — Describes the system for verifying registered prefixes for trust and validation.
- [**AIP-7:**](./aips/aip-7.md) (Planned) Cross-chain Protocol Compatibility — Describes how the protocol can be extended to support other blockchains.

## Example

An Actio transaction memo:

Example transaction logs: [Solscan](https://solscan.io/tx/SZFsQdTeJgpJVVbG7p5BKbUppwTWyUFggeqLbpBU9TfrTzDqwtTtoGN7hYJVqPFn1gKhFxPpuqezs7ErDjC5wBZ)

```
actioncodes:ver=1&pre=DEFAULT&ini=CCCCZSgqUBsmFLceNwgFBJC3mL5N8Be67WjRh1jhgzJ5&iss=CCCCZSgqUBsmFLceNwgFBJC3mL5N8Be67WjRh1jhgzJ5&int=H7fubezu5B76NMjsQGNcEdaZWXgXRDtTd7NQjAeTY6W3
```

## Links

We are currently in the process of rebranding, migrating to the new domain and product page.

- [Main Product Page](https://ota.codes) Will be replaced with https://actio.click
- [One-time Code Generator](https://app.ota.codes) Will be replaced with https://useactio.codes
- [Docs and SDK](https://github.com/useactio/sdk/tree/main/docs) Will be replaced with https://docs.useactio.codes
- [Rest API](https://service.ota.codes/docs) Will be replaced with https://docs.useactio.codes
- [Prefix Registry (WIP)](https://registry.actio.click) Not public yet

---

Copyright 2025 Actio Labs Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.