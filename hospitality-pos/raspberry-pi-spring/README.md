# Raspberry Pi (Spring)

This is the Raspberry Pi-hosted Spring side of the hospitality POS system, running as the local backend for a single restaurant site.

It coordinates the parts of the product that need to keep working on the LAN, persist state locally, integrate with external systems, and hold up under real operating conditions.

## Runtime Topology

```mermaid
flowchart LR
  subgraph LAN["Restaurant Site"]
    POS["POS Desktop"]
    WAITER["Waiter App"]
    KIOSK["Kiosk App"]
    NGINX["NGINX"]
    API["Spring Boot API"]
    DB[("PostgreSQL")]
    EMQX[("EMQX MQTT")]
  end

  SUPPORT["Remote Support (Tailscale)"]
  CLOUD["Cloud Platform"]
  TAX["Croatian Tax Authority"]

  POS --> NGINX
  WAITER --> NGINX
  KIOSK --> NGINX
  NGINX --> API
  API <--> DB
  API <--> EMQX
  SUPPORT --> NGINX
  API --> CLOUD
  API --> TAX
```

## Main Engineering Areas

- Local backend contracts across desktop POS, waiter, kiosk, and workstation flows
- Secure device bootstrap, device identity, and operator authentication
- Pull-based cloud sync plus sectioned local sync for desktop clients
- MQTT-backed real-time coordination for claims, dispatch, messaging, and health
- Correctness-sensitive receipt issuance, recovery, and Croatian tax authority integration
- Diagnostics collection, retention, and remote support retrieval
- Hardware discovery, workstation pairing, and routed print dispatch
- Raspberry Pi provisioning, pinned machine state, and post-install operations

## Stack and Deployment

- Java / Spring Boot
- PostgreSQL
- EMQX MQTT
- NGINX
- Tailscale
- Ubuntu Server on Raspberry Pi
- Provisioning and operations scripts for install, update, backup, restore, and logging

## What This Work Covers

- Backend architecture for a multi-client on-site system
- Real-time messaging and local coordination
- Sync and local-state ownership
- Operational deployment on a physical device
- Reliability-focused product engineering beyond the happy path
