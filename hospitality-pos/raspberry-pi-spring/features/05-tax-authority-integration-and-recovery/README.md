# Tax Authority Integration and Recovery

This flow is built around one outcome: one real sale must end as one canonical receipt, even when reporting to the tax authority is delayed or uncertain.

```mermaid
flowchart TD
  A["Client submits receipt issue request"] --> B["Raspberry records the workflow in the ledger"]
  B --> C["Signed SOAP request is sent to the tax authority"]
  C --> D{"Delivery outcome"}

  D -->|Success| E["Durable final outcome is recorded"]
  E --> F["Receipt view is projected locally"]

  D -->|Safe retry| G["Retry the same receipt workflow"]
  G --> H["Same receipt data<br/>new outbound message id"]
  H --> C

  D -->|Outcome uncertain| I["Stop blind resend"]
  I --> J["Workflow is blocked until someone resolves it or explicitly tries again"]

  B --> K["If the receipt is accepted after the original issue moment,<br/>delivery is marked as delayed"]
```

- The receipt itself stays stable: receipt number, business time, taxes, total, and receipt signature do not change during recovery.
- Delivery attempts are allowed to change: each outbound send can use a new message id while still representing the same receipt.
- The ledger stores the request, the response, and the recovery state so the server can replay the latest durable outcome instead of guessing.
- If a failed send is known not to have reached the tax authority, the same receipt workflow can continue automatically.
- If the remote outcome is uncertain, the system stops blind resend, because the previous attempt might already have been accepted by the tax authority.
- The workflow is considered successful only after a durable reported outcome is recorded, not just because a local receipt row already exists.

## What This Work Covers

- Signed tax-authority exchange from the Raspberry node
- Durable request and response recording in the ledger
- Delayed-delivery handling for receipts accepted after the original issue moment
- Recovery rules that separate safe retry from unsafe retry
- Receipt projection and canonical read recovery after tax-authority acceptance succeeds

## What This Accomplishes

This keeps tax-authority reporting safe under retries, outages, and ambiguous transport failures without letting the same real-world sale be reported twice.
