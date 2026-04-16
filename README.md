# Antonio Kadić

Product and Systems Engineer  
Zagreb, Croatia  
kadic.antonio@gmail.com

Hi, I'm Antonio Kadić, a product and systems engineer based in Zagreb.

I take complex software from concept to production across backend systems, desktop applications, integrations, infrastructure, and product-facing software.

## What I Do

- Design systems and products end to end.
- Build backend services, desktop applications, integrations, and operational tooling.
- Work across architecture, implementation, reliability, and user-facing product behavior.
- Deliver software that holds up in operating conditions.

## How This Repository Is Organized

- `hospitality-pos/`
  The main project in this repository, with the system split into:
  - `raspberry-pi-spring/`
  - `windows-tauri/`
- `cv/`
  CV materials.

## Hospitality POS System

I designed and built it as an operational POS system spanning backend architecture, desktop runtime, native workstation integration, messaging, sync, tax-compliant receipt workflows, diagnostics, and operator-facing product flows.

The system includes:

- Raspberry Pi-hosted local backend and service coordination
- Spring-based backend services and system architecture
- Windows desktop application built with Tauri, Rust, React, and TypeScript
- PostgreSQL and SQLite data storage
- local REST and MQTT service communication
- cloud synchronization and tax-compliant receipt workflows
- device discovery, workstation coordination, and native device integration
- operator-facing software built for service workflows

### Raspberry Pi (Spring)

It coordinates:

- desktop POS clients
- waiter and kiosk clients
- PostgreSQL transactional state
- MQTT-based real-time workflow coordination
- cloud sync
- Croatian tax authority integration
- diagnostic intake and retained support bundles
- printer and workstation dispatch

Main areas of work:

- backend architecture and service contracts across multiple local clients
- secure device bootstrap and two-level authentication
- sectioned sync with cursors, initial hydration, and incremental updates
- correctness-sensitive receipt lifecycle and recovery workflows
- workstation dispatch and routing
- diagnostics and remote support flows

### Windows (Tauri)

It combines:

- React UI
- Rust native runtime
- SQLite local persistence
- secure LAN discovery
- Windows device and driver integration
- hardware-facing system integration
- production diagnostics tooling

Main areas of work:

- interaction design for fast operator workflows
- interactive workspace grid systems
- venue floor plan editing
- table operations flows
- native device integration across the desktop-to-backend boundary
- tooling built for real-world edge cases

## Technologies

### Backend and Platform

- Java
- Spring Boot
- Spring Security
- Spring Web
- JPA / Hibernate
- PostgreSQL
- DuckDB
- JWT
- MQTT / EMQX
- AWS S3
- Docker / Docker Compose
- SOAP
- NGINX
- Tailscale
- Raspberry Pi deployment

### Desktop and Frontend

- Rust
- Tauri
- React
- Next.js
- TypeScript
- SQLite
- Web Workers
- OffscreenCanvas
- Windows device and driver integration
- Native desktop integration

### Additional Tools and Systems

- Python
- OpenSSL / X.509
- Backblaze B2
- JSF / PrimeFaces
- Elasticsearch
- Apache Ignite
- Bash / Shell scripting

## Other Projects Worth Mentioning

### DataForgeAI

A proof-of-concept analytics project using Next.js, Spring Boot, Python, MQTT / EMQX, DuckDB, AWS S3, and Docker Compose to explore chat-driven and multi-service analytics workflows.

### ProofKit

An internal Linux evidence tool for generating cryptographically signed evidence bundles with RFC 3161 timestamps, publication receipts, and object-lock retention support.
