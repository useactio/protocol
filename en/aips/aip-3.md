# AIP-3: Intent Resolution & Routing

- **Author**: Actio Core Team  
- **Status**: Final  
- **Created**: 2025-06-29

## Overview

This AIP defines how an action intent is resolved and routed to its appropriate target within the Actio Protocol. It ensures that the action linked to a code is correctly executed, whether it is signing, sending, or performing a protocol-defined task.

## Motivation

To standardize how action codes translate into executable instructions in the protocol backend or compatible clients, reducing ambiguity and ensuring compatibility across integrations.

## Specification

### Intent Resolution

Each code may include metadata fields at submission time (e.g. `label`, `message`, etc.) commonly aligned with Solana Pay tandards. These are attached by the submitter (e.g. merchant, dApp) and are not yet enforced or standardized by the protocol.

Currently, intents are interpreted in a flexible manner. The protocol does not yet enforce strict types like `pay`, `vote`, `mint`, etc. Instead, any valid Solana transaction can be used, and its meaning is inferred by the application or consumer.

Future versions may formalize intents via metadata and registered prefixes. See [AIP-5](./aip-5.md) for upcoming prefix-based routing and registry support.

### Routing

The protocol backend currently allows routing any Solana transaction submitted through the action code system. There is no dedicated per-intent handler yet. Actions are resolved generically and the result of execution (or signing) is recorded in the associated task state.

In the future, standardized routing based on metadata and prefix-level registration will be introduced.

## Notes

- This AIP supports future extensions with custom intent types.
- This system allows compatibility with universal checkout, dApps, wallets, and embedded flows.
- Intent metadata is encoded in the backend and referenced during task execution.
  
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