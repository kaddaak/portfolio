# Antonio Kadić

Product Engineer  
Zagreb, Croatia  
kadic.antonio@gmail.com

I build production software across backend systems, desktop applications, local infrastructure, and operator-facing workflows. My strongest work is a hospitality POS platform spanning a Raspberry Pi site node, a Windows Tauri register client, sync and recovery flows, tax-compliant receipt handling, and device coordination under real operating conditions.

## Hospitality POS System

I designed and built a production hospitality POS platform for real restaurant operations. It combines a Raspberry Pi site node, a Windows desktop register runtime, local and cloud sync, tax-compliant receipt handling, and device/workstation coordination.

<p align="center">
  <img src="./hospitality-pos/assets/intro.gif" alt="Hospitality POS platform overview demo">
</p>

Core elements:

- Raspberry Pi site node for local authority, persistence, trust, cloud reconciliation, and tax reporting
- Windows desktop runtime built with Tauri, Rust, React, TypeScript, and SQLite
- REST and MQTT coordination across POS, waiter, kiosk, printer, and workstation flows
- Offline-safe sync, recovery paths, diagnostics, and operator-facing workflows

### [Raspberry Pi (Spring)](./hospitality-pos/raspberry-pi-spring/README.md)
<table>
  <tr>
    <th align="left" valign="top" width="33%">Architecture scope</th>
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
    <th align="left" valign="top" width="33%">Runtime components</th>
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
      - <a href="./hospitality-pos/windows-tauri/features/06-orders-receipts-and-table-operations/README.md">Orders and receipt operations</a>
      <br>
      - <a href="./hospitality-pos/windows-tauri/features/07-register-to-register-chat/README.md">Register-to-register chat</a>
      <br>
      - <a href="./hospitality-pos/windows-tauri/features/08-theming-and-localization/README.md">Theming and localization</a>
    </td>
  </tr>
</table>

## Technologies

### Core backend and systems
`Java` · `Spring Boot` · `PostgreSQL` · `REST APIs` · `MQTT` · `EMQX`

### Desktop and UI
`Rust` · `Tauri` · `React` · `TypeScript` · `SQLite`

### Infrastructure and operations
`Docker` · `NGINX` · `Tailscale` · `Raspberry Pi` · `Bash`

## Other Relevant Work

Smaller projects with shorter writeups that highlight architectural thinking outside the POS system.

- **[DataForgeAI](./dataforge-ai/README.md)**: Analytics prototype for uploaded business data, chat-driven exploration, and generated charts, with backend-defined project scope and model access constrained to scoped jobs.
- **[ProofKit](./proofkit/README.md)**: Linux evidence pipeline for proving code authorship over time through signed, timestamped, immutably published repository snapshots.
