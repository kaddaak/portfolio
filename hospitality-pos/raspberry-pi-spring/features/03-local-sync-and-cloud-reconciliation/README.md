# Local Sync and Cloud Reconciliation

The Raspberry Pi hydrates from cloud once, reconciles incrementally after that, and serves local clients from one snapshot-bounded view of the site database.

```mermaid
flowchart TB
  Cloud["Cloud platform"]
  Hydrate["Initial cloud hydrate<br/>all sections must be ok"]
  Incremental["Incremental reconcile<br/>cloud cursors advance per section"]
  Local[("Local PostgreSQL")]
  Request["Trusted client asks for local sync"]
  Snapshot["Raspberry chooses one snapshotAt"]

  Cloud --> Hydrate --> Local
  Cloud --> Incremental --> Local
  Local --> Request --> Snapshot

  Snapshot --> C0
  Snapshot --> P0
  Snapshot --> M0
  Snapshot --> U0
  Snapshot --> D0

  subgraph S1["Cash Register"]
    C0["cursor: t1"] --> C1["read (t1, snapshotAt]"]
    C1 --> C2["status: ok"]
    C2 --> C3["next cursor = snapshotAt"]
  end

  subgraph S2["Products"]
    P0["cursor: t2"] --> P1["read (t2, snapshotAt]"]
    P1 --> P2["status: ok"]
    P2 --> P3["next cursor = snapshotAt"]
  end

  subgraph S3["Menus"]
    M0["cursor: t3"] --> M1["read (t3, snapshotAt]"]
    M1 --> M2["status: ok"]
    M2 --> M3["next cursor = snapshotAt"]
  end

  subgraph S4["Users"]
    U0["cursor: t4"] --> U1["version mismatch"]
    U1 --> U2["status: incompatible"]
    U2 --> U3["cursor unchanged"]
  end

  subgraph S5["Discounts"]
    D0["cursor: t5"] --> D1["section apply/read failure"]
    D1 --> D2["status: error"]
    D2 --> D3["cursor unchanged"]
  end
```

Legend

- `ok` advances that section to `snapshotAt`
- `incompatible` and `error` keep that section on its previous cursor

- Hydrate is all-or-nothing.
- Incremental cloud sync is per-section.
- Local sync is bounded by one `snapshotAt`.
- Only `ok` sections advance their cursor.

## What This Accomplishes

This keeps the site locally usable, lets failed sections recover cleanly without blocking the rest, and allows sync contracts to evolve section by section without corrupting client state or silently skipping data.
