# Antonio Kadić

Zagreb, Croatia  
+385 99 820 0209  
kadic.antonio@gmail.com

## Title

Product and Systems Engineer

## Profile

Independent product and systems engineer building production-grade backend systems, desktop software, native integrations, and custom interaction architectures from concept through deployment.

## Experience

### Independent Product and Systems Engineer

Zagreb, Croatia  
July 2025 - Present

Designed and built a production-grade hospitality point-of-sale platform spanning backend architecture, desktop runtime, native workstation integration, and operator-facing product systems.

- Independently designed and built the backend architecture and major runtime contracts for a Raspberry Pi-orchestrated hospitality POS platform where LAN-connected desktop POS, waiter, and kiosk clients operate independently while coordinating shared workflows and operational state through local REST and MQTT communication, PostgreSQL state, cloud sync, fiscalization, and on-site operational tooling.
- Designed the custom interaction, UI, and UX architecture for the desktop POS, including gesture orchestration, an interactive grid-workspace system with draggable items, automatic displacement, and workspace navigation, venue floor-plan editing, and table-operations flows built specifically for touch-heavy hospitality use.
- Built a Tauri-based desktop workstation that combines React UI, Rust native runtime, SQLite persistence, secure LAN discovery, Windows printing, hardware integration, and production diagnostics tooling.
- Designed a versioned sync model with per-section cursors, initial hydrate, and incremental sync for data exchange between services.
- Implemented a ledger-based fiscal recovery pipeline for receipt issuance, invoice mutations, and tips, including replay, projection healing, conflict detection, and recovery-state handling.
- Built secure device bootstrap and two-level authentication separating machine identity from operator identity across desktop, kiosk, and waiter clients.
- Built operator-facing product systems for workspace management, venue floor-plan editing, and table operations, including worker-based rendering, collision-aware interactions, and merge logic.
- Implemented MQTT-backed real-time workflow coordination across a LAN-connected register cluster, including order claiming and TTL-based release, workstation dispatch, prep-station routing, register messaging, operator chat, peer visibility, and native Windows print delivery across the desktop-to-backend boundary.
- Designed diagnostics and remote-support flows that collect crash and log bundles from Windows workstations into a retained archive on the Raspberry Pi.
- Built `DataForgeAI`, an in-progress analytics prototype using Next.js, Spring Boot, Python, MQTT / EMQX, DuckDB, AWS S3, and Docker Compose to explore multi-service, chat-driven analytics workflows.
- Built `ProofKit`, an internal Linux evidence tool that generates cryptographically signed, RFC 3161-timestamped evidence bundles with Backblaze B2 publication receipts and Object Lock retention support.

### Developer

Stratus IT d.o.o. / NauSYS platform  
September 2021 - June 2025

Built production features, real-time communication systems, mobile client workflows, external integrations, and internal tools for a production yacht charter booking and back-office management platform.

- Designed REST services and external integrations for client and partner workflows.
- Built production features, refactors, and internal tools in a JSF / PrimeFaces application backed by Elasticsearch, Apache Ignite, and supporting platform services.
- Built an interactive survey creation tool and other operational workflows, working directly with clients, support, and product stakeholders on requirements and delivery.
- Implemented real-time chat flows between charter companies, agencies, clients, and owners, plus a multi-channel notification bus spanning Firebase Cloud Messaging, Firestore, MQTT, and email.
- Built a mobile-first web client for charter customers with booking information, check-in and check-out details, surveys, chat, and supporting trip workflows.
- Implemented a shared-worker MQTT client for real-time notifications and messaging in the web client, and built custom Google OAuth login flows for easier access.
- Improved backend performance and optimized production workflows across platform services.

## Selected Projects

### Hospitality POS Desktop Client

Custom-built desktop client for the hospitality POS platform, built with Tauri, Rust, React, and TypeScript around original interaction design, operator workflows, interactive workspace and floor-plan systems, secure LAN discovery, and native workstation integration.

### DataForgeAI

In-progress analytics prototype for chat-driven workflows where AI-issued commands orchestrate backend services and generated charts are saved to persistent dashboards.

### ProofKit

Internal Linux evidence tool for signed evidence bundle generation, RFC 3161 timestamp verification, publication receipts, and Object Lock retention support.

## Skills

### Architecture and Systems

- End-to-end product architecture
- Backend architecture
- UI, UX, and interaction architecture
- Multi-service architecture
- Distributed and local state coordination
- Sync protocols
- Messaging and event-driven flows
- Correctness-sensitive business logic
- Recovery and replay workflows
- Desktop client architecture and operator workflow design

### Backend and Platform

- Java
- Python
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
- OpenSSL / X.509
- Backblaze B2
- SOAP
- Raspberry Pi deployment
- NGINX
- Tailscale

### Frontend and Desktop

- Rust
- Tauri
- React
- Next.js
- TypeScript
- SQLite
- Web Workers
- OffscreenCanvas
- Windows printing
- Native desktop integration

### Additional Experience

- JSF / PrimeFaces
- Elasticsearch
- Apache Ignite
- Bash / Shell scripting

## Education

Technical School Ruder Boskovic  
Computer Technician  
Zagreb, Croatia  
September 2009 - May 2013

## Languages

- Croatian: native
- English: C1
