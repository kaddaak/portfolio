# Antonio Kadić

Product Engineer  
Zagreb, Croatia  
kadic.antonio@gmail.com

Hi, I'm Antonio Kadić, a product and systems engineer based in Zagreb.

I take complex software from concept to production across backend systems, desktop applications, integrations, infrastructure, and product-facing software.

## What I Do

- Design and build software end to end across frontend, backend, desktop, integrations, and operations.
- Work across architecture, implementation, reliability, and product-facing behavior.
- Deliver software that holds up in operating conditions.

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

### [Raspberry Pi (Spring)](./hospitality-pos/raspberry-pi-spring/README.md)
<table>
  <tr>
    <th align="left" valign="top" width="33%">It coordinates</th>
    <th align="left" valign="top" width="33%">Main areas of work</th>
    <th align="left" valign="top" width="33%">Feature deep dives</th>
  </tr>
  <tr>
    <td valign="top" width="33%">
      - desktop POS clients
      <br>
      - waiter and kiosk clients
      <br>
      - PostgreSQL transactional state
      <br>
      - MQTT-based real-time workflow coordination
      <br>
      - cloud sync
      <br>
      - Croatian tax authority integration
      <br>
      - diagnostic intake and retained support bundles
      <br>
      - printer and workstation dispatch
    </td>
    <td valign="top" width="33%">
      - backend architecture and service contracts across multiple local clients
      <br>
      - secure device bootstrap and two-level authentication
      <br>
      - sectioned sync with cursors, initial hydration, and incremental updates
      <br>
      - correctness-sensitive receipt lifecycle and recovery workflows
      <br>
      - workstation dispatch and routing
      <br>
      - diagnostics and remote support flows
    </td>
    <td valign="top" width="33%">
      - <a href="./hospitality-pos/raspberry-pi-spring/features/01-provisioning-and-fleet-operations/README.md">Provisioning and fleet operations</a>
      <br>
      - <a href="./hospitality-pos/raspberry-pi-spring/features/02-device-bootstrap-and-auth/README.md">Device bootstrap and auth</a>
      <br>
      - <a href="./hospitality-pos/raspberry-pi-spring/features/03-local-sync-and-cloud-reconciliation/README.md">Local sync and cloud reconciliation</a>
      <br>
      - <a href="./hospitality-pos/raspberry-pi-spring/features/04-mqtt-coordination-and-lan-runtime/README.md">MQTT coordination and LAN runtime</a>
      <br>
      - <a href="./hospitality-pos/raspberry-pi-spring/features/05-tax-authority-integration-and-recovery/README.md">Tax authority integration and recovery</a>
      <br>
      - <a href="./hospitality-pos/raspberry-pi-spring/features/06-lan-printer-discovery-and-transport/README.md">Remote LAN printer discovery and transport</a>
    </td>
  </tr>
</table>

### [Windows (Tauri)](./hospitality-pos/windows-tauri/README.md)
<table>
  <tr>
    <th align="left" valign="top" width="33%">It combines</th>
    <th align="left" valign="top" width="33%">Main areas of work</th>
    <th align="left" valign="top" width="33%">Feature deep dives</th>
  </tr>
  <tr>
    <td valign="top" width="33%">
      - React UI
      <br>
      - Rust native runtime
      <br>
      - SQLite local persistence
      <br>
      - secure LAN discovery
      <br>
      - Windows device and driver integration
      <br>
      - hardware-facing system integration
      <br>
      - production diagnostics tooling
    </td>
    <td valign="top" width="33%">
      - interaction design for fast operator workflows
      <br>
      - interactive workspace grid systems
      <br>
      - venue floor plan editing
      <br>
      - table operations flows
      <br>
      - native device integration across the desktop-to-backend boundary
      <br>
      - tooling built for real-world edge cases
    </td>
    <td valign="top" width="33%">
      - <a href="./hospitality-pos/windows-tauri/features/01-raspberry-discovery-and-trusted-lan-routing/README.md">Raspberry discovery and trusted LAN routing</a>
      <br>
      - <a href="./hospitality-pos/windows-tauri/features/02-safe-mode-and-recovery-flows/README.md">Safe mode and recovery flows</a>
      <br>
      - <a href="./hospitality-pos/windows-tauri/features/03-gesture-orchestrator-and-touch-input/README.md">Gesture orchestrator and touch input</a>
      <br>
      - <a href="./hospitality-pos/windows-tauri/features/04-grid-workspace-system/README.md">Grid workspace system</a>
      <br>
      - <a href="./hospitality-pos/windows-tauri/features/05-floor-plan-editor/README.md">Floor plan editor</a>
      <br>
      - <a href="./hospitality-pos/windows-tauri/features/06-orders-receipts-and-table-operations/README.md">Orders, receipts, and table operations</a>
      <br>
      - <a href="./hospitality-pos/windows-tauri/features/07-register-to-register-chat/README.md">Register-to-register chat</a>
      <br>
      - <a href="./hospitality-pos/windows-tauri/features/08-theming-and-localization/README.md">Theming and localization</a>
    </td>
  </tr>
</table>

## Technologies

<table>
  <tr>
    <td valign="top" width="33%">
      <strong>Backend</strong>
      <br><br>
      <code>Java</code> <code>·</code> <code>Spring Boot</code> <code>·</code> <code>Spring Security</code>
      <br>
      <code>JPA (Hibernate, EclipseLink)</code>
      <br>
      <code>PostgreSQL</code> <code>·</code> <code>Elasticsearch</code>
      <br>
      <code>Apache Ignite</code>
      <br>
      <code>REST</code> <code>·</code> <code>SOAP</code>
      <br>
      <code>JWT</code>
      <br>
      <code>MQTT</code> <code>·</code> <code>EMQX</code>
    </td>
    <td valign="top" width="33%">
      <strong>Frontend and UI</strong>
      <br><br>
      <code>React</code> <code>·</code> <code>Next.js</code> <code>·</code> <code>TypeScript</code>
      <br>
      <code>JSF</code> <code>·</code> <code>PrimeFaces</code>
      <br>
      <code>Web Workers</code> <code>·</code> <code>OffscreenCanvas</code>
      <br>
      <code>UI</code> <code>·</code> <code>UX</code> <code>·</code> <code>interaction design</code>
    </td>
    <td valign="top" width="33%">
      <strong>Desktop and Operations</strong>
      <br><br>
      <code>Rust</code> <code>·</code> <code>Tauri</code>
      <br>
      <code>SQLite</code>
      <br>
      <code>Windows device integration</code>
      <br>
      <code>Docker</code> <code>·</code> <code>Docker Compose</code>
      <br>
      <code>NGINX</code> <code>·</code> <code>Tailscale</code>
      <br>
      <code>AWS S3</code> <code>·</code> <code>Backblaze B2</code>
      <br>
      <code>Raspberry Pi deployment and operations</code>
      <br>
      <code>Bash / shell scripting</code>
      <br>
      <code>Python</code>
      <br>
      <code>OpenSSL / X.509</code>
    </td>
  </tr>
</table>

## Other Relevant Work

These are brief project mentions rather than full case studies in this repository.

- **DataForgeAI**: A proof-of-concept analytics system using Next.js, Spring Boot, Python, MQTT / EMQX, DuckDB, AWS S3, and Docker Compose to explore chat-driven and multi-service analytics workflows.
- **ProofKit**: An internal Linux evidence tool for generating cryptographically signed evidence bundles with RFC 3161 timestamps, publication receipts, and immutable retention support.
