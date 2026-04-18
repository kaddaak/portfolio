# Orders, Receipts, and Table Operations

This is the operational layer where the register handles live orders across a site cluster, turns them into receipts, and keeps the work coherent even when multiple registers could try to act on the same order.

```mermaid
flowchart LR
  subgraph S["Order sources"]
    A["Local register orders"]
    B["Waiter orders"]
    C["Kiosk orders"]
  end

  B --> L["Claim / release locking"]
  C --> L

  A --> W["Shared working surface"]
  L --> W

  W --> X["Checkout"]
  X --> Y["Pending receipt"]
  Y --> Z["Issued receipt"]
  Y --> R["Recovery / delayed completion"]
  R --> Z
```

## Core Idea

- One surface lets the register work local orders, waiter orders, kiosk orders, and receipts without breaking the operator flow apart
- Orders from other channels are still coordinated at cluster level, so two registers do not silently work the same remote order at once
- Checkout is treated as a lifecycle, not a button click, which is why pending and issued receipts stay in the same operational view

## What It Covers

- Local table and standing orders on the register itself
- Claimed waiter and kiosk orders imported into the same working surface
- Pending receipts, issued receipts, storno, and payment correction
- Retry-backed receipt and order cleanup when work cannot finish immediately

## Why It Matters

This is what makes the register feel operationally powerful: one register can coordinate work across local service, external channels, and receipt issuance while the site cluster still stays consistent.
