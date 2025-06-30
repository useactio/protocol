# AIP-0: One-Time Action Code Architecture

- **Author**: Actio Core Team
- **Status**: Final
- **Created**: 2025-06-29

## Overview

Defines the foundational concept of the Actio Protocol: one-time codes that encode an action intent tied to a specific user’s public key.

## Motivation

Enable secure, one-time programmable actions that can be verified on-chain and used for payment, access, voting, and other workflows.

## Specification

Each Action Code:
- Is a short-lived, verifiable intent tied to a user’s public key.
- Is signed by a protocol authority.
- Includes metadata similar to Solana Pay fields (label, memo, and reference, etc.)
- Is resolved through a provided REST API or SDK.
- Is bound to a user’s wallet pubkey at creation or intent level.
- May include a registered prefix, allowing integration with branded or categorized systems. See [AIP-5](./aip-5.md) for details.
- Are currently generated via the official interface at [app.ota.codes](https://app.ota.codes), with future support moving to [useactio.codes](https://useactio.codes).

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