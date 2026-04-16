# Provisioning and Fleet Operations

This is how a blank Raspberry Pi becomes a site-ready POS node, and how installed nodes are updated afterward without full reprovisioning.

```mermaid
flowchart TB
  subgraph P[Provisioning]
    A["Blank Raspberry Pi"] --> B["Flash Ubuntu<br/>and installer payload"]
    B --> C["Boot from SD"]
    C --> D["Clone to SSD"]
    D --> E["Run first-boot installer"]
    E --> F["Provision local runtime<br/>and device identity"]
  end

  F --> G["Provisioned site node"]

  subgraph O[Fleet Operations]
    G --> H["Operations sync"]
    G --> I["App updates and env patches"]
    G --> J["Backups and restore"]
    G --> K["Logs and diagnostics"]
  end
```

## What It Covers

- First-boot installation for a fresh Raspberry Pi
- SSD-based deployment instead of running production from the SD card
- Pinned local runtime setup for Spring, PostgreSQL, EMQX, NGINX, and TLS
- Per-device identity and secret generation during installation
- Site-scoped configuration for access keys, VPN identity, and tax certificates
- Batch operations over Tailscale for updates, patches, backups, restores, and logs

## Why It Matters

This work was about making on-site deployment repeatable, site-scoped, and operationally safe. Each Raspberry is provisioned as its own node with its own generated secrets and identity, so devices are not interchangeable across sites and compromise blast radius stays confined to a single hospitality location. Once installed, nodes can be targeted remotely, updated in batches, and operated through a controlled runner with locking, audit logging, and rollback-aware workflows.
