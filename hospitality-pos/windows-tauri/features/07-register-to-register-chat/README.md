# Register-to-Register Chat

Register-to-register chat is a live coordination surface built into the desktop POS, so people on different registers can communicate without leaving the register itself.

The Raspberry Pi mediates the whole flow. Registers publish chat actions into the local site runtime, the Raspberry validates them, and connected registers receive the resulting room events back over LAN MQTT.

<p align="center">
  <img src="./assets/chat.gif" alt="Register-to-register chat demo">
</p>

## Runtime Flow

```mermaid
flowchart LR
  A["Registers"] -->|new / edit / delete| B["Raspberry Pi chat mediator"]
  B -->|created / edited / deleted| C["Register chat rooms"]
  C --> D["Connected registers"]
```

## Core Idea

- Register chat is part of the site runtime, not a separate external tool
- The Raspberry stays in the middle so room traffic is coordinated in one place instead of register-to-register peer traffic
- The chat is intentionally live and non-persistent, optimized for in-service coordination rather than long-term message history

## How It Works

- Each register loads the active desktop peers from the Raspberry and derives one shared room plus direct register-to-register rooms
- Sending, editing, and deleting a message publishes a room command into local MQTT instead of doing client-to-client networking
- The Raspberry validates that the sender is an active desktop register and that the requested room is allowed before it republishes the resulting room event
- Registers keep room state locally with unread counts and online indicators, while safe mode leaves chat visible but disables composition

## What It Enables

- Fast coordination across the same hospitality site without leaving the register UI
- Broadcast communication to the full register cluster plus direct register-to-register conversations
- A built-in communication layer for situations where staff or managers need to notify other registers immediately during service

## Why It Matters

This bakes live coordination directly into the register. In busy venues, registers can help each other immediately and managers can push a message across the site without introducing a separate messaging product or breaking the operator flow.
