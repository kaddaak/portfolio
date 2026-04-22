# Orders and Receipts

Orders from the register, waiter and kiosk apps can land in one register workflow. A register can keep working locally while shared order ownership and final receipt outcome remain under site authority.

<p align="center">
  <img src="./assets/orders-and-receipts.gif" alt="Orders and receipt operations demo">
</p>

## Runtime Flow

```mermaid
flowchart LR
  subgraph S["Order sources"]
    A["Local register orders"]
    B["Waiter orders"]
    C["Kiosk orders"]
  end

  B --> L["Claim / release coordination"]
  C --> L

  A --> W["Register working surface"]
  L --> W

  W --> X["Checkout"]
  X --> Y["Pending receipt"]
  Y --> Z["Issued receipt"]
  Y --> R["Recovery / delayed completion"]
  R --> Z
```

## Who Owns What

- The register owns the working surface, cart state, and in-progress edits.
- Waiter and kiosk orders become local only after claim and release coordination grants that claim.
- Receipt issuance becomes final only when the site-side receipt workflow records the final confirmed outcome.
- Recovery continues the same receipt lifecycle, so one sale stays on one receipt path.

## Why It Matters

This keeps two registers from working the same remote order and keeps a locally finished checkout aligned with the site's real receipt outcome.
