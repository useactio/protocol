# AIP-4: Task System

- **Author**: Actio Core Team  
- **Status**: Final  
- **Created**: 2025-06-29

## Overview

This AIP defines the task-based processing system used to manage the lifecycle of one-time action codes. Each code maps to a task, which abstracts execution, retries, status polling, and final resolution.

## Motivation

To provide a scalable and consistent mechanism for processing action flows regardless of the type of transaction or intent. This also simplifies client-side SDK integration by unifying status handling under a common model.

## Specification

### Task Lifecycle

Each submitted action creates a new task:

- **Created**: The code was resolved, but no interaction has occurred yet.
- **Pending**: Awaiting user signature or confirmation.
- **Processing**: Action is being executed (e.g. transaction is being sent).
- **Completed**: The transaction or signature has been successfully processed.
- **Cancelled**: The user or system rejected or expired the task.

### Structure

Each task is identified internally by a unique task ID (ephemeral, not included in memo) and includes:

- Associated public key (`int`) the action is intended for
- Resolved code metadata (see [AIP-3](./aip-3.md))
- Final action result (transaction signature, signed message, or cancellation)
- Timestamps for audit and history

### Polling

Clients may use the SDK to call `submitAndWait`, which wraps the polling and resolves the task once complete. Alternatively, `submit` and `getTaskStatus(taskId)` can be used manually.

### Design Goals

- Keep internal task logic hidden from the memo or transaction
- Allow status tracking for any Solana-compatible action 
- Ensure forward compatibility with future multi-chain support

## Notes

- Tasks are implemented server-side via an internal job queue
- In the future, tasks may be inspectable on-chain through anchors such as signatures or logs.
- The task system complements, but does not replace, transaction resolution in clients.

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