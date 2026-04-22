# Remote LAN Printer Discovery and Transport

The Raspberry Pi handles remote printer discovery and raw transport for printers elsewhere on the same site LAN. Desktop clients request remote printers from the Raspberry, which performs discovery and raw TCP 9100 transport on their behalf.

```mermaid
flowchart TD
  App["Desktop client"] -->|"request remote LAN printers"| API["Raspberry Pi API"]
  API --> Cache[("Discovery cache")]
  API -->|"live scan when needed"| Scan["Bounded LAN scan"]
  Scan --> Printer["Remote LAN printer"]
  API -->|"candidate printers"| App
  App -->|"send remote printer target + raw job"| API
  API -->|"TCP 9100 raw transport"| Printer
```

- Discovery is live and cache-backed.
- Scanning is bounded to the site LAN.
- The Raspberry handles raw printer transport at the site boundary.
- Clients choose the printer; the Raspberry handles raw transport and surfaces failures in one place.

## What This Accomplishes

This keeps remote printer discovery and raw transport at one site boundary, so clients can choose printers without each becoming its own LAN scanner and raw-socket transport client.
