# Raspberry Discovery and Trusted LAN Routing

The desktop client resolves the Raspberry through a bounded set of sources, confirms identity with one simple contract, and keeps hostname-based TLS trust while routing traffic to the discovered LAN IP.

```mermaid
flowchart TB
  subgraph S["Candidate sources"]
    O["Override"]
    C["Cached IP"]
    H["DNS / mDNS"]
    L["Bounded LAN scan"]
  end

  O --> P
  C --> P
  H --> P
  L --> P
  
  subgraph I["Identity confirmation"]
    P["Probe with /discovery"]
  end

  P --> W["Confirmed Raspberry IP"]
  P --> M["Safe mode<br/>degraded local operation"]

  subgraph R["Trusted routing"]
    W --> T["Hostname TLS + SPKI pin"]
    T --> X["Route traffic to resolved IP"]
    X --> K["Cache the result"]
  end
```

## How It Works

- Ordered candidate sources: explicit override, cached IP, hostname resolution, then bounded LAN scan
- Each candidate must satisfy one identity contract: `GET /discovery` must return `204`
- The winning LAN IP is applied through a runtime DNS override instead of replacing the trusted hostname
- HTTPS keeps using the Raspberry hostname and pinned SPKI trust while traffic is routed to the discovered IP
- The resolved IP is cached for faster restarts on the same site network

## Why It Matters

This lets the desktop client survive DHCP changes, broken `.local` resolution, and site-network churn while keeping trusted transport and sparing operators from manual workstation reconfiguration.
